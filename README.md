# Write Tage to Version File

Based on `Write Version to File`

A GitHub Action that fetches the latest git commit within a repo and writes this to a file.

## Inputs

### `filename`

**Required** - The filename to write the commit id to.

### `placeholder`

**Optional** - The placeholder in the filename to write the version tag to. Defaults to `${VERSION}`



## Example usage

Commit a file named `.VERSION` containing `${VERSION}` to the root of your repository. This string will be replaced with the latest git commit in the CI pipeline.

```
name: Write Version to File
on:
  push:
    branches:
      - master

jobs:
  write-version:
    runs-on: ubuntu-latest
    name: Write Tag to Version File
    steps:
    - uses: actions/checkout@master
    - name: Update version
      uses: lisandrogreco/write-commit-to-version-file@latest
      with:
        filename: '/.VERSION'
        placeholder: '${VERSION}'
```
