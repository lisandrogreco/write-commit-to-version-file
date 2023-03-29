# Write Tage to Version File

Based on `Write Version to File`

A GitHub Action that fetches the latest git tag within a repo and writes this to a file.

## Inputs

### `filename`

**Required** - The filename to write the version tag to.

### `placeholder`

**Optional** - The placeholder in the filename to write the version tag to. Defaults to `${VERSION}`

### `tag`

**Optional** - The version tag to write. If not set, the latest git tag will be write.

## Example usage

Commit a file named `.VERSION` containing `${VERSION}` to the root of your repository. This string will be replaced with the latest git tag in the CI pipeline.

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
      uses: eball/write-tag-to-version-file@latest
      with:
        filename: '/.VERSION'
        placeholder: '${VERSION}'
        tag: 'v1.0.0'
```
