
keywords: cli, manage resources, resource group, ibmcloud resource group, ibmcloud resource, service-instance, quotas, resource group cli, resource cli

subcollection: cli
---

{{site.data.keyword.attribute-definition-list}}

# Working with resources and resource groups (ibmcloud resource)

A resource group is a way for you to organize your account resources in customizable groupings. Use the following commands from the IBM Cloud Command Line Interface to manage IBM Cloud resources in a resource group.

## ibmcloud resource groups

List resource groups:

`ibmcloud resource groups [--default]`

### Command options

--default

- Get the default group of the current account


### Examples

List all resource groups under the currently targeted account:

`ibmcloud resource groups`

List default group of currently targeted account:

`ibmcloud resource groups --default`

## ibmcloud resource group

Show details of a resource group:

`ibmcloud resource group NAME [--id]`

### Command options

NAME (required)

-   Name of the resource group

--id
-   Show ID only


### Examples

Show resource group `example-group`:

`ibmcloud resource group example-group`

Show only ID of resource group `example-group`:

`ibmcloud resource group example-group --id`


## ibmcloud resource group-create

Create a resource group:

`ibmcloud resource group-create NAME`


### Command options

NAME (required)
-   Name of the resource group

### Examples

Create a resource group `example-group`:

`ibmcloud resource group-create example-group`


## ibmcloud resource group-update

Update an existing resource group:

`ibmcloud resource group-update NAME [-n, --name NEW_NAME] [-f, --force]`


### Command options

NAME (required)
-   Name of the target resource group

-n, --name
-   New name of the resource group

-f, --force
-   Force update without confirmation


### Examples

Rename resource group `example-group` to `trial-group`:

`ibmcloud resource group-update example-group -n trial-group`


## ibmcloud resource group-delete

Delete an existing resource group:

`ibmcloud resource group-delete NAME [-f, --force]`


### Command options

NAME (required)
-   Name of the target resource group

-f, --force
-   Force deletion without confirmation



### Examples

Delete resource group `example-group`:

`ibmcloud resource group-delete example-group -f`


## ibmcloud resource quotas

List all quota definitions:

`ibmcloud resource quotas`


### Examples

List all quota definitions:

`ibmcloud resource quotas`


## ibmcloud resource quota

Show details of a quota definition:

`ibmcloud resource quota NAME`


### Command options

NAME (required)
-   Name of the quota



### Examples

Show details of quota `free`:

`ibmcloud resource quota free`


## ibmcloud resource service-instances

List service instances:

`ibmcloud resource service-instances [--service-name SERVICE_NAME] [--location LOCATION] [--type INSTANCE_TYPE] [-g RESOURCE_GROUP | --all-resource-groups] [--long] [--limit LIMIT] [--offset OFFSET] [--output FORMAT] [-q, --quiet]`


### Command options

--service-name *SERVICE_NAME*
-   Name of belonging service

--location *LOCATION*
-   Filter by location

--type *INSTANCE_TYPE*
-   Type of instances. The `service_instance` type is used if not specified. Use all to list all types of instances.

-g *RESOURCE_GROUP*
-   Resource group name

--all-resource-groups
-   Query all resource groups

--long
-   Show more fields in output

--limit LIMIT
-   Number of resources to return

--offset OFFSET
-   Starting resource position number

--output FORMAT
-   Specify output format. Only JSON is supported now.

-q, --quiet
-   Suppress verbose output.


### Examples

List service instances of service `test-service`:

`ibmcloud resource service-instances --service-name test-service`


List next page of service instances with page size of 10:

`ibmcloud resource service-instances --offset 1 --limit 10`


## ibmcloud resource service-instance

Show details of a service instance:

`ibmcloud resource service-instance (NAME|ID) [--location LOCATION] [--id]`


### Command options

NAME (required), exclusive with ID
-   Name of the service instance

ID (required), exclusive with NAME
-   ID of the service instance

--location
-   Filter by location

--id
-   Display the ID of service instance



### Examples

Show details of service instance `my-service-instance`:

`ibmcloud resource service-instance my-service-instance`


## ibmcloud resource service-instance-create

Create a service instance:

