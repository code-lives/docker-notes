# 命令
### 服务器鉴权 [把公司镜像服务地址+账号+密码绑定到k8s]
```
kubectl create secret docker-registry lsbb-reg --docker-server=registry.cn-beijing.aliyuncs.com --docker-username=[$Username] --docker-password=[$Password] --docker-email=[$Email]
```
### ssl证书
```
kubectl create secret tls 【自定义名称】 --key 【证书key】 --cert 【证书pem】 【namespace】
```
### 常用命令
```
kubectl get pod 
kubectl exec -it pod名字 sh
kubectl apply -f deployment.yml
```

### pod 扩展数量
```
kubectl scale deployment pod名称 --replicas=100
```
### yml 更新
```
kubectl create -f deployment.yml --dry-run=client -o yaml |kubectl apply  -f -
```
### 启动pod
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app-release
  namespace: release
spec:
  replicas: 1 # 启动几个pod
  selector:
    matchLabels:
      app: app-release
  template:
    metadata:
      labels:
        app: app-release #  pod的名称 对应Service 下面app-name
    spec:
      containers:
        - name: app-release
          image: nginx //容器的路径+版本 docker pull nginx:1.1 或者 某个容器库
          imagePullPolicy: "Always"
          ports:
            - containerPort: 80
```
### Service 对外暴露 配置
```
apiVersion: v1
kind: Service
metadata:
  name: app-release
  namespace: release
spec:
  selector:
    app: app-release # 对应的app-name 
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80 # 容器的端口
```
### Ingress 网络配置
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: app-release
  namespace: release
spec:
  rules:
    - host: www.baidu.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: app-release # Service下面 metadata->name
                port:
                  number: 80  # Service下面 metadata->port
  tls:
    - hosts:
        - www.baidu.com
      secretName: app-release
```
