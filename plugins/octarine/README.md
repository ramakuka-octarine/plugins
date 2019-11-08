# Kubernetes Object Scanning Tool
Docker image which invokes Kubernetes security scanning using Octactl 

## Prerequisites:

Codefresh Subscription (Dedicated Infrastructure) - https://codefresh.io/

OctarineSec Subscription - https://www.octarinesec.com

## options

To use an ENVIRONMENT VARIABLE you need to add the variables to your Codefresh Pipeline and also to your codefresh.yaml.

Check the project [Github](https://github.com/octarinesec/validator) for a full list of config options 

## codefresh.yml

Codefresh Build Step to execute OctarineSec scan.
All `${{var}}` variables must be put into Codefresh Build Parameters
codefresh.yml
```console
 steps:
  validate_security:
    title: "Validating Security By Octarine"
    image: "octarinesec/validator:latest"
    environment:
      - OCTARINE_ACCOUNT=<ACCOUNT>
      - OCTARINE_SESSION_ID=<YOUR_SESSION_ID> 
      - OCTARINE_SESSION_ACCESSJWT=<YOUR ACCESS_JWT>
      - OBJECT_DIR=${{CF_VOLUME_PATH}}/${{CF_REPO_NAME}}/kubernetes/
    stage: "PreBuild test"
```
