
# Plateforme DevOps Démo (GitHub + Azure)

Cette démo déploie une application Node.js Hello World sur **Azure App Service** via **GitHub Actions**.

## Contenu
- Application Node.js minimaliste (Express)
- IaC **Bicep** pour créer le groupe de ressources + App Service + Plan
- Workflow **GitHub Actions** CI/CD
- Sécurité : **Dependabot**, **CodeQL**, **branch protection (à configurer)**

## Architecture
GitHub (code, PR, sécurité) → GitHub Actions (CI/CD) → Azure (App Service) 

## Mise en route (10-20 min)
1. Crée un repo GitHub et pousse ce contenu.
2. Dans Azure Portal, crée une **Service Principal** et colle le JSON dans `Settings > Secrets and variables > Actions > Repository secrets` sous la clé `AZURE_CREDENTIALS`.
   - Génère via Azure CLI :
     ```bash
     az ad sp create-for-rbac --name github-sp --role contributor            --scopes /subscriptions/<SUB_ID> --sdk-auth
     ```
3. Ouvre `.github/workflows/ci-cd.yml` et remplace `app-name` et `resourceGroupName` si besoin.
4. Push sur `main` → le workflow provisionne l’infra (Bicep) puis déploie l’app.

## Nettoyage
```bash
az group delete -n rg-devops-demo -y
```
