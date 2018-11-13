# Express-Served React App


This is a `create-react-app`-generated React application deployed with Express, running in a container built from [the official Node image](https://hub.docker.com/_/node/).

## What This Accomplishes

No frills--get up and running quickly. This is clearly not the most efficient way to deploy a Node application, but it is a nice place to start or just a quick way to get it going.

## How to Use This

Remove everything from the `/app` directory, and dump your project in there. Just be sure that the necessary requirements are outlined for Node in the `package.json`.

## Deploy

### Build

```bash
$ docker build .
```

Identifying the image later may be nice, so we tag it

```bash
$ docker build -t express-react-server .
```

### Run

By default, the application run on port 3000, so a common configuration will forward the host's port 80 onto the container's 3000

```bash
$ docker run -p 80:3000 express-react-server
```

This makes the application accessible at `http://localhost` on the host. Of course, other ports are fine.

## Want a Slimmer Deployment?

For a slimmer deployment container, go for multistage builds. This will allow building the web application in one (Node) container and then copy the build files over to another one (a server container) for serving.

I use a multistage build inside the frontend container in [this project](https://github.com/renciweb/publications/blob/master/frontend/Dockerfile-prod), which may be a nice reference until this project's versatility bulks up. The [Docker documentation on Multi-Stage Builds](https://docs.docker.com/develop/develop-images/multistage-build/) is a more informative resource, though.