# Fabric Data Science Workshop

**Prerequisite**: Access to external subscription

## Deploy Storage account and Fabric capacity

 ### <font color="Red"><b>Note:</b> Pause the fabric capacity when it is not in use to avoid incurring significant costs.</font>

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fumeshpawar2188%2Ffabricdsworkshop%2Fmain%2Finfra%2Ffabric_storage_template.json)


## Deploy OAI service

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fumeshpawar2188%2Ffabricdsworkshop%2Fmain%2Finfra%2Foai_template.json)


## Deploy AI search 

Reference - https://learn.microsoft.com/en-us/azure/search/search-get-started-arm

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fazure%2Fazure-quickstart-templates%2Fmaster%2Fquickstarts%2Fmicrosoft.search%2Fazure-search-create%2Fazuredeploy.json)

## Deploy AML workspace

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fumeshpawar2188%2Ffabricdsworkshop%2Fmain%2Finfra%2Faml_template.json)

## Deploy Azure AI Foundry Hub + Project

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fumeshpawar2188%2Ffabricdsworkshop%2Fmain%2Finfra%2Fai_foundry_template.json)

## Model Deployment
1. Deploy text-embedding-ada-002
2. gpt-35-turbo
3. gpt-4o (required for the Photo Upload & LLM Structured Output notebook)
   

## Hands-on Guide

### 1. Create Lakehouse
- Start by creating a new Lakehouse in Microsoft Fabric and pin it as the default.

### 2. Download the Repository from GitHub
- Open the GitHub repository in your web browser: [fabricdsworkshop](https://github.com/umeshpawar2188/fabricdsworkshop/tree/main).
- Click on the **Code** button, then select **Download ZIP**.
- Save the ZIP file to your local machine and extract its contents.

### 3. Locate the Notebooks
- After extracting the ZIP file, navigate to the folder that contains the Jupyter notebooks.

### 4. Access Microsoft Fabric
- Log in to the Microsoft Fabric portal.
- Navigate to the workspace where you want to upload the notebooks.

### 5. Upload Notebooks to Microsoft Fabric
- In the Microsoft Fabric workspace, go to the **Notebooks** section.
- use the **New ** dropdown and select **Import notebook**. 
- Then select the **Upload** and browse to the folder where you extracted the notebooks.
- Select the notebooks you want to upload and click **Open**.

### 6. Create Environment
- Use the `environment.yaml` file located in the `hands-on` directory to set up your environment.

## Notebooks

| # | Notebook | Description |
|---|----------|-------------|
| 1 | `1. OpenAI in Fabric Synapse ML.ipynb` | Using Azure OpenAI via SynapseML pre-built models |
| 2 | `2. OpenAI for Big Data (BYOK).ipynb` | Scaled OpenAI completions and embeddings with BYOK |
| 3 | `3. Prebuilt Text Analytics and Translator.ipynb` | Sentiment, language detection, key-phrase extraction |
| 4 | `4. Photo Upload and LLM Structured Output.ipynb` | Upload a photo to Azure Blob Storage, then use GPT-4o vision with tool calling to extract structured data |
| 5 | `5. Azure AI Foundry - Photo Upload and Structured Output.ipynb` | Same flow implemented via **Azure AI Foundry** Agent Service – includes step-by-step portal setup instructions then runnable code |

### Notebook 4 – Photo Upload and LLM Structured Output

**What it does:**
1. Uploads a local image to an Azure Blob Storage container.
2. Generates a time-limited SAS URL for the uploaded blob.
3. Sends the image URL to an Azure OpenAI **GPT-4o** (vision-capable) deployment via the Chat Completions API.
4. Forces the model to call a predefined **tool** (`extract_image_details`) so the response is fully structured JSON containing fields such as description, main subject, dominant colors, detected objects, scene type, and any visible text.
5. Loads the structured output into a **Spark DataFrame** ready for Lakehouse storage or downstream analytics.

**Additional prerequisites for Notebook 4:**
- Azure Storage Account (connection string + account key)
- Azure OpenAI deployment with a vision-capable model (e.g. `gpt-4o` or `gpt-4-turbo`)
- `azure-storage-blob` and `openai` packages (already in `environment.yaml`)

### Notebook 5 – Azure AI Foundry: Photo Upload and Structured Output

Implements the same photo-analysis workflow using **Azure AI Foundry** Agent Service.
The notebook begins with **six manual setup steps** (markdown-only – nothing to run), then provides all the code once you have completed the portal steps.

**Manual setup steps covered in the notebook:**

| Step | What you do in the portal |
|------|--------------------------|
| 1 | Create a Resource Group |
| 2 | Deploy an Azure OpenAI service and a GPT-4o model deployment |
| 3 | Create an AI Foundry Hub, connect the OpenAI resource, and create a Project – copy the **Project Connection String** |
| 4 | Create an Azure Blob Storage account and a `photos` container – copy the **account name and key** |
| 5 | Assign `Azure AI Developer` and `Storage Blob Data Contributor` roles to your Managed Identity *(Fabric only)* |
| 6 | Attach the workshop environment (from `environment.yaml`) to the notebook |

**Additional prerequisites for Notebook 5:**
- `azure-ai-projects==1.0.0` (added to `environment.yaml`)

