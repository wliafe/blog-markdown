# docker本地和容器之间的文件传输

## 获取容器id全称

```bash
docker inspect -f '{{.id}}' 容器名称
```

## 本地文件传输到容器

```bash
docker cp 本地文件路径 ID全称:容器路径
```

## 容器文件传输到本地

```bash
docker cp ID全称:容器路径 本地文件路径
```