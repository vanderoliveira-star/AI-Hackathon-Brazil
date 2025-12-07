# 🏆 Desafio 02: Transformação Intermediária e Análise Exploratório no Microsoft Fabric (Camada Silver)

📖 Cenário
A Contoso busca **avaliar a qualidade de seus dados** antes de construir modelos preditivos.
Para isso, a equipe deve **transformar e analisar os dados** provenientes da camada **Bronze**, gerando uma versão intermediária otimizada na camada **Silver**.

---

### 🎯 Sua Missão
Para completar este desafio você deve:

✅ Criar uma **tabela Silver** a partir dos dados limpos em **Bronze**.
✅ Aplicar **transformações intermediárias** que melhorem a estrutura e consistência dos dados.
✅ Realizar uma **análise exploratória** usando técnicas de agrupamento e machine learning (ML).
✅ Deixar os dados prontos para a etapa de **modelagem semântica (Gold)**.

---

## 🚀 Passo 1: Criar a tabela Silver a partir da Bronze
💡 *Por quê?* A camada Silver serve como base para aplicar transformações e análises intermediárias, preparando os dados para modelagem analítica posterior.

1️⃣ Acesse o **Lakehouse** no seu workspace do Microsoft Fabric.
2️⃣ Use um **notebook** ou um **Dataflow Gen2** para ler os dados da camada **Bronze**.
3️⃣ Aplique uma limpeza adicional se necessário (por exemplo, correção de formatos ou padronização de nomes de colunas).
4️⃣ Salve os dados transformados em uma nova tabela na **camada Silver**.

✅ **Resultado esperado:** Os dados estão disponíveis em Silver e prontos para transformações mais avançadas.

---

## 🚀 Passo 2: Aplicar Transformações Intermediárias
💡 *Por quê?* Essas transformações geram vistas analíticas e facilitam modelagem e segmentação.

1️⃣ Abra seu **notebook do Fabric** e carregue a tabela Silver criada.
2️⃣ Aplique transformações que agreguem valor analítico, por exemplo:
   - 📊 **Agregações:** identificar o **score de crédito médio por cliente**.
   - 🏷️ **Perfis de produto:** classificar produtos por categoria ou nível de vendas.
3️⃣ Crie novas colunas ou métricas úteis para análises posteriores (por exemplo, média de compras ou níveis de risco).

✅ **Resultado esperado:** A tabela Silver contém transformações úteis e pronta para análise exploratória ou segmentação.

---

## 🚀 Passo 3: Realizar Análise Exploratória com ML
💡 *Por quê?* Técnicas de **Machine Learning (ML)** ajudam a avaliar distribuição e similaridade nos dados, descobrindo padrões.

1️⃣ Use **funções de ML integradas** ou bibliotecas PySpark MLlib / scikit-learn no seu notebook.
2️⃣ Implemente um algoritmo **K-Means** para agrupar registros em k clusters:
   - 🎯 Agrupar clientes ou produtos por características numéricas similares.
   - 🔍 Analisar relações entre variáveis dentro de cada cluster.

✅ **Resultado esperado:** Você obtém uma segmentação dos dados e melhor compreensão de seu comportamento.

---

## 🚀 Passo 4: Preparar a tabela para Modelagem Semântica (Camada Gold)
💡 *Por quê?* Preparar a tabela Silver é o passo final antes de criar modelos analíticos ou dashboards de negócio.

1️⃣ Ajuste nomes de colunas, tipos de dados e chaves primárias necessárias para modelagem.
2️⃣ Salve a versão final da tabela no **Lakehouse (Silver)** ou publique como fonte para a **camada Gold**.

✅ **Resultado esperado:** Os dados estão prontos para consumo na camada Gold por ferramentas de BI ou modelos de análise avançada.

---

## 🏁 Pontos de Verificação Final

✅ A tabela Silver foi criada corretamente a partir da Bronze?
✅ Transformações intermediárias (agregações, cálculos, perfis) foram aplicadas?
✅ Foi implementado e analisado um modelo K-Means ou técnica ML similar?
✅ Os dados estão prontos para uso na camada Gold?
✅ As transformações e resultados do análise exploratória foram documentados?

---

## 📝 Documentação

- [Notebook de Transformações e ML](https://learn.microsoft.com/es-es/fabric/data-engineering/how-to-use-notebook)

💡 *Dica:* Mantenha registro dos parâmetros e resultados dos modelos — serão importantes para o próximo desafio: **modelagem e curadoria na camada Gold**. 🚀