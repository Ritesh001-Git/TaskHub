
# Deploying a Static Web App on Azure using GitHub Actions

This README explains the steps and details for deploying a static web application to Azure using GitHub Actions.

## 📌 Prerequisites

- An Azure account
- A GitHub repository containing your static website files
- Azure Static Web Apps resource created in the Azure portal

## 🚀 Steps to Deploy

### 1. Create Azure Static Web App

1. Go to the [Azure Portal](https://portal.azure.com/)
2. Click on **Create a Resource** > **Static Web App**
3. Fill in the required details:
   - Subscription and Resource Group
   - Name your app (e.g., `taskhub`)
   - Select your region
   - Select **Other** for deployment source (since we will configure GitHub manually)
4. After creation, copy the **Deployment Token** (also called `azure_static_web_apps_api_token`)

### 2. Add the Token to GitHub Secrets

1. Go to your GitHub repository
2. Click on **Settings** > **Secrets and variables** > **Actions**
3. Add a new secret:
   - Name: `AZURE_STATIC_WEB_APPS_API_TOKEN_PROUD_TREE_0F206FD00`
   - Value: *Paste your deployment token here*

### 3. Create GitHub Workflow

Inside your project, create a `.github/workflows/azure-deploy.yml` file and add the following:

```yaml
name: Build And Deploy
on:
  push:
    branches:
      - main

jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Build And Deploy
        id: builddeploy
        uses: Azure/static-web-apps-deploy@v1
        with:
          azure_static_web_apps_api_token: ${{ secrets.AZURE_STATIC_WEB_APPS_API_TOKEN_PROUD_TREE_0F206FD00 }}
          action: "upload"
          app_location: "/" # App source code path
          api_location: ""  # API path if any
          output_location: "/" # Build output directory
          skip_app_build: true
          github_id_token: ${{ steps.idtoken.outputs.result }}
```

### 4. Commit and Push

Push your code to the `main` branch. GitHub Actions will trigger the workflow and deploy your app.

### 5. Verify Deployment

- Visit the **URL** provided by Azure Static Web Apps.
- You should see your deployed static website.

## 📘 Notes

- If you have a frontend build process (e.g., React, Vue), set `skip_app_build` to `false` and specify the correct `output_location`.
- You can connect a custom domain via the Azure Portal.

---

© 2025 - Deployment via Azure Static Web Apps + GitHub Actions.