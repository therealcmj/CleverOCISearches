# CleverOCISearches
My (not yet so) big list of clever searches you can do in OCI's Search (also known as RQS)

# General

You can use the searches below in the console or from the CLI. The CLI has some other benefits over the GUI but you do you.

In general a search is something like

> query foo resources

or

> query foo resources where ...

or

> query foo resources return allAdditionalFields

or even

> query key resources return allAdditionalFields where ...

# Searches

## With the OwnerEmail tag

query all resources where ( definedTags.namespace = "Oracle-Standard" && definedTags.key="OwnerEmail")

## and without the OwnerEmail tag

query all resources where definedTags.key!="OwnerEmail"

## Vault

* find all keys in a vault 
  `query key resources where vaultId="ocid1.vault.oc1.iad.xxx`

* find vaults and count the keys, order by smallest to largest
`oci search resource structured-search --query-text 'query key resources return allAdditionalFields' | jq '.data.items[]."additional-details".vaultId' | sort | uniq -c | sort -n`

## Policies

* `query Policy resources return allAdditionalFields`

## VNICs

* `query Vnic resources return allAdditionalFields where subnetId="ocid1.subnet.oc1.iad.XXX"`


## Bastion

* `query bastion resources where targetSubnetId = “ocid1.subnet.oc1.iad.XXX”`

* `query bastion resources return allAdditionalFields where targetVcnId="ocid1.vcn.oc1.iad.XXX`

