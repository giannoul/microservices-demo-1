#### How to run the pipeline
1. `make kind-create`
2. `make deploy-argo-workflows`
3. `make apply-example-manifests`

Then on  anew shell run `make expose-argo-workflows-dashboard` and go to `https://localhost:2746/workflows` in order to see it in action.