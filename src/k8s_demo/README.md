# DEMO

- [Pod 基础](https://github.com/kangapp/Docker/tree/master/src/k8s_demo/pod-basic)

- [rc&&rs基础](https://github.com/kangapp/Docker/tree/master/src/k8s_demo/rc-rs-basic)

## kubectl 常用命令

>     kubectl create -f pod_ngin.yml    # 从文件创建资源  

>     kubectl delete -f pod_ngin.yml    # 从文件删除资源  

>     kubectl port-forward nginx 8080:80    # 映射pod端口到本地  

>     kubectl config use-context minikube  # 使用minikube作为context  

>     kubectl config view  # 当前config的详情  

>     kubectl config get-contexts # 查看当前存在的context  

>     kubectl get pods [-o wide] # 获取pod的[详细]信息  

>     kubectl describe pods nginx  # 获取某个资源的详细描述  

>     kubectl get node -o wide  # 获取集群节点信息