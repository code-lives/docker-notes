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
