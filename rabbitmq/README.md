<!-- apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: rabbitmq
  namespace: roboshop
  labels:
    app: rabbitmq
    tier: DB
    project: roboshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: rabbitmq
      tier: DB
      project: roboshop
  template:
    metadata:
      name: rabbitmq
      labels:
        app: rabbitmq
        tier: DB
        project: roboshop
    spec:
      containers:
      - name: rabbitmq
        image: rabbitmq
        volumeMounts:
        - name: rabbitmq
          mountPath: /var/lib/rabbitmq
  volumeClaimTemplates:
  - metadata:
      name: rabbitmq
    spec:
      accessModes: ["ReadWriteOnce"]
      storageClassName: "ebs-sc"
      resources:
        requests:
          storage: 1Gi
---
apiVersion: v1
kind: Service
metadata:
  name: rabbitmq
  namespace: roboshop
  labels:
    app: rabbitmq
    tier: DB
    project: roboshop
spec:
  clusterIP: None
  selector:
    # you should provide pod labels here
    app: rabbitmq
    tier: DB
    project: roboshop
  ports:
  - name: rabbitmq-amq
    protocol: TCP
    # service port
    port: 5672
    # pod port
    targetPort: 5672
  - name: rabbitmq-http
    protocol: TCP
    # service port
    port: 15672
    # pod port
    targetPort: 15672 -->
