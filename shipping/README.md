<!-- # apiVersion: v1
# kind: ConfigMap
# metadata:
#   name: shipping-config
# data:
#   CART_ENDPOINT: cart:8080
#   DB_HOST: mysql
# ---
# apiVersion: apps/v1
# kind: Deployment
# metadata:
#   name: shipping
#   namespace: roboshop
#   labels:
#     app: shipping
#     tier: app
#     project: roboshop
# spec:
#   replicas: 1
#   selector:
#     matchLabels:
#       app: shipping
#       tier: app
#       project: roboshop
#   template:
#     metadata:
#       name: shipping
#       labels:
#         app: shipping
#         tier: app
#         project: roboshop
#     spec:
#       containers:
#       - name: shipping
#         image: parasuramkoppada/shipping:k8
#         envFrom:
#         - configMapRef:
#             name: shipping-config
# ---
# apiVersion: v1
# kind: Service
# metadata:
#   name: shipping
#   namespace: roboshop
#   labels:
#     app: shipping
#     tier: app
#     project: roboshop
# spec:
#   selector:
#     # you should provide pod labels here
#     app: shipping
#     tier: app
#     project: roboshop
#   ports:
#   - name: shipping-port
#     protocol: TCP
#     # service port
#     port: 8080
#     # pod port
#     targetPort: 8080 -->
