# Instrucciones Laboratorio 5 - Kubernetes - HPA
En este laboratorio vamos a crear un HPA y ver cómo aumenta y disminuye el nº de réplicas en función de la carga de la aplicación

Creamos el HPA:

	[jota@curso ~]$ kubectl apply -f https://k8s.io/examples/application/php-apache.yaml
	deployment.apps/php-apache created
	service/php-apache created

Comprobamos que se ha creado:
	
	[jota@curso ~]$ kubectl get hpa
	NAME         REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
	php-apache   Deployment/php-apache   0%/50%    1         10        1          11d

En este ejemplo
