---
title: Migrate from Logs Search v2 to v3
description: Learn how to migrate from Auth0 Logs Search v2 to v3.
topics:
  - logs
  - search
contentType: how-to 
useCase:
  - logs
---

# Migrate from Logs Search v2 to v3

To provide our customers with the most reliable and scalable solution, Auth0 has deprecated Tenant Logs Search Engine v2 in favor of v3.
Auth0 is proactively migrating customers unaffected by this change, while those who are potentially affected are being notified to opt in for v3 during the provided grace period.

## Am I affected by the migration?

Affected customers are those:
* With tenants created before or on May 21st, 2019
* With tenants hosted in Auth0's public cloud in the AU or EU regions
* Who use the [GET /api/v2/logs](/api/v2#!/Logs/get_logs) or the [GET /api/v2/users/{user_id}/logs](/api/v2#!/Users/get_logs_by_user) endpoint with the parameter `include_totals=true` or the `q` parameter. 

The following tenants are NOT affected:
* Cloud customers in the US region who are already using Search Engine V3.
* PSaaS customers (Migration for PSaaS customers will begin at a later date).
* Cloud tenants in the EU and AU regions that:
  * are not using the `GET /api/v2/logs` or `GET /api/v2/users/{user_id}/logs` endpoints of Management API at all.
  * are consuming the logs from the Dashboard Logs section only.
  * are using the `GET /api/v2/logs endpoint` with the by checkpoint method (using `from` parameter).
  * are consuming logs using any of the [Auth0 Logs to External Service Dashboard extensions](/extensions#export-auth0-logs-to-an-external-service) (which use the by checkpoint method).

## What’s changing?

The breaking changes are minor, but you should review your queries to make sure the results you are getting are as expected.

Breaking changes are related to:
* Pagination: the value of the `totals` field returned in the summary result when calling `GET /api/v2/logs` or `GET /api/v2/users/{user_id}/logs` is changing
* Query Syntax: The query syntax when using the `q` parameter in the `GET /api/v2/logs` has minor changes that need to be taken into account

For more details on these changes, see [Logs Search Query Syntax](/logs/query-syntax#search-engine-v3-breaking-changes). 

## How to Migrate?

After reviewing your queries, you can opt in to Tenant Logs Search Engine v3 via the Dashboard. Go to *Tenant Settings > Advanced*, then scroll down to *Migrations*. Toggle the *Legacy Logs Search V2* switch to off. 
Toggling this switch to off disables the deprecated logs search engine v2 and forces the use of search engine v3.

![](/media/articles/logs/tenant-logs-migration.png)
 
If you need help with the migration, contact us using the [Support Center](https://support.auth0.com/).

## Keep reading
* [Tenant Logs Overview](/logs)
* [Query Syntax](/logs/query-syntax)
