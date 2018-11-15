# Express-Served React App


This is a `create-react-app`-generated React application deployed with Express, running in a container built from [the official Node image](https://hub.docker.com/_/node/).

## What This Accomplishes

No frills--get your basic React application up and running quickly.

## How to Use This

Your application should live in a directory called app that is a direct child of the root directory of this repository, as shown in the tree shown below.

```bash
$ tree -L 2
.
├── app        # <-- The "app" directory is the root of your React application
│   ├── node_modules
│   ├── package.json
│   ├── package-lock.json
│   ├── public
│   └── src
├── Dockerfile-dev
├── Dockerfile-prod
├── README.md
└── server.js
```

There is already a basic application (generated with `create-react-app`) in that folder, but yours should behave nicely. Just ensure that the necessary requirements are outlined for Node in the `package.json` file.

There are two flavors of docker-compose files and of Dockerfiles--one of each for development and production builds. Each docker-compose command references the appropriate file.

By default, the application will run on port 3000 in development. Thus a common configuration will forward the host's port 80 onto the container's 3000, making the application accessible at `http://localhost` on the host. Of course, other ports are fine. We configure that `server.js` to also listen on port 3000, so the `80:3000` is identical in both development and production.

## Development

##### Build

```bash
$ docker-compose build
```

##### Run

```bash
$ docker-compose up
```

## Production

##### Build and Serve with Express

This is clearly not the most efficient way to deploy a Node application, but it is a nice place to start or just a quick way to get it going. For a slimmer option, see [this similar repository](https://github.com/renciweb/nginx-react).

##### Build

```bash
$ docker-compose -f docker-compose-prod.yml build
```

##### Run

Here, we forward the host port 80 to the container's port 3000 since that port is the one on which `server.js` is expecting traffic.

```bash
$ docker-compose -f docker-compose-prod.yml up
```

## Additional References

- Docker: [https://docs.docker.com](https://docs.docker.com)
- Node.js: [Node.js](https://nodejs.org/)
- Express: [Express](https://expressjs.com/)
- React JS: [https://reactjs.org/](https://reactjs.org/)