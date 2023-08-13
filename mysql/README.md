<!-- apiVersion: v1
kind: ConfigMap
metadata:
  name: mysql-config
  namespace: roboshop
data:
  MYSQL_ALLOW_EMPTY_PASSWORD: "yes"
  MYSQL_DATABASE: cities
  MYSQL_USER: shipping
  MYSQL_PASSWORD: secret
---
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: mysql
  namespace: roboshop
  labels:
    app: mysql
    tier: DB
    project: roboshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mysql
      tier: DB
      project: roboshop
  template:
    metadata:
      name: mysql
      labels:
        app: mysql
        tier: DB
        project: roboshop
    spec:
      containers:
      - name: mysql
        image: parasuramkoppada/mysql:k8
        args:
        - "--ignore-db-dir=lost+found"
        envFrom:
        - configMapRef:
            name: mysql-config
        volumeMounts:
        - name: mysql
          mountPath: /var/lib/mysql
  volumeClaimTemplates:
  - metadata:
      name: mysql
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
  name: mysql
  namespace: roboshop
  labels:
    app: mysql
    tier: DB
    project: roboshop
spec:
  clusterIP: None
  selector:
    # you should provide pod labels here
    app: mysql
    tier: DB
    project: roboshop
  ports:
  - name: mysql-port
    protocol: TCP
    # service port
    port: 3306
    # pod port
    targetPort: 3306 -->
