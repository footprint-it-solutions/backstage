# Build

`docker run -it -v "$(pwd)":/backstage node:24-trixie /bin/bash`

then in the container:

```shell
cd backstage \
  && apt-get update && apt-get install -y python3 g++ build-essential libsqlite3-dev \
  && yarn config set --home enableTelemetry 0 \
  && yarn install \
  && yarn tsc \
  && yarn build:backend
exit
```

then

```shell
docker build -t backstage:latest . \
  && docker tag backstage:latest 330880211149.dkr.ecr.eu-west-2.amazonaws.com/backstage:latest \
  && docker push 330880211149.dkr.ecr.eu-west-2.amazonaws.com/backstage:latest
```
