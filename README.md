# ao.space

English | [简体中文](./README_CN.md)

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

### Platform repository introduction

The responsibility of AO.space Platform is to establish a transparent communication channel for personal equipment. It consists of the following repositories:

- [platform-proxy](https://github.com/ao-space/platform-proxy)：provide high-availability forwarding and horizontal expansion support for the requests from clients.
- [platform-base](https://github.com/ao-space/platform-base)：provide the registration service of AO.space, and coordinate and manage the platform network resources.
- [gt](https://github.com/ao-space/gt)：provides network support services that penetrate NAT access AO.space through relay forwarding.

### Server repository introduction @zhongguang

The server is the main data carrier of AO.space and is also the core of data protection. It consists of the following repositories:
  
- [space-agent](https://github.com/ao-space/space-agent)：It provides services such as device binding, system service module startup bootstrapping, and management.
- [space-aofs](https://github.com/ao-space/space-aofs)：It provides file access services, including interfaces for file querying, chunked uploading, downloading, and more.
- [space-gateway](https://github.com/ao-space/space-gateway)：The end-to-end request security processing module receives requests, decrypts them, and forwards them to the relevant modules. It encrypts the responses and sends them back to the requesting client.
- [space-filepreview](https://github.com/ao-space/space-filepreview)：It supports the generation of thumbnails and preview images for media files. This functionality allows users to generate smaller versions or preview images of their media files, which can be useful for displaying file previews or creating thumbnails for faster loading.
- [space-media-vod](https://github.com/ao-space/space-media-vod)：Provide streaming media data access services
- [space-web](https://github.com/ao-space/space-web)：Providing an Nginx reverse proxy service for serving web-based service resources and requests
- - [space-upgrade](https://github.com/ao-space/space-upgrade)：On-demand startup, mainly responsible for server-side upgrades

### Clients repository introduction @fuyu

The client supports Android, iOS, and web versions, and consists of the following repositories:

- [client-android](https://github.com/ao-space/client-android)：Provide a client on Android platform for AO.space.
- [client-ios](https://github.com/ao-space/client-ios)：Provide a client on iOS platform for AO.space.
- [space-web](https://github.com/ao-space/space-web)：Deployed on the server, providing a web-based client for AO.space.

## Build and deploy

To deploy and run the project from a release version, or to build and run it from the source code, please refer to [build-and-deploy](./docs/build-and-deploy.md).

## Document

- [API](https://github.com/ao-space/api-doc)

## Contribution Guidelines

Contributions to this project are very welcome. Here are some guidelines and suggestions to help you get involved in the project.

[Contribution Guidelines](./docs/contribution-guidelines.md)

## Contact us

- Email: <developer@ao.space>
- [Website](https://ao.space)
- [Discussion group](https://slack.ao.space)
- [Twitter](https://twitter.com/AOspaceOSC)

You can also [get support for AO.spcae!](https://ao.space/en/support/help)

## License

AO.space is open-sourced under Apache License 2.0, see [LICENSE](./LICENSE).
<!-- 非 2.0 的列出来。 -->

## Acknowledgments

AO.space heavily relies on the open-source achievements of other projects. We would like to express our special thanks to them:
[Redis](https://redis.io/)、[OpenResty](https://github.com/openresty/)、[nginx](http://nginx.org)、[Gitlab](https://about.gitlab.com/)、[postgres](https://github.com/postgres/postgres)、[Gin](https://github.com/gin-gonic/gin)、[kaltura/nginx-vod-module](https://github.com/kaltura/nginx-vod-module)、[gson](https://github.com/google/gson)、[glide](https://github.com/bumptech/glide)、[lottie](https://github.com/airbnb/lottie-android)、[fastjson](https://github.com/alibaba/fastjson)、[eventbus](https://github.com/greenrobot/EventBus)、[ExoPlayer](https://github.com/google/ExoPlayer)、[AndroidPdfViewer](https://github.com/barteksc/AndroidPdfViewer)、[SmartRefreshLayout](https://github.com/scwang90/SmartRefreshLayout)、[Android-Office](https://github.com/zjtone/Android-Office)、[okhttp](https://github.com/square/okhttp)、[Rxjava](https://github.com/ReactiveX/RxJava)、[RxAndroid](https://github.com/ReactiveX/RxAndroid)、
[Retrofit](https://github.com/square/retrofit)、[WebSocket](https://github.com/TooTallNate/Java-WebSocket)、[ZXing](https://github.com/zxing/zxing)、[BouncyCastle](https://github.com/bcgit/bc-java)、[YCBase](https://github.com/ungacy/YCBase)、[YCEasyTool](https://github.com/ungacy/YCEasyTool)、[SAMKeychain](https://github.com/soffes/SAMKeychain)、[OpenSSL-Universal](https://github.com/cute/OpenSSL-Universal)、[CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack)、[SocketRocket](https://github.com/facebookincubator/SocketRocket)、[Reachability](https://github.com/tonymillion/Reachability)、[MJExtension](https://github.com/CoderMJLee/MJExtension)、[FileMD5Hash](https://github.com/JoeKun/FileMD5Hash)、[AFNetworking](https://github.com/AFNetworking/AFNetworking)、[JSONModel](https://github.com/jsonmodel/jsonmodel)、[ISO8601](https://github.com/erlsci/iso8601)、[LookinServer](https://github.com/QMUI/LookinServer)、[SDWebImage](https://github.com/SDWebImage/SDWebImage)、[YYModel](https://github.com/ibireme/YYModel)、[YYCache](https://github.com/ibireme/YYCache)、[FLAnimatedImage](https://github.com/Flipboard/FLAnimatedImage)、[Masonry](https://github.com/SnapKit/Masonry)、[WCDB](https://github.com/Tencent/wcdb)、[SVProgressHUD](https://github.com/SVProgressHUD/SVProgressHUD)、[SDCycleScrollView](https://github.com/gsdios/SDCycleScrollView)、[IQKeyboardManager](https://github.com/hackiftekhar/IQKeyboardManager)、[SSZipArchive](https://github.com/wuhaiwei/SSZipArchive)、[GKPhotoBrowser](https://github.com/QuintGao/GKPhotoBrowser)、[GCDWebServer](https://github.com/swisspol/GCDWebServer)、[lottie-ios](https://github.com/airbnb/lottie-ios)、[preview-generator](https://github.com/algoo/preview-generator)、[quarkus](https://github.com/quarkusio/quarkus)、[graalvm](https://github.com/graalvm)、[lombok](https://github.com/projectlombok/lombok)、[guava](https://github.com/google/guava)、[okhttp](https://github.com/square/okhttp)、[pinyin4j](https://github.com/belerweb/pinyin4j)、[rest-assured](https://github.com/rest-assured/rest-assured)、[ip2region](https://github.com/lionsoul2014/ip2region)、[findbugs](https://findbugs.sourceforge.net/)、[commons-codec](https://commons.apache.org/proper/commons-codec/)、[java-totp](https://github.com/samdjstevens/java-totp)、[jakarta.mail](https://github.com/jakartaee/mail-api) and so on。

Finally, thank you for your contribution to this project. We welcome contributions in all forms, including but not limited to code contributions, issue reports, feature requests, documentation writing, etc. We believe that with your help, this project will become more perfect and stronger.
