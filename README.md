Ansible Role: Frontier Squid
============================

Install and configure a [Frontier squid cache](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid)

Inspired by the [Puppet Module](https://github.com/desalvo/puppet-frontier)

Requirements
------------

* EL6/7
* Optional UMD4 or OSG Repositories

Role Variables
--------------

Enable the CERN frontier repository as alternative to the grid repositories

    frontiersquid_enable_repo: false

Check the documentation for details

    frontiersquid_customize: |
      setoption("acl NET_LOCAL src", "10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 fc00::/7 fe80::/10")
      setoption("cache_mem", "128 MB")
      setoptionparameter("cache_dir", 3, "10000")

Run several instances. See the [documentation](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Running_multiple_services) for details

    frontiersquid_num_services: 1

Maximum size of the logfile for one service

    frontiersquid_max_access_log: 5G

Disable compressing of log files

    frontiersquid_compress_logs: true

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: hephyvienna.frontiersquid
           vars:
             frontiersquid_customize: |
                   setoption("acl NET_LOCAL src", "10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 fc00::/7 fe80::/10")
                   setoption("cache_mem", "128 MB")
                   setoptionparameter("cache_dir", 3, "10000")

License
-------

MIT

Author Information
------------------

Written by [Dietrich Liko](http://hephy.at/dliko) in May 2019

[Institute for High Energy Physics](http://www.hephy.at) of the
[Austrian Academy of Sciences](http://www.oeaw.ac.at)
