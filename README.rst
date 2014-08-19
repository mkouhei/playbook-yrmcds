==========================================
 The Ansible Playbooks for yrmcds cluster
==========================================

Purpose
-------

This playbook is prepared for the `yrmcds <http://cybozu.github.io/yrmcds/`_ cluster with corosync and pacemaker. This playbook supports IPv6 link-local unicast address or IPv4 address for virtual IP address for yrmcds, and floating IP address for Pacemaker.


Requirements
------------

* Edit inventory file `hosts` and variable file `group_vars/hosts`.
* Generate a new authkey formatted binary on local.

  * ansible (>= 1.5)
  * python-apt

Playbooks
---------

Execute next command under the each directories.::

  $ ansible-playbook -i hosts site.yaml -K

