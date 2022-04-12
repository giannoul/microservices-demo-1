#### How to create the contents for the file `ssh-key_secret.yaml`
```
kubectl create secret generic ssh-key-secret --from-file=ssh-privatekey=/home/ilias/.ssh/id_rsa  --from-file=known_hosts=/home/ilias/.ssh/known_hosts --from-file=config=/home/ilias/.ssh/config  --dry-run=client  -o yaml
```

and then add the annotation:
```
 annotations:
   tekton.dev/git-0: github.com
```

#### How to run the pipeline
1. `make kind-create`
2. `make deploy-tekton`
3. apply manifests via:
```
kubectl apply -f ssh-key_secret.yaml
kubectl apply -f dockerhub_secret.yaml
kubectl apply -f service_account.yaml
kubectl apply -f task_git_clone.yaml
kubectl apply -f task_kaniko.yaml
kubectl apply -f pipeline.yaml
kubectl apply -f pipelinerun.yaml
```