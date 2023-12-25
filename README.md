# [Golang](https://go.dev/)

Golang Playground to keep track of related projects.

Objetive is to save ready to run projects/code for future reference.

## [Installation](https://go.dev/doc/install)

Following instructions are for Linux OS

- Remove previous installation \
    `rm -rf /usr/local/go`
- Download last file from go.dev/dl/ \
    `wget https://go.dev/dl/go1.21.5.linux-amd64.tar.gz`
- Install \
    `tar -C /usr/local -xzf go1.21.5.linux-amd64.tar.gz`
- Add /usr/local/go/bin to the PATH environment variable. \    
    `echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc`
- Apply changes \
    `source ~/.bashrc`
- Check installation \
    `go version`
    <details><summary>Output</summary>
        go version go1.21.5 linux/amd64
    </details>

## Repo Organization

Number prefix increase with project complexity/size.

Folders named by frameworks contain examples of those, and will follow same prefix pattern than root Golang folder.

A *README.md* file can be (usually) find in each folder with breaf indications to reproduce the example from scratch.

Example:
```bash
Golang
│   ├── 00_HelloWorld
│   ├── 01_Packages
│   │   ├── README.md
```

## Common tools used among projects in the repo

## Source Control
* [GitHub](https://github.com/)
* [Visual Studio Online](https://vscode.dev/)
- [Go plugin for VSCode](https://marketplace.visualstudio.com/items?itemName=golang.go)

## Build/Package Tool
* [Build](https://github.com/pypa/build)
* [setuptools](https://pypi.org/project/setuptools/)
* [PyBuilder](https://pybuilder.io/)
* [scikit-build](https://scikit-build.readthedocs.io/en/latest/)  
* [Spack](https://github.com/spack/spack)
* [Conda](https://conda.io/en/latest/index.html)
 
## Continuous Integration
  * [Jenkins CI](https://jenkins-ci.org/)
   
## Static Analyzers
* [wemake-python-styleguide](https://analysis-tools.dev/tag/go)
* [mypy](https://github.com/python/mypy)
* [Codacy](https://www.codacy.com/)
* [Codefactor](https://www.codefactor.io/)
* [Pylint](https://github.com/pylint-dev/pylint)
* [flake8](https://flake8.pycqa.org/en/latest/)
* [pylint-django](https://github.com/pylint-dev/pylint-django)

## Code Formatting / Naming
* [Black](https://pypi.org/project/black/)

## Testing
    https://pkg.go.dev/testing
    https://go.dev/doc/security/fuzz/

## PROFILING
### Code Coverage Analysis
    https://golangdocs.com/profiling-in-golang
