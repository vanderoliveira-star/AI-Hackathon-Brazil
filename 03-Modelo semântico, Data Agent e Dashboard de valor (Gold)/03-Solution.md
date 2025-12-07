# Solução do Desafio 03 — Modelo Semântico, Data Agent e Dashboard de Valor (Camada Gold)

## Objetivo
Construir um ecossistema analítico completo no Microsoft Fabric que permita:
- Criar um modelo semântico Gold com dados curados
- Habilitar consultas em linguagem natural via Data Agent
- Desenhar visualizações efetivas em Power BI

## Requisitos prévios
- Tabelas Silver com dados limpos e transformados
- Workspace no Microsoft Fabric com permissões adequadas
- Power BI Desktop instalado (opcional; pode usar Fabric web)

## 1. Preparar tabelas Gold e relacionamentos

### Exemplo: Score Creditício
```python
from pyspark.sql.functions import col
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.clustering import KMeans

# Carregar tabela Silver (já limpa)
df_fin = spark.read.table("silver_financiero")

# Normalizar score
score_min = df_fin.agg({"score": "min"}).collect()[0][0]
score_max = df_fin.agg({"score": "max"}).collect()[0][0]
df_fin = df_fin.withColumn("score_normalizado", (col("score") - score_min) / (score_max - score_min))

# ML: clustering por score
features_fin = VectorAssembler(inputCols=["score_normalizado"], outputCol="features")
df_fin_vec = features_fin.transform(df_fin)

kmeans = KMeans(k=3, seed=42)
model_fin = kmeans.fit(df_fin_vec)
df_fin_clustered = model_fin.transform(df_fin_vec)

# Selecionar clientes do cluster com maior média de score
top_cluster = df_fin_clustered.groupBy("prediction").avg("score_normalizado").orderBy("avg(score_normalizado)", ascending=False).first()[0]
df_gold_fin = df_fin_clustered.filter(col("prediction") == top_cluster)

# Salvar em Gold
df_gold_fin.write.mode("overwrite").saveAsTable("gold_financiero")
```

### Exemplo: Retail (produtos)
```python
from pyspark.sql.functions import col, when, udf
from pyspark.sql.types import StringType
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.clustering import KMeans

# Carregar tabela Silver
df_retail = spark.read.table("productos_silver")

# Derivar valor comercial
df_retail = df_retail.withColumn("valor_comercial", col("Price") * col("Stock"))

# Derivar disponibilidade_binaria
df_retail = df_retail.withColumn("disponible", when(col("Availability") == "InStock", 1).otherwise(0))

# Filtrar registros válidos
 df_retail_clean = df_retail.filter(col("valor_comercial").isNotNull() & col("disponible").isNotNull())

# Vectorizar e aplicar KMeans
assembler = VectorAssembler(inputCols=["valor_comercial", "disponible"], outputCol="features")
df_retail_vec = assembler.transform(df_retail_clean)

kmeans = KMeans(k=3, seed=42)
model_retail = kmeans.fit(df_retail_vec)
df_retail_clustered = model_retail.transform(df_retail_vec)

# Etiquetar produtos e promover para Gold
cluster_scores = df_retail_clustered.groupBy("prediction").avg("valor_comercial").orderBy("avg(valor_comercial)", ascending=False).collect()
cluster_map = {}
for i, row in enumerate(cluster_scores):
    cluster_map[row["prediction"]] = ["Valioso", "Médio", "Baixo"][i]

def map_cluster(pred):
    return cluster_map.get(pred, "Desconhecido")

map_udf = udf(map_cluster, StringType())
df_segmentado = df_retail_clustered.withColumn("perfil_produto", map_udf(col("prediction")))

# Filtrar produtos valiosos e disponíveis
 df_gold_retail = df_segmentado.filter((col("perfil_produto") == "Valioso") & (col("disponible") == 1))

# Salvar em Gold
df_gold_retail.write.option("mergeSchema", "true").mode("overwrite").saveAsTable("productos_gold")
```

## 2. Projetar Modelo Semântico

### 2.1 Definir relações
No Power BI ou Fabric, estabelecer:
- `fact_sales[productID]` → `dim_products[productID]` (muitos para um)
- `fact_sales[customerID]` → `dim_credit_scores[customerID]` (muitos para um)

### 2.2 Medidas DAX exemplares
```dax
Valor_Comercial_Total = SUM(fact_sales[valor_comercial])

Produtos_Disponiveis = 
CALCULATE(
    COUNTROWS(dim_products),
    dim_products[availability] = "In Stock"
)

Score_Promedio = AVERAGE(dim_credit_scores[score_normalizado])

Tasa_Devolucion = 
DIVIDE(
    CALCULATE(COUNTROWS(fact_sales), fact_sales[is_returned] = TRUE),
    COUNTROWS(fact_sales)
)
```

## 3. Configurar Data Agent

1. Em Fabric → New → Data Agent
2. Nome: "Contoso_Retail_Agent"
3. Conectar ao modelo semântico Gold
4. Incluir perguntas frequentes (FAQ) para validação

## 4. Criar Dashboard no Power BI

- Páginas sugeridas: Visão Geral Financeira, Análise de Vendas, Produtos e Estoque
- Visualizações: KPI, gráficos de barras, treemap, linha temporal, tabelas

## 5. Checklist de validação
- Todas as relações estão em modo single (não bidirecional)
- Medidas DAX retornam valores esperados
- Data Agent responde corretamente
- Dashboard atualiza com novos dados
- Permissões atribuídas corretamente

## Referências
- [Modelos semânticos em Fabric](https://learn.microsoft.com/fabric/data-warehouse/semantic-models)
- [Power BI DAX Reference](https://learn.microsoft.com/dax/)
