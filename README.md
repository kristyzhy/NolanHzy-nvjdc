# nvjdc
Net core5  vue3 puppeteer sharp的一次尝试

## 提示
[TG 频道](https://t.me/joinchat/4nf-VfnBN6pmZDdl) 

[TG 群组](https://t.me/joinchat/dL-NJh1G6bc2OGM1) 

由于我自己的环境是centos x86，arm并未测试


更新自动五次滑块

在Fork就跑路

一个文档你们Fork啥啊，，
## 支持的架构
![image](https://user-images.githubusercontent.com/87279659/137679751-7c2e901f-0429-4c5c-a6d2-120b8848048f.png)
查看地址:https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md


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
sudo docker pull nolanhzy/nvjdc:0.3
```

9启动镜像

```
sudo docker run   --name nolanjdc -p 5701:80 -d  -v  "$(pwd)"/Config.json:/app/Config/Config.json:ro \
-v "$(pwd)"/.local-chromium:/app/.local-chromium  \
-it --privileged=true  nolanhzy/nvjdc:0.3 
```

10查看 日志 

```
docker logs -f nolanjdc 

```

  

出现 NETJDC  started 即可 



## 更新

删除容器
```
docker rm -f nolanjdc 
```
删除镜像
```
docker rm -f nolanhzy/nvjdc:0.2
```

进入你以前下载过 浏览器 和JSON配置的文件夹中 
如原来在 root 下 nolanjdc 文件夹中 下载的配置与浏览器
```
cd /root/nolanjdc 
``` 
然后重复后续步骤即可
## 注意事项

容器启动后第一次获取验证码的时候可能卡住刷新一下即可

Config.json 是配置文件 可以热更新 修改后不用重启容器

## 最后
觉得不错。回来帮我点个star
## 特别声明:

* 本仓库涉仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.

* 本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。

* Nolan对任何代码问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.

* 间接使用本仓库搭建的任何用户，包括但不限于建立VPS或在某些行为违反国家/地区法律或相关法规的情况下进行传播, Nolan对于由此引起的任何隐私泄漏或其他后果概不负责.

* 请勿将本项目的任何内容用于商业或非法目的，否则后果自负.

* 如果任何单位或个人认为该项目的脚本可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关代码.

* 任何以任何方式查看此项目的人或直接或间接使用本仓库项目的任何脚本的使用者都应仔细阅读此声明。Nolan 保留随时更改或补充此免责声明的权利。一旦使用并复制了任何本仓库项目的规则，则视为您已接受此免责声明.

**您必须在下载后的24小时内从计算机或手机中完全删除以上内容.**  </br>
> ***您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读***

## 多谢

