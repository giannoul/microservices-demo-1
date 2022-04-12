PWD       = $(shell pwd)

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


.PHONY: deploy-tekton
deploy-tekton:
	kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
	kubectl apply --filename https://github.com/tektoncd/dashboard/releases/latest/download/tekton-dashboard-release.yaml
	kubectl apply --filename https://storage.googleapis.com/tekton-releases/triggers/latest/release.yaml
	kubectl apply --filename https://storage.googleapis.com/tekton-releases/triggers/latest/interceptors.yaml

.PHONY: expose-tekton-dashboard
expose-tekton-dashboard:
	kubectl port-forward svc/tekton-dashboard -n tekton-pipelines 9097:9097