# ao.space

Englis | [简体中文](./README_CN.md)

AO.space is a solution that focuses on protecting personal data security and privacy. Utilizing end-to-end encryption and device-based authentication, users have complete control over their personal accounts and data. AO.space also employs various technologies, including transparent platform forwarding, peer-to-peer acceleration, and LAN direct connection, to enable fast access to personal data from anywhere at any time. Leveraging Progressive Web App and cloud-native technology, AO.space has developed an integrated application ecosystem that could include both front-end and back-end components.

AO.space is composed of three parts: server-side, client-side, and platform. The server-side and client-side run on personal devices and establish encrypted communication channels with public key authentication. The server-side supports x86_64 and aarch64 architectures and can run on personal servers, computers, or other similar devices. The client-side supports Android, iOS, and web platforms, providing users with the convenience of using AO.space anywhere and anytime.

## Architecture @haibo

- 系统架构介绍，以及主要工作方式。

更多内容，请访问 [官网](https://ao.space/blog)。

## Source code repository introduction

The overall project includes ：

- [./platform](./platform/)
- [./server](./server/)
- [./client](./client/) 。

### Platform repository introduction  @zuling

- 空间平台各模块介绍，包括模块名称，仓库地址，及主要功能

### Server repository introduction @zhongguang

The server is the main data carrier of AO.space and is also the core of data protection. It consists of the following repositories:
  
- [space-agent](https://github.com/ao-space/space-agent)：It provides services such as device binding, system service module startup bootstrapping, and management.
- [space-aofs](https://github.com/ao-space/space-aofs)：It provides file access services, including interfaces for file querying, chunked uploading, downloading, and more.
- [space-gateway](https://github.com/ao-space/space-gateway)：The end-to-end request security processing module receives requests, decrypts them, and forwards them to the relevant modules. It encrypts the responses and sends them back to the requesting client.
- [space-filepreview](https://github.com/ao-space/space-filepreview)：It supports the generation of thumbnails and preview images for media files. This functionality allows users to generate smaller versions or preview images of their media files, which can be useful for displaying file previews or creating thumbnails for faster loading.
- [space-media-vod](https://github.com/ao-space/space-media-vod)：Provide streaming media data access services
- [space-web](https://github.com/ao-space/space-web)：Providing an Nginx reverse proxy service for serving web-based service resources and requests

### Clients repository introduction @fuyu

客户端为傲空间的交互入口，让用户可在不同平台上快速安全的访问个人数据，由如下仓库组成：

- [client-android](https://github.com/ao-space/client-android)：Android平台客户端
- [client-ios](https://github.com/ao-space/client-ios)：iOS平台客户端

## Build and deploy

To deploy and run the project from a release version, or to build and run it from the source code, please refer to [build-and-deploy](./docs/build-and-deploy.md).

## 文档

- 跳转 api-doc 模块部署的 url

## 常见问题  @daqing

## 联系我们及协作贡献方式  @daqing

### 讨论组入口

### 提交问题的方式

### 提交代码的方式

## License

AO.space is open-sourced under Apache License 2.0, see [LICENSE](xxx).
非 2.0 的列出来。

## 致谢

AO.space heavily relies on the open-source achievements of other projects. We would like to express our special thanks to them: [Redis](xx)、[Postgres](xxx)、 [Mysql](xxx)、[OpenResty](xxx) and so on。

Finally, thank you for your contribution to this project. We welcome contributions in all forms, including but not limited to code contributions, issue reports, feature requests, documentation writing, etc. We believe that with your help, this project will become more perfect and stronger.
