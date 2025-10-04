#

<a alt="Nx logo" href="https://nx.dev" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/nrwl/nx/master/images/nx-logo.png" width="45"></a>

✨ Your new, shiny [Nx workspace](https://nx.dev) is almost ready ✨.

[Learn more about this workspace setup and its capabilities](https://nx.dev/nx-api/node?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) or run `npx nx graph` to visually explore what was created. Now, let's get you up to speed!

## Finish your CI setup

[Click here to finish setting up your workspace!](https://cloud.nx.app)

## Run tasks

To run the dev server for your app, use:

```sh
npx nx serve auth-service
```

To create a production bundle:

```sh
npx nx build auth-service
```

To see all available targets to run for a project, run:

```sh
npx nx show project auth-service
```

These targets are either [inferred automatically](https://nx.dev/concepts/inferred-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) or defined in the `project.json` or `package.json` files.

[More about running tasks in the docs &raquo;](https://nx.dev/features/run-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Add new projects

While you could add new projects to your workspace manually, you might want to leverage [Nx plugins](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) and their [code generation](https://nx.dev/features/generate-code?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) feature.

Use the plugin's generator to create new projects.

To generate a new application, use:

```sh
npx nx g @nx/node:app demo
```

To generate a new library, use:

```sh
npx nx g @nx/node:lib mylib
```

You can use `npx nx list` to get a list of installed plugins. Then, run `npx nx list <plugin-name>` to learn about more specific capabilities of a particular plugin. Alternatively, [install Nx Console](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) to browse plugins and generators in your IDE.

[Learn more about Nx plugins &raquo;](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) | [Browse the plugin registry &raquo;](https://nx.dev/plugin-registry?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

[Learn more about Nx on CI](https://nx.dev/ci/intro/ci-with-nx#ready-get-started-with-your-provider?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Install Nx Console

Nx Console is an editor extension that enriches your developer experience. It lets you run tasks, generate code, and improves code autocompletion in your IDE. It is available for VSCode and IntelliJ.

[Install Nx Console &raquo;](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Useful links

Learn more:

- [Learn more about this workspace setup](https://nx.dev/nx-api/node?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Learn about Nx on CI](https://nx.dev/ci/intro/ci-with-nx?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Releasing Packages with Nx release](https://nx.dev/features/manage-releases?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [What are Nx plugins?](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

And join the Nx community:

- [Discord](https://go.nx.dev/community)
- [Follow us on X](https://twitter.com/nxdevtools) or [LinkedIn](https://www.linkedin.com/company/nrwl)
- [Our Youtube channel](https://www.youtube.com/@nxdevtools)
- [Our blog](https://nx.dev/blog?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Create a express project

https://20.nx.dev/showcase/example-repos/add-express

```
nx add @nx/express
```

## Create the api-gateway

```
nx g @nx/express:app api-gateway --directory=apps/api-gateway --e2eTestRunner=none
```

It creates the api-gateway folder inside apps folder

## Modifications in package.json

Create scripts

To run all available services in our project

"dev": "npx nx run-many --target=serve --all"

The api-gateway port should be 8080 not 3333
The auth-servic port should be 6001 not 3000 (3000 is for NextJs application)

## Proxy Server

```
    npm i express-http-proxy
```

morgan is for logger
express-rate-limit is for protecting our server from attacks
It can limit the number of requests per minute
swagger-ui-express is for api documentation
cookie-parser is for cookie related stuff

```
    npm i cors morgan express-rate-limit swagger-ui-express axios cookie-parser
```

Import type versions of these packages

```
npm i --save-dev @types/cors
```

## To kill port

```
npx kill-port 8080
```

## Run the application

```
    npm run dev
```

Listening at http://localhost:8080/api
[ ready ] http://localhost:6001

```
    curl http://localhost:8080
```

Content : {"message":"Hello API"}

In auth-service

```
app.get('/', (req, res) => {
  res.send({ message: 'Hello API' });
});
```

Create a folder called "packages"
Create a folder called "middleware" inside "packages" folder
Create a folder called "error-handler" inside "packages" folder
Create a file called "error-middleware.ts" file inside "error-handler" folder

We have to create another file for Error Handling inside "error-handler" called "index.ts"

In auth-service -> tsconfig.app.json
Change rootDir as "../.."
"include": [
"../../packages/**/**.ts"
]

In auth-service -> main.ts
app.use(errorMiddleware);
