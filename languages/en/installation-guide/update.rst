..  _update:

Upgrade to a newer version
==========================

You should inform in advance end users that the platform will be stopped.
It can be done through mass mail engine and with a side-wide banner.

Check for upgrade
-----------------

As root, run:

::

    yum check-update tuleap\*


Note: you can update only the tuleap part (tuleap*) but we highly recommend you to upgrade the whole OS on regular basis.

Upgrade
-------

You should always read the :ref:`deployment guide instructions <deployment-guide>` before upgrading.

On RHEL/CentOS 7, run as root:

::

    # Stop service
    systemctl stop tuleap
    systemctl stop nginx
    systemctl stop httpd

    # Upgrade packages
    yum update
    # or to upgrade only Tuleap packages (/!\ you might miss security fixes in Tuleap dependencies):
    # yum update tuleap\*

    # Apply data upgrades
    /usr/lib/forgeupgrade/bin/forgeupgrade --config=/etc/tuleap/forgeupgrade/config.ini update

    # Deploy site configurations
    tuleap-cfg site-deploy

    # Restart service
    systemctl start httpd
    systemctl start nginx
    systemctl start tuleap

Do not forget to execute the forgeupgrade command, no warnings should be displayed
in the site administration about it (as Site Admin go in Admin > Plugin Administration).

Enjoy all your new features!
