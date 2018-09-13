## Configure the Build Environment
In order to build this, you must start the database

```
docker network create dspace-build
docker run -it -d --network dspace-build --name dspacedb dspace/dspace-postgres-pgcrypto
```

Build dspace docker (note dspace-6_x will build by default)

```
docker build . -t dspace-so_edu_mu:0.1 --network dspace-build --no-cache
```

## Destroy the Build Environment
In order to ensure that your next build starts from a clean environment, remove the components that were created.

```
docker network rm dspace-build
docker stop dspacedb
docker rm dspacedb
```