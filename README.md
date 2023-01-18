# GitHub Action for Auto-Publishing Docs

This action provides an integration for auto-publishing documentation on Github Pages. It will build the documentation with `forge doc --build --out <path>` and then upload the output to the `actions/upload-pages-artifact` action.

## Usage

To use this action, add the following to your workflow file:

```yaml
- uses: actions/upload-pages-artifact@master
```

You also need to enable Github Actions in your Pages configuration:
/settings/pages