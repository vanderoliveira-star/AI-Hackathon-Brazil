# Solução do Desafio 01 — Ingestão do Cosmos DB para Microsoft Fabric (Camada Bronze) + Limpeza Básica

Guia passo a passo para ingerir dados do Azure Cosmos DB para a camada Bronze da Lakehouse no Microsoft Fabric, aplicar limpeza inicial e validar o resultado.

## Objetivo
- Ingerir dados do Cosmos DB usando Dataflow Gen2 ou pipeline e aplicar transformações básicas (nulos, colunas, formatos).

## Requisitos prévios
- Conexão ao Cosmos DB a partir do Fabric (ver `00-Solution.md`).

## Passos

### 1 — Criar Dataflow Gen2

1. No Fabric: Data → New → Dataflow Gen2.
2. Selecione **Azure Cosmos DB** como fonte.
3. Preencha endpoint e key (ou selecione a conexão já criada).
4. Selecione a coleção/contêiner que contém `products` ou `creditScore`.

### 2 — Projetar transformações básicas

Dentro do designer do Dataflow:
- Elimine colunas não necessárias.
- Normalize formatos: converter datas, strings (trim, lower), normalizar decimais.
  ![exemplo formato datas](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Ejemplo%20transformacion%20fechas.png)
  
- Substitua ou marque valores nulos (por exemplo, `unknown` ou valores padrão).
   ![valores vazios](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Ejemplo%20transformacion%202.png)
- Filtre registros corrompidos ou incompletos (se aplicável).
  
Dica: adicione passos de validação intermediários e use amostras pequenas para testar transformações.

### 3 — Destino: Lakehouse Bronze

1. Configure o sink/destino como a Lakehouse `Contoso_Lakehouse` → esquema/tabela `bronze.sales`.
   ![Salvar em tabela bronze](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Guardar%20bronze%201.png)

   ![Salvar como tabela nova](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Guardar%20bronze%202.png)

3. Execute o Dataflow em modo de teste e depois em produção.

### 4 — Verificar e documentar

1. Abra a Lakehouse e verifique `bronze.sales`.
2. Verifique contagem de registros, colunas esperadas e formatos de coluna (datas, numéricos).
3. Registre a execução (logs) e capture evidências visuais.

## Validações chave
- Contagem total vs origem no Cosmos DB.
- Não há colunas removidas acidentalmente.
- Nulos tratados e formatos normalizados.

## Próximos passos sugeridos
- Automatizar com um pipeline (agendamento) para ingestões periódicas.
- Implementar testes de qualidade de dados (Data Quality checks) antes do movimento para Silver.
