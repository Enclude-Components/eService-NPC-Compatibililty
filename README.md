# eService-NPC-Compatibililty
Holds post-install metadata to make eService compatible with Nonprofit Cloud orgs, specifically with Person Accounts

## Pre-requisites
If you haven't already installed and configured eService, see the [Installation Instructions](https://github.com/EncludeLtd/eCASSV2.5/blob/main/docs/installation_instructions.md)


## Deploy

<a href="https://githubsfdeploy.herokuapp.com?owner=Enclude-Components&repo=eService-NPC-Compatibililty&ref=main">
  <img alt="Deploy to Salesforce"
       src="https://raw.githubusercontent.com/afawcett/githubsfdeploy/master/deploy.png">
</a>

## Setup

### Record Types
Ensure that **only** the following record types are active for any profiles using eService
- Person Account
  - Client Person Account
  - General Person Account[^1]
- Intervention (Attendance__c)
  - Course Attendance
- Service Referral (Referral__c)
  - Internal
  - Outgoing

[^1]: "General Person Account" may be labeled simply "Person Account" if eStart was not installed. It's recommended that you relabel it to "General Person Account" (Only change the **Label**, do not change the Name.)

### Page Layout Assignments
The following page layouts should be assigned to the listed Record Types.

#### Person Account[^2]
| Record Type | Page Layout |
| ----------- | ----------- |
| Client Person Account | Client Person Account Layout |

[^2]: Other record types and page layout assignments may be required for Account and Person Account if you have not installed eStart

#### Intervention (Attendance__c)
| Record Type | Page Layout |
| ----------- | ----------- |
| Course Attendance | Course Attendance Layout |

#### Service Referral (Referral__c)
| Record Type | Page Layout |
| ----------- | ----------- |
| Internal    | Internal Layout |
| Outgoing    | Outgoing Layout |

### Permissions

#### Permission Set Groups
- eService Permissions: Base permissions for eService Users. Assign this to all users who need access. Ensure that you are assigning the eService Permissions **GROUP** to the user, and not the Permission Set with the same name.

#### Permission Set
- eService Admin: Additional permissions to eService admins. Assign this to users who will create and edit Programmes. This should be assigned *in addition to* eService Permissions

If custom objects/fields are created as part of an org's develoment, it's recommended that they be put in a separate permission set. The custom permission set can then be added to the eService Permissions Permission Set Group.

## Developers
This repo is a [CumulusCI](https://cumulusci.readthedocs.io/en/latest/). A scratch org can be generated by cloning the repository and running the command
```bash
cci flow run dev_org --org dev
```