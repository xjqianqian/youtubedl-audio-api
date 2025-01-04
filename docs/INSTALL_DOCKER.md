# Installation Guide

This document provides instructions on how to set up and run the project.

## Prerequisites

Main tech stack:
- Python 3.10.x or higher
- Docker
- flask

## Installation with Docker
There's a [Dockerfile][3] available for creating an image.

You can use the Docker image to use it in development. (see Docker section) This command should do the trick:

```bash
docker container run --rm -it -p 5000:5000 <YOUR_IMAGE_NAME>
```

## Docker

By default, the Docker image created will publish the web in the port 5000. Uses the `python:3` image.

An example of building the image, running and testing:

```bash
docker image build -t yt-audio-api .
docker container run -d --rm -p 5000:5000 yt-audio-api # or melchor9000/youtubedl-audio-api from Docker Hub
curl http://localhost:5000/api/0RLvtm0EghQ
curl http://localhost:5000/api/q_E9fgeWtWQ
curl http://localhost:5000/api/S2iihI5G32Y
```

It is available a `docker-compose.yaml` file to test it out. Uses the image from Docker Hub and a redis server for caching.