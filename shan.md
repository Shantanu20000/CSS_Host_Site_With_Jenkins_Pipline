```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: css-deployment-1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: css
  template:
    metadata:
      labels:
        app: css
    spec:
      containers:
      - name: css
        image: shan20000/css_template:latest
        imagePullPolicy: Always
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: css-service
spec:
  selector:
    app: css # This should match the labels in the deployment
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer 
```