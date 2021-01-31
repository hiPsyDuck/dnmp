### dnmp

nginx + php8 + mysql5.7 + redis5

后续增加php7.4版本

---

### 简单说明

1. 将`.env-example`复制一份重命名为`.env`
2. 修改`.env`中的`mysql`和`redis`的密码，添加`git`的配置（如果需要）
3. 在根目录执行 `docker-compose up -d` 创建镜像和容器
4. 在`www`目录下为新项目新建文件夹，并配置`nginx`到`services/nginx/conf.d`

---

### 基本命令

```
docker-compose up -d     #启动（后台运行）
docker-compose stop      #停止
docker-compose restart   #重启
```
