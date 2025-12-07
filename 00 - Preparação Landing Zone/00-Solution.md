# Solução do Desafio 00 — Preparação da Landing Zone e Conexão de Dados (Microsoft Fabric)

Este documento descreve, passo a passo, como completar o *Desafio 00*: criar a zona de aterrissagem (landing zone) no Microsoft Fabric, provisionar o Azure Cosmos DB com os JSON fornecidos e conectar as duas plataformas.

## Objetivos
- Provisionar Azure Cosmos DB (NoSQL) e carregar os datasets JSON.
- Criar um workspace e uma Lakehouse no Microsoft Fabric com a estrutura Bronze / Silver / Gold.
- Conectar o Fabric ao Cosmos DB e verificar a ingestão inicial.

## Requisitos prévios
- Permissões para criar recursos no Azure.
- Arquivos JSON (por exemplo `creditScore.json`, `products.json`).

## Resultado esperado
- Cosmos DB com contêineres que contenham os JSON.
- Workspace no Fabric conectado a uma Capacity.
- Lakehouse `Contoso_Lakehouse` com pastas ou tabelas: `bronze`, `silver`, `gold`.

---

## 1. Criar Azure Cosmos DB (NoSQL)

1. Acesse o portal do Azure.
2. Procure **Azure Cosmos DB** → Criar → selecione a API **NoSQL**.
3. Preencha: resource group, account name (`contoso-cosmosdb`), região.

![Criar Cosmos](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Creando%20Cosmos%20-%20Basics.png)

![Review](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Creando%20Cosmos%20-%20Review.png)

4. Crie a conta. No *Data Explorer* crie o banco de dados e os contêineres (por exemplo `sales`, `credit`).
![Data Explorer](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/2%20-Data%20Explorer.png)

![New item](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/2%20-Upload%20Item.png)

5. Faça upload dos arquivos JSON (manualmente via Data Explorer ou usando Azure Data Factory para cargas repetíveis).
![Upload Json](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/2%20-Upload%20json.png)

**Verificação**
- No *Data Explorer* é possível visualizar documentos JSON no contêiner.

---

## 2. Criar Workspace no Microsoft Fabric

1. Abra o Microsoft Fabric e crie um workspace chamado `ContosoData-Fabric`.
2. Associe uma Fabric Capacity (se sua organização a possuir).

**Verificação**
- O workspace aparece na lista e você tem as permissões adequadas.

---

## 3. Criar Lakehouse e definir camadas

1. No workspace, crie uma Lakehouse `Contoso_Lakehouse`.
2. Dentro, crie pastas ou tabelas com a convenção:
	- `bronze.*` para dados brutos
	- `silver.*` para dados limpos
	- `gold.*` para dados curados/consumo

**Verificação**
- As pastas/tabelas estão visíveis no navegador da Lakehouse.

---

## 4. Conectar o Fabric ao Azure Cosmos DB

1. Criar novo item.
2. No DataFlow Gen2 do Fabric → New → Connection → Azure Cosmos DB.
![Criar Conexão](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Crear%20Dataflow%201.png)

![Buscar conector Cosmos](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Crear%20Dataflow%202.png)

![Buscar Conector 2](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Crear%20Dataflow%203.png)

3. Forneça o endpoint e a chave (Azure Portal → Cosmos DB → Keys).
![Conectar cosmos](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Connect%20Data%20source.png)

4. Teste e salve a conexão.

**Verificação**
- A conexão foi testada e você pode ver os containers/collections disponíveis.

---
