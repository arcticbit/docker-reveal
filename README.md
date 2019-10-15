# docker-reveal

Docker image for running your reveal.js presentations in a container.

## Setup

### Create a directory

```shell
$ mkdir slides
$ cd slides
```

### Export default template
```shell
$ docker create --name reveal arcticbit/reveal
$ docker cp reveal:/reveal/index.html ./index.html
$ docker cp reveal:/reveal/js ./js
$ docker cp reveal:/reveal/css ./css
```

### Start server
```shell
$ export SLIDES_PATH=$(pwd)
$ docker run -d \
    -p 8000:8000 \
    -v $SLIDES_PATH/index.html:/reveal/index.html \
    -v $SLIDES_PATH/js:/reveal/js \
    -v $SLIDES_PATH/css:/reveal/css \
    -v $SLIDES_PATH/public:/reveal/public \
    --name reveal \
    arcticbit/reveal
```