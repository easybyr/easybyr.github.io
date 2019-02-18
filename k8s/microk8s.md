### First step of kubernetes using microk8s

> Ubuntu16.04


install snap

```
$sudo apt-get install snapd
```


install microk8s
```
snap install microk8s --classic

microk8s.kubectl version
```

Start/status/stop kubernetes cluster
```
microk8s.start/status/stop
```

```
snap enable/disable microk8s
```

remove microk8s, 2 steps.
```
microk8s.reset
snap remove microk8s
```

run addons
```
microk8s.enable dns dashboard

microk8s.disable dns dashboard
```

在国内，GFW的原因，访问不到gcr（Google Container Registry，google镜像库），因此经常碰到如下类似错误：
```
failed pulling image k8s.gcr.io/pause:3.1
```

**解决办法**：手动下载镜像


首先去hub.docker.com上面找到相同的镜像并pull下来；

然后，重新打tag，错误提示找不到那个镜像，tag就打成什么名字。

microk8s也会自带一个docker，如果你的系统中已经安装了docker，microk8还是会用自带的docker。
```
microk8s.docker pull mirrorgooglecontainers/pause-amd64:3.1

microk8s.docker tag mirrorgooglecontainers/pause-amd64:3.1 k8s.gcr.io/pause:3.1
```


