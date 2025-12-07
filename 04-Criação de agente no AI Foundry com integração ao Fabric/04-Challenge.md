# 🏆 Desafio 04: Criação de um Agente Conversacional no AI Foundry com Integração ao Microsoft Fabric 🤖

📖 Cenário
A Contoso deseja que seus **analistas interajam com os dados em linguagem natural**, sem necessidade de conhecimento técnico em T-SQL ou modelagem.
O objetivo é criar um **agente no Azure AI Foundry** que consuma o **modelo semântico conectado ao Fabric via Data Agent**, entregando respostas claras, compreensíveis e baseadas em dados confiáveis.

---

### 🎯 Sua Missão
Ao concluir este desafio você deverá ser capaz de:

✅ Projetar um **agente conversacional no AI Foundry** integrado ao Microsoft Fabric.
✅ Conectar o agente a um **Data Agent** associado ao modelo semântico Gold.
✅ Configurar intents e prompts orientados a perguntas reais do negócio.
✅ Validar que o agente responda em **linguagem natural**, sem exibir código ou sintaxe técnica.
✅ Publicar o agente para uso de analistas via **Copilot, Power BI ou AI Foundry**.

---

## 🚀 Passo 1: Criar o Agente no AI Foundry
💡 *Por quê?* O agente é a interface conversacional que permitirá aos analistas consultar diretamente os dados do modelo semântico.

1️⃣ Acesse **Azure AI Foundry** dentro do Microsoft Fabric.
2️⃣ Selecione **Criar novo agente** e atribua um nome descritivo, por exemplo: `Contoso_AnalistaVirtual`.
3️⃣ Defina o **tipo de agente** como *Conversacional*.

✅ **Resultado esperado:** O agente foi criado e está configurado para interação conversacional.

---

## 🚀 Passo 2: Conectar o Agente ao Data Agent do Fabric
💡 *Por quê?* O Data Agent é o elo entre o AI Foundry e os dados governados no Microsoft Fabric.

1️⃣ Em **Fontes de dados** do agente, selecione o **Data Agent** criado no desafio anterior.
2️⃣ Verifique que o Data Agent esteja vinculado ao **modelo semântico Gold**, que inclui tabelas como:
   - `score_productos_gold`
   - `creditScore_gold`

3️⃣ Salve a configuração de conexão.

✅ **Resultado esperado:** O agente pode acessar o modelo semântico e consultar os dados de forma controlada.

---

## 🚀 Passo 3: Definir Intents e Prompts Orientativos
💡 *Por quê?* Intents ajudam a treinar o agente para compreender perguntas frequentes do negócio.

1️⃣ Crie intents que reflitam as necessidades analíticas da Contoso.
2️⃣ Exemplos sugeridos:

| **Intent / Tema** | **Prompt orientativo (pergunta do analista)** |
|--------------------|-----------------------------------------------|
| score_por_segmento | “Qual é o score médio por segmento?” |
| produtos_com_devolucao | “Quais produtos têm maior taxa de devolução?” |
| correlacao_score_valor | “Existe correlação entre score e valor da compra?” |
| produtos_valiosos_por_categoria | “Que categoria tem mais produtos valiosos?” |
| clientes_por_ocupacao | “Quantos clientes ativos há por ocupação?” |
| vendas_totais_por_marca | “Qual é o valor comercial total por marca?” |

✅ **Resultado esperado:** O agente entende as perguntas de negócio e responde de forma contextual.

---

## 🚀 Passo 4: Configurar o Comportamento do Agente
💡 *Por quê?* Controlar o tom e o formato das respostas garante experiência clara e sem linguagem técnica.

1️⃣ Na configuração de respostas, selecione:
   - “Respostas em **linguagem natural**”.
   - “**Ocultar código e sintaxe técnica**”.
   - “Não exibir código nem sintaxe técnica (ex.: T-SQL)”.
2️⃣ Ative explicações sucintas que justifiquem as respostas, por exemplo:
> “Segundo os dados do modelo, o score médio no segmento alto é 87.”

✅ **Resultado esperado:** O agente comunica os achados em linguagem natural, sem mostrar consultas.

---

## 🚀 Passo 5: Validar o Agente com Perguntas Reais
💡 *Por quê?* A validação confirma que o agente compreende consultas e correlações entre tabelas.

1️⃣ Teste no **AI Foundry** com perguntas como:
   - “Qual segmento tem maior score médio?”
   - “Qual marca tem mais produtos disponíveis?”
   - “Qual é a tendência mensal de risco?”
   - “Que perfil de produto gera mais receita?”

2️⃣ Verifique se as respostas:
   - São **claras e sem código**.
   - Entendem correlações entre entidades (ex.: score e produtos).
   - Derivam métricas do **modelo semântico conectado**.

✅ **Resultado esperado:** O agente responde consultas complexas de forma coerente e baseada nos dados do modelo.

---

## 🚀 Passo 6: Publicar e Habilitar o Agente
💡 *Por quê?* Publicar torna o agente acessível a analistas e times de negócio.

1️⃣ Publique o agente no **workspace da Contoso**.
2️⃣ Habilite seu uso em **Copilot, Power BI ou diretamente no AI Foundry**.
3️⃣ Confirme que o agente apareça na lista de recursos disponíveis para usuários autorizados.

✅ **Resultado esperado:** O agente está ativo e disponível para consultas em linguagem natural no ecossistema Contoso.

---

## 🏁 Pontos de Verificação Final

✅ O agente foi criado e configurado corretamente no AI Foundry?
✅ Está conectado ao Data Agent e ao modelo semântico Gold?
✅ Foram definidos intents e prompts alinhados ao negócio?
✅ O agente responde em linguagem natural sem exibir código?
✅ Está publicado e disponível para analistas?

---

## 📝 Documentação

- [Configuração de Agentes no AI Foundry](https://learn.microsoft.com/es-es/azure/ai-foundry/agents/environment-setup)
- [Conexão com Data Agent do Fabric](https://learn.microsoft.com/es-es/azure/ai-foundry/agents/how-to/tools/fabric?pivots=portal)
- [Exemplos de Intents e Prompts treinados](#)
- [Referência oficial - Criação de Agentes de Dados no Fabric](#)
