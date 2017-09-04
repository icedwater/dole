# Docker: Getting Started

This folder contains artifacts created while going through the [tutorial][get]
on the Docker website. I created this on Ubuntu 16.04 running docker 1.12 from
the repository.

Included below are notes about each of the steps in the tutorial.

## Part 1: Orientation and Setup

This part of the tutorial explains what images and containers are, and how the
container differs from your usual virtual machine. The site "requires" 1.13 or
higher, but I haven't seen any problems with the first few steps.

## Part 2: Containers

Here you get to [build your own container][con] which uses Flask and Redis and
Python 2.7. After working through this, you should have a `Dockerfile` for the
settings, a list of necessary packages in `requirements.txt`, and `app.py` for
the application itself.

Once you're in the directory with these files, build the docker image:

    docker build -t cutename .

**NOTE**: If you make changes to the app, remember to rebuild the container.

You'll find a new `cutename` image in the list of `docker images`. Running the
application requires a matching external _port mapping_, defined with `-p`:

    docker run -p 4000:80 cutename

Passing the `-d` argument to `docker run` pushes this to the background.

For a list of running containers, including the short ID you can use to stop a
running container, type:

    docker container ls

And of course, stop the container with:

    docker stop <short_ID>

As a bonus, you're shown how to share your container with others if you have a
[Docker Hub][hub] account:

    docker login
    docker tag cutename username/repository:tag
    docker push username/repository:tag

And to retrieve a copy of (your) container, what's the opposite of `push`? Nah
just kidding, you only need to `run` it, it should be pulled if it isn't there
yet.

    docker run -p 4000:80 username/repository:tag

**NOTE**: There is another [list of commands][d2r] at the bottom of the page.
If you make changes to the app, remember to rebuild the container.

[get]: https://docs.docker.com/get-started/
[con]: https://docs.docker.com/get-started/part2/
[d2r]: https://docs.docker.com/get-started/part2/#recap-and-cheat-sheet-optional
[hub]: https://cloud.docker.com/
