## reusables

The reusables code repository contains common reusable GitHub Actions workflows frequently used by Node-related apps. They are available on call from `workflow_call`.

### Table of Contents

- [Lint Node App](#lint-node-app)
- [Lint Multiple Node Apps](#lint-multiple-node-apps)

## Workflows

### Lint Node App

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

<br>

### Lint Multiple Node Apps

#### `lint-node-multiple.yml`

**lint-node-multiple.yml** is a reusable workflow that lints **multiple** Node apps by folder path using the **matrix** strategy, running the `"npm run lint"` NPM script defined in each directory's `"package.json"` file. It exits if there are Lint errors.

| Input | Description |
| --- | --- |
| `node_version` | Node version to use with the runner i.e., 16.x, 16.14.2, etc. |
| `paths` | (Optional) List of directory path(s) in a string array to execute lint, relative to the `.github` directory. Defaults to the root repository directory if not provided.<br><br>Sample format looks like:<br>`paths: "['client', 'server', 'scripts']"` |

### Sample Usage

<details>
<summary>Reusable Lint Workflow - Multiple Node Apps</summary>
<br>

```
name: Reusable Lint Workflow

on:
  push:
    branches:
      - main

jobs:
  lint-files:
    uses: weaponsforge/reusables/.github/workflows/lint-node-multiple.yml@main
    with:
      node_version: "18.15.0"
      paths: "['client', 'server']"
```

</details>

<br><br>

@weaponsforge<br>
20240929
