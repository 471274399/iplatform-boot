# MySQL部署手册

> 作者 xx

## 1. 安装

### 1.1 前提

* JDK1.8+
* 磁盘剩余空间大于xxxMB
* 空闲内存大于xxxGB

### 2.2 安装

1. 下载安装包

```bash

```

2. 解压缩

```bash

```
3. 参数配置

```xml

```

4. 启动

```bash

```

5. 验证安装
6. 停止

## 2. Docker

> 基于Docker的单节点配置

```yaml
version: '3.2'
services:
  oneitom-mysql:
    image: boco/alpine-mysql:10.1.28
    hostname: oneitom-mysql
    container_name: oneitom-mysql
    restart: always
    networks:
      - oneitom-network
    ports:
      - '3306:3306'
    volumes:
      - ${ONEITOM_VOLUME_PATH}/oneitom-mysql:/app:rw
    environment:
      - TZ=Asia/Shanghai
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=authdb,notifydb,gulfdataflowdb
      - MYSQL_USER=authdb-user,notifydb-user,gulfdataflowdb-user
      - MYSQL_PASSWORD=authdb-password,notifydb-password,gulfdataflowdb-password
    labels:
     - oneitom-mysql-cluster
networks:
  oneitom-network:
    external: true
```


