COD Ansible Role
=========

Deploys the Common Operational Datasync (COD) service to a target node.

Requirements
------------

If using the default configuration, to deploy as a systemd service, you will need to place the cod binary (cod-some_version) into the `files`
with a valid Peer Ditto License (PDL) file.

The binary file should be in the form of `cod-v0.2.3` and match the version provided as the variable: `cod_version`.

The PDL and binary file should be available in the root/next to the playbook or in an expected path.

Role Variables
--------------

To deploy COD as a container, executable with `docker-compose` be sure to set `cod_container` to TRUE.  This will also disable the deployment of COD as a systemd-service.

Defaults:
```yml
---
cod_node_name: cod              # Override this in an inventory file
cod_version: v0.2.3             # The version of COD to deployed
cod_container: FALSE            # Set to TRUE to deploy COD as a container
cod_platform: x86_64            # Node targets should override in an inventory
cod_c2_port: 9990
cod_agent_port: 9991
cod_mission_select_limit: 1
cod_telemetry_select_limit: 10
cod_interagent_select_limit: 1
cod_use_mdns: "true"            # To disable set to `"false"`
cod_pdl_path: cod.pdl           # The name of the PDL file
```

Dependencies
------------

Requires `requests` Python module to be installed locally, where Ansible is executing the playbook.

Example Playbook
----------------

    - hosts: cod_nodes
      roles:
         - { role: kitplummer.ansible-cod }

License
-------

MIT

Author Information
------------------

This role is made available to Ditto customers using the Common Operational Datasync (COD) service and does not include requisite
licensing for it.  Contact support@ditto.com for more information.
