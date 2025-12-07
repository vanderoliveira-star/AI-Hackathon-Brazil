# 📖 Solução: Automação do Processamento de Documentos com Logic Apps

## 🔹 Objetivo

Neste desafio você irá:

✅ Configurar uma **Azure Logic App** para processar PDFs automaticamente
✅ Habilitar Managed Identity e atribuir permissões à Logic App
✅ Usar **Document Intelligence (Form Recognizer)** para analisar PDFs
✅ Criar um pipeline ADF para mover PDFs do Fabric para uma Storage Account
✅ Armazenar saídas JSON analisadas na Storage Account
✅ Validar que os JSONs sejam gravados corretamente

---

## 🚀 Passo 1: Criar Logic App

1. No Azure Portal, vá em **Logic Apps** → **+ Create**.
2. Configure Resource Group, região e nome (`YourLogicApp`).
3. Selecione **Plan Type**: `Consumption`.
4. Review + Create → Create.

---

## 🚀 Passo 2: Habilitar Managed Identity

1. Abra **YourLogicApp** → **Identity** → habilite **System Assigned Identity**.
2. Salve e copie o **Object (Principal) ID**.

---

## 🚀 Passo 3: Atribuir permissões

- No Storage Account e no recurso de Document Intelligence → **Access Control (IAM)**.
- Role assignments para a Managed Identity:
  - **Storage Blob Data Contributor**
  - **Storage Account Contributor**
  - **Cognitive Services Contributor**

---

## 🚀 Passo 4: Configurar Logic App (Designer)

- Trigger: **When a blob is added or modified (properties only)**
  - Storage Account: `Your Storage Account`
  - Container: `incoming-docs`
  - Trigger conditions: `Ends with .pdf`

- Step: **Analyze Document (Prebuilt-Invoice)**
  - Storage URL: `https://yourstoragename.blob.core.windows.net/incoming-docs/@{triggerOutputs()?['body']['name']}`

- Step: **Create Blob**
  - Container: `processed-json`
  - Blob Name: `analyzed-document-@{triggerOutputs()?['body']['name']}.json`
  - Blob Content: `@body('Analyze_Document_for_Prebuilt_or_Custom_models_(v4.x_API)')`

---

## 🚀 Passo 5: (Opcional) Usar JSON do workflow

Cole o JSON de definição no Code View do Logic App para acelerar a configuração.

---

## 🚀 Passo 6: Criar Azure Data Factory (ADF)

1. No Azure Portal → Data Factory → + Create.
2. Configure subscription, resource group, região e nome (`YourADFInstance`).

---

## 🚀 Passo 7: Criar pipeline Copy no ADF

- Source: Microsoft Fabric Lakehouse Files (Service Principal)
- Sink: Azure Blob Storage (container para os JSONs)
- Validate → Trigger Now → Publish

---

## 🚀 Passo 8: Verificar JSONs em Storage

- No Azure Portal → Storage Account → `processed-json` → verificar arquivos JSON.

---

## 🚀 Passo 9: Criar Lakehouse em Fabric para os JSONs analisados

- No Microsoft Fabric → Workspace → + New Item → criar novo Lakehouse para dados analisados.

---

## 🎯 Passo 10: Challenge

- Importar os JSONs analisados para seu Lakehouse no Fabric.

---

## ✅ Resultado final
Os documentos processados são salvos como JSON na Storage Account e estão prontos para serem consumidos em análises dentro do Fabric.
