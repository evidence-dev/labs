# Evidence Labs

Evidence Labs contains experiemental components and features for [Evidence](https://evidence.dev) projects.
- Github: https://github.com/evidence-dev/labs
- npm: https://www.npmjs.com/package/@evidence-dev/labs

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



## Component List

### Maps
- [Maps](/maps)

### UI
- [Grid](/grid)
- [Footnote](/footnote)
- [Github Stars](/github-stars)
- [Slider](/slider) - contributed by [@kuatroka](https://github.com/kuatroka)

### Embeds
- [Google Sheet](/google-sheet)
- [PDF](/pdf)

### Data
- [Cohort Analysis](/cohort-analysis)
- [Summarizer Component](/summarizer)


## Adding a New Component to Evidence Labs

<Alert status=warning>
Note: Do you need to do this, or should you be creating your own plugin? See README
</Alert>

1. Fork and clone the repo: `https://github.com/evidence-dev/labs`
1. Add  `YourComponent.svelte` to the `src/lib` folder, making sure you add an evidenceInclude flag (see examples)
1. Test it by adding it to `pages/your-component/index.md` (you will need to import it, and the syntax is a bit annoying - see other components for examples)
1. Export it from `src/lib/index.js` so it can be imported by other projects when it is published
1. Open a PR to the main repo
