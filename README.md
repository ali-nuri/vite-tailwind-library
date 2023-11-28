# ⚡️ Vite, React, Typescript and Tailwind npm package

This library is a template for building UI library npm package with **Vite Library mode** and supercharged with Tailwind CSS.

Please check this 👉 [blog post](https://nuri.gg/vite-react-typescript-tailwind-npm-package) 👈 for a step by step walkthrough on how this library is built.

The components are located in the `lib` folder. 

*If you want to showcase a component in Storybook, you can add a story file next to the component. see the example component*

<br>

## ䷴ Developing components

To develop the components, follow these steps:

1. Write your component code in the `lib` folder.
2. Export the component in the `lib/main.ts` file.
3. Create a corresponding story file next to the component to showcase it in Storybook.
4. Run `npm run storybook` to view your developed component live on the Storybook viewer.

<br>

## 🚀 Publish

### To publish the package on Gitlab Package Registry, follow these steps:

1. Modify the name and version in the `package.json` file according to this pattern: `@your-scope/package-name`.
2. Generate a developer token from your GitLab account. This token will be needed in step 6.
3. Create a repository on GitLab for your library.
4. Add an `.npmrc` file at the root of this package with the following content:

```
@your-scope:registry=https://gitlab.com/api/v4/projects/your_project_id/packages/npm/
//gitlab.com/api/v4/projects/your_project_id/packages/npm/:_authToken="${NPM_TOKEN}"
```

Replace `your_project_id` with the Project ID that can be found in the GitLab repository.

5. Run the command `NPM_TOKEN=token npm publish` to publish the package to the npm registry.

<br>

### To publish the package on Github Package Registry, follow these steps:

To publish the package on GitHub Package Registry, follow these steps:

1. Modify the name and version in the `package.json` file according to this pattern: `@your-scope/package-name`.
2. Create a personal access token (PAT) with the `write:packages` scope. You can create a PAT by going to your GitHub account settings and navigating to "Developer settings" > "Personal access tokens".
3. Create a `.npmrc` file at the root of this package with the following content:

```
@NAMESPACE:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=YOUR_PAT
```

Replace `NAMESPACE` with your GitHub username and `YOUR_PAT` with your personal access token.

4. login to npm on scope level via

```
$ npm login --scope=@NAMESPACE --auth-type=legacy --registry=https://npm.pkg.github.com


> Username: USERNAME
> Password: TOKEN

```

5. Run the command `npm publish` to publish the package to the GitHub Package Registry.

<br>

## ✔️ Installing the package

*The library does not bundle the Tailwind CSS library, Therefore, you need to configure Tailwind CSS on your project to use this component library<br>
For more information, refer to the [Tailwind CSS installation guide](https://tailwindcss.com/docs/installation/framework-guides).*

To use the UI Library in your project, follow these steps:

1. Provide the `.npmrc` file with the following credentials on the target repository.
2. Clone the released package on the target repository using the command `npm i @your-scope/ui-kit`.
3. Configure Tailwind to scan the library components by adding this line to the content array on the `tailwind.config.js`.

```
content: [
    ...

    './node_modules/@your-scope/ui-kit/dist/ui-kit.umd.js',
  ],
```

4. Import the library in your component, for example: `import {Button} from '@scope/ui-kit'`.
5. Use the component: `<Button color="blue" > Click me! </Button>`.

<br>