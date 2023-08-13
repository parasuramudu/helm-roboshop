<!-- apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: redis
  namespace: roboshop
  labels:
    app: redis
    tier: DB
    project: roboshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis
      tier: DB
      project: roboshop
  template:
    metadata:
      name: redis
      labels:
        app: redis
        tier: DB
        project: roboshop
    spec:
      containers:
      - name: redis
        image: redis
        volumeMounts:
        - name: redis
          mountPath: /data
  volumeClaimTemplates:
  - metadata:
      name: redis
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
  name: redis
  namespace: roboshop
  labels:
    app: redis
    tier: DB
    project: roboshop
spec:
  clusterIP: None
  selector:
    # you should provide pod labels here
    app: redis
    tier: DB
    project: roboshop
  ports:
  - name: redis-port
    protocol: TCP
    # service port
    port: 6379
    # pod port
    targetPort: 6379 -->
