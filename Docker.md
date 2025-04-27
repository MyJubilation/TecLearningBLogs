# 常用命令

- ```
  // 启动docker
  systemctl start docker
  // 启动时便启动docker
  systemctl enable docker
  
  // 进入root
  su
  
  // vi 编辑
  vi xxx
  // 换写文件内容
  echo xxx >（>>） xxx               eg:echo "hello" > index.html
      ----">"为直接覆盖，">>"为在末尾续写
  ```

- ```
  // 查看当前docker容器
  docker ps
  ```

- 关于nginx

  ```
  // 在docker run nginx后，想退出nginx
  ctrl+c
  // nginx页面存储位置
  /usr/share/nginx/html
  ```

- 关于vim

  ```
  vim xxxxx
  // 执行写操作
  i
  // 保存退出
  esc
  :wq
  ```

- 关于镜像

  ```
  // 检索
  docker search
  // 下载
  docker pull     ||   docker pull:latest    ||    docker pull:1.26.0
  // 列表
  docker images
  // 删除
  docker rmi
  ```

- 关于容器

  ```
  // 运行
  docker run
      ----docker run -d xxx            ----后台启动
      ----docker run -d -p 88:80       ----后台启动，并将88端口映射为80端口，88不能重复，80可以重复（80是独立容器内的端口，每个容器都有80端口，88是整个docker的端口）
  // 查看
  docker ps
  // 停止
  docker stop
  // 启动
  docker start
  // 重启
  docker restart
  // 状态
  docker stats
  // 日志
  docker logs
  // 进入
  docker exec
      ----docker exec -it xxx /xx/xx   ----交互模式进入
  // 删除
  docker rm
      ----docker rm -f xxx             ----强制删除
  ```

- 关于保存镜像

  ```
  // 提交
  docker commit
  // 保存
  docker save
  // 加载
  docker load
  ```

- 关于分享社区

  ```
  // 登录
  docker login
  // 命名
  docker tag
  // 推送
  docker push
  ```

  

# docker存储

- 目录挂载和卷目录区别：一个相当于外设一个目录（类似于C盘D盘），一个相当于复制目录内容后新开一个文件夹

## 目录挂载

> 每次重启容器后，对应容器内容会初始化，之前设置的内容将会消失。

![image-20250304163916038](D:\MdBlogs\img\Docker\image-20250304163916038.png)

![image-20250304164432196](D:\MdBlogs\img\Docker\image-20250304164432196.png)



## 卷目录

> 在目录挂载后，如/etc/nginx在外部目录没有对应文件，启动时会报错，需要将外部目录同步内部初始状态时的文件。

- 卷映射:-v ngconf:/etc/nginx
- 存储的路径默认为：/var/lib/docker/volumes/<volume-name>