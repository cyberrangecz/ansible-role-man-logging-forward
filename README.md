# MAN Logging Forwarder

This role configures the device to listen to syslog messages from devices running `kypo-sandbox-logging-forward`. It also forwards the logs to `kypo-head` using TCP (using the standard defined in `RFC5424`).

## Requirements

* This role requires root access, so you either need to specify `become` directive as a global or while invoking the role.

    ```yaml
    become: yes
    ```

## Role parameters

Mandatory parameters
* `kmlf_destination` - A resolvable hostname or IP address of the destination log host.

Optional parameters
* `kmlf_source_ip` -  The IP address to bind to. By default, syslog-ng listens on every available interface for the logs from hosts (default: `0.0.0.0`).
* `kmlf_source_port` - The port number to bind to (default: `514`).
* `kmlf_source_protocol` - Specifies the protocol used to receive messages from the source (default: `tcp`).
* `kmlf_source_max_connections` - Specifies the maximum number of simultaneous connections.
* `kmlf_destination_port` - The port of the destination log host.
* `kmlf_destination_protocol` - The transport protocol used for transmission of the logs to the remote host. Values `tcp`, and `udp` are supported (default: `tcp`).

# Example

```yaml
- name: Run syslog server
  hosts: man
  become: yes
  roles:
    - role: kypo-man-logging-forward
      kmlf_destination: "{{ kypo_global_head_ip }}"
```
