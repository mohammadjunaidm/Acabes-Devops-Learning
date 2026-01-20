i created this pod yaml with 2 containers and executed into the business-app container and curl the localhost with port 8080

yaml:
apiVersion: v1
kind: Pod
metadata:
  name: rate-limiter
  namespace: junaid
spec:
  container:
  - name: business-app
    image: business-app-image
    ports:
    - containerPort: 8080
      - name: ambassador
        image: ambassador-image
        ports:
        - containerPort: 8081
      restartPolicy: Never                                                        

        
     
