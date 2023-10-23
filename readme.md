# Micro Frontend - React

This project is a proof of concept to show how to create a module federation micro frontend system with React and Vite. The primary use case for module federation is the distribution of software at runtime on both client and server. This is a great fit for micro frontends, where we want to load different parts of the application from different servers and components sharing can be bidirectional, that is, an application can expose and import components at the same time.

## Documentation

- [React Micro Frontends with Vite](https://dev.to/getjv/react-micro-frontends-with-vite-5442)
- [React Micro Frontends with Module Federation](https://www.nearform.com/blog/react-micro-frontends-module-federation/)
- [Git submodules](https://www.atlassian.com/git/tutorials/git-submodule)

## Main dependencies

- [React](https://reactjs.org/)
- [Vite](https://vitejs.dev/)
- [Federation](https://github.com/originjs/vite-plugin-federation)
- [Concurrently](https://github.com/open-cli-tools/concurrently)

## Getting started

Clone this repo with submodules for each service and the app-container:

```bash
git clone --recurse-submodules https://github.com/albrtogarcia/federation-micro-frontend.git
```

In this way, you'll have the app-container and the services projects in the same folder and can edit all projects in the same instance of your editor but you can commit changes per project. Just checkout Source Control view in VSCode and you'll see the changes in each project separately.

Or clone it without submodules, delete them and build your own services and app-container.

Install dependencies on each project:

```bash
npm install
```

If needed, edit the `start-all` command in `package.json` with the correct paths for each service and the app-container. In this case we'll use the following:

- `app-container`: Application host that contains components and pages imported from services apps.
- `service-*:` Applications that can import remote components from other services and can expose its own components to the other services an `the app-container`.

For this example, we have three services apps: `service-library`, `service-auth` and `service-dashboard`. The first service, library, exposes a component UI library to the other services, and auth and dashboard services exposes pages to the `app-container`.

This folder contains the `app-container` and all the services and only runs a package that can run multiple commands concurrently in the same terminal window for development environments.

### File structure

```
This folder (name it as you want)
  │
  └─ app-container
  │
  └─ library
  │
  └─ service-auth
  │
  └─ service-dashboard
```

This structure is just an example, you can organize your micro frontends as you want.

### Start the project

Clone the app-container and the services projects in this folder and run the following command:

```bash
npm run start-all
```

## Workflow

- Production branch: `main`
- Staging branch: `staging`
- Development branch: `develop`
- Feature branches: `feature/feature-name`