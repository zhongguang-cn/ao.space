# 构建部署

[English](build-and-deploy.md) | 简体中文

## Source code download

请按顺序执行一下命令，下载整个项目源码:

- 创建本地目录， 执行命令: `mkdir ao.space`
- 进入项目目录，执行命令: `cd ao.space`
- 初始化，执行命令: `git submodule init`
- 下载源码，执行命令: `git submodule update`

## 构建和部署

### 平台构建和部署

我们在 [platform-deploy仓库](https://github.com/ao-space/platform-deploy) 中详细介绍了平台的构建和部署过程。

需要提醒的是上述过程使用了 platform-deploy 仓库中的 docker-compose.yml 文件来编排相关组件的容器部署，其所使用的镜像为 github 镜像仓库中 dev 分支的最新镜像。

如果您希望用本地自己构建的镜像来替换部分组件，可将相关组件的 image 项修改为您自己编译的镜像地址，并执行 `docker-compose up -d` 命令即可。

### 服务端构建和部署 @xuyang

#### 环境准备

- docker (>=18.09)
- git
- golang 1.18 +

#### 服务端构建

docker镜像构建方式基本一样，都是用Dockerfile来构建镜像

构建之前，我想提醒您，如果您希望用本地自己构建的镜像来运行傲空间

建议您先构建除了 space-agent 之外的其他镜像，最后再构建space-agent 

在构建 aospace-agent 之前， 需要将 space-agent/res/docker-compose_run_as_docker.yml （win/Mac）

或者 space-agent/res/docker-compose_run_as_docker_network_mode_host.yml （linux） 中的相关 image 项修改为您自己编译的镜像地址

例如这里用的 *local/space-aofs:{tag}* 

```shell
#构建镜像

cd space-aofs ; docker build -t local/space-aofs:{tag} .
cd space-gateway ; docker build -t local/space-gateway:{tag} .
cd space-web ; docker build -t local/space-web:{tag} .
cd space-filepreview ; docker build -t local/space-filepreview:{tag} .
cd space-media-vod ; docker build -t local/space-media-vod:{tag} .
cd space-postgresql;docker build -t local/space-postgresql:{tag} .
cd space-agent ; docker build -t local/space-agent:{tag} .

```

可以通过 `docker images` 查看自己是否构建成功
#### 服务端部署

全部构建完成后，您可以开始部署自己的傲空间

确保space-agent 中的docker-compose 文件在编译前已被修改使用本地的image后

使用以下命令部署并运行

- Linux

```shell
        sudo docker network create ao-space;
        sudo docker run -d --name aospace-all-in-one  \
        --restart always  \
        --network=ao-space  \
        --publish 5678:5678  \
        --publish 127.0.0.1:5680:5680  \
        -v $AOSPACE_HOME_DIR:/aospace  \
        -v /var/run/docker.sock:/var/run/docker.sock:ro  \
        -e AOSPACE_DATADIR=$AOSPACE_HOME_DIR \
        -e RUN_NETWORK_MODE="host"  \
        local/space-agent:{tag}
```
你需要将{tag} 修改为自己本地构建的镜像tag

- Windows

```shell
docker network create ao-space
docker run -d --name aospace-all-in-one `
--restart always `
--network=ao-space `
--publish 5678:5678 `
--publish 127.0.0.1:5680:5680 `
-v c:/aospace:/aospace ` # you can change c:/ to your own disk ,like d:/
-v //var/run/docker.sock:/var/run/docker.sock:ro `
-e AOSPACE_DATADIR=/run/desktop/mnt/host/c/aospace `
local/space-agent:{tag}
```
你需要将{tag} 修改为自己本地构建的镜像tag

- MacOS

```zsh
docker network create ao-space
HOME="/Users/User-Name-Here" # you can change User-Name-Here to your own name
DATADIR="$HOME/aospace"
docker run -d --name aospace-all-in-one  \
--restart always  \
--network=ao-space  \
--publish 5678:5678  \
--publish 127.0.0.1:5680:5680  \
-v $DATADIR:/aospace  \
-v /var/run/docker.sock.raw:/var/run/docker.sock:ro  \
-e AOSPACE_DATADIR=$DATADIR  \
local/space-agent:{tag}
```
你需要将{tag} 修改为自己本地构建的镜像tag

### 客户端构建和运行  @fuyu

Android 和 iOS 分开写

## Release 版本下载和部署

### Platform download and deploy

你可以在 [这里](https://ao.space/download/platform) 找到我们最新发布的版本，解压缩后，按照 README.md 文档进行部署。

### Server download and deploy @xuyang

你可以在[这里]()找到我们最新发布的版本

如果你想要安装最新版本的傲空间

#### 环境准备

- docker (>=18.09) 

#### 安装部署

- Linux

```shell
        sudo docker network create ao-space;
        sudo docker run -d --name aospace-all-in-one  \
        --restart always  \
        --network=ao-space  \
        --publish 5678:5678  \
        --publish 127.0.0.1:5680:5680  \
        -v $AOSPACE_HOME_DIR:/aospace  \
        -v /var/run/docker.sock:/var/run/docker.sock:ro  \
        -e AOSPACE_DATADIR=$AOSPACE_HOME_DIR \
        -e RUN_NETWORK_MODE="host"  \
        ghcr.io/ao-space/space-agent:dev
```
你需要将{tag} 修改为自己本地构建的镜像tag

- Windows

```shell
docker network create ao-space
docker run -d --name aospace-all-in-one `
--restart always `
--network=ao-space `
--publish 5678:5678 `
--publish 127.0.0.1:5680:5680 `
-v c:/aospace:/aospace ` # you can change c:/ to your own disk ,like d:/
-v //var/run/docker.sock:/var/run/docker.sock:ro `
-e AOSPACE_DATADIR=/run/desktop/mnt/host/c/aospace `
ghcr.io/ao-space/space-agent:dev
```

- MacOS

```zsh
docker network create ao-space
HOME="/Users/User-Name-Here" # you can change User-Name-Here to your own name
DATADIR="$HOME/aospace"
docker run -d --name aospace-all-in-one  \
--restart always  \
--network=ao-space  \
--publish 5678:5678  \
--publish 127.0.0.1:5680:5680  \
-v $DATADIR:/aospace  \
-v /var/run/docker.sock.raw:/var/run/docker.sock:ro  \
-e AOSPACE_DATADIR=$DATADIR  \
ghcr.io/ao-space/space-agent:dev
```

更多部署文档请参考[官网](https://ao.space/open/documentation/105001)

### Clients download and run  @fuyu
