==========================================
 The Ansible Playbooks for yrmcds cluster
==========================================

Purpose
-------

This playbook is prepared for the `yrmcds <http://cybozu.github.io/yrmcds/>`_ cluster with corosync and pacemaker. This playbook supports IPv6 link-local unicast address or IPv4 address for virtual IP address for yrmcds, and floating IP address for Pacemaker.


Requirements
------------

* Edit inventory file `hosts` and variable file `group_vars/hosts`.
* Generate a new authkey formatted binary on local, and copy roles/pacemaker/files
* Install packages on local as follows;

  * Git
  * ansible (>= 1.5)
  * python-apt
  * python-netaddr

* git clone this repository, initialize library directory as submodule.::

    $ git clone https://github.com/mkouhei/playbook-yrmcds.git
    $ cd playbook-yrmcds
    $ git submodule init
    $ git submodule update

* It is required to applied applied `supporting IPv6 link-local unicast address patch <https://github.com/cybozu/yrmcds/commit/ff98d27443915a1c031a5a87733edf109efbf4af>`_ to yrmcds. `Debian official package <https://packages.qa.debian.org/y/yrmcds.html>`_ 1.0.4-5 over is applied this patch.

Restrictions
------------

* You must configure the network with IPv4/IPv6 dual stack,
  even though in such a case of using IPv6 link-local address at virtual_ip.
  Because of using IPv6 only, slave servers cannot run yrmcdsd.

Playbooks
---------

Execute next command under the each directories.::

  $ ansible-playbook -i hosts site.yaml -K

