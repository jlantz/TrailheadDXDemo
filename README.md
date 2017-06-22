# Trailhead DX Demo


`src` holds the metadata source for the managed package Trailhead DX Demo
**Namespace**: tdxccidemo



# Dependencies

This project extends [NPSP: Managed Extension Package](https://github.com/SalesforceFoundation/Cumulus) and inherits the dependencies from its `cumulusci.yml` file



# Deploying to a Salesforce Org

## Prerequisites

* A local git clone of this repostory
* **CumulusCI**: This project is configured for use with [CumulusCI](http://cumulusci.readthedocs.io) which you will need to have installed and configured locally.  The `cci` command should be available in your local environment.

## Useful Build Commands

`cci flow run dev_org`
completely configures a development org for the project

`cci flow run ci_feature`
Deploys the all dependencies and unmanaged metadata and runs all Apex tests

`cci flow run ci_master --org packaging`
Deploys the all dependencies and metadata to the packaging org to prepare for managed package version upload

`cci flow run release_beta --org packaging`
Uploads a managed beta version of the package metadata currently in the packaging org and creates a Github Release

`cci flow run install_beta`
Installs all dependencies and the latest beta release

`cci flow run install_prod`
Installs all dependencies and the latest production release

# Using Scratch Orgs via Salesforce DX

This repository is configured to allow easy use of Scratch Orgs if you have access to Salesforce DX, have the `sfdx` CLI command available, and have authorized and set a `defaultdevhubusername`.  With these prerequisites in place (refer to Salesforce DX documentation), you can work with scratch orgs with the following commands:

`cci org scratch dev dev_scratch --default`
Creates a scratch org using the `dev` configuration from `orgs/dev.json` and names the org `dev_scratch` in the `cci` keychain.  The `--default` flag makes the newly created org the default org for future commands

**NOTE**: If your scratch org gets deleted by the platform, you can rerun the above command to refresh the entry in the `cci` keychain so you can recreate the org.

`cci org info dev_scratch`
Triggers the creation of the actual scratch org instance and returns information about the org including the username and password.  Once the org is created the first time it will persist in your `cci` keychain until it is deleted with `cci org scratch_delete dev_scratch` or it is automatically deleted by the platform.

`cci org browser dev_scratch`
Opens a browser and logs into the `dev_scratch` org.
