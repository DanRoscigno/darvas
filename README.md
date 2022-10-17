# darvas

Hugo blog for OSE October

## Create a src dir

```bash
mkdir src
```

## Init the quickstart files using the go Docker image

```bash
docker run -it --rm \
  -v $(pwd)/src:/src \
  --name go \                                                    
  golang:1.19 bash
```

## Build command for local dev

### Start the container and mount a local dir

docker run -it --rm \
  --name hugo \
  -v $(pwd):/src \
  klakegg/hugo:0.101.0 bash

### Start Golang in Docker

```bash
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo:0.101.0
```

## GitHub Action for build and deploy

TBD

