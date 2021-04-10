[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

<div style="text-align:center">
    <img src="https://pic.zhoutao123.com/lib/simple-docker/logo-tm.png" width="200" alt="" >
</div>

**SimpleDocker** 是一个简单的Docker控制面板，致力于可以让用户更方便、更无障碍、更舒适的使用Docker,其界面简洁、操作便捷，功能强大，可以带来更好地运维体验。

**个人开发维护不易，麻烦给个 Star ✨ 鼓励一下作者,您的鼓励是我最大的动力 😛！！！**

> 🎉 🔥 ✨ 新发布的 V0.0.4 版本支持 容器在线终端管理、在线文件浏览及文件下载、容器性能监控等功能，欢迎体验 & 提交PR

---
预计发布的V0.0.5新支持特性

+ 完善细节(进行中.....)
+ 重构容器创建流程，使用向导模式创建容器(完成)
+ 新增容器异常的钉钉通知(完成)
+ 首页新增系统信息(完成)
+ 接入Redis作为存储中间件(完成)

## 背景

Docker是目前一种非常主流的容器化方案，支持非常多的特性，给开发者带来便利，但是 Docker 镜像以及容器管理复杂的参数让新手望而却步，基于此开发 SimpleDocker 控制面板，方便新手和相关的运维同学使用!!!

> 本项目是基于学习的目的的，致力于提供一个 界面清晰、免费的、简单的、专注于 Docker 服务管理的控制面板(当然也会持续开发下去~)，目的只想做一个适合自己的管理软件！！！
> Tip: 您可以在Issues中提出需求和您发现的bug！[需求 & BUG 管理](https://github.com/taoes/SimpleDocker/issues)


** 🎉 目前支持以下特性:**

|特性|支持功能|
|---|---|
|镜像|详情、拉取、运行、导出、导入、删除|
|容器|详情、启动、停止、运行、暂停、删除、精简、导出、重命名|
|高级|终端、日志、文件管理、网络配置、异常通知|
|存储|管理、创建、删除、精简|
|网络|管理、创建、连接、精简|
|安全|登录、密码重置|
|设置|容器创建模式，容器异常通知配置|
|监控|容器异常通知、容器性能监控|

** 🛠 计划支持的特性: **

0. 新增Docker控制窗口，支持相关Docker脚本的执行
1. DockerCompose 镜像编排管理(计划中)
2. DockerSwarm 集群管理(计划中)

## 应用安装

+ Docker 安装

1. 确保Docker已经部署并且启动成功
2. 执行下面的脚本，会自动拉取镜像并启动在8080端口

```sh
docker run  -d -p 8080:4050 -v /var/run/docker.sock:/var/run/docker.sock --name SimpleDocker  registry.cn-hangzhou.aliyuncs.com/seven-tao/simple-docker:0.0.4
```

3. 浏览器访问 http://localhost:8080
4. 默认账号: admin 默认密码: SimpleDocker2020
5. 如果使用了域名并且通过服务器进行反向代理，请配置反向代理服务器支持
   WebSocket，否则终端功能可能无法使用 [1. Nginx 配置支持WebSocket](https://www.xncoding.com/2018/03/12/fullstack/nginx-websocket.html)

+ 手动编译

0. 准备Redis环境
1. 克隆代码到本地，并启动 beego项目

```shell
git clone https://gitee.com/taoes_admin/SimpleDocker
cd ./SimpleDocker
bee run
```

2. 新建终端窗口，切换到 `ui` 目录下打开前端项目

3. 修改 `ui/src/api/Config.js` 文件内容，确保请求前缀和 beego 启动端口一致

```shell
cd ui
yarn install && yarn server
```

4. 打开相应的前端端口，即可访问，调试

## 预览

+ Docker 信息
  ![Docker 信息](./img/info.png)

+ 容器危险操作通知

  ![img.png](img/container_notify.png)

+ Image 信息
  ![Image 信息](./img/image.png)

+ 运行新的容器
  ![Image 信息](./img/runContainer.png)

+ Container 信息
  ![Container 信息](./img/container.png)

+ 容器终端在线管理
  ![终端管理](./img/terminal.png)

+ 容器文件在线管理
  ![终端管理](./img/file.png)

+ 容器性能监控
  ![终端监控](./img/monitor.png)

+ 容器日志以及日志下载
  ![Image 信息](./img/containerLog.png)

+ Volume 信息
  ![Volume 信息](./img/volume.png)

+ Network 信息
  ![Network 信息](./img/network.png)

## Q & A

1. 忘记密码

> 忘记密码时候，你可以切换到`~/.local/simpleDocker` 目录，修改auth.json 文件，将password值修改为`B923E7672631F71B510FEDB20A77EA8A` 即可恢复默认密码 `SimpleDocker2020`

## 相关依赖

- [GoLang](https://golang.org/)
- [Vuex](https://vuex.vuejs.org/)
- [VueJs 2.x](https://vuejs.org/)
- [Ant Design Vue](https://www.antdv.com/docs/vue/introduce-cn/)
- [Docker API Engine](https://docs.docker.com/engine/api/sdk/)

## 我的信息

+ [燕归来兮的 GitEE ](https://gitee.com/taoes_admin)
+ [燕归来兮的 GitHub](https://github.com/taoes)
+ [燕归来兮的技术博客](https://www.zhoutao123.com)

## 讨论

本项目完全开源，如有任何需求或者BUG反馈，欢迎提交Issue[Open an issue](https://github.com/taoes/SimpleDocker/issues/new) 或者提交PR！

## 开源方案

[GPL](./LICENSE)
