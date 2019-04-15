# Serviece 基础

>     kubectl get svc   # 获取service列表信息  

>     kubectl expose pods nginx-pod  # 为pod资源创建默认的service，ClusterIP  
>     kubectl expose deployment service-test  # 为deployment资源创建默认的service，ClusterIP  
>     --type 指定service类型

## NodePort类型的service

```bash
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  ports:
  - port: 8080
    nodePort: 32100
    targetPort: nginx-port
    protocol: TCP
  selector:
    app: nginx
  type: NodePort
```

> 可以通过集群[nodeIP]:[nodePort]访问  
> 也可以通过[clusterIp]:[port]访问，kubectl get service 查看service对应的clusterIp
