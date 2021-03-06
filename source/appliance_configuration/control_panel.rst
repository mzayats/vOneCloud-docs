.. _control_panel:

================================================================================
Control Panel
================================================================================

This is a web based interface available at ``http://<appliance_ip>:8000`` which handles many aspects of the vOneCloud platform configuration.

To log in the administrator will need the ``oneadmin`` account, which is set in the initial configuration of the Control Console.

The next section documents the available information and actions in this interface

Appliance Management
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In the dashboard of the Control Panel you will be able to see the following information:

+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|     Parameter     |                                                                                    Description                                                                                     |
+===================+====================================================================================================================================================================================+
| UUID              | Each vOneCloud appliance has an automatically generated UUID used to identify it. This information is required by vOneCloud Support for users with an active support subscription. |
+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Installation Date | Records the date of the vOneCloud first deployment.                                                                                                                                |
+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Version           | Active vOneCloud version                                                                                                                                                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Upgrade Date      | Records the date of last vOneCloud upgrade.                                                                                                                                        |
+-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. image:: /images/control_panel_dashboard_2.png
    :align: center

Additionally vOneCloud will report the subscription status:

* No subscription detected
* Active subscription
* Expired subscription

.. warning:: If you click on **Upgrade** or **Upgrade Now** (to upgrade the vOneCloud version, or the system packages, respectively), you will see that a few jobs appear in `pending` state in the job queue. You will not receive any further user feedback until it finishes executing. This may take a long time: 15 minutes for **Upgrade**, and even more than an hour for **Upgrade Now**, depending on your internet access speed. If a job failed, it will turn to red, if it's successful, it will turn to green. So please, **be patient until all the jobs finish executing**.

Configuration Management
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The configuration action handles the supported configuration of the vOneCloud appliance:

* :ref:`Active Directory or LDAP integration <authentication>`.
* :ref:`System Options - Enable SSH <control_panel_system_options_ssh>`.
* :ref:`System Options - Enable SSL <control_panel_system_options_ssl>`.

If the configuration is changed while OpenNebula is running, it will need to be restarted. A warning will appear in the dashboard reminding the user to restart the OpenNebula service.

System options
^^^^^^^^^^^^^^

It is possible to configure SSH and SSL:

.. image:: /images/system_options.png
    :align: center

.. _control_panel_system_options_ssh:

SSH
"""

By default SSH access is disabled. If you want to enable it, enable the ``SSH Password Authentication`` checkbox.

You can choose whether to allow password based authentication. If you only want public ssh key authentication you need to fill in the ``SSH Authorized Public Key(s) for root`` field.

.. _control_panel_system_options_ssl:

SSL
"""

If you want to enable SSL you will need to:

* Enable the ``SSL enabled`` checkbox
* Provide a Certificate (copy&paste the contents of the file)
* Provide a Key Certificate (copy&paste the contents of the file)
* Optionally, provide the CA Certificate (copy&paste the contents of the file)

.. note:: If you are going to use a self-signed SSL certificate, and do not have the CA certificate, you will need to have your browser trust that certificate, in both 443 and 29876 ports in the vOneCloud IP or FQDN. Otherwise VNC may not work

Service Management
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The OpenNebula services can be managed in the main dashboard: start, stop and restart.

Any of this actions will trigger one or more tasks. If one of this tasks fails, the user will be notified, and those with an active support subscription will be able to send the error report to the vOneCloud Support.

.. _control_panel_automatic_upgrades:

Log Access
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Control Panel features the possibility to access the OpenNebula logs.

Automatic Upgrades
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When a new vOneCloud release is available for download users will be notified both in Sunstone and in the Control Panel. Users with an active support subscription will be able to upgrade with a single click. In the main Dashboard area the user will be notified if there is a new release available. In that case the user will be able to click a button that will start the upgrade.

.. note::
    Before running an automatic upgrade users are recommend to create a vCenter snapshot of the vOneCloud appliance in order to revert back to it in case of failure.

Opening the Control Panel from Sunstone
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Once OpenNebula and Sunstone have been started in the Control Panel, you will be able to see a link the Sunstone GUI to go back to the Control Panel. Of course, you can also manually open ``http://<appliance_ip>:8000``.

.. image:: /images/control_panel_link.png
    :align: center
