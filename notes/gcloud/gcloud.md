Gcloud
===

# Config

Local config file
~/.config/gcloud

gcloud auth use sqllite3
~/.config/gcloud/credentilas.db

Gcloud config default
~/.config/gcloud/active_default
~/.config/gcloud/configurations/config_default

# Gcloud Roles

https://cloud.google.com/iam/docs/understanding-roles

### Registry

Required Permissions:
- Service Account User
- Storage Admin

### Cloud build

[Missing permissions on cloud container builder role #120](https://github.com/GoogleCloudPlatform/cloud-builders/issues/120)
Required Permissions:
- Viewer on the project
- Builder Editor role
