# darvas

Hugo blog for OSE October

## Adding a post

- Navigate to the dir where this repo is cloned, or clone it if on a new machine
- Start the container

  Note: make sure that the path for the volume (`-v /home...`) is correct

  Note: make sure the UID/ GID (`1000:1000`) are also correct

  ```bash
  docker run \
    --env GOCACHE=/go/src/.cache -it \
    --rm \
    --user 1000:1000 \
    --network="host" \
    -v /home/droscigno/GitHub/darvas/src:/go/src \
    --name go golang:1.18 bash
   ```

- Add a post

  ```bash
  hugo new posts/my-first-post.md
  ```

## GitHub Action for build and deploy

TBD

## This content is for the initial setup, don't run these again

### Create a src dir

```bash
mkdir src
```

#### Add hugo as a submodule

```bash
cd src
git submodule add https://github.com/gohugoio/hugo.git hugo
```

### Init the quickstart files using the go Docker image

```bash
docker run --env GOCACHE=/go/src/.cache -it --rm --user 1000:1000 --network="host" -v /home/droscigno/GitHub/darvas/src:/go/src --name go golang:1.18 bash
```
#### Within the container just started:

##### Install Hugo

```bash
cd src
cd hugo
go install --tags extended -buildvcs=false
```

##### Deploy the quickstart

```bash
cd ../
hugo new site quickstart
```

##### Add a theme

This needs to be run on the host machine, not in the Docker container as the entire repo `darvas` is not mounted in the container, and the submodule command will fail.
```bash
cd quickstart
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo theme = \"ananke\" >> config.toml
```

##### Add a post

```bash
hugo new posts/my-first-post.md
```

##### Start a webserver with drafts enabled

```bash
hugo server -D
```

### Edit files

You can edit the files in src/quickstart and the changes will be visible in the browser,
