nomad
=====

[![Ansible Role](https://img.shields.io/ansible/role/5300.svg)](https://galaxy.ansible.com/list#/roles/5300)

Installs Nomad

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name                              | Default                                                          | Description                                                                                                                                                                                                                                |
|-----------------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| nomad_version                     | 0.2.3                                                            | Version of Nomad to install                                                                                                                                                                                                                |
| nomad_sha256sum                   | 0f3a7083d160893a291b5f8b4359683c2df7991fa0a3e969f8785ddb40332a8c | SHA 256 checksum of package                                                                                                                                                                                                                |
| nomad_client                      | true                                                             | Install Nomad client (nomad_server must be false)                                                                                                                                                                                          |
| nomad_server                      | false                                                            | Install Nomad server (nomad_client must be false)                                                                                                                                                                                          |
| nomad_telemetry                   | false                                                            | Enable Nomad telemetry                                                                                                                                                                                                                     |
| nomad_atlas                       | false                                                            | Enable Atlas                                                                                                                                                                                                                               |
| nomad_region                      | "global"                                                         | Specifies the region the Nomad agent is a member of                                                                                                                                                                                        |
| nomad_datacenter                  | "dc1"                                                            | Datacenter of the local agent                                                                                                                                                                                                              |
| nomad_name                        | ''                                                               | The name of the local node                                                                                                                                                                                                                 |
| nomad_log_level                   | "INFO"                                                           | Controls the verbosity of logs the Nomad agent will output. Valid log levels include "WARN", "INFO", or "DEBUG" in increasing order of verbosity                                                                                           |
| nomad_bind_addr                   | "127.0.0.1"                                                      | Used to indicate which address the Nomad agent should bind to for network services, including the HTTP interface as well as the internal gossip protocol and RPC mechanism                                                                 |
| nomad_enable_debug                | false                                                            | Enables the debugging HTTP endpoints                                                                                                                                                                                                       |
| nomad_ports_http                  | 4646                                                             | The port used to run the HTTP server                                                                                                                                                                                                       |
| nomad_ports_rpc                   | 4647                                                             | The port used for internal RPC communication between agents and servers, and for inter-server traffic for the consensus algorithm (raft)                                                                                                   |
| nomad_ports_serf                  | 4648                                                             | The port used for the gossip protocol for cluster membership                                                                                                                                                                               |
| nomad_addresses_http              | "{{ nomad_bind_addr }}"                                          | The address the HTTP server is bound to                                                                                                                                                                                                    |
| nomad_addresses_rpc               | "{{ nomad_bind_addr }}"                                          | The address to bind the internal RPC interfaces to                                                                                                                                                                                         |
| nomad_addresses_serf              | "{{ nomad_bind_addr }}"                                          | The address used to bind the gossip layer to                                                                                                                                                                                               |
| nomad_advertise_rpc               | "{{ nomad_bind_addr }}"                                          | The address to advertise for the RPC interface                                                                                                                                                                                             |
| nomad_advertise_serf              | "{{ nomad_bind_addr }}"                                          | The address advertised for the gossip layer                                                                                                                                                                                                |
| nomad_leave_on_interrupt          | false                                                            | Enables gracefully leaving when receiving the interrupt signal                                                                                                                                                                             |
| nomad_leave_on_terminate          | false                                                            | Enables gracefully leaving when receiving the terminate signal                                                                                                                                                                             |
| nomad_enable_syslog               | false                                                            | Enables logging to syslog                                                                                                                                                                                                                  |
| nomad_syslog_facility             | "LOCAL0"                                                         | Controls the syslog facility that is used                                                                                                                                                                                                  |
| nomad_disable_update_check        | false                                                            | Disables automatic checking for security bulletins and new version releases                                                                                                                                                                |
| nomad_disable_anonymous_signature | false                                                            | Disables providing an anonymous signature for de-duplication with the update check                                                                                                                                                         |
| nomad_telemetry_statsite_address  | ''                                                               | Address of a statsite server to forward metrics data to                                                                                                                                                                                    |
| nomad_telemetry_statsd_address    | ''                                                               | Address of a statsd server to forward metrics to                                                                                                                                                                                           |
| nomad_telemetry_disable_hostname  | false                                                            | Indicates if gauge values should not be prefixed with the local hostname                                                                                                                                                                   |
| nomad_server_bootstrap_expect     | 3                                                                | This is an integer representing the number of server nodes to wait for before bootstrapping                                                                                                                                                |
| nomad_server_data_dir             | "{{ nomad_data_dir }}/server"                                    | This is the data directory used for server-specific data, including the replicated log                                                                                                                                                     |
| nomad_server_protocol_version     | ''                                                               | The Nomad protocol version spoken when communicating with other Nomad servers                                                                                                                                                              |
| nomad_server_num_schedulers       | "{{ ansible_processor_cores }}"                                  | The number of parallel scheduler threads to run. This can be as many as one per core, or 0 to disallow this server from making any scheduling decisions                                                                                    |
| nomad_server_enabled_schedulers   | []                                                               | This is an array of strings indicating which sub-schedulers this server will handle                                                                                                                                                        |
| nomad_client_state_dir            | "{{ nomad_data_dir }}/client"                                    | This is the state dir used to store client state                                                                                                                                                                                           |
| nomad_client_alloc_dir            | "{{ nomad_data_dir }}/alloc"                                     | A directory used to store allocation data                                                                                                                                                                                                  |
| nomad_client_servers              | []                                                               | An array of server addresses                                                                                                                                                                                                               |
| nomad_client_node_id              | ''                                                               | This is the value used to uniquely identify the local agent's node registration with the servers. This can be any arbitrary string but must be unique to the cluster. By default, if not specified, a randomly- generate UUID will be used |
| nomad_client_node_class           | ''                                                               | A string used to logically group client nodes by class. This can be used during job placement as a filter                                                                                                                                  |
| nomad_client_meta                 | {}                                                               | This is a key/value mapping of metadata pairs                                                                                                                                                                                              |
| nomad_atlas_infrastructure        | ''                                                               | The Atlas infrastructure name to connect this agent to                                                                                                                                                                                     |
| nomad_atlas_token                 | ''                                                               | The Atlas token to use for authentication                                                                                                                                                                                                  |
| nomad_atlas_join                  | false                                                            | Indicates if the auto-join feature of Atlas should be enabled                                                                                                                                                                              |
| nomad_atlas_endpoint              | ''                                                               | The address of the Atlas instance to connect to                                                                                                                                                                                            |
| nomad_server_node_gc_threshold    | ''                                                               | Controls how long a node must be in a terminal state before it is garbage collected and purged from the system                                                                                                                             |
| nomad_server_rejoin_after_leave   | ''                                                               | When provided, Nomad will ignore a previous leave and attempt to rejoin the cluster when starting                                                                                                                                          |
| nomad_server_retry_join           | []                                                               | Similar to start_join but allows retrying a join if the first attempt fails                                                                                                                                                                |
| nomad_server_retry_interval       | 30s                                                              | The time to wait between join attempts                                                                                                                                                                                                     |
| nomad_server_retry_max            | 0                                                                | The maximum number of join attempts to be made before exiting with a return code of 1. By default, this is set to 0 which is interpreted as infinite retries                                                                               |
| nomad_server_start_join           | []                                                               | An array of strings specifying addresses of nodes to join upon startup. If Nomad is unable to join with any of the specified addresses, agent startup will fail.                                                                           |


Dependencies
------------

- [kbrebanov.unzip](https://github.com/kbrebanov/ansible-unzip)

Example Playbook
----------------

Install Nomad

```yaml
- hosts: all
  roles:
    - { role: kbrebanov.nomad }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
