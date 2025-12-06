# Naming Standards for git Repo
## Folders
Folders will always be in `kebab-case`, which is all lowercase, with hyphens to separate words.

## Files
File names will always be in `kebab-case`

### Exceptions
If the file or folder cannot be named with `kebab-case` (for exmaple fabric lakehouses) then fall to `snake_case` as the next option. If for some reason `snake_case` is not an option, then default to all lowercase, no spaces.

# Naming Standards for Azure
## Resource Groups
`<orgOrBU>-<env>-<region>-<workloadOrFunction>-rg`

## Resources
Always reference the azure naming convention to find abbreviation  
https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations
`<orgOrBU>-<env>-<region>-<workloadOrFunction>-<svc>`

Examples of service abbreviations:  
Logic App - `logic`  
Storage account (general use) - `stcd<workload, application, or project><###>`  
Function App - `func`


## Env
Will be one of these three, depending on which subscription it is deployed to.
1. dev
1. qa
1. prod

## Region
Default to `westus2`, `wus2` and `westus3`, `wus3` if the first option is not available.
