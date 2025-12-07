# 🧠 AI Fabric Hackathon

## 🎯 Objetivos do Hackathon

Ao final deste hackathon, os participantes serão capazes de:

- Preparar, transformar e enriquecer dados financeiros e de seguros usando **Microsoft Fabric**, aplicando o modelo **medalhão** para estruturar camadas de valor analítico.
- Ingerir dados de sistemas core, fontes externas e APIs por meio de **pipelines, notebooks e conectores nativos do Fabric**.
- Projetar **modelos semânticos** robustos que facilitem o consumo de dados por analistas, auditores e sistemas de inteligência.
- Monitorar e otimizar o consumo de capacidade no **Fabric**, aplicando métricas-chave para governança operacional e eficiência de recursos.
- Construir **agentes de inteligência artificial** com **AI Foundry** para análise preditiva, detecção de fraude e geração de insights financeiros.
- Orquestrar fluxos multi-agente e processos de dados com **pipelines e triggers**, habilitando automação inteligente em cenários bancários e de seguros.
- Aplicar **controles de segurança e governança** de dados sensíveis, configurando papéis, permissões e políticas em workspaces do Fabric.
- Integrar **Microsoft Purview** para rastreabilidade, classificação e conformidade normativa, fortalecendo a governança de dados em ambientes regulados.
- Visualizar **insights estratégicos** com **Power BI no Microsoft Fabric**, habilitando painéis interativos para decisões orientadas por dados.


# Agenda


| Dia  | Atividade                                                                 | Tipo   |
|------|---------------------------------------------------------------------------|--------|
| Dia 1 | Preparação de dados (estruturação, limpeza, profile)                    | Reto   |
| Dia 1 | Ingestão de dados de fontes internas e externas                         | Reto   |
| Dia 1 | Transformação de dados com notebooks e pipelines                        | Reto   |
| Dia 1 | Enriquecimento de dados e criação de modelo semântico                   | Reto   |
| Dia 1 | Fabric Metrics: monitoramento de capacidade, consumo e performance      | Demo   |
| Dia 1 | Mesa redonda: Q&A com especialistas e participantes                     | Reto   |
| Dia 1 | Encerramento e resumo do dia                                             | Encerramento |
| Dia 2 | Construção de agente AI Foundry para análise preditiva                 | Reto   |
| Dia 2 | Orquestração multi-agente com pipelines e triggers                     | Reto   |
| Dia 2 | Segurança no Fabric: papéis, objetos, workspaces (opcional)            | Reto   |
| Dia 2 | Integração com Microsoft Purview: linhagem, classificação, governança  | Demo   |
| Dia 2 | Sessão de valor: Q&A sobre adoção, impacto e próximos passos           | Encerramento |
| Dia 2 | Encerramento e entrega de reconhecimentos                              | Encerramento |


# Arquitetura
![Arquitetura](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/Architecture/Architecture.png)


# 📖 História do Caso de Uso
 
## "Contoso e a Inteligência de Dados Multissetorial em Ação"
 
**Contoso**, uma organização presente nos setores **financeiro e comercial**, enfrenta o desafio de consolidar informações provenientes de múltiplas fontes para habilitar análises confiáveis, automação inteligente e experiências conversacionais baseadas em dados. Neste hackathon, os participantes assumem o papel de **equipe técnica** responsável por construir uma solução moderna sobre **Microsoft Fabric**, colocando em prática suas habilidades em um cenário realista e multissetorial.
 
### 🗃️ Fontes de Dados
O cenário começa com dois conjuntos de dados em formato **JSON**, ambos ingeridos a partir do **Cosmos DB**:
 
• **Conjunto de score de crédito:** informações de clientes, comportamento de pagamento e perfil financeiro  
• **Conjunto de produtos retail:** dados sobre disponibilidade, valor comercial, categoria e marca  
 
