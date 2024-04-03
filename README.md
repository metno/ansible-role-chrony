chrony
======

`chronyd` is a daemon for synchronisation of the system clock. It can synchronise the clock with NTP servers, reference clocks (e.g. a GPS receiver), and manual input using wristwatch and keyboard via chronyc. It can also operate as an NTPv4 (RFC 5905) server and peer to provide a time service to other computers in the network.


Bugs
----
Not able to set time in rhel8 due to bug in rhel8


Version
-------

* `3.2.0` --- Added Ubuntu Noble support
* `3.1.3` --- Allow Fedora CoreOS 39
* `3.1.2` --- fix checkmode
* `3.1.1` --- bug fix, ansible-lint
* `3.1.0` --- added support for Fedora CoreOS (FCOS 38.x.x.x) but with no tests
* `3.0.1` --- bug fix, ansible-lint
* `3.0.0` --- updated to ansible version 2.12
* `2.3.0` --- added RHEL 9 and CentOS Stream 8  support
* `2.2.0` --- added configuration options to use role for ntp server configuration, including leap second smearing
* `2.1.0` --- add ubuntu jammy and removed centos8 support + rettet noe syntax i meta og template
* `2.0.0` --- remove ubuntu xenial support + add rtcsync and allow config
* `1.5.0` --- add support for setting timezone
* `1.4.0` --- add rhel8 and remove trusty+centos6
* `1.3.0` --- remove ubuntu precise from testing
* `1.2.1` --- fix lint problem
* `1.2.0` --- added ubuntu focal, 20.04
* `1.1.2` --- tested with Ansible 2.9.11
* `1.1.1` --- prepare for github
* `1.1.0` --- ensure NTP traffic on port `123`, for firewall purposes
* `1.0.2` --- removed unsupported directive for v3
* `1.0.1` --- fixed restart when config changes
* `1.0.0` --- initial version
* `master` --- latest development version

Requirements
------------

This role is limited to

* Ubuntu 24.04 - Noble
* Ubuntu 22.04 - Jammy
* Ubuntu 20.04 - Focal
* Ubuntu 18.04 - Bionic
* Ubuntu 16.04 - Xenial
* CentOS 7
* CentOS Stream 8
* RHEL 8
* RHEL 9
* Fedora CoreOS 38
* Rocky Linux 8
* Rocky Linux 9
* AlmaLinux 8
* AlmaLinux 9

Role Variables
--------------

* `chrony_allow_enable` --- enable allow config, default `false`
* `chrony_allow` --- list of IP addresses/networks allowed to connect to chrony, default [127.0.0.1]
* `chrony_disable_ntpd` --- disable the old NTP daemon, default `true`
* `chrony_enable` --- enable `chrony` NTP daemon, default `true`
* `chrony_log_enable` --- enable logging, default `false`
* `chrony_log` --- configure logging (requires chrony_logging_enable set to true), default `measurements statistics tracking`
* `chrony_logdir` --- configure log directory (requires chrony_logging_enable set to true), default `/var/log/chrony/`
* `chrony_ntp_servers` --- list of NTP servers in use, default `['0.pool.ntp.org', '1.pool.ntp.org', '2.pool.ntp.org', '3.pool.ntp.org']`
* `chrony_rtcsync` --- enable kernel synchronization of the real-time clock (RTC), default `false`
* `chrony_smearing` --- enable leap second smearing (should only be used for NTP servers), default `false`
* `chrony_timezone` --- timezone for the system. Run `timedatectl list-timezones` on any systemd system to list available timezones, default `UTC`


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: chrony
           chrony_allow_enable: true
           chrony_allow:
             - 10.10.10.0/24
             - 127.0.0.1
             - ::/0
           chrony_disable_ntpd: true
           chrony_enable: true
           chrony_log_enable: true
           chrony_log: measurements statistics tracking
           chrony_logdir: /var/log/chrony/
           chrony_ntp_servers:
             - 0.ubuntu.pool.ntp.org
             - 1.ubuntu.pool.ntp.org
             - 2.ubuntu.pool.ntp.org
             - 3.ubuntu.pool.ntp.org
           chrony_rtcsync: true
           chrony_smearing: true
           chrony_timezone: "Europe/Oslo"

Testing
-------

NOTICE: Fedora CoreOS is tested manually, but currently no automatic tests
are added for FCOS.

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

GPLv2

Author Information
------------------

Created 2020 by [Arnulf Heimsbakk](mailto:arnulf.heimsbakk@met.no) for MET Norway.
Modified 2022 by [Silje Amundsen](mailto:siljeba@met.no) for MET Norway.

###### set vim: spell spelllang=en:
