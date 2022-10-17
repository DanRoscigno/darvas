# darvas

Hugo blog for OSE October

## Create a src dir

```bash
mkdir src
```

## Init the quickstart files using the go Docker image

```bash
docker run -it --rm --network="host" -v /home/droscigno/GitHub/darvas/src:/go/src --name go golang:1.19 bash
```
### Within the container just started:

#### Install Hugo

```bash
cd src
git clone https://github.com/gohugoio/hugo.git
cd hugo
go install --tags extended
```

#### Deploy the quickstart

```bash
cd ../src
hugo new site quickstart
```

#### Add a theme

```bash
cd quickstart
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo theme = \"ananke\" >> config.toml
```

#### Add a post

```bash
hugo new posts/my-first-post.md
```

## Build command for local dev

### Start the container and mount a local dir

docker run -it --rm --name hugo -v /home/droscigno/GitHub/darvas/src:/src klakegg/hugo:0.101.0 bash

### Start Golang in Docker

```bash
docker run --rm -it -v /home/droscigno/GitHub/darvas/src:/src klakegg/hugo:0.101.0
```

## GitHub Action for build and deploy

TBD