### 🎯 Objetivo Principal
Transformar, limpar e estruturar ambos os datasets em um **modelo enriquecido** que sirva de base para a criação de **agentes de inteligência artificial**. Para isso, os participantes aplicarão o **modelo medalhão** (Bronze → Silver → Gold), assegurando qualidade, rastreabilidade e valor analítico das informações.
 
### 📊 Modelo Semântico e Métricas-Chave
Uma vez estruturados os dados na **camada Gold**, será projetado um **modelo semântico no Power BI**, que permitirá correlacionar métricas importantes como:
 
• Score médio por segmento  
• Valor comercial por categoria  
• Taxa de devolução por marca  
• Tendências mensais de risco ou vendas  
 
### 🤖 Agentes Conversacionais
Utilizando **AI Foundry**, os participantes criarão **agentes** capazes de interagir com os dados por meio de **linguagem natural**, sem expor código técnico, resolvendo desafios de automação e orquestrando fluxos multi-agente com **modelos de linguagem de grande escala (LLMs)**. Esses agentes estarão conectados aos modelos semânticos via **Data Agents**, permitindo consultas conversacionais, por exemplo:
 
• *"Qual segmento tem maior score médio?"*  
• *"Quais produtos têm maior taxa de devolução?"*  
• *"Existe relação entre score e valor da compra?"*  
 
### 📈 Visualização e Insights
Finalmente, os **insights gerados** serão visualizados em **painéis interativos no Power BI**, facilitando a tomada de decisões baseada em dados tanto para **analistas financeiros** quanto **comerciais**. Este caso exemplifica uma adoção realista e escalável do **Microsoft Fabric** em ambientes híbridos, onde a **inteligência de dados** se torna vantagem competitiva para a Contoso, impulsionando inovação, eficiência operacional e democratização da análise.
 
---
 
# 🎯 Resumo dos Desafios - Do Insight à Decisão
 
## 🏆 Desafio 00: Configuração da Zona de Aterrissagem e Preparação de Dados
 
**📖 Cenário:** A Contoso deve preparar o ambiente de trabalho no Microsoft Fabric, conectando dados armazenados no Azure Cosmos DB e estabelecendo uma zona de aterrissagem estruturada em camadas.
 
### 🎯 Objetivos Principais:
- ✅ Criar Azure Cosmos DB NoSQL e carregar datasets JSON (financeiro e retail)
- ✅ Configurar workspace no Microsoft Fabric com estrutura de camadas
- ✅ Estabelecer conexão entre Cosmos DB e Fabric
- ✅ Criar Lakehouse com arquitetura medalhão (Bronze, Silver, Gold)
- ✅ Explorar e validar a estrutura dos dados JSON
 
### 🚀 Entregáveis:
- Cosmos DB configurado com contêineres de dados
- Workspace do Fabric com Lakehouse estruturado por camadas
- Documentação do fluxo de dados planejado
 
---
 
## 🏆 Desafio 01: Ingestão de Dados do Cosmos DB ao Microsoft Fabric (Camada Bronze)
 
**📖 Cenário:** Consolidar dados operacionais da Contoso no Microsoft Fabric por meio da ingestão a partir do Azure Cosmos DB para a camada Bronze, aplicando limpeza básica.
 
### 🎯 Objetivos Principais:
- ✅ Implementar ingestão com Dataflows Gen2 a partir do Cosmos DB
- ✅ Aplicar limpeza básica (valores nulos, colunas desnecessárias, normalização)
- ✅ Validar carga e estrutura de dados na camada Bronze
- ✅ Preparar dados para transformações avançadas
 
### 🚀 Entregáveis:
- Dataflow Gen2 funcional com transformações básicas
- Tabela Bronze com dados limpos e estruturados
- Validação de integridade dos dados ingeridos
 
---
 
## 🏆 Desafio 02: Transformação Intermediária e Análise Exploratória (Camada Silver)
 
**📖 Cenário:** Avaliar qualidade dos dados e criar versão intermediária otimizada na camada Silver, aplicando transformações avançadas e análise exploratória com Machine Learning.
 
