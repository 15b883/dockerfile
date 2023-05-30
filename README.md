## Dockerfile

docker image 存储建议本地搭建一个自己的仓库

* artifactory（jfrog）
* harbor
* gitHub packages
* aws ecr
* ...



1、先通过docker hub 下载到本地，

2、根据需求修改好dockerfile后 

3、打上tag 

4、上传到自建的仓库

5、内部分享使用（使用内部URL）





Build image 

```
# docker build -t python3.10:v1 . 
```

Run docker 

```
# docker run --rm -it python3.10:v1
Hi Python3.10
```







## 支持

- [ ] python3.10
- [ ] python-flask
- [ ] python-fastapi
- [ ] python-django
- [ ] linux-centos
- [ ] linux-ubuntu
- [ ] nginx-js
- [ ] nginx-react
- [ ] nginx-vue
- [ ] go
- [ ] java









## 拓展

### 通过dockerfile 设置build和使用一个单独的机器进行build有什么不通？

使用 Dockerfile 进行构建和在单独的机器上进行构建的主要区别在于可移植性和环境隔离方面。

通过 Dockerfile 进行构建可以确保构建环境的一致性和可移植性，使得构建出来的镜像可以在任何支持 Docker 运行时的机器上进行部署和运行。同时，由于 Docker 使用的是容器虚拟化技术，可以有效地隔离不同的应用和环境，防止构建时的依赖冲突和环境变化等问题。

而在单独的机器上进行构建可能会受到宿主机器上已安装的软件和系统环境的影响，导致构建环境的不一致性和可移植性较差，可能会导致在其他机器上运行出现问题。同时，由于构建机器通常是一台共享的机器，可能会因为其他用户的操作或者系统维护等原因导致构建时间和质量不稳定。

因此，使用 Dockerfile 进行构建是更加推荐的做法，可以确保构建环境的一致性和可移植性，同时保持环境的隔离和稳定性。

使用Dockerfile进行构建的效率通常会更高，因为Dockerfile会将构建过程的各个步骤缓存起来，只需要在某个步骤修改了代码或配置等内容时才需要重新构建。而单独的机器进行构建则需要从头开始构建，无法利用缓存，构建时间通常会更长。此外，使用Dockerfile还能保证构建过程的可重复性，即在任何机器上构建都能得到相同的结果，而单独的机器构建则会受到机器配置和环境等因素的影响，结果可能不一致。