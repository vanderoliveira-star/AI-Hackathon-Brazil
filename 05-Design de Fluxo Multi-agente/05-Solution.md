# 🤖 Guia de Preparação do Ambiente para Azure AI Foundry (Resumo)

## Parte 1: Preparação do ambiente

### Requisitos prévios
- Acesso ao **Azure AI Studio**
- Projeto criado em **Azure AI Foundry**
- Dataset enriquecido disponível (CSV ou tabela no Fabric)

### Passos
1. Criar projeto no Azure AI Foundry (ex.: `Projeto_ClientesAI`).
2. Fazer upload do dataset enriquecido em Data Assets.
3. Verificar campos chave: `customerId`, `total_gastado`, `frequencia_compra`, `pais`, `fecha`.

## Parte 2: Design de Prompt Flows

### Reto 1: Resumos de compra
Prompt base com campos do cliente para gerar um resumo breve.

### Reto 2: Classificação de clientes
Prompt base para classificar cliente em categorias (Alto valor, Frequente, Ocasional) com justificativa.

### Reto 3: Insights narrativos
Gerar relatório mensal por país com total de compras e valor.

## Parte 3: Implementação em Prompt Flow
1. Criar Flow por desafio.
2. Usar Data Input para conectar CSV.
3. Usar LLM Prompt e Output Parser.
4. Executar e validar.

## Parte 4: Resultado esperado
- Três flows funcionais que aplicam LLMs sobre dados enriquecidos.
- Prompts reutilizáveis para outros casos.
- Base para recomendações ou geração de conteúdo.

---

# Solução Desafio 05 — Design e Orquestração de Fluxo Multi-agente

## Objetivo
- Projetar um fluxo multi-agente (ingestão, análise, decisão) com contratos de mensagens, tratamento de erros e métricas de validação.

## Requisitos prévios
- Definição de fontes de dados e esquema de mensagens.

## Passos

### 1 — Definir papéis e contratos
1. Documentar 3 agentes com entradas/saídas:
   - Ingestão: recebe raw, publica `NEW`.
   - Análise: consome `NEW` → `SCORED`.
   - Decisão/Ejecução: consome `SCORED` → `EXECUTED`.
2. Definir contrato de mensagens (headers: `correlationId`, `timestamp`; payload: entidade/atributos; status).

### 2 — Projetar fluxo e condições
1. Esboçar fluxo: Ingestão → Análise → Decisão.
2. Adicionar ramificações condicionais (p.ex., enrich se faltarem dados, DLQ em erros irreparáveis).

### 3 — Implementar resiliência
1. Estratégias:
   - Retries exponenciais para falhas transitórias.
   - Dead-letter queue para mensagens não processáveis.
   - Timeouts e circuit-breakers.

### 4 — Simular e validar
1. Gerar dados sintéticos que reproduzam volumes e variabilidade.
2. Executar simulações medindo tempo E2E (P50/P90), throughput e taxa de erros.

### 5 — Métricas e melhoria contínua
1. Exportar métricas para dashboard: latência, erros, retries, sucesso.
2. Definir thresholds e runbooks para operação.

## Documentação final
- Diagrama de fluxo com IDs e condições.
- Contratos de mensagens versionados.
- Resultados de simulação e dashboard de métricas.
