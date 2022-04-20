.PHONY: kind-create
kind-create:
	kind \
	  create \
	  cluster \
	  --name kind-labs-cluster \
	  --config .kind/kind.conf

.PHONY: kind-delete
kind-delete:
	kind \
	  delete \
	  cluster \
	  --name kind-labs-cluster


.PHONY: deploy-argo-workflows
deploy-argo-workflows:
	kubectl create ns argo
	kubectl apply -n argo -f https://raw.githubusercontent.com/argoproj/argo-workflows/master/manifests/quick-start-minimal.yaml

.PHONY: expose-argo-workflows-dashboard
expose-argo-workflows-dashboard:
	kubectl port-forward svc/argo-server -n argo 2746:2746

.PHONY: apply-example-manifests
apply-example-manifests:
	kubectl apply -k manifests

.PHONY: delete-example-manifests
delete-example-manifests:
	kubectl delete -k manifests
	