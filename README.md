# testMymailbox

<p>
  <img src="https://img.shields.io/badge/version-0.1.0-blue" alt="Version Badge"/>
  <a href="https://nodejs.org/docs/latest-v16.x/api/index.html"><img src="https://img.shields.io/badge/node-16.x-green.svg" alt="node"/></a>
  <a href="https://www.typescriptlang.org/"><img src="https://img.shields.io/badge/typescript-5.x-blue.svg" alt="typescript"/></a>
  <a href="https://fastify.dev/"><img src="https://img.shields.io/badge/Web_Framework-Fastify_⚡-black.svg" alt="fastify"/></a>
  <a href="https://swc.rs/"><img src="https://img.shields.io/badge/Compiler-SWC_-orange.svg" alt="swc"/></a>
  <a href="https://www.docker.com/"><img src="https://img.shields.io/badge/Dockerized 🐳_-blue.svg" alt="docker"/></a>
</p>

## Description

testMymailbox provides an environment for managing emails in development environments. This project is intended only for testing applications or environments with testing needs.

> [!WARNING]  
> At no time send confidential or legal information through this medium. The author and collaborators of this project will not be responsible for any type of damage, harm, legal problem, as well as any other derived from the use of the product other than those established. You are the only responsible in such case.

## 🧑‍💻 Developing

First, we will need to create our .env file, we can create a copy from the example one:

```bash
cp .env.example .env
```

The project is fully dockerized 🐳, if we want to start the app in **development mode**, we just need to run:

```bash
docker-compose up -d testmymailbox-dev
```

This development mode with work with **hot-reload** and exposing a **debug port**, the `9229`, so later we can connect from our editor to it.

Now, you should be able to start debugging configuring using your IDE. For example, if you are using vscode, you can create a `.vscode/launch.json` file with the following configuration:

```json
{
  "version": "0.1.0",
  "configurations": [
    {
      "type": "node",
      "request": "attach",
      "name": "Attach to docker",
      "restart": true,
      "port": 9229,
      "remoteRoot": "/app"
    }
  ]
}
```

Also, if you want to run the **production mode**, you can run:

```bash
docker-compose up -d testmymailbox
```

This service is providing just a health endpoint which you can call to verify the service is working as expected:

```bash
curl --request GET \
  --url http://localhost:3000/health
```

Change localhost to the ip address of your machine in a production environment and port to the port specified in the PORT environment variable.

If you want to stop developing, you can stop the service running:

```bash
docker-compose down
```

## ⚙️ Building

```bash
npm run build
```

## ✅ Testing

The service provide different scripts for running the tests, to run all of them you can run:

```bash
npm run test
```

If you are interested just in the unit tests, you can run:

```bash
npm run test:unit
```

Or if you want e2e tests, you can execute:

```bash
npm run test:e2e
```

## 💅 Linting

To run the linter you can execute:

```bash
npm run lint
```

And for trying to fix lint issues automatically, you can run:

```bash
npm run lint:fix
```

## Features

- work in progress

## Thanks

This project is based on the template <a href="https://github.com/AlbertHernandez/nestjs-service-template">nestjs-service-template</a> by <a href="https://github.com/AlbertHernandez">@AlbertHernandez</a> and some configurations are based on this template, again, thanks to <a href="https://github.com/AlbertHernandez">@AlbertHernandez</a> for the template.

Other templates by <a href="https://github.com/AlbertHernandez">@AlbertHernandez</a>:

- [Template for new Typescript Libraries](https://github.com/AlbertHernandez/typescript-library-template)
- [Template for new Typescript Express Services](https://github.com/AlbertHernandez/express-typescript-service-template)
- [Template for new GitHub Actions based on NodeJS](https://github.com/AlbertHernandez/github-action-nodejs-template)

## License

MIT
