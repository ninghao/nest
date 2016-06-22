> 使用 Docker 搭建本地的开发环境，是现在我推荐的方法 ：）

这是[宁皓网](http://ninghao.net) 介绍 Docker 相关技术用的小项目，可以作为本地的 PHP 应用的开发环境。

1 → 克隆仓库到本地
```
git clone https://github.com/ninghao/nest.git
```
2 → 进入项目所在目录
```
cd nest
```
3 → 创建并启动服务
```
docker-compose build
docker-compose up -d
```
4 → 在浏览器里打开
```
http://localhost:8080
```
<img src="http://talk.ninghao.net/uploads/default/original/2X/f/f7effbdc7b09ad54b71e525596f0683f70c24801.png" width="662" height="389">

把您的 PHP 应用比如 drupal 或 wordpress 放到 app 这个目录里面，然后去安装一下就行了。注意在安装的时候，数据库主机的名字应该是 `db`，而不是 `localhost` 。

[ninghao.net](http://ninghao.net)