### 🎯 Objetivos Principais:
- ✅ Criar tabela Silver com transformações intermediárias
- ✅ Aplicar agregações e métricas analíticas (score de crédito por cliente, perfis de produto)
- ✅ Implementar análise exploratória com clustering K-Means
- ✅ Preparar dados para modelagem semântica na Gold
 
### 🚀 Entregáveis:
- Tabela Silver com transformações e métricas de negócio
- Análise de clustering com insights de segmentação
- Dados otimizados prontos para a camada Gold
 
---
 
## 🏆 Desafio 03: Modelo Semântico, Data Agent e Dashboard de Valor (Camada Gold)
 
**📖 Cenário:** Habilitar análise de negócio por meio de modelo semântico robusto, Data Agent conversacional e dashboard interativo para responder perguntas-chave do negócio.
 
### 🎯 Objetivos Principais:
- ✅ Projetar modelo semântico Gold com medidas e dimensões relevantes
- ✅ Criar Data Agent conectado ao modelo semântico
- ✅ Desenvolver dashboard Power BI com visualizações de valor
- ✅ Validar respostas a perguntas de negócio via Copilot
 
### 🚀 Entregáveis:
- Modelo semântico com medidas-chave (valor_comercial_total, produtos_disponiveis)
- Data Agent funcional para consultas em linguagem natural
- Dashboard Power BI publicado com métricas estratégicas
 
---
 
## 🏆 Desafio 04: Criação de Agente Conversacional no AI Foundry
 
**📖 Cenário:** Permitir que analistas interajam com dados usando linguagem natural, criando um agente no Azure AI Foundry integrado ao modelo semântico do Fabric.
 
### 🎯 Objetivos Principais:
- ✅ Projetar agente conversacional no AI Foundry integrado ao Fabric
- ✅ Conectar agente ao Data Agent associado ao modelo semântico Gold
- ✅ Configurar intents e prompts orientados a perguntas reais de negócio
- ✅ Validar respostas em linguagem natural sem código técnico
- ✅ Publicar agente para uso dos analistas
 
### 🚀 Entregáveis:
- Agente conversacional funcional no AI Foundry
- Configuração de intents para perguntas de negócio frequentes
- Integração completa com o modelo semântico do Fabric
- Validação de respostas em linguagem natural
 
---
 
## 🏆 Desafio 05: Orquestração Multi-agente e Fluxos Colaborativos
 
**📖 Cenário:** Projetar e documentar um fluxo multi-agente que coordene ingestão, análise e execução para automatizar tarefas complexas e adaptar-se dinamicamente a cenários mutáveis.
 
### 🎯 Objetivos Principais:
- ✅ Definir três agentes especializados (Ingestão, Análise/Avaliação, Decisão/Execução)
- ✅ Projetar fluxo orquestrado com feedback e tratamento de erros
- ✅ Implementar contratos de mensagens e esquemas de dados
- ✅ Simular cenários de negócio e validar métricas de eficácia
- ✅ Documentar o design para replicabilidade e escalabilidade
 
### 🚀 Entregáveis:
- Arquitetura de três agentes com papéis definidos
- Fluxo orquestrado com condições e feedback
- Simulação de cenários com métricas de desempenho
- Documentação completa do design multi-agente
 
---
 
## 📚 Recursos e Documentação
 
### 🔗 Links de Referência:
- [Documentação Microsoft Fabric](https://learn.microsoft.com/es-es/fabric/)
- [Azure AI Foundry](https://learn.microsoft.com/es-es/azure/ai-foundry/)
- [Power BI Embedded](https://learn.microsoft.com/es-es/power-bi/)
- [Azure Cosmos DB](https://learn.microsoft.com/es-es/azure/cosmos-db/)
 
### 🎯 Próximos Passos:
Com estes desafios concluídos, você terá construído uma solução completa que vai **do insight à decisão**, implementando:
- ✅ Pipeline de dados completo com arquitetura medalhão
- ✅ Modelo semântico robusto para análise de negócio
- ✅ Agentes conversacionais para democratização de dados
- ✅ Orquestração inteligente para automação de processos
