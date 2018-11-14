# Express-Served React App


This is a `create-react-app`-generated React application deployed with Express, running in a container built from [the official Node image](https://hub.docker.com/_/node/).

## What This Accomplishes

No frills--get your basic React application up and running quickly.

## How to Use This

Replace everything in the `/app` directory with your project, ensuring that the necessary requirements are outlined for Node in the `package.json` file.

Tagging the builds and naming the running containers can be nice, as can running the containers detached. Thus those options appear in the examples below, as do a few of these other common things:

- There are two types of Dockerfiles--one designed for a development build and onw for a production build. Each build command references the appropriate file.
- By default, the application will run on port 3000. Thus a common configuration will forward the host's port 80 onto the container's 3000, making the application accessible at `http://localhost` on the host. Of course, other ports are fine.

## Development

##### Build

```bash
$ docker build -t react-app/dev -f Dockerfile-dev .
```

##### Run

```bash
$ docker run -p 80:3000 --name webapp-dev -d react-app/dev
```

## Production

##### Build and Serve with Express

This is clearly not the most efficient way to deploy a Node application, but it is a nice place to start or just a quick way to get it going. For a slimmer option, see [this similar repository](https://github.com/renciweb/nginx-react).

##### Build

```bash
$ docker build -t react-app/prod -f Dockerfile-prod .
```

##### Run

```bash
$ docker run -p 80:3000 --name webapp-prod -d react-app/prod
```

## Additional References

- Docker: [https://docs.docker.com](https://docs.docker.com)
- Node.js: [Node.js](https://nodejs.org/)
- Express: [Express](https://expressjs.com/)
- React JS: [https://reactjs.org/](https://reactjs.org/)