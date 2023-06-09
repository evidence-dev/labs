# Evidence Labs

Evidence labs contains experiemental components and features for [Evidence](https://evidence.dev) projects.

To install Evidence

```bash
npx degit evidence-dev/template my-project
cd my-project
npm install
npm run dev
```

## Using Evidence Labs Components

1. Install the package from npm:
    ```bash
    npm install --save @evidence-dev/labs
    ```
2. Include it in your `evidence.plugins.yaml` file:

    ```yaml 
    components:
        @evidence-dev/core-components: {}
        @evidence-dev/labs: {}
    ```
3. Add the component to your page!

<Alert status=info>
Ensure you restart your dev server after adding the plugin!
</Alert>

## Build your own plugin

1. Clone this repository
2. Add your components to the `src/lib` directory
3. Test they work by adding them to a page in the `pages/` directory
4. Edit the name in `package.json` from `@evidence-dev/labs` to `your-plugin-name` and set the version to `0.0.1`
5. Publish to npm with `npm publish` (You will need to be logged in to an [npm](https://www.npmjs.com/signup) account)
