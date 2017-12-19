# 基本概念：
##  镜像
    Docker 镜像就是一个只读的模板。
    例如：一个镜像可以包含一个完整的 centos 操作系统环境，里面仅安装了 nginx 或其它应用程序。
    镜像可以用来创建 Docker 容器。
    Docker 提供了一个很简单的机制来创建镜像或者更新现有的镜像，用户甚至可以直接从其他人那里下载一个已经做好的镜像来直接使用。
## 容器
    Docker 利用容器来运行应用。
    容器是从镜像创建的运行实例。它可以被启动、开始、停止、删除。每个容器都是相互隔离的、保证安全的平台。
    可以把容器看做是一个简易版的 Linux 环境（包括root用户权限、进程空间、用户空间和网络空间等）和运行在其中的应用程序。
## 仓库
    仓库是集中存放镜像文件的场所。有时候会把仓库和仓库注册服务器（Registry）混为一谈，并不严格区分。实际上，仓库注册服务器上往往存放着多个仓库，
    每个仓库中又包含了多个镜像，每个镜像有不同的标签（tag）。
    仓库分为公开仓库（Public）和私有仓库（Private）两种形式。
    最大的公开仓库是 Docker Hub，存放了数量庞大的镜像供用户下载。 国内的公开仓库包括 Docker Pool 等，可以提供大陆用户更稳定快速的访问。
    当然，用户也可以在本地网络内创建一个私有仓库。
    当用户创建了自己的镜像之后就可以使用 push 命令将它上传到公有或者私有仓库，这样下次在另外一台机器上使用这个镜像时候，只需要从仓库上 pull 下来就可以了。
    
*注：Docker 仓库的概念跟 Git 类似，注册服务器可以理解为 GitHub 这样的托管服务。*


# 安装（这个安装建议看官网，获取CE版） 
    官网centos安装教程链接：
    https://docs.docker.com/engine/installation/linux/docker-ce/centos/
    安装之前，先把之前的给清除掉：
```bash
    yum remove docker \
                  docker-common \
                  docker-selinux \
                  docker-engine
```
    如果已经安装过了，执行上面那个是不够的，还要在 /var/lib/docker/ 下面给删除。
    安装CE版，参考上面的官网地址即可，如果安装失败，建议改下yum源地址，再次尝试。
    
    下面是其他朋友写的安装方法，作参考：
```bash                
    yum install docker        # CentOS 中安装
    apt-get install docker-ce # Ubuntu 中安装
    pacman -S docker          # Arch 中安装
    emerge --ask docker       # Gentoo 中安装
```
    #=====================

    docker version      # 通过查看版本，检查安装是否成功
    # Client:
    #  Version:         1.12.6
    #  API version:     1.24
    #  Package version: docker-1.12.6-55.gitc4618fb.el7.centos.x86_64
    #  Go version:      go1.8.3
    #  Git commit:      c4618fb/1.12.6
    #  Built:           Thu Sep 21 22:33:52 2017
    #  OS/Arch:         linux/amd64
    # 
    # Server:
    #  Version:         1.12.6
    #  API version:     1.24
    #  Package version: docker-1.12.6-55.gitc4618fb.el7.centos.x86_64
    #  Go version:      go1.8.3
    #  Git commit:      c4618fb/1.12.6
    #  Built:           Thu Sep 21 22:33:52 2017
    #  OS/Arch:         linux/amd64



