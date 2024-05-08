```
sudo chmod 666 /var/run/docker.sock  # 赋予docker命令root权限

docker build --network=host -t flasky:latest .

docker system prune  # 清空docker容器里的所有镜像内容

MAIL_PASSWORD=fmhbhgyzfzwprzbl
                         nqhvtqdqzjspyzdj

docker images  # 查看现有容器

docker run --name flasky1 -d -p 8000:5000 -e SECRET_KEY=57d40f677aff4d8d96df97223c74d217 -e MAIL_USERNAME=happlay18@gmail.com -e MAIL_PASSWORD=fmhbhgyzfzwprzbl flasky:latest  # 启动容器
# 容器ID
5d2e9d3a7d645a7125b3c61a4ffd778d0691bb61768594340b30cdaeb34eaaca
```

# 创建软连接

**会报错！！！**

```
mklink /j "C:\Program Files\Docker" "E:\Program Files\Docker"
为 C:\Program Files\Docker <<===>> E:\Program Files\Docker 创建的联接
```

