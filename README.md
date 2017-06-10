irods-server-cfg
================

This role can be used to completely configure an iRODS server once iRODS is installed.


Requirements
------------

None


Role Variables
--------------

Here are the role variables. None of them are required.

Variable                                | Default                                 | Choices | Comment
--------------------------------------- | --------------------------------------- | ------- | -------
`irods_server_cfg_service_account_name` | irods                                   |         | The account used to run iRODS
`irods_server_cfg_group_account_name`   | `irods_server_cfg_service_account_name` |         | The group used to run iRODS


Dependencies
------------

None


Example Playbook
----------------

    - hosts: rs
      roles:
        - role: cyverse.irods-server-cfg


License
-------

See [license](./license.md)


Author Information
------------------

Tony Edgin  
<tedgin@cyverse.org>  
[CyVerse](http://cyverse.org)
