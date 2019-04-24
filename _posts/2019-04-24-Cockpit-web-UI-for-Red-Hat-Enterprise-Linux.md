---
layout: post
title: Cockpit Web UI for Red Hat Enterprise Linux
---

*Cockpit: Web UI for Red Hat Enterprise Linux*

Cockpit is a web UI packaged with Red Hat Enterprise Linux that aids in system administration. Many common administrative tasks such as local user account management, package installation/updates, Red Hat subscription management, network interface configuration, storage device and file system management are exposed by the web UI. Additionally, the web UI is only started by `systemd` only when a connection to the Cockpit socket is initiated. 

Every RHEL server can expose Cockpit functionality. However, there is another configuration where a single Cockpit instance can be deployed and can serve as the master node to access administrative tasks on all other nodes. The package that makes this possible is `cockpit-dashboard`. This means that cockpit does not have to be installed on all RHEL instances, and only one firewall rule needs to be maintained for the Cockpit server running the dashboard. The user that logs into the master node must have ssh access to the rest of the nodes in order for the dashboard and admin tasks to work properly.

Getting started with Cockpit is fairly easy. However, to make it a bit easier, I've created an Ansible playbook and two roles that configure an environment to for Cockpit. When applying the master role, a json node definition file is created on the master and public keys for the nodes are added to a `known_hosts` file for Cockpit. 

When the playbook has completed, you should be able access a dashboard of all hosts in the environment from the master node. The github repository for this playbook is here: [https://github.com/cloin/ansible-cockpit](https://github.com/cloin/ansible-cockpit)

In the future, more functionality will be moved to Cockpit. For example, RHEL 8 includes a `virt-manager` like interface for managing virtual machines running on RHEL 8.

*Be sure to view the sample inventory file included.*

![Cockpit screenshot](https://github.com/cloin/ansible-cockpit/blob/master/cockpit-dashboard.gif?raw=true)