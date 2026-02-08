charts.yaml

    apiVersion: 1.0.0
    name: web-app
    version: 2.5.5
--------------------------------------------------------------------

values.yaml

    service_port: 80
    container_port: 8080
--------------------------------------------------------------------
create a template directory - 

    mkdir templates

--------------------------------------------------------------------
create deployment yaml for the app within the templates directory

    apiVersion: v1
    kind: Deployment
    metadata:
      name: my-app
      labels: 
       app: prod
    
    spec:
     Containers:
      - image: dummy-image
        name: junaid-container
        ports:
        - ContainerPort: {{.Values.container_port}}
          protocol: TCP


-------------------------------------------------------------------

Create a service yaml for the app within the same templates directory


    apiVersion: v1
    kind: Service
    metadata: 
      namespace: junaid-namespace
      labels:
       app: prod
    
    spec:
      type: ClusterIP
      selector:
        app: prod
      ports:
       protocol: TCP
       port: {{ .Values.service_port }}
       targetPort: {{ .Values.container_port }}



To create a Helm package, used this command

    helm package .

Helm is created as **.tgz**

Now to install into as helm chart, used this command....

    helm install --namespace web-app --create-namespace --set service-port=9090 hello-world .

Verified the service and pods using this command

    kubectl get services,pods -n web-app

Finally uninstalled it using the below command 

    helm uninstall hello-world -n web-app


Finally uninstalled it using this command

helm uninstall hello-world -n web-app


