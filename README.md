# docker-project
docker编排时的目录结构, 基于dockerfile , docker-compose 


### 多项目多镜像的目录结构
```
docker
├── project1
│   ├── container
│   │   ├── dev // 单独实例一个镜像
│   │   │   ├── data
│   │   │   ├── docker-compose.yml
│   │   │   ├── resouce
│   │   │   └── shell
│   │   ├── mysql
│   │   ├── redis
│   │   └── test
│   ├── image
│   │   ├── dev
│   │   │   ├── docker-entrypoint.sh
│   │   │   ├── Dockerfile
│   │   │   └── resource
│   │   ├── mysql
│   │   ├── redis
│   │   └── test
│   ├── data // 项目中共享的数据
│   ├── docker-compose.yml // 配置由多个容器组成项目
│   └── resource // 项目中共享的资源
├── project2
└── project3
```

### 单项目多镜像的目录结构
```
docker
├── container // 容器, 镜像的实例
│   ├── data
│   ├── docker-compose.yml
│   ├── resource
│   └── shell
├── image // 自定义镜像
│   ├── dev
│   │   ├── docker-entrypoint.sh
│   │   ├── Dockerfile
│   │   └── resource
│   ├── mysql
│   ├── redis
│   └── test
├── data // 项目中共享的数据
├── resource // 项目中共享的资源
└── docker-compose.yml // 配置信息
```

如果这个docker目录下面包含了多个项目, 需要创建各个项目的目录, 如果只有一个项目则可以省略项目目录.

每个项目均由 image 和 container 目录组成

**image**   
用于存放构建自定义镜像的先关文件, 如果有多个镜像需要构建, 则根据镜像的用途分别命名目录, 

**container**   
用于存放运行各个镜像的各种配置, 目录和镜像目录一一对应, 
