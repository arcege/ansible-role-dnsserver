DNS Server
==========

Set up a server as a DNS (bind9) server, including populating zone files with data from variables.

Requirements
------------

None.

Role Variables
--------------

dnsdir = top level directory of the bind9 system, defaults to /etc/bind
zonedir = top level directory with the zone files, defaults to /etc/bind
dnssvc = service name of the DNS software, defaults to bind9
forwarders = sequence of IP addresses to upstream DNS servers, defaults to Google DNS servers, 8.8.4.4, 8.8.8.8
domains = sequence of structures defining information on a zone/domain

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: dnsservers
      roles:
         - arcege.dnsserver

Data would likely come from group\_vars/dnsservers.yml with the data to push.

License
-------

GPLv3

Author Information
------------------

Michael P. Reilly <http://bitbucket.org/Arcege>
