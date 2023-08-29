# ao.space

[English](README.md) | 简体中文

AO.space（傲空间）是一个以保护个人数据安全和隐私为核心的解决方案。通过端对端加密、基于设备认证等技术，确保用户完全掌控个人账号和数据。同时，采用平台透明转发、点对点加速、局域网直连等技术，让用户随时随地的极速访问个人数据。傲空间利用 PWA（Progressive Web App）和云原生技术，设计并打造前后端一体的应用生态。

AO.space（傲空间）由服务端、客户端、平台三个部分组成。服务端和客户端只运行在个人设备上，使用公钥认证建立加密通信通道。服务端是傲空间管理保护用户数据的核心部分，目前支持 x86_64 和 aarch64 两个架构，可运行在个人服务器、个人计算机等设备上。客户端让用户在不同平台上快速安全的访问个人数据，目前支持多个平台，包括 Android、iOS 和 Web ，方便用户随时随地使用。

## 系统整体架构

- 系统架构介绍，以及主要工作方式。

更多内容，请访问 [官网](https://ao.space/blog)。

## 源码仓库介绍

项目整体包含三大部分 ：

- 空间平台 [platform](./platform/)
- 服务端 [server](./server/)
- 客户端 [client](./client/) 。

### 空间平台(platform)仓库介绍  @zuling

- 空间平台各模块介绍，包括模块名称，仓库地址，及主要功能

### 服务端(server)仓库介绍 @zhongguang

服务器为傲空间主要数据载体，也是数据保护的核心，由如下仓库组成：
  
- [space-agent](https://github.com/ao-space/space-agent)：提供设备绑定、系统服务模块启动引导和管理等服务
- [space-aofs](https://github.com/ao-space/space-aofs)：提供文件访问服务，包括文件查询、分片上传、下载等接口
- [space-gateway](https://github.com/ao-space/space-gateway)：端到端的请求安全处理模块，收到请求后解密后转发给相关模块，对回应加密后响应给请求端。
- [space-filepreview](https://github.com/ao-space/space-filepreview)：支持媒体文件的缩略图、预览图的生成
- [space-media-vod](https://github.com/ao-space/space-media-vod)：提供流媒体播放服务
- [space-web](https://github.com/ao-space/space-web)：提供 web 端的服务资源及请求的 nginx 反向代理服务

### 客户端（client）仓库介绍 @fuyu

客户端支持Android、iOS、web版本，由如下仓库组成：

- [client-android](https://github.com/ao-space/client-android)：提供 Android 端的傲空间客户端
- [client-ios](https://github.com/ao-space/client-ios)：提供 iOS 端的傲空间客户端
- [space-web](https://github.com/ao-space/space-web)：部署在 server 上，提供 web 端的傲空间客户端

## 构建和部署

从发布版进行部署，或从源码构建并部署，请参考 [build-and-deploy](./docs/build-and-deploy_CN.md)

## 文档

- 跳转 api-doc 模块部署的 url

## 贡献指南 

我们非常欢迎对本项目进行贡献。以下是一些指导原则和建议，希望能够帮助您参与到项目中来。

[贡献指南](./docs/contribution-guidelines_CN.md)

## 联系我们

- [傲空间官网](https://ao.space)
- [讨论组](https://slack.ao.space)
- [Twitter](https://twitter.com/AOspaceOSC)
- [Medium](https://medium.com/@aospacecommunity)

## License

AO.space is open-sourced under Apache License 2.0, see [LICENSE](xxx).
非 2.0 的列出来。

## 致谢

我们的项目，离不开其它项目的开源成果，在此特别感谢 [Redis](xx)、[Postgres](xxx)、 [Mysql](xxx)、[OpenResty](xxx) 等。

最后，感谢您对本项目的贡献。我们欢迎各种形式的贡献，包括但不限于代码贡献、问题报告、功能请求、文档编写等。我们相信在您的帮助下，本项目会变得更加完善和强大。
