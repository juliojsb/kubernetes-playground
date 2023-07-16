# Troubleshooting

	$ kubectl get nodes
	$ kubectl cluster-info
	$ kubectl cluster-info dump

Logs de componentes:

	$ /var/log/kube-apiserver.log
	$ /var/log/kubelet.log

Logs e info de aplicación, servicios...
	
	$ kubectl logs [pod-name]
	$ kubectl describe pod [pod-name]
	$ kubectl get endpoints [service-name]
