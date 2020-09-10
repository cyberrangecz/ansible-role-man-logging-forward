MAN Logging Forwarder
=========

This role configures the device to listen to syslog messages from devices running `kypo-sandbox-logging-forward`. It also forwards the logs to `kypo-head` using TCP (using the standard defined in `RFC5424`).

## Authors

Name          | Email          
------------- | ------------
Pavel Šeda    |   441048@mail.muni.cz

## Requirements

* This role requires root access, so you either need to specify `become` directive as a global or while invoking the role.

    ```yml
    become: yes
    ```


Role parameters
--------------
Mandatory parameters
* `kmlf_syslog_target_host` - IP address of the syslog server 

Optional parameters
* `kmlf_syslog_target_port` - Syslog target port

Example 
----------------

```
- name: Run rsyslog server
  hosts: man
  become: yes
  roles:
    - role: kypo-man-logging-forward
      kmlf_syslog_target_host: "{{ kypo_global_head_ip }}"
```
