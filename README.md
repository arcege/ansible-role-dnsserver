DNS Server
==========

Set up a server as a DNS (bind9) server, including populating zone files with data from variables.

The domains are defined by a sequence of structures.  An example structure is:

```
domains:
 - name: example.com
   network: 192.168.1.0/24
   master: ns.example.com
   nameservers:
     - ns.example.com
     - ns.qa.example.com
   serial: 5
   hosts:
     - name: gw
       addr: 192.168.1.1
     - name: larry
       addr: 192.168.1.2
       cnames:
         - ns
         - ns1
     - name: curly
       addr: 192.168.1.3
       cnames:
         - git
         - svn
     - name: moe
       addr: 192.168.1.4
       cnames:
         - mail
  - name: qa.example.com
    network: 192.168.2.0/24
    master: ns.qa.example.com
    nameservers:
      - ns.qa.example.com
      - ns.example.com
    serial: 3
    hosts:
      - name: gw
        addr: 192.168.2.1
      - name: ns
        addr: 192.168.2.2
```

This would create two zones, four files (forward and reverse DNS), db.example.com, db.qa.example.com, db.192.168.1.0 db.192.168.2.0.  The serial value needs to be updated, just as with standard DNS files.

Requirements
------------

None.

Role Variables
--------------

- dnsdir = top level directory of the bind9 system, defaults to /etc/bind
- zonedir = top level directory with the zone files, defaults to /etc/bind
- dnssvc = service name of the DNS software, defaults to bind9
- forwarders = sequence of IP addresses to upstream DNS servers, defaults to Google DNS servers, 8.8.4.4, 8.8.8.8
- domains = sequence of structures defining information on a zone/domain

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
