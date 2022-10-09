# spinningup/docker

Via <https://github.com/openai/spinningup/issues/3#issuecomment-449139665> by <https://github.com/gvgramazio>:

I've written a basic dockerfile with the requirements stated so far (is capable of running examples and plotting results) to be included in the main project. See [my fork](https://github.com/gvgramazio/spinningup/tree/docker) to try it.

In order to work with it, simply build the image:

```bash
docker build -t spinningup -f ./docker/Dockerfile .
```

Adjust the permissions of xhost:

```bash
xhost +local:root
```

Run the container exposing the xhost so that container can render to the correct display by reading and writing through the X11 Unix socket:

```bash
sudo docker run -it --rm \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  spinningup
```

Enjoy your container. Of course, you can plot results.

When have you done with it, adjust again the permissions of xhost:

```bash
xhost -local:root
```

Note that I'm writing this post in order to receive a feedback and feature requests. I don't consider it ready for a pull request yet.

I will be satisfied by adding the support for python (currently works only with python3) and managing in a better and safer way the x11 redirection. Both things should be done by tomorrow. Feel free to ask for more features.
