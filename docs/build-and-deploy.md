# build and deploy

Englis | [简体中文](build-and-deploy_CN.md)

## Source code download

Please execute the following command to download the entire source code of the project:

- Create a local directory, run cmd: `mkdir ao.space`
- Enter the folder/directory, run cmd: `cd ao.space`
- Init submodule, run cmd: `git submodule init`
- Download source code, run cmd: `git submodule update`

## Build and deploy

### Platform build and deploy @zuling
<!-- 包括环境准备、构建和部署 !-->

### Server build and deploy @xuyang
#### 环境准备

- docker (>=18.09)
- git
- golang 1.18 +

#### 服务端构建

Docker images are built in basically the same way, using a Dockerfile to build the image.

Before building, I would like to remind you that if you want to run space-agent with your own locally-built image, it is recommended that you build all the images except space-agent first, and then build space-agent last.

It is recommended that you build everything except space-agent first, and then build space-agent last.

Before building aospace-agent, you need to set space-agent/res/docker-compose_run_as_docker.yml (Win/Mac)

or space-agent/res/docker-compose_run_as_docker_network_mode_host.yml (linux) to the address of the image you compiled.

For example, *local/space-aofs:{tag}* is used here.

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
#### 服务端部署

Once all the builds are complete, you can start deploying your own AOspace

After making sure that the docker-compose file in space-agent has been modified before compiling using a local image

Use the following command to deploy and run

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
you need to change {tag} to your own build tag
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
you need to change {tag} to your own build tag
- MacOS

```bash
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
local/space-agent:{tag}  # you can change {tag} to your own build tag
```
you need to change {tag} to your own build tag

### Clients build and run  @fuyu
<!-- 包括环境准备、构建和部署 !-->

## Release download and deply

### Platform download and deploy @zuling

### Server download and deploy @xuyang

you can find our newest published image at [here]()

if you want to deploy newest AOspace

#### Prepare Environment

- docker (>=18.09)

#### Deploy

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

more docs refer to [AOspace Website](https://ao.space/open/documentation/105001)

### Clients download and run  @fuyu
