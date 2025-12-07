# 🚀 Desafio: Governança e Data Products com Purview + Fabric

## 🌍 Contexto
A organização **Contoso Retail** pretende estabelecer um **quadro de governança de dados unificado** que permita às equipes de análise e negócios **identificar, classificar e consumir dados** de forma confiável dentro do **Microsoft Fabric**.

Para isso, é necessário **configurar o Microsoft Purview** como ferramenta de governança e usar o **Fabric** como plataforma de análise e colaboração.

---

## 🎯 Objetivo geral
Desenhar e implementar um ambiente governado que permita:
- Catalogar ativos de dados via **Purview**.
- Integrar fontes de dados com **Fabric**.
- Criar e documentar **data products** consumíveis por diferentes times.

---

## 🧠 Tarefas do desafio

### 🔹 1. Configuração inicial do Purview
- Criar uma conta **Microsoft Purview** e acessar o **Data Map**.
- Adicionar uma coleção chamada **ContosoData** para organizar ativos.
- Registrar ao menos uma **fonte de dados proveniente do Fabric** (Lakehouse ou Warehouse).
- Executar um **scan automático** para descobrir metadados.
- Verificar que ativos apareçam catalogados no **Data Map**.

---

### 🔹 2. Classificação e etiquetagem de dados
- Aplicar **classificadores automáticos ou manuais** a colunas sensíveis (nome, e-mail, país).
- Criar **glossários de negócio** para definir termos-chave (ex.: *Cliente*, *Venda*, *Produto*).
- Associar termos do glossário aos ativos catalogados para melhorar busca semântica.

---

### 🔹 3. Integração com Microsoft Fabric
- No **Fabric**, criar um **Lakehouse** chamado `Contoso_Sales_Lakehouse`.
- Carregar **dados de exemplo** (vendas e clientes) e validar sua visibilidade no **Data Hub**.
- No **Purview**, vincular a fonte do **Fabric** ao catálogo para habilitar **visualização de linhagem**.

---

### 🔹 4. Criação de Data Products
- Em **Fabric**, dentro de Data Activator ou Warehouse, construir um **data product** que combine clientes e vendas.
- Publicar o produto com o nome **Sales Insights Product**.
- Documentar no catálogo do **Purview**:
  - Propósito do data product.
  - Qualidade dos dados.
  - Responsáveis.
  - Linhagem dos dados desde a fonte até o consumo.

---

### 🔹 5. Validação da Governança
- Verificar que usuários consigam **buscar e descobrir ativos** no catálogo do **Purview**.
- Revisar a **linhagem de dados** para confirmar rastreabilidade da fonte ao produto final.
- Gerar um **relatório resumo** com:
  - Ativos catalogados.
  - Termos do glossário criados.
  - Data products publicados.

---

## 🏁 Resultado esperado
Um ambiente **governado e colaborativo**, onde todos os ativos do **Microsoft Fabric** estejam:
- Catalogados e classificados em **Purview**.
- Vinculados com linhagem completa da origem ao consumo.
- Documentados e disponíveis como **data products** para analistas ou cientistas de dados.
