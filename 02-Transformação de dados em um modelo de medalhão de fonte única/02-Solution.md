# **Desafio 02 – Transformação intermediária e análise exploratória (Silver) 🔧📊**

## **Objetivo e solução passo a passo 🧭**

### **Objetivo 🎯**
Transformar os dados Bronze e realizar análise exploratória em Silver.

---

## **Solução passo a passo 🪜**

### **Conjunto de score de crédito e conjunto de produtos 🧩**

- Criar novo Dataflow Gen2
- Configurar a origem na tabela Bronze.
- Aplicar transformações intermediárias
- Criar coluna de score estimado
- Segmentar clientes por perfil de crédito
- Identificar o cluster com maior média de score
- Filtrar os clientes pertencentes a esse cluster
- Resultado: subconjunto de clientes com perfil de crédito alto

---

# **Segmentação de clientes por score creditício 🧮**

Importar funções necessárias

```python
from pyspark.sql.functions import col, when, udf
from pyspark.sql.types import StringType
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.clustering import KMeans
```


## **Carregar tabela Silver com dados financeiros 🧾**

```python
df_fin = spark.read.table("creditScore_silver")
```

---

## **Derivar coluna score_estimado baseada em comportamento de pagamento e uso de crédito 💳**

```python
df_fin = df_fin.withColumn("score_estimado",
    when(col("Payment_Behaviour") == "High_spent_Small_value_payments", 650)
    .when(col("Payment_Behaviour") == "Low_spent_Large_value_payments", 750)
    .when(col("Payment_Behaviour") == "High_spent_Large_value_payments", 800)
    .when(col("Payment_Behaviour") == "Low_spent_Small_value_payments", 600)
    .otherwise(620)
)
```

---

## **Penalização por pagamentos em atraso ⏰**

```python
df_fin = df_fin.withColumn("score_estimado",
    col("score_estimado") - (col("Num_of_Delayed_Payment") * 5)
)
```

---

## **Penalização por alto uso de crédito 📉**

```python
df_fin = df_fin.withColumn("score_estimado",
    when(col("Credit_Utilization_Ratio") > 0.8, col("score_estimado") - 20)
    .otherwise(col("score_estimado"))
)
```

---

## **Limitar score entre 300 e 850 ⚙️**

```python
df_fin = df_fin.withColumn("score_estimado",
    when(col("score_estimado") < 300, 300)
    .when(col("score_estimado") > 850, 850)
    .otherwise(col("score_estimado"))
)
```

---

## **Filtrar registros válidos para clustering 🧹**

```python
df_fin_clean = df_fin.filter(col("score_estimado").isNotNull())
```

---

## **Vectorizar coluna score_estimado para ML 🤖**

```python
assembler = VectorAssembler(inputCols=["score_estimado"], outputCol="features")
df_fin_vec = assembler.transform(df_fin_clean)
```

---

## **Aplicar KMeans clustering para segmentar clientes 🧠**

```python
kmeans = KMeans(k=3, seed=42)
model_fin = kmeans.fit(df_fin_vec)
df_fin_clustered = model_fin.transform(df_fin_vec)
```

---

## **Etiquetar perfis creditícios conforme média de score por cluster 🏷️**

```python
cluster_scores = df_fin_clustered.groupBy("prediction") \
    .avg("score_estimado") \
    .orderBy("avg(score_estimado)", ascending=False) \
    .collect()
```

---

## **Criar mapa de etiquetas: Alto, Médio, Baixo 🗺️**

```python
cluster_map = {}
for i, row in enumerate(cluster_scores):
    cluster_map[row["prediction"]] = ["Alto", "Médio", "Baixo"][i]
```

---

## **UDF para atribuir etiqueta ⚡**

```python
def map_cluster(pred):
    return cluster_map.get(pred, "Desconhecido")

map_udf = udf(map_cluster, StringType())
df_segmentado = df_fin_clustered.withColumn("perfil_crediticio", map_udf(col("prediction")))
```

---

## **Contar clientes por perfil (opcional para validação) 📊**

```python
df_segmentado.groupBy("perfil_crediticio").count().orderBy("count", ascending=False).show()
```

---

## **Filtrar clientes com perfil Alto 🥇**

```python
df_gold_fin = df_segmentado.filter(col("perfil_crediticio") == "Alto")
```

---

## **Salvar tabela Gold com clientes de melhor perfil creditício 💾**

```python
df_gold_fin.write.option("mergeSchema", "true").mode("overwrite").saveAsTable("creditScore_gold")
```

---




# **Segmentação ML + Promoção a Gold (Retail por produto) 🛍️🤖**

---

## **📌 Importar funções necessárias**

```python
from pyspark.sql.functions import col, when, udf
from pyspark.sql.types import StringType
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.clustering import KMeans
```

---

## **Carregar tabela Silver com catálogo de produtos retail 🧾**

```python
df_retail = spark.read.table("productos_silver")
```

---

## **🧮 Derivar coluna valor_comercial = Price × Stock**

```python
df_retail = df_retail.withColumn("valor_comercial", col("Price") * col("Stock"))
```

---

## **🧮 Derivar coluna disponibilidade_binaria**

```python
df_retail = df_retail.withColumn("disponible",
    when(col("Availability") == "InStock", 1).otherwise(0)
)
```

---

## **🧹 Filtrar registros válidos para clustering**

```python
df_retail_clean = df_retail.filter(
    col("valor_comercial").isNotNull() & col("disponible").isNotNull()
)
```

---

## **📊 Vectorizar colunas para ML**

```python
assembler = VectorAssembler(inputCols=["valor_comercial", "disponible"], outputCol="features")
df_retail_vec = assembler.transform(df_retail_clean)
```

---

## **🤖 Aplicar KMeans clustering para segmentar produtos**

```python
kmeans = KMeans(k=3, seed=42)
model_retail = kmeans.fit(df_retail_vec)
df_retail_clustered = model_retail.transform(df_retail_vec)
```

---

## **🏷️ Etiquetar produtos conforme valor comercial médio por cluster**

```python
cluster_scores = df_retail_clustered.groupBy("prediction") \
    .avg("valor_comercial") \
    .orderBy("avg(valor_comercial)", ascending=False) \
    .collect()
```

---

## **Criar mapa de etiquetas: Valioso, Médio, Baixo 🗺️**

```python
cluster_map = {}
for i, row in enumerate(cluster_scores):
    cluster_map[row["prediction"]] = ["Valioso", "Médio", "Baixo"][i]
```

---

## **UDF para atribuir etiqueta ⚡**

```python
def map_cluster(pred):
    return cluster_map.get(pred, "Desconhecido")

map_udf = udf(map_cluster, StringType())
df_segmentado = df_retail_clustered.withColumn("perfil_produto", map_udf(col("prediction")))
```

---

## **🔍 Contagem por perfil (opcional para validação)**

```python
df_segmentado.groupBy("perfil_produto").count().orderBy("count", ascending=False).show()
```

---

## **🥇 Filtrar produtos valiosos e disponíveis**

```python
df_gold_retail = df_segmentado.filter(
    (col("perfil_produto") == "Valioso") & (col("disponible") == 1)
)
```

---

## **💾 Salvar tabela Gold com produtos valiosos**

```python
df_gold_retail.write.option("mergeSchema", "true").mode("overwrite").saveAsTable("productos_gold")
```
