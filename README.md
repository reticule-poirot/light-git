### Minimal git backend

Minimal git backend. Do not use in production due lack of security.

How to [run](README.Docker.md)

### Usage

Default repo name is 'project'

```shell
git clone git://localhost:2222/project && cd project
```

```
Cloning into 'project'...
warning: You appear to have cloned an empty repository.
```

```commandline
touch README.md
git add .
git commit -m 'add README.md'
git push
```

### Add another repo

```commandline
docker exec -it git-server git init --bare /git-data/project2.git
```