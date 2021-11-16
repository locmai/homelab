.POSIX:
.EXPORT_ALL_VARIABLES:

KUBECONFIG = ../metal/kubeconfig.yaml

default: charts apply

charts:
	helm dependency update

namespace:
	kubectl create namespace argocd --dry-run=client --output=yaml \
		| kubectl apply -f -

apply: namespace
	# ArgoCD only uses Helm as YAML generator
	helm template --include-crds argocd . \
		| kubectl apply -n argocd -f -
