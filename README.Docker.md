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
### Docker desktop k8s example
Set up a [restry](https://www.docker.com/blog/how-to-use-your-own-registry-2/) or use any existing.
Build and push to registry
```shell
docker build . --tag=registry.example.local:5000/light-git
docker push registry.example.local:5000/light-git
```
Create deployment
```shell
kubectl create deployment git-server --image registry.example.local:5000/light-git --port 2222
```
Create service
```shell
kubectl expose deployment git-server --type=ClusterIP --port=2222
```
Forward ports or use `LoadBalancer` service type
```shell
kubectl port-forward services/git-server 2222:2222
```
