# Template Metadata files

This repository is a collection of metadata files that should be used to initialize new repositories
if appropriate (no strong arguments speak against it).

## Repository-related metadata files

- `LICENSE`: using this file is mandatory for all CUBI repositories
- `CITATION.md`: using this file is mandatory for all CUBI repositories
  - if no other - more specific - citation information applies to a repository,
    a link to this CITATION file must be added at the end of the top-level
    repository README (same wording as at the end of this README).
- `.editorconfig`: using this file is mandatory for all CUBI repositories
- `.gitignore`: strongly recommended, contains ignore rules for Python, R and some custom entries by default.
    There must be a good reason not to use (an extended version of) this file.

## CUBI metdata files

By convention, and for convenience, all CUBI metadata are organized in form of a `pyproject.toml` file
containing a minimal amount of descriptive entries. This file must be located at the top-level of the
respective repository. The "hierarchy" in these files is as follows:

1. include [Python tool settings](tomls/tool/pyproject.toml) for coherent formatting of Python code
    - if the repository does not contain any Python code, this may be omitted
2. include [the CUBI metadata information](pyproject.toml), i.e., the top-level `pyproject.toml` in this repository
3. include specific metadata...
    - ...for a [project repository](tomls/cubi/project/pyproject.toml)
    - ...for a [workflow template repository](tomls/cubi/workflow/template/pyproject.toml)
    - ...for a [workflow repository](tomls/cubi/workflow/pyproject.toml)

As a reminder, read the development guidelines to learn about key characteristics
of workflows and projects, and naming conventions:

[CUBI dev process in the knowledge base](https://github.com/core-unit-bioinformatics/knowledge-base/wiki/Dev-process#repository-types)

[CUBI naming conventions in the knowledge base](https://github.com/core-unit-bioinformatics/knowledge-base/wiki/Naming-and-style#naming-repositories)


## Conda environment template

This repository contains a minimal Conda environment file despite the fact that this repo
does not include any executable code. This Conda environment template file should be used
as the base file for more complex environments where applicable and reasonable:

[Conda env template](envs/conda/template.yaml)

This template environment encodes a few hard requirements for CUBI code developments:

```YAML
dependencies:
  - Python=3.11.*  # the target Python3 version
  - pip=25.1.*
  # For conda itself:
  # most recent; whatever can be resolved.
  # Oct. '23 marks the switch to the libmamba
  # solver and since then, there should not be
  # too much of a speed difference between
  # conda and mamba
  - conda>23.10.0
  # All of the below:
  # There are config options set for these
  # tools in 'tomls/formatting/pyproject.toml'
  # and, hence, changing any of the versions
  # requires checking that all options/parameters
  # are still supported:
  - pyyaml=6.0.*
  - toml=0.10.*
  - semver=3.0.*
  - pylint=3.3.*
  - isort=6.0.*
  - black=24.10.*
  - ruff=0.12.*
```

# Citation

If not indicated otherwise above, please follow [these instructions](CITATION.md) to cite this repository in your own work.
