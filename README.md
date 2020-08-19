Command monitoring collector
=========

This role configures the device to listen to syslog messages from devices running command-monitoring-client. It also forwards the logs to central server using TCP. See the command-monitoring-client role for more information.

## Requirements

* This role requires root access, so you either need to specify `become` directive as a global or while invoking the role.

    ```yml
    become: yes
    ```


Role parameters
--------------
Mandatory parameters
* `clc_syslog_target_host` - IP address of the kypo-head server

Optional parameters
* `clc_syslog_target_port` - Syslog target port

Example 
----------------

```
- name: Run rsyslog server
  hosts: man
  become: yes
  roles:
    - role: command-monitoring-collector
      clc_syslog_target_host: "{{ kypo_global_head_ip }}"
```
License
-------

MIT
