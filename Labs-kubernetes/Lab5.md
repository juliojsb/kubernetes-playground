# Instrucciones Laboratorio 5 - Kubernetes - HPA
En este laboratorio vamos a crear un HPA y ver cómo aumenta y disminuye el nº de réplicas en función de la carga de la aplicación

Creamos el HPA:

	$ vi deployment-apache.yaml
 
	apiVersion: apps/v1
	kind: Deployment
	metadata:
	  name: apache
	spec:
	  selector:
	    matchLabels:
	      run: apache
	  template:
	    metadata:
	      labels:
	        run: apache
	    spec:
	      containers:
	      - name: apache
	        image: registry.k8s.io/hpa-example
	        ports:
	        - containerPort: 80
	        resources:
	          limits:
	            cpu: 500m
	          requests:
	            cpu: 200m

 	$ vi svc-apache.yaml
  
	apiVersion: v1
	kind: Service
	metadata:
	  name: apache
	  labels:
	    run: apache
	spec:
	  ports:
	  - port: 80
	  selector:
	    run: apache

	$ kubectl apply -f deployment-apache.yaml
 	$ kubectl apply -f svc-apache.yaml

Comprobamos que se han creado los recursos:

	$ kubectl get pod
 	$ kubectl get deploy
  	$ kubectl get svc

En este ejemplo
