# Complete-app-deployment-with-gitops
This repo mirrow a python app deployment to a kubernetes cluster using Helm, gitactions and ArgoCD

## App Structure
App source - https://github.com/ChisomJude/student-progress-tracker2

```
my-repo/
├─ Dockerfile
├─ requirements.txt
├─ src/
│  └─ app/                 # your FastAPI (etc.) already here
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

