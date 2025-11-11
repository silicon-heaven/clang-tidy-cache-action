# clang-tidy-cache for GitHub Actions
This action downloads and sets up [clang-tidy-cache](https://github.com/matus-chochlik/ctcache) for use on GitHub Actions. This action was inspired by [hendrikmuhs/ccache-action](https://github.com/hendrikmuhs/ccache-action).

## Usage
```yaml
name: Lint

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  clang-tidy:
    name: clang-tidy
    runs-on: ubuntu-22.04
    steps:
      - name: Clone the repository
        uses: actions/checkout@v4
        with:
          submodules: true

      - name: Set up clang-tidy-cache
        uses: silicon-heaven/clang-tidy-cache-action@v1.2.0

      - name: Run the linter
        shell: bash
        run: |
          # create your build directory, e.g. `build`
          clang-tidy-cache clang-tidy -p build src/*
```
