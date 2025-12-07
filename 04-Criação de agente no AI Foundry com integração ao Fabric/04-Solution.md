# Solução do Desafio 04 — Criar Agente Conversacional no AI Foundry integrado ao Fabric

## Objetivo
- Criar um agente no AI Foundry que consulte o Data Agent no Fabric (modelo semântico) e responda em linguagem natural sem expor código.

## Requisitos prévios
- Modelo semântico Gold e Data Agent criados (Desafio 03).

## Passos

### 1 — Criar o agente no AI Foundry

1. Acesse Azure AI Foundry (pelo Fabric ou Portal).
2. Criar -> Novo agente conversacional (nome: `Contoso_AnalistaVirtual`).

### 2 — Conectar ao Data Agent do Fabric

1. Em configuração de fontes, adicione a conexão ao Data Agent (selecionar o Data Agent já criado).
2. Verifique permissões e escopo (apenas leitura nas medidas/tabelas necessárias).

### 3 — Definir intents e prompts

1. Liste intents conforme perguntas de negócio (score_por_segmento, vendas_totais_por_marca, produtos_valiosos).
2. Para cada intent defina exemplos de pergunta e respostas esperadas.

### 4 — Ajustar comportamento (tom e formato)

1. Configure respostas em linguagem natural. Desative a exposição de consultas (T-SQL) ou qualquer sintaxe técnica.
2. Habilite explicações breves que justifiquem a resposta.

### 5 — Testar e publicar

1. Execute testes com perguntas reais e valide que as respostas sejam corretas e sem código.
2. Publique o agente e habilite seu uso via Copilot / Power BI / UI do AI Foundry.

## Validações
- O agente responde com sentenças naturais e não exibe consultas SQL.
- As respostas coincidem com os números do modelo Gold.
