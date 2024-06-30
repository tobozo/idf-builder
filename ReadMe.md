
# ESP IDF artifact builder

Use `tobozo/idf-builder` github action to compile an esp-idf project.

It wraps `espressif/esp-idf-ci-action` for the building process and creates a merged binary that will be saved as an artifact.

## Requirements

An esp-idf project to compile.


## Usage

```yml
name: IDFBuild
on:
  push:
  pull_request:
  workflow_dispatch:

jobs:

  build:

    runs-on: ubuntu-latest

    steps:
    - name: Test Action
      uses: tobozo/idf-builder@v1
      with:
        target_repo: user/esp-idf-project # github repository
        # target_repo_ref: main
        # idf_project_folder: relative/path/to/target/repo/examples/blah
        idf_version: v5.1 # esp-idf version, must match a tag listed at https://hub.docker.com/r/espressif/idf/tags
        idf_target_chip: esp32s3 # any chip supported by the picked version of esp-idf
        merged_bin: merged.bin # optional
        artifact_name: merged_bin # optional
```
