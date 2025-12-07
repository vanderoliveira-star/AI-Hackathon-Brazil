# 🏆 Desafio: Automação do Processamento de Documentos com Logic Apps 🚀

## 📖 Objetivo

Neste desafio você deverá:

✅ Configurar uma **Azure Logic App** para processar arquivos PDF automaticamente
✅ Habilitar **Managed Identity** para acesso seguro aos recursos
✅ Atribuir **permissões** à Logic App para armazenamento e processamento com IA
✅ Usar **Document Intelligence (Form Recognizer)** para analisar PDFs
✅ Criar um **pipeline ADF** para mover PDFs do **Fabric** para uma **Storage Account**
✅ Salvar os **JSON analisados** na **Storage Account**
✅ Validar que os **arquivos processados** sejam gravados corretamente no Storage

---

## 🚀 Passo 1: Criar uma Logic App

💡 *Por quê?* A Logic App automatiza a detecção de novos PDFs e aciona o processamento com **Document Intelligence**.

### 1️⃣ Criar uma Azure Logic App
🔹 No **Azure Portal**, crie uma **Logic App (Consumption Plan)**.

✅ **Resultado:** Logic App criada e pronta para configuração.

---

## 🚀 Passo 2: Habilitar Managed Identity para a Logic App

💡 *Por quê?* A Logic App precisa autenticar-se com segurança para acessar o **Blob Storage** e o **Document Intelligence**.

### 1️⃣ Ativar System-Assigned Managed Identity
🔹 Na configuração da Logic App, habilite **System-Assigned Identity**.
🔹 Copie o **Object (Principal) ID** para uso posterior.

✅ **Resultado:** A Logic App possui identidade para autenticação.

---

## 🚀 Passo 3: Atribuir Permissões à Logic App

💡 *Por quê?* A Logic App precisa acessar o Blob Storage para leitura/escrita e usar serviços de IA.

### 1️⃣ Atribuir papéis (IAM)
🔹 No **Storage Account** e no recurso de **Document Intelligence**, vá em **Access Control (IAM)**.
🔹 Atribua os seguintes papéis à Managed Identity da Logic App:
  - **Storage Blob Data Contributor**
  - **Storage Account Contributor**
  - **Cognitive Services Contributor** (para Document Intelligence)

✅ **Resultado:** A Logic App pode ler PDFs e gravar JSONs processados.

---

## 🚀 Passo 4: Configurar a Logic App (Designer)

💡 *Por quê?* É necessário definir o workflow para processar PDFs.

### 1️⃣ Construir o workflow no Logic App Designer
🔹 Inicie com **Blank Logic App**.
🔹 **Trigger:** "When a blob is added or modified (properties only)" (Azure Blob Storage)
  - **Storage Account:** `Your Storage Account`
  - **Container:** `incoming-docs`
  - **Condição:** arquivos que terminem com `.pdf`

🔹 **Passo de processamento:**
  - Adicione **Analyze Document (Prebuilt-Invoice)** (Document Intelligence)
  - Forneça a **URL do blob**:
    ```
    https://yourstoragename.blob.core.windows.net/incoming-docs/@{triggerOutputs()?['body']['name']}
    ```

🔹 **Salvar a saída:**
  - Adicione **Create Blob** em Azure Blob Storage
  - **Container:** `processed-json`
  - **Blob Name:** `analyzed-document-@{triggerOutputs()?['body']['name']}.json`
  - **Blob Content:** `@body('Analyze_Document_for_Prebuilt_or_Custom_models_(v4.x_API)')`

✅ **Resultado:** A Logic App analisa automaticamente PDFs e grava JSONs no Storage.

---

## 🚀 Passo 5: (Alternativa) JSON do workflow

Você pode colar um JSON de definição no Code View do Logic App para acelerar a configuração (ajuste conforme necessário).

---

## 🚀 Passo 6: Criar um Azure Data Factory (ADF)

### 1️⃣ Criar instância ADF
- No **Azure Portal** → **Data Factory** → **+ Create**
- Configure subscription, resource group, região e nome (`YourADFInstance`).

✅ **Resultado:** Instância ADF criada.

---

## 🚀 Passo 7: Criar pipeline Copy no ADF

- Em `adf.azure.com`, crie um novo pipeline com a atividade **Copy Data**.

### Origem (Fabric Lakehouse Files)
- Linked Service: Microsoft Fabric Lakehouse Files (Service Principal)
- Authentication: Service Principal (Tenant ID, Client ID, Client Secret)
- Folder Path: `/Files/`

### Destino (Azure Blob Storage)
- Linked Service: Azure Blob Storage
- Container: `Your Container` (onde serão armazenados os JSONs analisados)

- Valide e execute o pipeline (Trigger Now → Publish).

✅ **Resultado:** PDFs são movidos do Fabric ao Storage, ativando a Logic App.

---

## 🚀 Passo 8: Verificar JSONs processados

- No Azure Portal → Storage Account → `processed-json` → verifique os arquivos JSON.

✅ **Resultado final:** Documentos processados gravados em JSON no Storage.

---

## 🚀 Passo 9: Criar Lakehouse em Fabric para os JSONs analisados

- No **Microsoft Fabric**, crie um novo Lakehouse para armazenar/consumir os JSONs analisados.

---

## 🎯 Passo 10: Challenge Time!

- **Importe os JSONs analisados para seu Lakehouse no Fabric**.

### 🔹 Dicas:
- Logic App
- Pipeline ADF
- Upload manual
