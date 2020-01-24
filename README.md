chrony
======

`chronyd` is a daemon for synchronisation of the system clock. It can synchronise the clock with NTP servers, reference clocks (e.g. a GPS receiver), and manual input using wristwatch and keyboard via chronyc. It can also operate as an NTPv4 (RFC 5905) server and peer to provide a time service to other computers in the network.

Version
-------

* `master` --- latest development version

Requirements
------------

This role is limited to

* Ubuntu 18.04 - Bionic
* Ubuntu 16.04 - Xenial
* Ubuntu 14.04 - Trusty
* Ubuntu 12.04 - Precise
* CentOS 8
* CentOS 7
* CentOS 6

Role Variables
--------------


* `crhony_disable_ntpd` --- disable the old NTP daemon, default `true`
* `chrony_enable` --- enable `chrony` NTP daemon, default `true`
* `chrony_ntp_servers` --- list of NTP servers in use, default `['0.pool.ntp.org', '1.pool.ntp.org', '2.pool.ntp.org', '3.pool.ntp.org']`

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: chrony
           crhony_disable_ntpd: true
           chrony_enable: true
           chrony_ntp_servers:
             - 0.ubuntu.pool.ntp.org
             - 1.ubuntu.pool.ntp.org
             - 2.ubuntu.pool.ntp.org
             - 3.ubuntu.pool.ntp.org

Testing
-------

### Test environment for all OSes

```bash
cd tests
vagrant up
```

### Rerun role

Run role on all OSes again.

```bash
vagrant provision
```

### Debug interactively

This uses cluster ssh to work with all vagrant boxes at the same time.

```bash
vagrant ssh-config > ~/.ssh/config
cat ~/.ssh/config | grep ^Host | cut -d\  -f2 | xargs cssh
```

License
-------

MIT / BSD

Author Information
------------------

Created 2020 by [Arnulf Heimsbakk](mailto:arnulf.heimsbakk@met.no) for MET Norway.

###### set vim: spell spelllang=en:
