# wal-g

on-premise DB tool

## release/

```bash
tar -zxvf wal-g-mongo-ubuntu-20.04-amd64.tar.gz
mv wal-g-mongo-ubuntu-20.04-amd64 /usr/local/bin/wal-g
```

## submodules/

```bash
cd submodules/wal-g
# 1. 拉取主子模組 remote 的更新內容，並且與 main 進行 merge
git submodule update --remote --merge

# 2. 把更新內容 push 上去到主模組那邊，讓 remote 那邊的子模組也可以指到新的內容
git add .
git commit -m "update submodule"
git push
```

```bash
# 主子模組整個都要更新
git pull --recurse-submodules <branch>

# Clone 主子模組
git clone --recurse-submodules <remote_url>
```

## Build Docker Image

> - `docker build -t wal-g-mongo -f ./build/package/Dockerfile . --no-cache`
> - `docker save -o wal-g-mongo.tar wal-g-mongo`
> - `docker load -i wal-g-mongo.tar`

### split large tar into multiple files (25MB)

```bash
ls -lh images.tar.gz
split -b 25000000 images.tar.gz img.part
ls -lh img.*
```

### How to Join Tar Files After Splitting

```bash
cat img.part* | tar xzvf -
```

## Reference

> - [wal-g github](https://github.com/wal-g/wal-g)
> - [wal-g release](https://github.com/wal-g/wal-g/releases)
