## About Docker LNMP 
###多容器间协作互连


## 描述

这是一个 Docker 多容器间协作互连的例子。使用的是最常见的 LNMP 的技术栈，既 `Nginx` + `PHP` + `MySQL` + `Redis`。

在这个例子中，我使用的是 Docker Compose，这样比较简洁，如果使用 `docker` 命令也可以做到同样的效果，当然，过程要相对繁琐一些。

## Docker使用说明

可以自定义自己的`nginx`、 `mysql`、`php` 、 `redis`版本, 直接在`.env`配置就行

```
  mv env.example .env
  
  // 启动服务
  docker-compose up
  // 停止服务
  docker-compose stop
  // 重启服务
  docker-compose restart
  // 删除服务
  docker-compose down
```

PS:若果修改了DockerFile则必须运行 `docker-compose build` 命令，再次运行`docker-composer up`启动

## 关于项目运行配置说明

* 可以直接在`code`文件夹下进行`git clone`你的项目 
* 回到根目录 运行`docker-compose exec php bash` 命令进入容器, 运行`composer install`, `composer update`等命令
* 回到`nginx`目录 复制一份`default.example.conf`到`conf.d`文件夹下，然后按下面的修改

```
 root /usr/share/nginx/html;   // 修改成  root  /usr/share/nginx/html/{projectdir}

```

## 配置文件目录

在这个例子中，每个服务的配置文件均采用挂载宿主目录中的配置文件的形式，配置文件位于各个服务对应的目录中：

*   `nginx`：nginx 的默认站点配置文件：`./nginx/conf/nginx.conf`；
*   `php`： PHP 配置文件 `./php/php.ini`；

修改配置文件后重新运行服务，就会加载其配置。



