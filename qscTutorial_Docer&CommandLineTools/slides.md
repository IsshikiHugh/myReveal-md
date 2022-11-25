---
title: Page Title Here
separator: <!--s-->
verticalSeparator: <!--v-->
theme: league
highlightTheme: tomorrow-night-bright
revealOptions:
  width: 1280
  height: 960
  margin: 0.04
  transition: 'convex'
  slideNumber: true
---

# <font size = 10>[后端内训] 部分 Docker 和 一些即兴发挥</font>

<font size="6"> 2022秋冬vol.4 </font>

<div align="right"><font size="6"> 👉 Given by pacman</font></div>

<div align="right"><font size="6">

👉 Powered by [reveal.js](https://github.com/hakimel/reveal.js)

</font></div>

Note: Test note.

<!--s-->

## 何为&为何 Docker

- 尽管原理上存在本质不同，但是你可以暂时将它当作一个轻量级的“虚拟机”。
  - 关于 Docker 和 VM 的区别，推荐阅读：[Docker vs. Virtual Machines: Differences You Should Know](https://cloudacademy.com/blog/docker-vs-virtual-machines-differences-you-should-know/)

- 从模式上来讲，Docker 专注于三件事：`Build Image`, `Ship Image`, `Run Image`.
  - 而这里的 `Image` 则是学习 Docker 过程中必须理解的一个概念。

<!--v-->

设想这样一个背景：

- 你在你的本地机器上写了一个复杂的服务，除了 GoLang 以外还配置了一大堆其他的依赖；

- 这时候你需要把它部署到一个干干净净的服务器上，并且该发行版有很多你并不熟悉的特性……

如果你未曾了解过 Docker，那你或许只能选择再花一个下午在上面配置环境，甚至还会踩到更多的坑；但是如果你会用 Docker，那么你只需要为你的项目写一个 Dockerfile，并确保服务器上安装了 Docker，接下来只需要通过 Docker 直接部署即可。

<!--v-->

- 按照我的理解，Docker 就是为了在部署过程中便捷地构建一个必须的环境而存在的。

- 按照上面那个不太恰当的的“虚拟机”的比喻，就是在远程服务器上快速启一个配置好的虚拟机，并在里面运行对应的服务。

<!--s-->

## 关键词辨析

- Image
  - Docker Image 是用来构建 Docker Container 的一系列资源，你可以当它是一个“模板”，而 Container 是其实例化。其本质是一堆静态文件，并不具备执行能力。

- Container
  - Container 是 Image 的实例化，是一系列进程（当然你可以选择停止他们），它们根据 Image 中的内容被初始化创建，并基本上与你的宿主系统隔离，只留下一些用来进行交互的通道。

- [Docker Hub](https://security.feishu.cn/link/safety?target=https%3A%2F%2Fhub.docker.com%2F&scene=ccm&logParams=%7B"location"%3A"ccm_docs"%7D&lang=zh-CN)
  - 类似于 GitHub，你可以在上面搜索查看公开的 Image，从中挑选你需要的并拉取到本地进行使用。

<!--v-->

- 关于命令行的说明，我将融合在之后的内容中在对应的使用场景中介绍，如果想要查看列表类型的命令说明，可以查看：
  - https://docs.docker.com/engine/reference/commandline/cli/
  - https://docs.docker.com/engine/reference/commandline/docker/

- 在这里，我将简单介绍两种 Docker 的使用流程。分别对应“使用 Docker Hub 的 Docker 镜像”和“本地构建镜像并创建容器使用”。

<!--s-->

## 使用 Docker Hub 的 Docker 镜像

- 刚好我之前写过一篇用 Docker 安装 FSL 的博客，直接拿这个做介绍了。
  - https://www.yuque.com/isshikixiu/notes/sna3ru

- 查找镜像
  - *Docker Hub 支持命令行交互，但使用起来大概不如直接浏览 Docker Hub 方便，所以这里不做介绍* 。

- 使用 `docker pull` 来拉取镜像

- 使用 `docker run` 来生成容器并运行

<!--s-->

## 本地构建镜像并创建容器使用

首先，在考虑服务器之前，请先在本地做好这些事：

- 准备好的你的代码。
  - 例如我们需要在服务器上部署一个后端服务，那么首先你需要把这个后端服务的源代码准备好，否则“部署”将无从谈起。

- 写 Dockerfile
  - 具体来说，Dockerfile 指导 Docker 如何构建一个镜像，包括但不限于要如何准备你所需要的依赖、如何组织你的源代码、如何编译你的源代码、镜像中会包含什么等。
  - 关于 Dockerfile 的语法，可以参考我展示的例子，但是并不仅限于这些。

<!--v-->

- [非必需] 写一个部署脚本
  - 使用 Docker 已经很大程度上便利了在服务器上的部署，但是仍然还是需要一些步骤，而多数情况写我们需要多次修改源代码并重新部署，为了偷懒提高效率，我们还可以血已干部署脚本来让我们的部署真正实现“一键化”；
  - 由于我们在这个流程中需要在部署端准备源代码，那么将不可避免的涉及到“源代码版本管理”这件事，显然这件事和 Docker 无关（如果你使用在本地把镜像上传到 Docker Hub 上，并在部署端拉取 Image 的模式，那么这件事就和 Docker 有关了），所以我们需要在脚本中写上一些 git 指令；
  - 除此之外，由于我们需要多次重新部署，那么对于老版本的容器和镜像也需要一定的管理，即删除没有用的镜像和容器；
  - 当然，最重要的还有从镜像的构建到容器的运行这一系列操作；

当然，还有一个叫 CI/CD 的东西可以提到这个，这里就不展开了。

<!--s-->

# 即兴发挥

<!--v-->

## alias

- `alias`
- `unalias`

<!--v-->

## ssh

- https://www.openssh.com/manual.html
- [ssh command usage, options, and configuration in Linux/Unix.](https://www.ssh.com/academy/ssh/command#ssh-command-in-linux)

<!--v-->

## 包管理器们

- `pacman` / `yay` / `yum` / `apt-get` / `homebrew` / ...
- `pip` / `npm` / ...

<!--v-->

## tmux

- [1. TMUX commands — TMUX Guide documentation](https://tmuxguide.readthedocs.io/en/latest/tmux/tmux.html)
- [not elegant] 一种持久化的实现

<!--s-->

# Homework

<!--v-->

## Docker 实践

1. 找一个 image，把它 pull 下来；
2. 尝试将自己的任意代码打包成镜像并上传到 hub.docker.com 上，并且成功部署在其他位置；
3. 在你的 Linux 里多玩会儿；

<!--s-->

<font size=10>Any Question?</font>

<font size=5>虽然我基本答不上来.jpg</font>

<!--v-->

# Over!



- 请留意后端项目组分配表！
