Oracle Instant Client role
=========
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-sonarqube/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-oracle-instant-client.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-oracle-instant-client)

Summary
-------

This role installs and configures oracle instant client.

Requirements
------------

  - Minimal Version of the ansible for installation: 2.5

  -  Prepared ansible inventory file with listed VMs with python. These machines should be accessible via SSH.
Supported CentOS 6.* and Centos 7.*

  -  oracle db client version 12.1 supported oracle server version: 12.2.0, 12.1.0, 11.2.0 (https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=366329397565814&id=207303.1&_afrWindowMode=0&_adf.ctrl-state=1cp26b7isr_4)

Role Variables
--------------

  - `transport` - artifact source transport default: `local`

    available:
      - `web` - fetch artifact from custom web uri
      - `local` - local artifact

  - `transport_web` - URI for http/https artifact default: `"http://my-storage.example.com"`
  - `transport_local` - path for local artifact default: `"/tmp"`
  - `oracle_instantclient_packages` - Oracle instant client package and tools

    default:
      - `- "oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm"`
      - `- "oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm"`
      - `- "oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm"`

  - `download_path` - local folder for downloading artifacts default: `/tmp`

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```yaml
- name: "Install oracle instant client"
  hosts: "all"

  roles:
    - role: "lean_delivery.oracle_instant_client"
      transport: "web"
      transport_web: "http://my-storage.example.com"
      oracle_instantclient_packages:
        - "oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm"
        - "oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm"
        - "oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm"
```
```yaml
- name: "Install oracle instant client"
  hosts: "all"

  roles:
    - role: "lean_delivery.oracle_instant_client"
      transport: "local"
      transport_local: "/tmp"
      oracle_instantclient_packages:
        - "oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm"
        - "oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm"
        - "oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm"
```


License
-------
Apache2

Author Information
------------------

authors:
  - Lean Delivery Team <team@lean-delivery.com>
