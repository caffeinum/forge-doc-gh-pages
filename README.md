# GitHub Action for Auto-Publishing Docs

This action provides an integration for auto-publishing documentation on Github Pages. It will build the documentation with `forge doc --build --out <path>` and then upload the output to the `actions/upload-pages-artifact` action.

## Usage

To use this action, add the following to your workflow file:

```yaml
- name: Upload Forge docs to GitHub Pages
  uses: caffeinum/forge-doc-gh-pages@main
```

Important! You also need to provide access to wiki and githubpages. Add this to your workflow:

```yaml
jobs:
  # ... other jobs ...

  build-gh-pages:

    # Grant GITHUB_TOKEN the permissions required to make a Pages deployment
    # from https://github.com/actions/deploy-pages
    permissions:
      pages: write # to deploy to Pages
      id-token: write # to verify the deployment originates from an appropriate source

    # Deploy to the github-pages environment
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
      
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - name: Upload Forge docs to GitHub Pages
        uses: caffeinum/forge-doc-gh-pages@main
```

You also need to enable Github Actions in your Pages configuration.
