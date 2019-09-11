# crd2openapi
Convert Kubernetes CRDs into openapi specifications

# Purpose
This tempalte can be used to convert Kubernetes Custom Resource Definitions (CRDs) to openapi specifications. It can be used for generating client APIs for different programming languages.

# Motivation
Usually, the process to create a go-lang specific client to access CRDs is as suggested in [https://github.com/kubernetes/kube-openapi/issues/13]
1. Create the objects in go lang with specific annotations
2. Generate the openapi using a kubernetes instance
3. Generate a client based on the generated openapi specification

This process is not valid for the different programming languages, as the code generation and routes are only based on go-lang. This templates allows
to invert the process and create the client based on an openapi specification, generated using the crd.

# Usage
## Requirements
The template is based on jinja2 template engine. It is tested using the `j2cli` command line tool and needs to be installed.

**Using pip:**
```
pip install j2cli
```

## Generate the openapi specification
**Example:**
```
j2 crd-openapi.json.j2 [path/to/crd.yaml] > openapi.json
```

# Status and limitations
* The template not handle properly `status` and `scale` subresources
* It can only generate the specification for one CRD. In order to generate multiple a manual merge is needed.
