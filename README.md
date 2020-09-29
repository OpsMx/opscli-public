# opscli - a tool for managing with Spinnaker applications and pipelines

## Overview 

opscli is a command line interface for onboarding and managing applications and  pipelines in Spinnaker, thereby making the management of large scale enterprise adoption of Spinnaker easy. 

Creation, deletion and management of Apps and Pipeline: This aids in the creation, deletion and editing of applications and pipelines

Templates for defining Applications and pipelines. These templates are jinja2 templates and are  processed at runtime to create, modify and delete apps and pipelines.  

Automatic Creation of Accounts: In order to simplify, Any accounts that are defined as part of an application are created by the tool automatically. For Kubernetes, these are part of the dynamic account infrastructure within Spinnaker and does not require any restart of any Spinnaker component. 

## Usage: opscli [global options] command [command options] [arguments...]

```
Commands to Create or Update CD Pipeline Project:
init      initialize your project, generating the required pipeline files
config    configure login credentials, template git location, pipelines, accounts git location
upgrade   upgrade your project files to be compliant with the newest version of opscli

Commands to Create, Update or Delete CD Pipeline Entities:
create    create application, pipeline resources and accounts
delete    delete application, pipeline resources and accounts
update    edit application, pipeline resources and accounts
list      fetch resources that you have access

Utility Commands:
template    used to generate templates out of the files in your templates folder
version     prints the version
help, h     Shows list of commands

Global Options:
   --debug, -d             enable debug logging
   --root value, -r value  used to set the context for opscli commands (default: "./") [$OPSCLI_ROOT]
   --version, -v           print the version

```

## Example usage:
### opscli create application -f application.yaml 
creates an application in Spinnaker using values in application.yaml 

### opscli create pipeline -f pipelineconfig.yaml
creates a pipeline based on pipelineconfig.yaml in Spinnaker. Creates clouddriver account(s) and publishes to remote repository

### opscli delete pipeline -f pipelineconfig.yaml 
deletes a pipeline configured based on name specified in pipelineconfig.yaml. The accounts associated may not be deleted if other pipelines are using them

### opscli list applications 
list all applications in the 

### opscli list pipelines --application=app1
list all pipelines in application app1 

### opscli list accounts 
list all clouddriver accounts (similar to /gate/credentials)

### opscli list accounts --application=app1 
list all clouddriver accounts associated with pipelines in app1 

### opscli config create gitaccount --name ACCOUNT_NAME --tokenfile <file>
create a git account for use with Spinnaker 

### opscli config create gitaccount --type bitbucket --name ACCOUNT_NAME --tokenfile <file>
create a git account for use with Spinnaker 

### opscli config create jenkins --name jenkinsaccount --address ADDR --username USERNAME --password 
create a Jenkins account for use with Spinnaker
