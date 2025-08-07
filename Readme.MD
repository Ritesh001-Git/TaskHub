
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
