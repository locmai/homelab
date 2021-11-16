.POSIX:
.EXPORT_ALL_VARIABLES:

KUBECONFIG = ../metal/kubeconfig.yaml

default: charts apply

charts:
	helm dependency update

apply:
	# ArgoCD only uses Helm as YAML generator
	helm template . | kubectl apply -f -
