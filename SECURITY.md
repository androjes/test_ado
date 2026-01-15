
# Sécurité
- Activer **branch protection** sur `main` (reviews + status checks).
- Secrets : utiliser `AZURE_CREDENTIALS` au format `--sdk-auth`.
- Scans : CodeQL + Dependabot sont activés via workflows/Dependabot.
- Éviter les secrets en clair (préférer Key Vault si nécessaire).
