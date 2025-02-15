### 安装 Rainbond

1. 添加 Helm 仓库。

Run `helm repo add rainbond https://chart.rainbond.com && helm repo update`{{exec}}

2. 使用 Helm 安装 Rainbond。

Run `helm install rainbond rainbond/rainbond --create-namespace -n rbd-system --set Cluster.rainbondImageRepository=rainbond`

3. 访问 Rainbond

现在你就可以通过这个链接 [endpoint]({{TRAFFIC_HOST1_7070}}) 访问 Rainbond 页面了。