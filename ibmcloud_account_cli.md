keywords: cli, ibmcloud account cli, managing accounts cli, managing users cli, account, account update command

subcollection: cli

---

{{site.data.keyword.attribute-definition-list}}

# Managing accounts and users (ibmcloud account)


Use the following commands from the IBM Cloud Command Line Interface to manage accounts and users in an account.


## ibmcloud account show


Show account details:
ibmcloud account show


### Examples


Show details of currently targeted account:
ibmcloud account show


## ibmcloud account update


Update a specific account:
ibmcloud account update (--service-endpoint-enable true | false)


### Command options


--service-endpoint-enable true | false
:   Enable or disable service endpoints connectivity for a SoftLayer account.


### Examples


Enable service endpoint connectivity for current account:
ibmcloud account update --service-endpoint-enable true


## Classic infrastructure account audit-logs


List SoftLayer account audit logs:
account audit-logs [-u, --user-name USER_NAME] [-t, --object-type OBJECT_TYPE] [-o, --object OBJECT] [-a, --action ACTION] [-s, --start-date START_DATE] [-e, --end-date END_DATE]


### Command options


-a, --action *ACTION*
:   Action. List audit logs with the action.

-e, --end-date *END_DATE*
:   End date. List audit logs before the end date. Supported formats are yyyy-MM-ddTHH:mm:ss.

o, --object *OBJECT*
:   Object. List audit logs with the object.

t, --object-type *OBJECT_TYPE*
:   Object type. List audit logs with the object type.

s, --start-date *START_DATE*
:   Start date. List audit logs after the start date. Supported formats are yyyy-MM-ddTHH:mm:ss.

u, --user-name *USER_NAME*
:   User name. List audit logs with the user name.

### Examples


List audit logs:
ibmcloud account audit-logs


## ibmcloud account audit-logs


List account audit logs:
ibmcloud account audit-logs [--user-name USER_NAME] [--object-type OBJECT_TYPE] [--object OBJECT] [--action ACTION] [--start-date START_DATE] [--end-date END_DATE]


### Command options


--user-name *USER_NAME* (optional)
:   List audit logs with the user name.

--object-type *OBJECT_TYPE* (optional)
:   List audit logs with the object type.

--object *OBJECT* (optional)
:   List audit logs with the object.

--action *ACTION* (optional)
:   List audit logs with the action.

--start-date *START_DATE* (optional)
:   List audit logs after the start date. Supported formats are yyyy-MM-ddTHH:mm:ss.

--end-date *END_DATE* (optional)
:   List audit logs before the end date. Supported formats are yyyy-MM-ddTHH:mm:ss.


## ibmcloud account users


Displays users that are associated with the account. To view the required permissions to run this command,
see [Retrieve users in the account](/apidocs/user-management#list-users).
ibmcloud account users [-c, --account-id ACCOUNT_ID]


### Command options


-c (optional)
:   Account ID. If not specified, default to current account.

## ibmcloud account user-remove


Remove a user from an account (account owner only).
ibmcloud account user-remove USER_ID [-c ACCOUNT_ID] [-f, --force]


### Command options


USER_ID (required)
:   User ID

-c ACCOUNT_ID
:   Account ID. If not specified, default to current account.

-f, --force
:   Force removal without confirmation.

## ibmcloud account user-invite


Invite a user to the account:
ibmcloud account user-invite USER_EMAIL [-o ORG [--org-role ORG_ROLE] [-s SPACE, --space-role SPACE_ROLE]] [-r, --region REGION]


### Command options


USER_EMAIL (required)
:   The email of the user to be invited.

-o, --org ORG (deprecated)
:   Organization to invite user to.

--org-role ORG_ROLE (deprecated)
:   Organization role. Valid inputs are: `OrgManager`, `BillingManager`, `OrgAuditor`, and `OrgUser`. If omitted, the `OrgUser` role is set.

-s, --space SPACE (deprecated)
:   Space to invite user to.

--space-role SPACE_ROLE (deprecated)
:   Space role. Valid inputs are: `SpaceManager`, `SpaceDeveloper`, and `SpaceAuditor`.

-r, --region REGION (deprecated)
:   Region name. Defaults to current region if not specified.


If you aren't ready to assign access, or want to assign an IAM policy, you can invite a user and assign it later. For more information about assigning access to users, see [Managing access to resources](/docs/account?topic=account-assign-access-resources).


## ibmcloud account user-reinvite


Resend invitation to a user (account admin):
ibmcloud account user-reinvite USER_EMAIL


### Command options


USER_EMAIL (required)
:   The email of the user to be invited again.

## ibmcloud account user-preference


Show user preference details:
ibmcloud account user-preference


## ibmcloud account user-preference-update


Update user preferences:
ibmcloud account user-preference-update (--position NEW_POSITION)


### Command options


--position *NEW_POSITION* (optional)
:   Set a user's position, such as `manager` or `student`.

## ibmcloud account user-status


Show user's status:
ibmcloud account user-status [USER_ID] [--output FORMAT] [-q, --quiet]


### Command options


USER_ID
:   User ID. If not specified, default to current user.

--output FORMAT
:   Specify output format. Only 'JSON' is supported.

-q, --quiet
:   Suppress verbose output.

## ibmcloud account user-status-update


Update user's status:
ibmcloud account user-status-update USER_ID NEW_STATUS [--output FORMAT] [-q, --quiet]


### Command options


USER_ID (required)
:   User ID.

NEW_STATUS (required)
:   Set a user's status, such as `SUSPENDED` or `ACTIVE`. For more information, see [User account status](https://cloud.ibm.com/apidocs/user-management#user-states) for a list of possible statuses. This option can also take in values in lowercase such as `suspended` or `active`.

--output FORMAT
:   Specify output format. Only 'JSON' is supported.

-q, --quiet
:   Suppress verbose output.

### Examples


Suspend user `user@ibm.com`:
ibmcloud account user-status-update user@ibm.com SUSPENDED

## ibmcloud account platform-notification-subscribe


Subscribe platform notification:
ibmcloud account platform-notification-subscribe (--type TYPE)


### Command options


--type *TYPE* (optional)
:   Notification type, one of `unplanned_events`, `planned_maintenance`.

## ibmcloud account platform-notification-unsubscribe


Unsubscribe platform notification:
ibmcloud account platform-notification-unsubscribe (--type TYPE)


### Command options


--type *TYPE* (optional)
:   Notification type, one of `unplanned_events`, `planned_maintenance`.
