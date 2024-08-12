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

## Model Deployment
1. Deploy text-embedding-ada-002
2. gpt-35-turbo
   

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

