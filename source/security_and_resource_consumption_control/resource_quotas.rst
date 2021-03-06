.. _resource_quotas:

===============
Resource Quotas
===============

vOneCloud quota system tracks user and group usage of system resources, allowing the cloud administrator to set limits on the usage of these resources.

Quota limits can be set for:

- **users**, to individually limit the usage made by a given user.
- **groups**, to limit the overall usage made by all the users in a given group.

Tracking the usage on:

- **Compute**: Limit the overall memory, cpu or VM instances

Quotas can be updated either from the vCenter View or from the Group Admin View.

.. image:: /images/sunstone_update_quota.png
    :align: center

Refer to :onedoc:`this guide <operation/users_groups_management/quota_auth.html>` to find out more.
