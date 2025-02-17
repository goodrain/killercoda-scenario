### 一、安装 Rainbond

使用以下命令安装 Rainbond

Run `curl -o install.sh https://get.rainbond.com && export IMGHUB_MIRROR=rainbond && echo | bash ./install.sh`{{exec}}

### 二、检查 Rainbond

> killercoda 提供的环境只有 4GB 内存，也许要多等待几分钟

使用以下命令确认 Rainbond 是否正常启动

Run `docker exec -it rainbond bash`{{exec}}

Run `kubectl get pod -n rbd-system`{{exec}}

出现以下 Pods 代表正常，请继续下一步

```bash
NAME                                      READY   STATUS
helm-install-rainbond-cluster-657rg       0/1     Completed
local-path-provisioner-766d4c5cb4-bv7jg   1/1     Running
minio-0                                   1/1     Running
rainbond-operator-745d5954b5-z2jlh        1/1     Running
rbd-api-78cd5f485b-7nf6c                  1/1     Running
rbd-app-ui-59b854c868-dhj58               1/1     Running
rbd-chaos-9dxjc                           1/1     Running
rbd-gateway-5f4c47fbcc-j57w9              2/2     Running
rbd-hub-5c7c695f97-fttvn                  1/1     Running
rbd-monitor-0                             1/1     Running
rbd-mq-6c88789769-97f64                   1/1     Running
rbd-worker-676f8cc8b4-bzg6j               1/1     Running
```

### 三、访问 Rainbond

现在你就可以通过这个链接 [endpoint]({{TRAFFIC_HOST1_7070}}) 访问 Rainbond 页面了。

### 四、配置 WebSocket

[killercoda](https://github.com/killercoda/scenario-examples/blob/main/network-traffic/step1.md) 只允许通过端口转发的方式访问，所以需要修改 Rainbond 的 WebSocket 地址才能正常使用日志推送功能。

进入 Rainbond 的 `平台管理 -> 集群 -> 编辑集群`，修改 WebSocket地址为 `wss://` ，请从这个链接 [endpoint]({{TRAFFIC_HOST1_6060}}) 中复制 URL （不带HTTPS）。


> killercoda 提供的环境磁盘可使用仅有 15G 左右，因此需要清理掉安装后的镜像包。  
> `rm -f /opt/rainbond/k3s/agent/images/rbd-images.tar`{{exec}}