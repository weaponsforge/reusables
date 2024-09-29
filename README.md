## reusables

The reusables code repository contains common reusable GitHub Actions workflows frequently used by Node-related apps. They are available on call from `workflow_call`.

## Workflows

### Lint Node Files

#### `lint-node.yml`

**lint-node.yml** is a reusable workflow that lints a Node app by running the `"npm run lint"` NPM script defined in its `"package.json"` file. It exits if there are Lint errors.

| Input | Description |
| --- | --- |
| `node_version` | Node version to use with the runner i.e., 16.x, 16.14.2, etc. |
| `path` | (Optional) Directory path to execute lint, relative to the `.github` directory. Defaults to the root repository directory if not provided. |

### Sample Usage

<details>
<summary>Reusable Lint Workflow</summary>
<br>

```
name: Reusable Lint Workflow

on:
  push:
    branches:
      - main

jobs:
  lint-files:
    uses: weaponsforge/reusables/.github/workflows/lint-node.yml@main
    with:
      node_version: "20.15.0"
      path: "./server"
```

</details>

<br><br>

@weaponsforge<br>
20240929
