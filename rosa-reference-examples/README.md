# ROSA Reference examples

This section of the repo gives examples on how to build various configurations of ROSA. It is not meant as a quickstart guide but instead to give some working examples of how to achieve various builds for people new to Terraform.


## ROSA HCP Cluster using official Red Hat Module

This can be found in the ./rosa_hcp_new_modules folder. This example uses the official Red Hat module which is documented here: https://registry.terraform.io/modules/terraform-redhat/rosa-hcp/rhcs/latest

This example allows a single terraform resource that will build all needed components for ROSA.

## ROSA Classic Cluster using official Red Hat Module

This can be found in the ./rosa_classic_new_modules folder. This example uses the official Red Hat module which is documented here: https://registry.terraform.io/modules/terraform-redhat/rosa-classic/rhcs/latest

This example allows a single terraform resource that will build all needed components for ROSA.

## ROSA Classic Cluster using official Red Hat provider

This can be found in the ./rosa_classic_no_modules folder. This example uses no modules at all, and is designed for people who would like to understand the raw resources that are needed to make a ROSA Cluster. This example splits each of the components of ROSA into it's own file for easy understanding and reading. It is not designed as a quickstart or production setup.

This example uses a managed OIDC config bucket (where the public components of the OIDC provider are hosted by Red Hat)

## ROSA Classic Cluster using a managed OIDC provider and local modules

This can be found in the ./rosa_classic_managed_oidc folder. This example uses local modules to build a cluster with a managed OIDC provider. This example is useful if you are running Terraform from a location that is not permitted to pull public modules.

This example uses a managed OIDC config bucket (where the public components of the OIDC provider are hosted by Red Hat)

## ROSA Classic Cluster using an unmanaged OIDC provider and local modules

This can be found in the ./rosa_classic_unmanaged_oidc folder. This example uses local modules to build a cluster with an unmanaged OIDC provider. This example is useful if you are running Terraform from a location that is not permitted to pull public modules.

This example uses an unmanaged OIDC config bucket (where the public components of the OIDC provider are hosted by the customer in a public bucket)

## FAQ

1. Do I want managed or unmanaged OIDC providers?

The managed OIDC provider creates the underlying resources in a Red Hat account, which you can consume. An unmanaged OIDC provider creates the underlying resources in your own account. If you are unsure, starting with Managed is probably easier.

2. I'm getting this error, what do I do?

```
│ Error: either a token, an user name and password or a client identifier and secret are necessary, but none has been provided
```

Please export your RHCS_TOKEN as an environment variable, you can get this from https://console.redhat.com/openshift/token/rosa

3. Why is my cluster name something random like rosa-233is?

A random name is generated for your cluster if you do not provide the variable `cluster_name`

4. How do I add default tags for my clusters?

You can export an environment variable like so:

```
export TF_VAR_default_aws_tags='{"owner"="mobb@redhat.com"}'
```
