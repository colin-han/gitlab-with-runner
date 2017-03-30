#准备工作
###No1.
安装docker和docker compose
- win10：https://www.docker.com/docker-windows
- Mac：https://www.docker.com/docker-mac
- win7（Docker ToolBox）：https://www.docker.com/products/docker-toolbox
tips：最好安装Docker的GUI工具 Kitematic

###No2.
输入命令` docker-machine env`,将输出的5行export写成.bashrc文件
将.bashrc文件将放于个人目录下（Windows下为c:\Users\\\[YourName]\）


# 安装服务
建议用阿里docker镜像加速：
- 首先通过`docker-machine ssh <machine-name>`登录虚拟机
- 然后修改`/var/lib/boot2docker/profile`文件，将`--registry-mirror=https://pee6w651.mirror.aliyuncs.com`添加到EXTRA_ARGS中
- 最后`sudo /etc/init.d/docker restart`重启Docker服务就可以了

然后开始安装服务：
```sh
docker network create 'gitlab'
docker-compose up -d
```
这样镜像就被pull了下来，容器也开始运行了

#注册runner
gitlab service服务启动后，执行下面的命令在gitlab service上注册node6 runner
```sh
docker exec gitlab-runner \
					gitlab-runner \
					register -n \
							 --name "node6" \
							 --tag-list "node,node6" \
							 --docker-image "colinhan/p2m-node6:latest"
```
你可以用上面的命令在docker容器中注册多个runner实例

# 用法
连接到 http://localhost. （或者用Kitematic点击进入）默认用户名为 `root`, 默认密码为 `xA123456`







