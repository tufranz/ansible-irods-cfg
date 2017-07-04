irods-server-cfg
================
[![Build Status](https://travis-ci.org/CyVerse-Ansible/ansible-irods-server-cfg.svg?branch=master)](https://travis-ci.org/CyVerse-Ansible/ansible-irods-server-cfg)

This role can be used to completely configure an iRODS server once iRODS is installed.


Requirements
------------

None


Role Variables
--------------

Here are the role variables. None of them are required.

Variable                                                                     | Default                                                            | Choices                                         | Comment
---------------------------------------------------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------- | -------
`irods_server_cfg_access_entries`                                            | []                                                                 |                                                 | A list of access entry objects defining who can access iRODS and from where, see below
`irods_server_cfg_authentication_file`                                       |                                                                    |                                                 | the authentication file for the clerver
`irods_server_cfg_clerver_default_hash_scheme`                               | `irods_server_cfg_default_hash_scheme`                             | MD5, SHA256                                     | checksum scheme for clerver
`irods_server_cfg_clerver_default_resource`                                  | `irods_server_cfg_default_resource_name`                           |                                                 | the name of the resource used for clerver operations if one is not specified
`irods_server_cfg_clerver_encryption_algorithm`                              | `irods_server_cfg_server_control_plane_encryption_algorithm`       |                                                 | EVP-supplied encryption algorithm for parallel transfer
`irods_server_cfg_clerver_encryption_key_size`                               | 32                                                                 |                                                 | key size for parallel transport encryption
`irods_server_cfg_clerver_encryption_num_hash_rounds`                        | `irods_server_cfg_server_control_plane_encryption_num_hash_rounds` |                                                 | number of hash rounds for parallel transfer encryption
`irods_server_cfg_clerver_encryption_salt_size`                              | 8                                                                  |                                                 | salt size for parallel transfer encryption
`irods_server_cfg_client_server_negotiation`                                 | request_server_negotiation                                         | none, request_server_negotiation                | whether or not advanced negotiation is desired for the clerver
`irods_server_cfg_client_server_policy`                                      | CS_NEG_DONT_CARE                                                   | CS_NEG_DONT_CARE, CS_NEG_REFUSE, CS_NEG_REQUIRE | which SSL policy for the clerver to use
`irods_server_cfg_cwd`                                                       | `irods_server_cfg_home`                                            |                                                 | the initial working collection for the admin user
`irods_server_cfg_debug`                                                     |                                                                    |                                                 | desired verbosity of the debug logging level for clerver
`irods_server_cfg_default_dir_mode`                                          | 0750                                                               |                                                 | the Unix file system octal permission mode for a newly created directory
`irods_server_cfg_default_file_mode`                                         | 0600                                                               |                                                 | the Unix file system octal permission mode for a newly created file
`irods_server_cfg_default_hash_scheme`                                       | SHA256                                                             | MD5, SHA256                                     | the hash scheme used for file integrity checking
`irods_server_cfg_default_number_of_transfer_threads`                        |                                                                    |                                                 | the default maximum number of threads allowed for parallel transfer
`irods_server_cfg_default_resource_directory`                                |                                                                    |                                                 | the default Vault directory for the initial resource on server installation
`irods_server_cfg_default_resource_name`                                     |                                                                    |                                                 | the name of the initial resource on server installation
`irods_server_cfg_default_temporary_password_lifetime`                       |                                                                    |                                                 | the default number of seconds a server-side temporary password is valid
`irods_server_cfg_environment_variables`                                     | {}                                                                 |                                                 | a set of environment variables to add to the server process environment
`irods_server_cfg_federation`                                                | []                                                                 |                                                 | an array of federation objects identifying the zones this zone federates with, see below
`irods_server_cfg_group_account_name`                                        | `irods_server_cfg_service_account_name`                            |                                                 | the group used to run iRODS
`irods_server_cfg_gsi_server_dn`                                             |                                                                    |                                                 | the distinguished name of the GSI server
`irods_server_cfg_home`                                                      | /`irods_server_cfg_zone_name`/home/`irods_server_cfg_zone_user`    |                                                 | the home collection of the admin user
`irods_server_cfg_host`                                                      | `ansible_inventory_name`                                           |                                                 | the fully qualified domain name of the server the clerver connects to
`irods_server_cfg_host_entries`                                              | []                                                                 |                                                 | an array of host entry objects grouping host names and addresses referring to the same host, see below
`irods_server_cfg_icat_host`                                                 | `irods_server_cfg_host`                                            |                                                 | the fully qualified domain name of the iCAT enabled server
`irods_server_cfg_kerberos_name`                                             |                                                                    |                                                 | Kerberos distinguished name for KRB and GSI authentication
`irods_server_cfg_log_level`                                                 |                                                                    |                                                 | desired verbosity of logging
`irods_server_cfg_match_hash_policy`                                         | compatible                                                         | compatible, strict                              | indicates to iRODS whether to use the hash used by the client or the data at rest, or to force the use of the default hash scheme
`irods_server_cfg_maximum_number_of_concurrent_rule_engine_server_processes` |                                                                    |                                                 | the maximum number of rule engine processes to run    
`irods_server_cfg_maximum_size_for_single_buffer`                            |                                                                    |                                                 | the maximum size in mebibytes for a single buffer
`irods_server_cfg_maximum_temporary_password_lifetime`                       |                                                                    |                                                 | the maximum number of seconds a server-side temporary password can be valid
`irods_server_cfg_negotiation_key`                                           | TEMPORARY_32byte_negotiation_key                                   |                                                 | a 32-byte encryption key shared by the zone for use in the advanced negotiation handshake at the beginning of an iRODS client connection
`irods_server_cfg_pam_no_extend`                                             |                                                                    | false, true                                     | set PAM password lifetime: normally 8 hours, but extended is 2 weeks
`irods_server_cfg_pam_password_length`                                       |                                                                    |                                                 | maximum length of a PAM password
`irods_server_cfg_pam_password_max_time`                                     |                                                                    |                                                 | maximum allowed PAM password lifetime
`irods_server_cfg_pam_password_min_time`                                     |                                                                    |                                                 | minimum allowed PAM password lifetime
`irods_server_cfg_re_additional_data_variable_mappings`                      | []                                                                 |                                                 | an array of file names (without the .dvm extension) that will be loaded in order before core.dvm is loaded
`irods_server_cfg_re_additional_function_name_mappings`                      | []                                                                 |                                                 | an array of file names (without the .fnm extension) that will be loaded in order before core.fnm is loaded
`irods_server_cfg_re_additional_rulebases`                                   | []                                                                 |                                                 | an array of file names (without the .re extension) that will be loaded in order before core.re is loaded
`irods_server_cfg_schema_validation_base_uri`                                | https://schemas.irods.org/configuration                            | a URI or 'off'                                  | the URI against which the iRODS server configuration is validated. 'off' means to skip validation
`irods_server_cfg_server_control_plane_encryption_algorithm`                 | AES-256-CBC                                                        |                                                 | the algorithm used to encrypt control plane communications
`irods_server_cfg_server_control_plane_encryption_num_hash_rounds`           | 16                                                                 |                                                 | the number of hash rounds used in the control plane communications
`irods_server_cfg_server_control_plane_key`                                  | TEMPORARY__32byte_ctrl_plane_key                                   |                                                 | the the encryption key required for communicating with the iRODS grid control plane, must be 32 bytes
`irods_server_cfg_server_control_plane_port`                                 | 1248                                                               |                                                 | the port on which the control plane operates
`irods_server_cfg_server_control_plane_timeout`                              | 10000                                                              |                                                 | the number of milliseconds before control plane times out
`irods_server_cfg_server_port_range_start`                                   | 20000                                                              |                                                 | the beginning of the port range available for re-connections, parallel transfer and RBUDP transfer
`irods_server_cfg_server_port_range_end`                                     | 20199                                                              |                                                 | the ending of the port range available for re-connections, parallel transfer and RBUDP transfer
`irods_server_cfg_service_account_name`                                      | irods                                                              |                                                 | the account used to run iRODS
`irods_server_cfg_ssl_ca_certificate_file`                                   |                                                                    |                                                 | location of a file of trusted CA certificates in PEM format
`irods_server_cfg_ssl_ca_certificate_path`                                   |                                                                    |                                                 | location of a directory containing CA certificates in PEM format
`irods_server_cfg_ssl_certificate_chain_file`                                |                                                                    |                                                 | the file containing the server's certificate chain
`irods_server_cfg_ssl_certificate_key_file`                                  |                                                                    |                                                 | private key corresponding to the server's certificate in the certificate chain file
`irods_server_cfg_ssl_dh_params_file`                                        |                                                                    |                                                 | the Diffie-Hellman parameter file location
`irods_server_cfg_ssl_verify_server`                                         |                                                                    | cert, hostname, none                            | level of server certificate based authentication to perform
`irods_server_cfg_transfer_buffer_size_for_parallel_transfer`                |                                                                    |                                                 | the buffer size in mebibytes for parallel transfer                    
`irods_server_cfg_transfer_chunk_size_for_parallel_transfer`                 |                                                                    |                                                 | the chunk size in mebibytes for parallel transfer
`irods_server_cfg_xmsg_host`                                                 |                                                                    |                                                 | the host name of the XMessage server
`irods_server_cfg_xmsg_port`                                                 |                                                                    |                                                 | the port on which the XMessage server operates should it be enabled
`irods_server_cfg_zone_auth_scheme`                                          | native                                                             | gsi, krb, native, pam                           | the authentication scheme used by `irods_server_cfg_zone_user`
`irods_server_cfg_zone_key`                                                  | TEMPORARY_zone_key                                                 |                                                 | the shared secret used for authentication and identification on server-to-server communication, it cannot contain hyphens (`-`)
`irods_server_cfg_zone_name`                                                 | tempZone                                                           |                                                 | the name of the in which the server participates
`irods_server_cfg_zone_port`                                                 | 1247                                                               |                                                 | the main port used by the zone for communication
`irods_server_cfg_zone_user`                                                 | rods                                                               |                                                 | the name of the rodsadmin user running this iRODS instance

The `irods_server_cfg_access_entries` variables is an array of `access_entry` objects. An `access_entry` object has the following fields, all of them required.

Field     | Choices | Comments
--------- | ------- | --------
`address` |         | the IPv4 address of a host or network that is able to access
`group`   |         | the iRODS group able to access
`mask`    |         | the network mask when `address` is a network address
`user`    |         | the iRODS user able to access

The `irods_server_cfg_environment_variables` variable is a dictionary where the key is the name of a server process environment variable, and the value is the value of the environment variable.

The `irods_server_cfg_federation` variable is an array of `federation` objects. A `federation` object has the following fields, all of them required.

Field             | Choices | Comments
----------------- | --------| --------
`icat_host`       |         | the host name of the iCAT server in the federated zone
`negotiation_key` |         | the 32-byte encryption key of the federated zone
`zone_key `       |         | the shared authentication secret with the federated zone
`zone_name`       |         | the name of the federated zone

The `irods_server_cfg_host_entries` variable is an array of `host_entry` objects. A `host_entry` object has the following fields, all of them required.

Field          | Choices       | Comments
-------------- | ------------- | --------
`address_type` | local, remote | indicates if this host is localhost.
`addresses`    |               | an array of names and addresses referring to this host


Dependencies
------------

The role CyVerse-Ansible.irods-env is used internally to update the server's irods_environment.json file.


Example Playbook
----------------

    - hosts: rs
      roles:
        - role: cyverse.irods-server-cfg
          irods_server_cfg_default_hash_scheme: MD5
          irods_server_cfg_default_number_of_transfer_threads: 16
          irods_server_cfg_default_resource_directory: "{{ irods_resource_dir }}"
          irods_server_cfg_default_resource_name: "{{ irods_default_resource }}"
          irods_server_cfg_environment_variables:
            amqp_host: "{{ irods_amqp_host }}"
          irods_server_cfg_federation:
            - icat_host: irods.tacc.utexas.edu
              negotiation_key: "Don't you wish!                !"
              zone_key: crack me
              zone_name: tacc
          irods_server_cfg_host_entries:
            - address_type: local
              addresses:
                - ares.iplantcollaborative.org
                - data.cyverse.org
                - data.iplantcollaborative.org
          irods_server_cfg_negotiation_key: Just guess it                  .
          irods_server_cfg_re_additional_data_variable_mappings:
            - cyverse
          irods_server_cfg_re_additional_function_name_mappings:
            - cyverse
          irods_server_cfg_re_additional_rulebases
            - ipc_custom
          irods_server_cfg_port_range_start: "{{ irods_server_port_range_start }}"
          irods_server_cfg_server_control_plane_key: "I'm not telling                ."
          irods_server_cfg_server_port_range_end: "{{ irods_server_port_range_end }}"
          irods_server_cfg_transfer_buffer_size_for_parallel_transfer: 32
          irods_server_cfg_zone_key: secret
          irods_server_cfg_zone_name: iplant


License
-------

See [license](/license.md)


Author Information
------------------

Tony Edgin  
<tedgin@cyverse.org>  
[CyVerse](https://cyverse.org)
