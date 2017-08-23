# vue-beer
## Default

## Docker based
```bash
# Create your docker image based on your local source code
$ docker build -t coconut .
[...]

# run a container based on the coconut docker image
$ docker run -d --restart always -p 8080:8080 coconut
8f3fe2e82a739033f2e5c67a7774b930c73f436e906d5a74c8417568f15d1072

# test it
$ curl http://localhost:8080

# stop the container
# get the id return by the docker run command
$ docker stop 8f3fe2e82a739033f2e5c67a7774b930c73f436e906d5a74c8417568f15d1072
```
