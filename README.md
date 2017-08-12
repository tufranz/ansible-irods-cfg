irods-cfg
================
[![Build Status](https://travis-ci.org/CyVerse-Ansible/ansible-irods-cfg.svg?branch=master)](https://travis-ci.org/CyVerse-Ansible/ansible-irods-cfg)
[![Ansible Galaxy](https://img.shields.io/ansible/role/19612.svg)](https://galaxy.ansible.com/CyVerse-Ansible/irods-cfg/)

Eventually this role will be able to be used to completely configure an iRODS server once iRODS is installed. At the moment, it can maintain the following configuration files.

* /etc/irods/database_config.json
* /etc/irods/host_access_control_config.json
* /etc/irods/hosts_config.json
* /etc/irods/server_config.json
* /etc/irods/service_account.config
* /var/lib/irods/.irods/irods_environment.json


Requirements
------------

iRODS 4.1.10 is installed.


Role Variables
--------------

Here are the role variables. None of them are required.

Variable                                                              | Default                                                     | Choices                                          | Comment
--------------------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------ | -------
`irods_cfg_access_entries`                                            | []                                                          |                                                  | A list of access entry objects defining who can access iRODS and from where, see below
`irods_cfg_authentication_file`                                       | /var/lib/irods/.irods/.irodsA                               |                                                  | the authentication file for the clerver
`irods_cfg_catalog_database_type`                                     | postgres                                                    | mysql, oracle, postgres                          | the type of database iRODS is using for the iCAT           
`irods_cfg_clerver_default_hash_scheme`                               | `irods_cfg_default_hash_scheme`                             | MD5, SHA256                                      | checksum scheme for clerver
`irods_cfg_clerver_default_resource`                                  | `irods_cfg_default_resource_name`                           |                                                  | the name of the resource used for clerver operations if one is not specified
`irods_cfg_clerver_encryption_algorithm`                              | `irods_cfg_server_control_plane_encryption_algorithm`       |                                                  | EVP-supplied encryption algorithm for parallel transfer
`irods_cfg_clerver_encryption_key_size`                               | 32                                                          |                                                  | key size for parallel transport encryption
`irods_cfg_clerver_encryption_num_hash_rounds`                        | `irods_cfg_server_control_plane_encryption_num_hash_rounds` |                                                  | number of hash rounds for parallel transfer encryption
`irods_cfg_clerver_encryption_salt_size`                              | 8                                                           |                                                  | salt size for parallel transfer encryption
`irods_cfg_client_server_negotiation`                                 | request_server_negotiation                                  | none, request_server_negotiation                 | whether or not advanced negotiation is desired for the clerver
`irods_cfg_client_server_policy`                                      | CS_NEG_DONT_CARE                                            | CS_NEG_DONT_CARE, CS_NEG_REFUSE, CS_NEG_REQUIRE  | which SSL policy for the clerver to use
`irods_cfg_cwd`                                                       | `irods_cfg_home`                                            |                                                  | the initial working collection for the admin user
`irods_cfg_db_host`                                                   | localhost                                                   |                                                  | the hostname of the DBMS
`irods_cfg_db_name`                                                   | ICAT                                                        |                                                  | the name of the database used as the iCAT
`irods_cfg_db_odbc_type`                                              | unix                                                        |                                                  | the ODBC type
`irods_cfg_db_password`                                               | testpassword                                                |                                                  | the password used by `irods_cfg_db_username` to connect to `irods_cfg_db_name`
`irods_cfg_db_port`                                                   | 5432                                                        |                                                  | the port on which the database server is listening
`irods_cfg_db_username`                                               | irods                                                       |                                                  | the database user name
`irods_cfg_debug`                                                     | ''                                                          | '' or any combination of 'CAT', 'RDA', and 'SQL' | desired verbosity of the debug logging level for clerver. e.g., 'CATRDA' means include CAT and RDA debugging in debug log messages
`irods_cfg_default_dir_mode`                                          | 0750                                                        |                                                  | the Unix file system octal permission mode for a newly created directory
`irods_cfg_default_file_mode`                                         | 0600                                                        |                                                  | the Unix file system octal permission mode for a newly created file
`irods_cfg_default_hash_scheme`                                       | SHA256                                                      | MD5, SHA256                                      | the hash scheme used for file integrity checking
`irods_cfg_default_number_of_transfer_threads`                        | 4                                                           |                                                  | the default maximum number of threads allowed for parallel transfer
`irods_cfg_default_resource_directory`                                | null                                                        |                                                  | the default Vault directory for the initial resource on server installation
`irods_cfg_default_resource_name`                                     | demoResc                                                    |                                                  | the name of the initial resource on server installation
`irods_cfg_default_temporary_password_lifetime`                       | 120                                                         |                                                  | the default number of seconds a server-side temporary password is valid
`irods_cfg_environment_variables`                                     | {}                                                          |                                                  | a set of environment variables to add to the server process environment
`irods_cfg_federation`                                                | []                                                          |                                                  | an array of federation objects identifying the zones this zone federates with, see below
`irods_cfg_gsi_server_dn`                                             | null                                                        |                                                  | the distinguished name of the GSI server
`irods_cfg_home`                                                      | /`irods_cfg_zone_name`/home/`irods_cfg_zone_user`           |                                                  | the home collection of the admin user
`irods_cfg_host`                                                      | `ansible_inventory_name`                                    |                                                  | the fully qualified domain name of the server the clerver connects to
`irods_cfg_host_entries`                                              | []                                                          |                                                  | an array of host entry objects grouping host names and addresses referring to the same host, see below
`irods_cfg_icat_host`                                                 | `irods_cfg_host`                                            |                                                  | the fully qualified domain name of the iCAT enabled server
`irods_cfg_kerberos_name`                                             | null                                                        |                                                  | Kerberos distinguished name for KRB and GSI authentication
`irods_cfg_log_level`                                                 | 5                                                           | 1 - 10                                           | desired verbosity of logging
`irods_cfg_match_hash_policy`                                         | compatible                                                  | compatible, strict                               | indicates to iRODS whether to use the hash used by the client or the data at rest, or to force the use of the default hash scheme
`irods_cfg_maximum_number_of_concurrent_rule_engine_server_processes` | 4                                                           |                                                  | the maximum number of rule engine processes to run    
`irods_cfg_maximum_size_for_single_buffer`                            | 32                                                          |                                                  | the maximum size in mebibytes for a single buffer
`irods_cfg_maximum_temporary_password_lifetime`                       | 1000                                                        |                                                  | the maximum number of seconds a server-side temporary password can be valid
`irods_cfg_negotiation_key`                                           | TEMPORARY_32byte_negotiation_key                            |                                                  | a 32-byte encryption key shared by the zone for use in the advanced negotiation handshake at the beginning of an iRODS client connection
`irods_cfg_pam_no_extend`                                             | null                                                        | false, true, or null                             | set PAM password lifetime: normally 8 hours, but extended is 2 weeks
`irods_cfg_pam_password_length`                                       | null                                                        |                                                  | maximum length of a PAM password
`irods_cfg_pam_password_max_time`                                     | null                                                        |                                                  | maximum allowed PAM password lifetime
`irods_cfg_pam_password_min_time`                                     | null                                                        |                                                  | minimum allowed PAM password lifetime
`irods_cfg_re_additional_data_variable_mappings`                      | []                                                          |                                                  | an array of file names (without the .dvm extension) that will be loaded in order before core.dvm is loaded
`irods_cfg_re_additional_function_name_mappings`                      | []                                                          |                                                  | an array of file names (without the .fnm extension) that will be loaded in order before core.fnm is loaded
`irods_cfg_re_additional_rulebases`                                   | []                                                          |                                                  | an array of file names (without the .re extension) that will be loaded in order before core.re is loaded
`irods_cfg_schema_validation_base_uri`                                | https://schemas.irods.org/configuration                     | a URI or 'off'                                   | the URI against which the iRODS server configuration is validated. 'off' means to skip validation
`irods_cfg_server_control_plane_encryption_algorithm`                 | AES-256-CBC                                                 |                                                  | the algorithm used to encrypt control plane communications
`irods_cfg_server_control_plane_encryption_num_hash_rounds`           | 16                                                          |                                                  | the number of hash rounds used in the control plane communications
`irods_cfg_server_control_plane_key`                                  | TEMPORARY__32byte_ctrl_plane_key                            |                                                  | the the encryption key required for communicating with the iRODS grid control plane, must be 32 bytes
`irods_cfg_server_control_plane_port`                                 | 1248                                                        |                                                  | the port on which the control plane operates
`irods_cfg_server_control_plane_timeout`                              | 10000                                                       |                                                  | the number of milliseconds before control plane times out
`irods_cfg_server_port_range_end`                                     | 20199                                                       |                                                  | the ending of the port range available for re-connections, parallel transfer and RBUDP transfer
`irods_cfg_server_port_range_start`                                   | 20000                                                       |                                                  | the beginning of the port range available for re-connections, parallel transfer and RBUDP transfer
`irods_cfg_service_account_name`                                      | irods                                                       |                                                  | the account used to run iRODS
`irods_cfg_service_group_name`                                        | `irods_cfg_service_account_name`                            |                                                  | the group used to run iRODS
`irods_cfg_ssl_ca_certificate_file`                                   | null                                                        |                                                  | location of a file of trusted CA certificates in PEM format
`irods_cfg_ssl_ca_certificate_path`                                   | null                                                        |                                                  | location of a directory containing CA certificates in PEM format
`irods_cfg_ssl_certificate_chain_file`                                | null                                                        |                                                  | the file containing the server's certificate chain
`irods_cfg_ssl_certificate_key_file`                                  | null                                                        |                                                  | private key corresponding to the server's certificate in the certificate chain file
`irods_cfg_ssl_dh_params_file`                                        | null                                                        |                                                  | the Diffie-Hellman parameter file location
`irods_cfg_ssl_verify_server`                                         | hostname                                                    | cert, hostname, none                             | level of server certificate based authentication to perform
`irods_cfg_transfer_buffer_size_for_parallel_transfer`                | 4                                                           |                                                  | the buffer size in mebibytes for parallel transfer                    
`irods_cfg_transfer_chunk_size_for_parallel_transfer`                 | 40                                                          |                                                  | the chunk size in mebibytes for parallel transfer
`irods_cfg_xmsg_host`                                                 | null                                                        |                                                  | the host name of the XMessage server
`irods_cfg_xmsg_port`                                                 | 1279                                                        |                                                  | the port on which the XMessage server operates should it be enabled
`irods_cfg_zone_auth_scheme`                                          | native                                                      | gsi, krb, native, pam                            | the authentication scheme used by `irods_cfg_zone_user`
`irods_cfg_zone_key`                                                  | TEMPORARY_zone_key                                          |                                                  | the shared secret used for authentication and identification on server-to-server communication, it cannot contain hyphens (`-`)
`irods_cfg_zone_name`                                                 | tempZone                                                    |                                                  | the name of the in which the server participates
`irods_cfg_zone_port`                                                 | 1247                                                        |                                                  | the main port used by the zone for communication
`irods_cfg_zone_user`                                                 | rods                                                        |                                                  | the name of the rodsadmin user running this iRODS instance

The `irods_cfg_access_entries` variables is an array of `access_entry` objects. An `access_entry` object has the following fields, all of them required.

Field     | Choices | Comments
--------- | ------- | --------
`address` |         | the IPv4 address of a host or network that is able to access
`group`   |         | the iRODS group able to access
`mask`    |         | the network mask when `address` is a network address
`user`    |         | the iRODS user able to access

The `irods_cfg_environment_variables` variable is a dictionary where the key is the name of a server process environment variable, and the value is the value of the environment variable.

The `irods_cfg_federation` variable is an array of `federation` objects. A `federation` object has the following fields, all of them required.

Field             | Choices | Comments
----------------- | --------| --------
`icat_host`       |         | the host name of the iCAT server in the federated zone
`negotiation_key` |         | the 32-byte encryption key of the federated zone
`zone_key `       |         | the shared authentication secret with the federated zone
`zone_name`       |         | the name of the federated zone

The `irods_cfg_host_entries` variable is an array of `host_entry` objects. A `host_entry` object has the following fields, all of them required.

Field          | Choices       | Comments
-------------- | ------------- | --------
`address_type` | local, remote | indicates if this host is localhost.
`addresses`    |               | an array of names and addresses referring to this host


Dependencies
------------

None


Example Playbook
----------------

    - hosts: rs
      roles:
        - role: CyVerse-Ansible.irods-cfg
          irods_cfg_db_host: irods_db.cyverse.org
          irods_cfg_db_password: secret
          irods_cfg_db_user: icatuser
          irods_cfg_default_hash_scheme: MD5
          irods_cfg_default_number_of_transfer_threads: 16
          irods_cfg_default_resource_name: CyVerseRes
          irods_cfg_environment_variables:
            amqp_host: "{{ irods_amqp_host }}"
          irods_cfg_federation:
            - icat_host: irods.tacc.utexas.edu
              negotiation_key: "Don't you wish!                !"
              zone_key: crack me
              zone_name: tacc
          irods_cfg_host_entries:
            - address_type: local
              addresses:
                - ares.iplantcollaborative.org
                - data.cyverse.org
                - data.iplantcollaborative.org
          irods_cfg_negotiation_key: Just guess it                  .
          irods_cfg_re_additional_data_variable_mappings:
            - cyverse
          irods_cfg_re_additional_function_name_mappings:
            - cyverse
          irods_cfg_re_additional_rulebases
            - ipc_custom
          irods_cfg_server_control_plane_key: "I'm not telling                ."
          irods_cfg_server_port_range_end: 20399
          irods_cfg_transfer_buffer_size_for_parallel_transfer: 32
          irods_cfg_zone_key: secret
          irods_cfg_zone_name: iplant
          irods_cfg_zone_user: cyverse_admin


License
-------

See [license](/license.md)


Author Information
------------------

Tony Edgin  
<tedgin@cyverse.org>  
[CyVerse](https://cyverse.org)
