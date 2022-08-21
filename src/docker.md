# reclaim disk space
```shell
docker container prune -f
docker volume prune -f
docker image prune -ff
```

# compile in docker
```shell
docker run --rm -v $(pwd):$(pwd) -w $(pwd) zloymult/wasm-build-kit \
clang --target=wasm32 -O3 -nostdlib -Wl,--no-entry -Wl,--export-all -o dragon-curve.wasm dragon-curve.c
```

# rewrite entry point
```shell
docker run -it --rm --entrypoint /bin/sh
```

# export docker image
`docker save myimage:latest | gzip > myimage_latest.tar.gz`
`docker load -i myimage_latest.tar.gz`
