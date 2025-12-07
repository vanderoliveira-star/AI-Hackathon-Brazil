# 🏆 Desafio 01: Ingestão de Dados do Cosmos DB para Microsoft Fabric (Camada Bronze) + Limpeza Básica

📖 Cenário
A Contoso precisa consolidar seus **dados operacionais** no **Microsoft Fabric**.
A equipe de dados deve realizar a **ingestão a partir do Azure Cosmos DB** para a camada **Bronze** e aplicar uma **limpeza inicial** para preparar os dados antes de avançar às próximas fases de transformação.

---

### 🎯 Sua Missão
Ao concluir este desafio você deverá ser capaz de:

✅ Ingerir dados do **Azure Cosmos DB** para o **Microsoft Fabric** usando **Dataflows Gen2**.
✅ Aplicar uma **limpeza básica** que inclua:
- Tratamento de valores nulos ou vazios.
- Eliminação de colunas desnecessárias.
- Normalização de formatos básicos (datas, texto, etc.).
✅ Gerar uma tabela limpa dentro da camada **Bronze** do Lakehouse.

---

## 🚀 Passo 1: Criar um Dataflow Gen2 para a Ingestão a partir do Cosmos DB
💡 *Por quê?* Os **Dataflows Gen2** permitem realizar ingestão e transformação inicial sem código, conectando facilmente fontes externas como o Cosmos DB ao seu Lakehouse.

1️⃣ No **Microsoft Fabric**, crie um novo **Dataflow Gen2** dentro do seu workspace.
🔹 Selecione **Azure Cosmos DB** como fonte de dados.
🔹 Insira as credenciais de conexão (endpoint e chave de acesso).
🔹 Conecte-se ao contêiner que contém os dados de **vendas** ou **finanças**.
🔹 Defina como destino seu **Lakehouse (Bronze)** para armazenar os dados ingeridos.

✅ **Resultado esperado:** Os dados JSON do Cosmos DB estão armazenados na camada Bronze do Lakehouse.

---

## 🚀 Passo 2: Validar a Carga e a Estrutura dos Dados
💡 *Por quê?* Validar a ingestão garante que os dados estejam completos e consistentes antes de iniciar a limpeza.

1️⃣ Acesse seu **Lakehouse** a partir do Dataflow ou do painel do Fabric.
🔹 Verifique se as tabelas ou arquivos criados contêm os campos esperados.
🔹 Confirme que não há erros de formato ou registros incompletos.

✅ **Resultado esperado:** A estrutura básica dos dados foi validada corretamente.

---

## 🚀 Passo 3: Aplicar Limpeza Básica no Dataflow Gen2
💡 *Por quê?* Esse passo melhora a qualidade dos dados, garantindo consistência e usabilidade para análises posteriores.

1️⃣ Edite seu **Dataflow Gen2** para adicionar passos de transformação:
   - 🧹 **Eliminar colunas desnecessárias** que não agreguem valor analítico.
   - 🩹 **Substituir ou remover valores nulos ou vazios.**
   - 🕒 **Normalizar formatos básicos** (por exemplo, campos de data ou texto em minúsculas).
2️⃣ Salve e execute o Dataflow para aplicar as transformações.
3️⃣ Publique os resultados na **camada Bronze** do seu Lakehouse.

✅ **Resultado esperado:** A tabela “Bronze” contém dados limpos, estruturados e prontos para transformação na camada Silver.

---

## 🏁 Pontos de Verificação Final

✅ A ingestão a partir do Cosmos DB via Dataflows Gen2 foi concluída?
✅ As transformações básicas foram aplicadas corretamente?
✅ Os dados resultantes estão armazenados e acessíveis na camada Bronze?
✅ Os passos realizados e evidências visuais foram documentados?

---

## 📝 Documentação

- [Criação Dataflow Gen2](https://learn.microsoft.com/es-mx/fabric/data-factory/create-first-dataflow-gen2)
