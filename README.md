# Unduck

DuckDuckGo's bang redirects are too slow. Add the following URL as a custom search engine to your browser. Enables all of DuckDuckGo's bangs to work, but much faster.

```
https://unduck.link?q=%s
```

## How is it that much faster?

DuckDuckGo does their redirects server side. Their DNS is...not always great. Result is that it often takes ages.

I solved this by doing all of the work client side. Once you've went to https://unduck.link once, the JS is all cache'd and will never need to be downloaded again. Your device does the redirects, not me.

## How to setup a Docker Container 🐳?

To build the Docker image you can use this Docker Compose with the image that I have already prebuilt.

```docker
version: '3.8'

services:
  unduck:
    image: ghcr.io/csmith1865/unduck-docker:latest
    volumes:
      - unduck:/app
    ports:
      - "8083:80"  # Do not change the right port
    restart: unless-stopped  # Optional: restart policy for the container
volumes:
  unduck:
```

## How to build the Docker Image 🐳?

To build the Docker Image you can use the provided Dockerfile and run this command.

```sh
sudo docker build -t unduck .
```
