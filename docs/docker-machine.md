# Docker machine example

```bash
docker-machine create -d virtualbox \
    --engine-env HTTP_PROXY=http://example.com:8080 \
    --engine-env HTTPS_PROXY=https://example.com:8080 \
    --engine-env NO_PROXY=example2.com \
    proxbox
```


https://stackoverflow.com/questions/36844213/how-to-set-proxy-in-docker-toolbox
