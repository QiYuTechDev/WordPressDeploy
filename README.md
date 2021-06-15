# WordPressDeploy

在您的 VPS 上部署 WordPress

# WordPress 部署

1. 使用 `wp_init` 初始化
1. 使用 `wp_gen_secrets` 生成新的 WordPress 密钥 (强烈建议您保存的版本控制系统中)
1. 使用 `docker-compose up -d` 启动 WordPress 服务器
1. 配置反向代理服务器 (nginx 或者 caddy)
1. 通过外网访问 WordPress 服务器，然后完成安装

提示:

    本仓库搭建的 WordPress 默认端口可以通过 `docker-compose.yaml` 修改

# WordPress 备份

* `wordpress` 目录是所有 WordPress 的源文件

建议您创建一个私有的 **git** 仓库，然后本目录的所有配置都提交到 *git* 仓库

# MySQL 数据备份

```shell
$ docker exec some-mysql sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > /some/path/on/your/host/all-databases.sql
```

# MySQL 恢复数据

For restoring data. You can use docker exec command with -i flag, similar to the following:

```shell
$ docker exec -i some-mysql sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' </some/path/on/your/host/all-databases.sql
```
