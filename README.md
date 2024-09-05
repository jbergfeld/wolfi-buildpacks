# Wolfi Buildpacks
[Paketo Buildpacks](https://github.com/paketo-buildpacks) using the [Wolfi](https://github.com/wolfi-dev/) stack.

### Requirements
Install the [pack cli](https://buildpacks.io/docs/for-platform-operators/how-to/integrate-ci/pack/)

### Create Base and Run images for the Wolfi [Stack](https://paketo.io/docs/concepts/stacks/)

```
cd base-image
docker build . -t cnbs/base-image:wolfi
```
(add `--platform=linux/amd64` if on a Mac with an arm processor.)

```
cd run-image
docker build . -t cnbs/run-image:wolfi
```
(add `--platform=linux/amd64` if on a Mac with an arm processor.)

### Create a [Builder](https://buildpacks.io/docs/for-platform-operators/how-to/build-inputs/create-builder/builder/) to use the Wolfi Stack
```
cd builder
pack builder create wolfi-builder --config ./builder.toml
```
(add `--target=linux/amd64` if on an arm Mac.)

### Build a sample app using the `wolfi-builder`
```
git clone -b wolfi https://github.com/jbergfeld/hello-kubernetes.git
cd hello-kubernetes/src/app
pack build hello-wolfi --builder wolfi-builder
docker run --rm --net=host hello-wolfi
```
You can access the running app from your browser http://localhost:8080

Feedback always welcome!