`ibmcloud resource service-instance-create NAME (SERVICE_NAME | SERVICE_ID) SERVICE_PLAN_NAME LOCATION [-d, --deployment DEPLOYMENT_NAME] [-p, --parameters @JSON_FILE | JSON_STRING ] [-g RESOURCE_GROUP] [--service-endpoints SERVICE_ENDPOINTS_TYPE] [--allow-cleanup] [--lock]`


### Command options

NAME (required)
-   Name of the service instance

SERVICE_NAME or SERVICE_ID (required)
-   Name or ID of the service. To list service offerings, use the `ibmcloud catalog service-marketplace`[command](/docs/cli/reference/ibmcloud?topic=cli-ibmcloud_catalog#ibmcloud_catalog_service_marketplace).

SERVICE_PLAN_NAME or SERVICE_PLAN_ID (required)
-   Name or ID of the service plan

LOCATION (required)
-   Target location or environment to create the service instance

-d, --deployment *DEPLOYMENT_NAME*
-   Name of the deployment

-p, --parameters *@JSONFILE or JSON_STRING*
-   JSON file or JSON string of parameters to create service instance

-g *RESOURCE_GROUP*
-   Resource group name

--service-endpoints *SERVICE_ENDPOINTS_TYPE*
-   Types of the service endpoints. Possible values are 'public', 'private', 'public-and-private'. The default value for service endpoints is the type configured by the service in {{site.data.keyword.cloud}}.

--allow-cleanup
-   Whether the service instance should be deleted (cleaned up) during the processing of a region instance delete call

--lock
-   Whether to create the service instance with locked state



### Examples

Create a service instance that is named `my-service-instance`, that uses service plan `test-service-plan` of service `test-service` on location `eu-gb`:

`ibmcloud resource service-instance-create my-service-instance test-service test-service-plan eu-gb`


## ibmcloud resource service-instance-update

Update service instance:

`ibmcloud resource service-instance-update ( NAME | ID ) [-n, --name NEW_NAME] [--service-plan-id SERVICE_PLAN_ID] [-p, --parameters @JSON_FILE | JSON_STRING ] [-g RESOURCE_GROUP] [--service-endpoints SERVICE_ENDPOINTS_TYPE] [-f, --force]`


### Command options

Name (required)
-   Name of the service instance, exclusive with ID

ID (required)
-   ID of the service instance, exclusive with NAME

-n, --name *NEW_NAME*
-   New service instance name

--service-plan-id *SERVICE_PLAN_ID*
-   New Service Plan ID

-p, --parameters *@JSON_FILE | JSON_STRING*
-   JSON file or JSON string of parameters to create service instance

-g *RESOURCE_GROUP*
-   Resource group name

--service-endpoints *SERVICE_ENDPOINTS_TYPE*
-   Types of the service endpoints. Possible values are 'public', 'private', 'public-and-private'.

-f, --force
-   Force update without confirmation



### Examples

Update service instance `my-service-instance`, change its name to `new-service-instance`:

`ibmcloud resource service-instance-update my-service-instance -n new-service-instance`


## ibmcloud resource service-instance-delete

Delete service instance. If provisioning is in progress, the command attempts to cancel the provisioning process. Some services might not support cancellation:

`ibmcloud resource service-instance-delete (NAME|ID) [-f, --force] [--recursive]`


### Command options

Name (required)
-   Name of the service instance, exclusive with ID

ID (required)
-   ID of the service instance, exclusive with NAME

-f, --force
-   Force deletion without confirmation

--recursive
-   Delete all belonging resources



### Examples

Delete resource service-instance `my-service-instance`:

`ibmcloud resource service-instance-delete my-service-instance`


## ibmcloud resource service-instance-lock

Lock service instance:

`ibmcloud resource service-instance-lock ( NAME | ID ) [-g RESOURCE_GROUP] [-f, --force]`


### Command options

Name (required)
- Name of the service instance, exclusive with ID

ID (required)
- ID of the service instance, exclusive with NAME

-g *RESOURCE_GROUP*
- Resource group name

-f, --force
- Force locking without confirmation



### Examples

Lock resource service-instance `my-service-instance`:

`ibmcloud resource service-instance-lock my-service-instance`


## ibmcloud resource service-instance-unlock

Unlock service instance:

`ibmcloud resource service-instance-unlock ( NAME | ID ) [-g RESOURCE_GROUP] [-f, --force]`


### Command options

Name (required)
- Name of the service instance, exclusive with ID

ID (required)
- ID of the service instance, exclusive with NAME

-g *RESOURCE_GROUP*
- Resource group name

-f, --force
- Force locking without confirmation



### Examples

Unlock resource service-instance `my-service-instance`:

`ibmcloud resource service-instance-unlock my-service-instance`


## ibmcloud resource service-keys

List service keys of service instance:

`ibmcloud resource service-keys [ --instance-id ID | --instance-name NAME ]`


### Command options

--instance-id
- Service Instance ID

--instance-name
- Service Instance Name


### Examples

List service keys of service instance `my-service-instance`:

`ibmcloud resource service-keys --instance-name my-service-instance`


## ibmcloud resource service-key

Displays the details of any number of service keys, where the first *n* characters of the service key name matches the supplied KEY_NAME:

`ibmcloud resource service-key (NAME | ID) [-g RESOURCE_GROUP] [--id]`


### Command options

NAME
- Name of the key

ID
- ID of the key

-g
- Resource group name

--id
- Display the ID of service key. This option is exclusive with '--output'.

-g RESOURCE_GROUP
- Resource group name

### Examples

Show details of service keys `my-service-key`:

`ibmcloud resource service-key my-service-key`


Show details of service key with ID `crn:v1:bluemix:public:cloudantnosqldb:us-south:a/537860630a5ba7115be954e8d5aa5689:cc2a6d6c-8f5e-4038-b975-b09b51d1d8dc:resource-key:9057f12e-fbf5-421d-8865-764422217a79`:


`ibmcloud resource service-key crn:v1:bluemix:public:cloudantnosqldb:us-south:a/537860630a5ba7115be954e8d5aa5689:cc2a6d6c-8f5e-4038-b975-b09b51d1d8dc:resource-key:9057f12e-fbf5-421d-8865-764422217a79`


## ibmcloud resource service-key-create

Create a service key:

`ibmcloud resource service-key-create NAME [ROLE_NAME] ( --instance-id SERVICE_INSTANCE_ID | --instance-name SERVICE_INSTANCE_NAME) [--service-id SERVICE_ID] [-p, --parameters @JSON_FILE | JSON_TEXT] [-g RESOURCE_GROUP] [--service-endpoint SERVICE_ENDPOINT_TYPE] [-f, --force] [-f, --force] [-q, --quiet]`


### Command options

NAME (required)
- Name of the key.

ROLE_NAME (optional)
- Name of the IAM service role. The specified role cannot be one of the default platform roles. You can verify eligibility of any role for use with this option by running `ibmcloud iam roles --service <your-service>` and checking that `serviceRole` appears in the role's CRN.

--instance-id *SERVICE_INSTANCE_ID*
- Service instance ID.

--instance-name *SERVICE_INSTANCE_NAME*
- Service instance name.

--service-id *SERVICE_ID*
- Name or UUID of the service ID, which the role belongs to.

-p, --parameters *@JSON_FILE | JSON_TEXT*
- Parameters JSON file or JSON string.

-g *RESOURCE_GROUP*
- Resource group name.

--service-endpoint *SERVICE_ENDPOINT_TYPE*
- Type of the service endpoint. Possible values are 'public' or 'private'.

--output FORMAT (optional)
- Specify the output format. Only JSON is supported.

-f, --force
- Force creation without confirmation

-q, --quite
- Suppress verbose output.



### Examples

Create a service key named `my-service-key` with role `Administrator` for service instance `my-service-instance`:

`ibmcloud resource service-key-create my-service-key Administrator --instance-name my-service-instance`


Create a service key named `my-service-key` without any role for a non-iam-enabled service instance `my-service-instance`:

`ibmcloud resource service-key-create my-service-key --instance-name my-service-instance`


## ibmcloud resource service-key-update

Update a service key:

`ibmcloud resource service-key-update ( NAME | ID ) [-n, --name NEW_NAME] [-g RESOURCE_GROUP] [-f, --force]`


### Command options

NAME | ID
- Name or ID of the key

-n, --name NEW_NAME
- New name of the key

-g RESOURCE_GROUP
- ID of the resource group to which the key belongs

-f, --force
- Force update without confirmation



### Examples

Update a service key named `my-service-key`, give it a new name `my-service-key-2`:

`ibmcloud resource service-key-update my-service-key -n my-service-key-2`


## ibmcloud resource service-key-delete

Delete a service key:

`ibmcloud resource service-key-delete ( KEY_NAME | KEY_ID ) [-f, --force]`


### Command options

KEY_NAME | KEY_ID
- Name of the key or the ID of the key

-f, --force
- Force deletion without confirmation



### Examples

Delete service key `my-service-key`:

`ibmcloud resource service-key-delete my-service-key`


## ibmcloud resource search

Search resources by using Lucene query syntax:

`ibmcloud resource search LUCENE_QUERY [-o, --offset OFFSET] [-l, --limit LIMIT] [-s, --sort-by (name, family, region, type, crn)] [-p, --provider PROVIDER] [-ir, --is-reclaimed (false, true, any)] [--output FORMAT]`


### Command options

-ir, --is-reclaimed
- Search for account resources that have been reclaimed. By default the search returns only active resources, however you can set is-reclaimed to any to search for resources whether they have been reclaimed or not. Set this option to `true` to apply the search criteria only to reclaimed resources. Set this option to `false` to search only for active resources. `false` is the default behavior.

-o, -offset
- Starting resource position number

-l, -limit
- Number of resources to return, up to a maximum of 10000.

-s, --sort-by
- Property to sort by. Accepted values are `name`, `family`, `region`, `type`, `crn`.

-p, --provider
- Display classic infrastructure resources. The only supported value is `classic-infrastructure`.

### Searchable attributes

You can search for the following attributes:

name
- The user-defined name of the resource.

region
- The geographical location where the resource is provisioned. For example: us-south, us-east, au-syd, eu-gb, eu-de, and jp-tok.

service_name
- The name of the service as it appears in the Name column of the output of 'ibmcloud catalog service-marketplace'.

family
- The cloud component to which your resource belongs. The allowed values are containers, resource_controller, vmware, or ims.

doc.resource_group_id
- The ID of the resource group.

type
- The resource type. The allowed values are k8-cluster, resource-instance, resource-group, vmware-solutions, cloud-objects-storage-infrastructure, block-storage, file-storage, cloud-backup.

creation_date
- The date on which the resource is created.

modification_date
- The last modification date of the resource. It is in the format yyyy-mm-ddThh:mm:ssZ

_objectType
- The type of the classic infrastructure resource. Allowed values are SoftLayer_Virtual_DedicatedHost, SoftLayer_Hardware, SoftLayer_Network_Application_Delivery_Controller, SoftLayer_Network_Subnet_IpAddress, SoftLayer_Network_Vlan, SoftLayer_Network_Vlan_Firewall and SoftLayer_Virtual_Guest.

tags, tagReferences.tag.name
- The tag attached to a resource. Use tagReferences.tag.name when searching for tags attached to classic infrastructure resources

### Examples

Search for Resource Controller resources in the specified location (i.e. in us-south region):

`ibmcloud resource search "region:us-south AND family:resource_controller"`


Search for resource groups with name default:

`ibmcloud resource search "name:default AND type:resource-group"`


Search for a resource with the specified Cloud Resource Name (CRN):

`ibmcloud resource search "crn:\"crn:v1:bluemix:public:cloudantnosqldb:us-south:s/4948af7e-cc78-4321-998a-e549dd5e9210:41a031cd-e9e5-4c46-975d-9e4a6391322e:cf-service-instance:\""`


Search for a resource with the specified tag:

`ibmcloud resource search "tags:\"mykey:myvalue\""`


Search for Classic Infrastructure Virtual Guest resource with the specified id (only with -p classic-infrastructure):

`ibmcloud resource search "id:12345678 _objectType:SoftLayer_Virtual_Guest"`


Search for Classic Infrastructure Hardware resource with the specified tag name (only with -p classic-infrastructure):

`ibmcloud resource search "tagReferences.tag.name:name _objectType:SoftLayer_Hardware"`


## ibmcloud resource tags

List all tags in your billing account:


`ibmcloud resource tags [-o, --offset OFFSET] [-l, --limit LIMIT]  [-p, --provider classic-infrastructure] [-d, --details true] [-a, --attached true] [--output FORMAT] [--tag-type TAG_TYPE] [--account-id ACCOUNT_ID]`


### Command options

--offset value, -o value
- Starting resource position number (default: 0).

--limit value, -l value
- Number of resources to return (maximum 1000) (default: 100).

--provider value, -p value
- Display Classic Infrastructure resources, only value allowed is: classic-infrastructure. Use it for resources of type SoftLayer_Hardware, SoftLayer_Network_Application_Delivery_Controller, SoftLayer_Network_Subnet_IpAddress or SoftLayer_Network_Vlan.

--details value, -d value
- Show additional attributes for each tag, only value allowed is true.

--attached value, -a value
- Show only filtered attached tags to a resource, only value allowed is true.

--tag-type value
- Type of the tag. Only allowed values are: user, service or access (default value : user).

--account-id value
- The ID of the account that owns the tags that you want to list (required if tag-type is set to service).

--output value
- Specify output format. Only JSON is supported now.

-q, --quiet
- Suppress verbose output.

## ibmcloud resource tag-create

Create an access management tag:

`ibmcloud resource tag-create --tag-names TAG_NAMES`


### Command options

--tag-names value
- Comma separated list of tag names.

-q, --quiet
- Suppress verbose output.

This command is only valid for access management tags. For example:

* Run the following command to create the access management tag `project:myproject`:
   
`ibmcloud resource tag-create —tag-names “project:myproject”`


## ibmcloud resource tag-attach

Attach one or more tags to a resource:

`ibmcloud resource tag-attach --tag-names TAG_NAMES (--resource-name NAME | --resource-id RESOURCE_ID ) [--resource-type RESOURCE_TYPE] [--tag-type TAG_TYPE] [--account-id ACCOUNT_ID] [--replace] [--update]`


### Command options

--tag-names value
- Comma-separated list of tag names.

--resource-name value
- Name of the resource on which the tags should be attached.

--resource-id value
- CRN of the resource on which the tags should be attached (for Classic Infrastructure resource, it is the ID of the resource).

--resource-type value
- Type of the tag. Only allowed values are: user, service or access (default value : user).

--tag-type value
- The type of the tag. The only allowed values are `user` or `service`. The default value is `user`.

--account-id value
- The ID of the account that owns the resources to be tagged (required if tag-type is set to service).

--replace
- The list of tag names will replace the current list of tag names attached to the resource.

--update
- The tag names in the format `key:value` will be updated. The option has no effect on tag names that are not in that format.

-q, --quiet
- Suppress verbose output.

### Examples

* To attach the user tag `MyTag` to a Kubernetes cluster named `MyCluster`, first look for the CRN of the cluster you would like to tag:
    
    `ibmcloud resource search 'type:k8\-cluster AND name:MyCluster'`

    Take note of the CRN, which is a string similar to the following example:
    
    `crn:v1:bluemix:public:containers-kubernetes:us-south:a/a27a4741a57dcf5c965939adb66fe1c7:a46242e638ca47b09f10e9a3cbe5687a::`


    To attach the tag, run the following command:
    
    `ibmcloud resource tag-attach --tag-names MyTag --resource-id rn:v1:bluemix:public:containers-kubernetes:us-south:a/a27a4741a57dcf5c965939adb66fe1c7:a46242e638ca47b09f10e9a3cbe5687a::`
   

* To attach the user tag `MyTag` to a resource named `MyResource`:
    
    `ibmcloud resource tag-attach --tag-name MyTag --resource-name  'MyResource'`


* To attach the user tag `MyTag` to a classic infrastructure virtual guest named `MyVM`, first look for the ID of the virtual guest you would like to tag:
    
    `ibmcloud resource search 'fullyQualifiedDomainName:MyVM  _objectType:SoftLayer_Virtual_Guest' -p classic-infrastructure`


    Take a note of the ID, which is a string similar to `48373549`.

    To attach the tag, run the following command:
    
    `ibmcloud resource tag-attach --tag-names MyTag --resource-id 48373549 --resource-type SoftLayer_Virtual_Guest`


* To attach the access management tag `project:myproject`, that you previously created, to an instance of IBM Cloud Object Storage called `Project data`, run the following command:
    
    `ibmcloud resource tag-attach --tag-names "project:myproject" --resource-name Project data -—tag-type access`


* To update to `production` the value of the `env` user tag on a resource named `MyResource` run the following command:

    
    `ibmcloud resource tag-attach --tag-names 'env:production' --resource-name 'MyResource' --update`


* To update to `production` the value of the `env` access management tag on a resource named `MyResource` run the following command:

    
    `ibmcloud resource tag-attach --tag-names 'env:production' --resource-name 'MyResource' --update --tag-type access`

* To replace all user tags of `MyResource` with a new set of tags `tag1`, `tag2`, and `tag3` run the following command:

    
    `ibmcloud resource tag-attach --tag-names 'tag1,tag2,tag3' --resource-name 'MyResource' --replace`


* To replace all access management tags of `MyResource` with the tag `compliance:hipaa` run the following command:

    
    `ibmcloud resource tag-attach --tag-names 'compliance:hipaa' --resource-name 'MyResource' --replace --tag-type access`


## ibmcloud resource tag-detach

Detaching one or more tags from a resource:

ibmcloud resource tag-detach --tag-names TAG_NAMES (--resource-name NAME | --resource-id RESOURCE_ID ) [--resource-type RESOURCE_TYPE] [--tag-type TAG_TYPE] [--account-id ACCOUNT_ID]


### Command options

--tag-names value
- Comma-separated list of tag names.

--resource-name value
- Name of the resource on which the tags should be attached.

--resource-id value
- CRN of the resource on which the tags should be attached (for Classic Infrastructure resource, it is the ID of the resource).

--resource-type value
- Resource type on which the tags should be attached (required for Classic Infrastructure resource of type SoftLayer_Hardware, SoftLayer_Network_Application_Delivery_Controller, SoftLayer_Network_Subnet_IpAddress or SoftLayer_Network_Vlan only).

--tag-type value
- Type of the tag. Only allowed values are: user, service or access (default value : user).

--account-id value
- The ID of the account that owns the resources to be detached (required if tag-type is set to service).

-q, --quiet
- Suppress verbose output.

### Examples

* To detach the user tag `MyTag` from a Kubernetes cluster named `MyCluster`, first look for the CRN of the cluster you would like to detach the tag from:
    
    `ibmcloud resource search 'type:k8\-cluster AND name:MyCluster'`


    Take note of the CRN, which is a string similar to the following example:
    
    `crn:v1:bluemix:public:containers-kubernetes:us-south:a/a27a4741a57dcf5c965939adb66fe1c7:a46242e638ca47b09f10e9a3cbe5687a::`

* To detach the tag, run the following command:
    
    `ibmcloud resource tag-detach --tag-names MyTag --resource-id rn:v1:bluemix:public:containers-kubernetes:us-south:a/a27a4741a57dcf5c965939adb66fe1c7:a46242e638ca47b09f10e9a3cbe5687a::`


* To detach the user tag `MyTag` to a resource named `MyResource`:
    
    `ibmcloud resource tag-detach --tag-name MyTag --resource-name 'MyResource'`

* To detach the user tag `MyTag` to a classic infrastructure virtual guest named `MyVM`, first look for the ID of the virtual guest you would like to detach the tag from:
    
    `ibmcloud resource search 'fullyQualifiedDomainName:MyVM  _objectType:SoftLayer_Virtual_Guest' -p classic-infrastructure`


    Take a note of the ID, which is a string similar to `48373549`.

* To detach the tag, run the following command:
    
    `ibmcloud resource tag-detach --tag-names MyTag --resource-id 48373549 --resource-type SoftLayer_Virtual_Guest`


* To detach the access management tag `project:myproject` from an instance of IBM Cloud Object Storage called `Project data`, run the following command:
    
    `ibmcloud resource tag-detach --tag-names "project:myproject" --resource-name Project data -—tag-type access`


* To detach the `env:value` tag from `MyResource`, regardless of its value, run the following command:

    
    `ibmcloud resource tag-detach --tag-names 'env:*' —resource-name 'MyResource'`


* To detach all tags from `MyResource` run the following command:

    
    `ibmcloud resource tag-detach --tag-names '*' —resource-name 'MyResource'`


## ibmcloud resource tag-delete

Delete a tag:

`ibmcloud resource tag-delete (--tag-name TAG_NAME | -a, --all  [-f, --force]) [-p, --provider PROVIDER] [--tag-type TAG_TYPE] [--account-id ACCOUNT_ID]`


### Command options

--tag-name value
- Tag name to be deleted.

--provider value, -p value
- Delete the tag in the specified provider (only supported value is classic-infrastructure). Use it for resources of type SoftLayer_Hardware, SoftLayer_Network_Application_Delivery_Controller, SoftLayer_Network_Subnet_IpAddress or SoftLayer_Network_Vlan.

--tag-type value
- Type of the tag. Only allowed values are: user, service or access (default value : user).

account-id value
- The ID of the account that owns the tags to be deleted (required if tag-type is set to service).

--force, -f
- Delete the tags without confirmation.

--all, -a
- Delete all tags not attatched to any resources.

-q, --quiet
- Suppress verbose output.



A tag can be deleted only if it isn't attached to any resource.

### Examples

* To delete the user tag `MyTag` from the account:
    
    `ibmcloud resource tag-delete --tag-name "MyTag"`


* To delete the access management tag `project:myproject` from the account:
    
   `ibmcloud resource tag-delete --tag-name "project:myproject" --tag-type access`


* To delete all unused user tags from the account:
    
    `ibmcloud resource tag-delete -a`


* To delete all unused access management tags from the account:
    
    `ibmcloud resource tag-delete -a --tag-type access`



## ibmcloud resource reclamations

List reclaimed resources that can be restored or deleted:

`ibmcloud resource reclamations [--resource-instance-id INSTANCE_ID]`


### Command options

--resource-instance-id
- The globally unique ID (GUID) of the resource instance

### Examples

List all resource reclamations:

`ibmcloud resource reclamations`


List resource reclamations of a particular service instance:

`ibmcloud resource reclamations --resource-instance-id abcd1234-ef56-486e-b293-22d6c7eb6699`


## ibmcloud resource reclamation

Show details of a resource reclamation:

`ibmcloud resource reclamation RECLAMATION_ID`


### Command options

RECLAMATION_ID
- Resource reclamation ID


### Examples

Show details of a resource reclamation:

`ibmcloud resource reclamation daf12d343ef`


## ibmcloud resource reclamation-restore

Restore a reclaimed resource so that the resource is available again:

`ibmcloud resource reclamation-restore ID [--comment COMMENT]`


### Command options

ID
- ID of the resource reclamation

--comment
- Comments about the action


### Examples

Restore a resource reclamation with ID `d9fendfwlw`:

`ibmcloud resource reclamation-restore "d9fendfwlw"`


Restore a resource reclamation with ID `d9fendfwlw`, leave a comment of `need to use for another 3 months`, and show JSON output:


`ibmcloud resource reclamation-restore "d9fendfwlw" --comment "need to use for another 3 months" --output JSON`


## ibmcloud resource reclamation-delete

Delete a reclaimed resource so that the resource can no longer be restored:

`ibmcloud resource reclamation-delete ID [--comment COMMENT] [--f, --force]`


### Command options

ID
- ID of the resource reclamation

--comment
- Comments about the action

-f, --force
- Force deletion without confirmation


### Examples

Delete a resource reclamation with ID `d9fendfwlw`:

`ibmcloud resource reclamation-delete "d9fendfwlw"`


Delete a resource reclamation with ID `d9fendfwlw` and leave a comment of `no longer needed` without confirmation:


`ibmcloud resource reclamation-delete "d9fendfwlw" --comment "no longer needed" -f`

