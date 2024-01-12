### Building and running with compose
Build and run
```shell
docker compose up
```

Cleanup
```shell
docker compose down --rmi all
```

### Building and running without compose

Build
```shell
docker build . --tag=my-git
```
Run
```shell
docker run --name git-server -p 2222:2222 -d my-git
```
Cleanup
```shell
docker rm -f git-server && docker rmi my-git
```