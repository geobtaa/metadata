# B1G Custom Elements


This is an overview of the custom metadata elements for the B1G Profile

| b1g-id | Label                                         | URI                             | Obligation  |
| ------ | --------------------------------------------- | ------------------------------- | ----------- |
| b1g-01 | [Code](#code)                               | b1g_code_s                    | Required    |
| b1g-02 | [Status](#status)                           | b1g_status_s                  | Required    |
| b1g-03 | [Accrual Method](#accrual-method)           | b1g_dct_accrualMethod_s      | Required    |
| b1g-04 | [Accrual Periodicity](#accrual-periodicity) | b1g_dct_accrualPeriodicity_s | Optional    |
| b1g-05 | [Date Accessioned](#date-accessioned)       | b1g_dateAccessioned_s         | Required    |
| b1g-06 | [Date Retired](#date-retired)               | b1g_dateRetired_s             | Conditional |
| b1g-07 | [Child Record](#child-record)               | b1g_child_record_b           | Optional    |
| b1g-08 | [Mediator](#mediator)                       | b1g_dct_mediator_sm          | Conditional |
| b1g-09 | [Access](#access)                           | b1g_access_s                  | Conditional |

## Code

| Label                 | Status                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | b1g_status_s                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Profile ID            | b1g-02                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Obligation            | Required                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Multiplicity          | 1-1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Field type            | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Purpose               | To indicate if a record is currently active, retired, or unknown                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Entry Guidelines      | Only one of three values is allowed: Active, Inactive, Unknown                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Commentary            | These are mainly used to group records that have been retired. Retired records are not removed from Solr, so they can be accessed by direct link. This allows us to continue using them for comparative analytics from when they were live. It also reduces link rot issues. If a user has a direct link to the item, they will be able to see that the record has been retired. Occasionally, retired records may become active again if a data provider republishes them with the same link. |
| Controlled Vocabulary | yes-strict                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Example value         | Active                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Element Set           | B1G                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

## Status

## Accrual Method

## Accrual Periodicity

## Date Accessioned

## Date Retired

## Child Record

## Mediator

## Access