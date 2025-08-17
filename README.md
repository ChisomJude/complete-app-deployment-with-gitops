# Complete-app-deployment-with-gitops
This repo mirrow a python app deployment to a kubernetes cluster using Helm, gitactions and ArgoCD

## App Structure
Origin App source - https://github.com/ChisomJude/student-progress-tracker2

```
my-repo/
├─ Dockerfile
├─ requirements.txt
├─ src/
│  └─ app/                 # your FastAPI 
│     ├─ main.py
│     └─ ... 
├─ .github/
│  └─ workflows/
│     └─ ci.yaml           # Builds/pushes image + bumps Helm tag
└─ helm/
   └─ student-progress/
      ├─ Chart.yaml
      ├─ values.yaml
      └─ templates/
         ├─ deployment.yaml
         ├─ service.yaml
         ├─ secret-vault.yaml
         └─ _helpers.tpl


```

## Ensure to Apply your application locally on the cluster

kubectl apply -n argocd -f argocd/student-progress-app.yaml

## Create your APP secret as well 

kubectl -n my-app create secret generic vault-secrets \
  --from-literal=VAULT_ADDR="http://44.204.193.107:8200" \
  --from-literal=VAULT_ROLE_ID="..." \
  --from-literal=VAULT_SECRET_ID="..."