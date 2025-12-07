# Solução do Desafio 06 — Governança de Dados e Data Products (Purview + Fabric)

## Objetivo
- Implementar catalogação e governança com Microsoft Purview, integrar o Fabric como fonte e publicar Data Products documentados.

## Requisitos prévios
- Permissões para criar recursos no Purview e registrar fontes.

## Passos

### 1 — Provisionar Microsoft Purview

1. No portal do Azure, crie uma conta Purview (ou use existente).
2. Acesse o Data Map e crie uma coleção `ContosoData`.

### 2 — Registrar e escanear fontes (Lakehouse no Fabric)

1. Em Purview → Sources → Register new source → escolha o recurso do Fabric (Lakehouse ou Warehouse).
2. Configure autenticação (Managed Identity ou credenciais) e execute um scan.
3. Revise o Data Map para confirmar o descobrimento de tabelas e linhagem.

### 3 — Classificar e criar glossário

1. Execute classificadores automáticos e adicione classificadores manuais para dados sensíveis.
2. Crie um glossário de negócio com termos (`Cliente`, `Venda`, `Produto`) e documente definições.
3. Associe termos do glossário aos ativos catalogados.

### 4 — Criar Data Products no Fabric

1. No Fabric, crie um data product (ex.: `Sales Insights Product`) combinando `customers` e `sales`.
2. Documente no Purview: propósito, responsáveis, qualidade, linhagem e SLA.

### 5 — Validação e governança contínua

1. Teste a busca de ativos a partir do Purview.
2. Verifique linhagem desde a origem (Lakehouse Bronze) até o produto final (Gold/Data Product).
3. Gere um relatório com: ativos catalogados, termos criados e data products publicados.

## Resultados esperados
- Purview com ativos e linhagem visíveis.
- Data Products publicados e documentados com responsáveis e métricas de qualidade.

---

Referências
- Purview docs: https://learn.microsoft.com/purview
