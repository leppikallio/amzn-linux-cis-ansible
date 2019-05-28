Role Name
=========

amzn-linux-cis-ansible

Original artwork by Mr. Anth Courtney, https://github.com/anthcourtney/ansible-role-cis-amazon-linux


Requirements
------------


Amazon Linux and SE Linux
----------------
By default SElinux is disabled via grub in amazon linux.

To enable edit ;

```/boot/grub/menu.lst```

Modifiy ```selinux=0  to  selinux=1```

```touch /etc/selinux/config```

Also install the following package to allow the ansible SElinux module to function on the host.

```yum install libselinux-python```

A reboot will be neccessary for the changes to take effect.


Role Variables
--------------

See ```defaults/main.yml```

Dependencies
------------

Example Playbook
----------------

An example playbook which uses this role is as follows:

```
---

- hosts: localhost
  connection: local
  gather_facts: true
  become: yes

  roles:
    - anthcourtney.cis-amazon-linux
```

A more advanced example, which includes modifications to the default values used, as well as the exclusion of some items in the benchmark which are considered unnecessary for a fictional environment, is as follows:

```
---

- hosts: localhost
  connection: local
  gather_facts: true
  become: yes

  vars:
    cis_level_1_exclusions:
      - 5.4.4
      - 3.4.2
      - 3.4.3
      - 6.2.13   
    cis_pass_max_days: 45
    cis_umask_default: 002
 
  roles:
    - anthcourtney.cis-amazon-linux

```

Note that the use of ```become: yes``` is required as 99% of tasks require privileged access to execute.

License
-------

MIT/BSD

Author Information
------------------
