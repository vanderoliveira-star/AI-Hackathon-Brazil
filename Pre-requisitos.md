# Guia de Pré-requisitos para o Hackathon  
### 🧩 Preparativos essenciais para participar com sucesso

---

## ✅ Registro de Provedores de Recursos
Certifique-se de que os seguintes provedores de recursos estejam registrados na sua assinatura do **Azure**:
- `Microsoft.PolicyInsights`
- `Microsoft.Cdn`
- `Microsoft.StreamAnalytics`

**Como registrá-los:**
1. Vá ao **Portal do Azure** → Configuração da assinatura → *Provedores de recursos*.
2. Selecione cada provedor e clique em **Registrar**.

---

## ✅ Identidade e Autenticação
**Principal de Serviço e Autenticação:**
- ID do cliente e segredo *(que não expirem antes do segundo dia do evento)*.
- Os participantes devem ter disponível seu **ID do cliente** e **segredo** durante o hackathon.

---

## ✅ Pré-requisitos do Microsoft Fabric
**Opções de acesso:**
- Criar uma **nova trial do Microsoft Fabric**, ou
- Usar uma **capacidade do Fabric já provisionada** na sua assinatura do Azure.

**Requisitos de configuração do Fabric:**
- Pelo menos um membro designado como **administrador do Microsoft Fabric**.
- Um **workspace do Fabric** atribuído à equipe.
- Capacidade para criar **Lakehouses** e **Modelos Semânticos** no Fabric.
- Acesso ao **OneLake** (armazenamento do Fabric) para upload de arquivos.

---

## ✅ Requisitos do Azure OpenAI
**Cota TPM para Modelos OpenAI:**
- `text-embedding-ada-002`
- `gpt-35-turbo-16k`

Se a cota atual for menor que **100.000**, solicite um aumento antes do evento para garantir disponibilidade.
> ⏱️ As aprovações costumam levar 24 horas, por isso é crítico completar esta etapa com antecedência.

**Passos recomendados:**
- Verifique sua cota atual → [Guia de Cotas do Azure OpenAI](#)
- Solicite aumento de cota → [Solicitação de Aumento de Cota](#)

---

## ✅ Requisitos de Rede e Acesso
Garanta acesso sem restrições às seguintes plataformas:
- **Azure AI Foundry**
- **Azure Data Factory**
- **Document Intelligence Studio**
- **Portal do Azure**
- **Microsoft Fabric**

---

## ✅ Requisitos do Visual Studio Code
**Extensões necessárias no VS Code:**
- Python 🐍
- Azure Tools ☁️
- Azure Semantic Kernel Tools 🧠

---

## 🎯 O que Esperar
- 💡 Desafios técnicos práticos
- 🤝 Colaboração com profissionais afins
- 🧩 Resolução de problemas ao vivo e orientação especializada
- 🚀 Oportunidade para aprimorar habilidades e gerar ideias com nossas equipes

---

## 🚀 Lista Final de Verificação
✔️ Complete todos os pré-requisitos antes do evento
✔️ Verifique seu acesso ao **Azure**, **Microsoft Fabric** e **serviços do OpenAI**
✔️ Confirme que você pode acessar **todos os recursos e ferramentas necessárias**

---

# Requisitos Dia 2

# 🔐 Funções no Azure e seu Uso

| **Função no Azure** | **Uso Principal** |
|---------------------|-------------------|
| **Owner ou Contributor** | Permite **criar e gerenciar recursos** como *AI Services*, *Azure ML*, *App Services*, entre outros. |
| **Cognitive Services Contributor** | Habilita a **configuração e gerenciamento de recursos do Cognitive Services**. |
| **Storage Blob Data Contributor** | Concede **acesso completo ao armazenamento** utilizado pelo *AI Foundry* (leitura, escrita e exclusão de blobs). |
| **Azure OpenAI Contributor (se aplicável)** | Concede **acesso a modelos GPT, embeddings e outros serviços** do *Azure OpenAI*. |
| **Key Vault Administrator (opcional)** | Permite **gerenciar segredos, certificados e chaves API** armazenadas no *Azure Key Vault*. |

## 🎉 Nos vemos no Hackathon!
Esperamos um evento **dinâmico e inspirador** — e, acima de tudo, uma **experiência de aprendizado enriquecedora para todos**.

Se tiver perguntas ou precisar de assistência, **não hesite em nos contatar**.

> 🚀 Prepare-se para inovar, colaborar e construir soluções potencializadas por IA! 🎉
