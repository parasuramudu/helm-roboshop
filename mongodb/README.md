<!-- # apiVersion: apps/v1
# kind: StatefulSet
# metadata:
#   name: mongodb
#   namespace: roboshop
#   labels:
#     app: mongodb
#     tier: DB
#     project: roboshop
# spec:
#   replicas: 1
#   selector:
#     matchLabels:
#       app: mongodb
#       tier: DB
#       project: roboshop
#   template:
#     metadata:
#       name: mongodb
#       labels:
#         app: mongodb
#         tier: DB
#         project: roboshop
#     spec:
#       containers:
#       - name: mongodb
#         image: parasuramkoppada/mongodb:k8
#         volumeMounts:
#         - name: mongodb
#           mountPath: /data/db
#   volumeClaimTemplates:
#   - metadata:
#       name: mongodb
#     spec:
#       accessModes: ["ReadWriteOnce"]
#       storageClassName: "ebs-sc"
#       resources:
#         requests:
#           storage: 1Gi
# ---
# apiVersion: v1
# kind: Service
# metadata:
#   name: mongodb
#   namespace: roboshop
#   labels:
#     app: mongodb
#     tier: DB
#     project: roboshop
# spec:
#   clusterIP: None
#   selector:
#     # you should provide pod labels here
#     app: mongodb
#     tier: DB
#     project: roboshop
#   ports:
#   - name: mongo-port
#     protocol: TCP
#     # service port
#     port: 27017
#     # pod port
#     targetPort: 27017 -->
