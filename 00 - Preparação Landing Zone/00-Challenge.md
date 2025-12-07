# 🏆 Desafio 00: Configuração da Zona de Aterrissagem e Preparação de Dados no Microsoft Fabric  
📖 Cenário  
A Contoso Retail carregou dois conjuntos de dados em formato **JSON**:  
- Um **financeiro**, com informações de **score de crédito**.  
- Outro de **retail**, com dados de **vendas e produtos**.  

Sua missão é **preparar o ambiente de trabalho no Microsoft Fabric**, conectando os dados armazenados no **Azure Cosmos DB** e estabelecendo uma **zona de aterrissagem (landing zone)** estruturada em camadas para iniciar o processo de transformação.

---

### 🎯 Sua Missão  
Ao completar este desafio você deverá ser capaz de:

✅ Criar Cosmos DB (NoSQL) e carregar os arquivos nos contêineres.
✅ Configurar um **workspace** no Microsoft Fabric para gestão dos dados.
✅ Conectar **Azure Cosmos DB** como fonte de dados.
✅ Explorar e compreender a estrutura dos arquivos JSON financeiros e de retail.
✅ Criar uma **Lakehouse** com estrutura por camadas (**Bronze**, **Silver**, **Gold**).
✅ Definir e documentar o fluxo de dados entre as camadas.

---
## 🚀 Passo 1: Criar Azure Cosmos DB (NoSQL)
💡 *Por quê?* O Cosmos DB será a fonte dos dados que serão ingeridos a partir do Fabric

1️⃣ Acesse o portal do **Microsoft Azure** e crie uma conta Azure Cosmos DB para NoSQL.  
🔹 Atribua um nome descritivo (por exemplo, `ContosoData-Source`).  
🔹 Crie o contêiner e defina um nome identificável.  
🔹 Faça o upload do dataset em formato JSON.

✅ **Resultado esperado:** Você terá um Cosmos DB com um contêiner contendo as informações prontas para ingestão no Fabric.

## 🚀 Passo 2: Criar um Workspace no Microsoft Fabric
💡 *Por quê?* O workspace é o ambiente central onde se gerenciam datasets, dataflows, pipelines e notebooks.

1️⃣ Acesse o **Microsoft Fabric** e crie um novo workspace para o projeto Contoso.  
🔹 Atribua um nome descritivo (por exemplo, `ContosoData-Fabric`).  
🔹 Garanta que esteja associado a uma **Fabric Capacity** (se já estiver configurada, você pode pular este passo).

✅ **Resultado esperado:** Você terá um workspace dedicado para os recursos do Fabric.

---

## 🚀 Passo 3: Conectar ao Azure Cosmos DB
💡 *Por quê?* Estabelecer esta conexão permite que o Fabric acesse e ingira diretamente os dados JSON do Cosmos DB.

1️⃣ No seu workspace do Fabric, crie uma nova **conexão de dados** para o **Azure Cosmos DB**.  
🔹 Forneça o **endpoint** e a **chave de acesso** corretos.  
🔹 Verifique se as permissões estão configuradas adequadamente.

✅ **Resultado esperado:** Seu workspace estará conectado ao Cosmos DB e pronto para ingestão de dados.

---

## 🚀 Passo 4: Criar uma Lakehouse e Definir a Estrutura de Camadas
💡 *Por quê?* A Lakehouse é a base da arquitetura de dados e permite separar as etapas de processamento.

1️⃣ No Fabric, crie uma **Lakehouse** chamada `Contoso_Lakehouse`.
2️⃣ Dentro da Lakehouse, defina a seguinte estrutura de pastas:
   - 🥉 **Bronze:** Dados brutos e não processados, ingeridos diretamente do Cosmos DB.
   - 🥈 **Silver:** Dados limpos, normalizados e consistentes.
   - 🥇 **Gold:** Dados curados e prontos para análise ou visualização.

✅ **Melhor prática:** Mantenha uma convenção clara de nomes para pastas e tabelas que facilite o acompanhamento do fluxo de dados.

✅ **Resultado esperado:** Sua Lakehouse terá uma estrutura organizada que suportará as transformações e análises.

---

## 🏁 Pontos de Verificação Final

✅ O Cosmos DB e os contêineres foram criados corretamente?
✅ O workspace do Microsoft Fabric foi criado e está conectado ao Cosmos DB?
✅ A estrutura dos datasets JSON em Cosmos foi validada?
✅ A Lakehouse está organizada com as camadas Bronze, Silver e Gold?
✅ A estratégia de fluxo de dados entre as camadas foi documentada?

---

💡 **Próximos Passos:**
Com a **zona de aterrissagem configurada**, você está pronto para avançar ao próximo desafio, onde começará a **ingestão, limpeza e transformação de dados** dentro do Fabric. 🚀

---

**📄 Documentação**
- [Criação Cosmos DB](https://learn.microsoft.com/es-es/azure/cosmos-db/nosql/quickstart-portal)
- [Permitir IP público no Firewall](https://learn.microsoft.com/en-us/azure/devops/organizations/security/allow-list-ip-url?view=azure-devops&tabs=IP-V4)
- [Criação Workspace no Fabric](https://learn.microsoft.com/es-es/fabric/data-warehouse/tutorial-create-workspace)
- [Criação de Lakehouse no Fabric](https://learn.microsoft.com/es-es/fabric/data-engineering/tutorial-build-lakehouse)
- [Criar Pipeline](https://learn.microsoft.com/es-mx/fabric/data-factory/create-first-pipeline-with-sample-data)
