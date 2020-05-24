Command monitoring collector
=========

This role configures the device to listen to syslog messages from devices running command-monitoring-client. It also forwards the logs to central server using Reliable Event Logging Protocol (RELP). See the command-monitoring-client role for more information.

Requirements
------------

* Rsyslog


Role Variables
--------------

* `central_server_address` IP address of the central server
* `central_server_certificate_sha:` SHA hash of the certificate. Must be in this format: "27:7A:EF:69:E2:EF:EE:C0:EA:4C:32:CA:39:CD:91:4D:4C:1D:AB:8C"


Example Playbook
----------------


    - hosts: logger
      vars:
          central_server_address: "78.128.251.179" 
          central_server_certificate_sha: "27:7A:EF:69:E2:EF:EE:C0:EA:4C:32:CA:39:CD:91:4D:4C:1D:AB:8C"
      become: yes
      roles:
        - command-monitoring-collector

License
-------

MIT
