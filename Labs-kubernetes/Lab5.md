# Instrucciones Laboratorio 5 - Kubernetes - HPA
En este laboratorio vamos a crear un HPA y ver cómo aumenta y disminuye el nº de réplicas en función de la carga de la aplicación

  [jota@curso ~]$ kubectl apply -f https://k8s.io/examples/application/php-apache.yaml
  deployment.apps/php-apache created
  service/php-apache created
