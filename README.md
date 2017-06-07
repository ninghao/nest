# nest

nest 是一个用 Docker 搭建的本地 PHP 应用开发与运行环境。

## 准备

安装 Docker for Windows 或 Docker for Mac。

## 服务

* db：使用 mariadb 作为应用的数据库
* php：解释 php 脚本，使用 php-fpm
* web：使用 NGINX 作为应用的 web 服务器
* console：常用工具
* phpmyadmin：管理数据库的 web 界面

## 结构

* app：这个目录存储应用，database 放数据库，web 放应用的代码。
* services： 环境里定义的服务需要的一些资源，比如 nginx 的配置文件在 nginx/config/default.conf 。
* docker-compose-dev.yml：定义本地开发环境需要的服务。
* docker-compose.yml：生产环境需要的服务，暂时为空白。
* docker-sync.yml：同步文件用的配置文件。
* example.env：环境文件示例，复制一份这个文件，把复制的文件命名为 .env 。

## 使用

准备：

```
git clone https://github.com/ninghao/nest.git
cd nest
cp example.env .env
```

基本用法：

```
docker-compose up -d
```

同步文件：

```
docker-sync start
docker-compose up -d
```

或：

```
docker-sync-stack start
```
