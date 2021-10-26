# nvjdc
Net core5  vue3 puppeteer sharp的一次尝试

## 提示
由于我自己的环境是centos x86，理论是支持arm的需要自行测试

## 安装教程
1 执行命令

```
yum install wget unzip -y
```

2创建一个目录放配置以及chromium

```
mkdir nolanjdc && cd nolanjdc
```

3下载config.json 配置文件 并且修改自己的配置 不能缺少

```
wget -O Config.json  https://raw.githubusercontent.com/NolanHzy/nvjdc/main/Config.json
```
国内请使用
 ```
wget -O Config.json   https://ghproxy.com/https://raw.githubusercontent.com/NolanHzy/nvjdc/main/Config.json
```

4 创建chromium文件夹并进入

```
mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
```

5下载 chromium 

```
wget https://mirrors.huaweicloud.com/chromium-browser-snapshots/Linux_x64/884014/chrome-linux.zip && unzip chrome-linux.zip
```

6删除刚刚下载的压缩包 

```
rm  -f chrome-linux.zip
```

7 回到刚刚创建的目录

```
cd  /nolanjdc
```

8拉镜像

```
sudo docker pull nolanhzy/nvjdc:0.2
```

9启动镜像

```
sudo docker run   --name nolanjdc -p 5701:80 -d  -v  "$(pwd)"/Config.json:/app/Config/Config.json:ro \
-v "$(pwd)"/.local-chromium:/app/.local-chromium  \
-it --privileged=true  nolanhzy/nvjdc:0.1 
```

10查看 日志 

```
docker logs -f nolanjdc 

```

  

出现 NETJDC  started 即可 


## 修改消息推送二维码
```
docker exec -it nolanjdc /bin/bash
```

```
cd wwwroot/img
```
下载你的二维码文件
```
wget -O push.png 你的二维码链接
```
或者删除二维码
```
rm -f push.png
```
## 更新
```
docker rm -f nolanjdc 
```
```
docker rm -f nolanhzy/nvjdc:0.1
```
之前安装过 浏览器的可以不用再次安装。 配置文件里多了一些配置 建议拉取新的配置

## 注意事项

容器启动后第一次获取验证码的时候可能卡住刷新一下即可

Config.json 是配置文件 可以热更新 修改后不用重启容器

## 最后
觉得不错。回来帮我点个stars
