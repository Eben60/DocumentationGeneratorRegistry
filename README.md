# DocumentationGeneratorRegistry

[![CI](https://github.com/JuliaDocs/DocumentationGeneratorRegistry/actions/workflows/CI.yml/badge.svg)](https://github.com/JuliaDocs/DocumentationGeneratorRegistry/actions/workflows/CI.yml)

This registry allows package authors to specify where to find and how to build the documentation for their
packages displayed on e.g. [juliahub.com](https://juliahub.com/ui/Packages).

## Usage
Just add a new entry to `Registry.toml` by hand following the `Specifications` below (order doesn't matter) or with the provided `add_to_registry.jl` script:
```
julia add_to_registry.jl Package1 Package2 Package3
```

## Options

There are three options for specifying how (with the `method` key) and where (with the `location` key) to find a package's documentation:
- `vendored`: The documentation *source* is located in a folder (specified by `location`) in the package's root directory.
- `git-repo`: The documentation *source* is located in the git repo given by `location`.
- `hosted`: The *built* documentation is reachable under the URL given by `location`.

## Specifications

Each package is specified by UUID, which is also the top-level key. Required sub-keys are `method`, `location`, and `name`:
```
# replace by the actual UUID of the package "PackageName" 
[uuid]
name = "PackageName"
method = "hosted"
location = "https://thisismy.hosted.documentation.org/stable"
```
