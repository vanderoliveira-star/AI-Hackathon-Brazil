# 🏆 Desafio 03: Modelo Semântico, Data Agent e Dashboard de Valor no Microsoft Fabric (Camada Gold)

📖 Cenário
A Contoso busca **habilitar análises de negócio sobre dados confiáveis**.
A equipe de dados deve construir um **modelo semântico**, criar um **Data Agent conectado ao modelo** e desenhar um **dashboard de valor** no Power BI que responda às perguntas-chave do negócio.

---

### 🎯 Sua Missão
Ao concluir este desafio você deverá ser capaz de:

✅ Desenhar um **modelo semântico** na camada **Gold** com medidas e dimensões relevantes.
✅ Criar um **Data Agent** no Microsoft Fabric conectado a esse modelo.
✅ Construir um **dashboard interativo em Power BI** com visualizações de valor.
✅ Validar que o modelo responda corretamente a perguntas de negócio via Copilot ou Power BI.

---

## 🚀 Passo 1: Criar a Tabela Gold com Agregações e Relações Chave
💡 *Por quê?* A camada **Gold** contém dados curados e prontos para análise, onde se aplicam as agregações finais.

1️⃣ No workspace do **Microsoft Fabric**, crie uma **tabela Gold** baseada nas tabelas da camada Silver.
2️⃣ Aplique **agregações** e defina **relações chave** entre tabelas por `productID`.
3️⃣ Garanta que todas as tabelas necessárias para análise estejam consolidadas e com chaves corretamente relacionadas.

✅ **Resultado esperado:** A camada Gold tem uma estrutura otimizada, pronta para criar o modelo semântico.

---

## 🚀 Passo 2: Projetar o Modelo Semântico
💡 *Por quê?* O modelo semântico representa medidas, dimensões e relações do negócio para que os usuários consultem e analisem os dados facilmente.

1️⃣ No Power BI ou no Fabric, projete o **modelo semântico Gold**, incluindo:
   - 🔹 **Dimensões:** `Brand`, `Category`, `perfil_produto`, `availability`.
   - 📏 **Medidas chave:**
     - `valor_comercial_total = SUM([valor_comercial])`
     - `produtos_disponiveis = COUNTROWS(FILTER(dim_products, dim_products[availability] = "In Stock"))`
2️⃣ Valide que medidas e relacionamentos estejam configurados corretamente.
3️⃣ Se existirem várias tabelas (clientes, produtos, transações), crie relações por **productID** ou campos equivalentes.

✅ **Resultado esperado:** O modelo semântico Gold está completo e reflete a lógica de negócio da Contoso.

---

## 🚀 Passo 3: Validar o Modelo com Perguntas de Negócio
💡 *Por quê?* Validar garante que consultas em linguagem natural via Copilot ou Power BI retornem respostas precisas.

1️⃣ Teste perguntas no **Copilot ou Power BI**, por exemplo:
   - 💬 “Qual categoria tem mais produtos valiosos?”
   - 💬 “Qual é o valor comercial total por marca?”
   - 💬 “Quantos produtos estão disponíveis?”
   - 💬 “Qual perfil de produto gera mais receita?”
2️⃣ Se alguma resposta estiver incorreta, ajuste medidas ou relações no modelo.

✅ **Resultado esperado:** O modelo responde com precisão a perguntas de negócio.

---

## 🚀 Passo 4: Desenhar um Dashboard no Power BI
💡 *Por quê?* O dashboard comunica métricas-chave e facilita a tomada de decisão.

1️⃣ Abra o **Power BI (no Fabric ou Desktop)** e crie um dashboard conectado ao modelo Gold.
2️⃣ Inclua visualizações como:
   - 📊 **Score médio por segmento (financeiro)**.
   - 💰 **Produtos mais valiosos e taxa de devolução (retail)**.
   - 📈 **Tendências semanais ou mensais**.
3️⃣ Personalize cores, títulos e formatos.
4️⃣ Publique o dashboard no **workspace** correspondente.

✅ **Resultado esperado:** O dashboard publicado e conectado ao Data Agent, pronto para consultas em tempo real.

---

## 🚀 Passo 5: Criar um Data Agent Conectado ao Modelo
💡 *Por quê?* Um **Data Agent** permite que usuários consultem dados via linguagem natural, potencializando o uso do **Copilot**.

1️⃣ No Microsoft Fabric, crie um **Data Agent** e conecte-o ao **modelo semântico Gold**.
2️⃣ Configure permissões e acesso para usuários do workspace.
3️⃣ Teste consultas em linguagem natural para validar respostas.

✅ **Resultado esperado:** O Data Agent está conectado ao modelo e responde interativamente.

---

## 🏁 Pontos de Verificação Final

✅ A tabela Gold foi criada com agregações e relações chave?
✅ O modelo semântico foi desenhado com medidas e dimensões adequadas?
✅ O modelo responde corretamente a perguntas no Copilot/Power BI?
✅ O Data Agent foi criado e testado?
✅ O dashboard está publicado e funcionando?

---

## 📝 Documentação

- [Modelos Semânticos Gold (Power BI/Fabric)](https://learn.microsoft.com/fabric/data-warehouse/semantic-models)
- [Criar Data Agent](https://learn.microsoft.com/fabric/data-science/how-to-create-data-agent)

💡 *Dica:* Documente relações, medidas e fontes de dados — este modelo servirá como base para copilotos empresariais e análises preditivas avançadas. 🚀
