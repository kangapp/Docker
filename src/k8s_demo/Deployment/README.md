# Deployment 基础

>     kubectl get deployment   # 获取deployment列表信息  

>     kubectl get deployment -o wide   # 获取获取deployment的更多信息

>     kubectl set image deployment nginx-deployment nginx=nginx:1.13 --record=true  #升级image版本

>     kubectl rollout history deployment nginx-deployment  # 获取更新历史

>     kubectl rollout undo deployment nginx-deployment  # 回滚到上一个版本

>     kubectl rollout undo deployment nginx-deployment --to-revision=2  # 回滚到指定版本

>     kubectl scale deployment nginx-deployment --replicas=10  # 动态伸缩pod

>     kubectl edit deployment service-test  # 进入yml编辑页面
