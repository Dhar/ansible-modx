MODX
======

Installs [MODX](http://modx.com/) using Nginx.

Requirements
------------

This role was created on/for Ubuntu Trusty installations and was specifically tested in an OpenVZ container environment.

Role Variables
--------------

The role uses the following variables, set in the defaults/main.yml file:

* `modx_version` - Specific version of MODX to install (defaults to 2.2.14-pl)
* `modx_install_dir` - Directory to install MODX (defaults to /var/www)
* `modx_database_server` - Hostname of MySQL database (defaults to localhost)
* `modx_database_name` - Name of the MODX database (defaults to modx_modx)
* `modx_database_user` - MODX database username (defaults to modx)
* `modx_database_password` - MODX database user password (defaults to wkc87kdo)
* `modx_table_prefix` - Prefix to prepend to every created database table (defaults to modx_)
* `modx_admin_username` - MODX administrator username (defaults to admin)
* `modx_admin_password` - MODX administrator password (defaults to ocwn3o9cnjf)
* `modx_admin_email` - MODX administrator email (defaults to modx@example.com)
* `modx_timezone` - MODX server timezone (defaults to America/Los_Angeles)

Dependencies
------------

Depends on the [Ansibles.mysql](https://galaxy.ansible.com/list#/roles/509) role.

Usage
-----

    ansible-galaxy install garnold.modx

Also check the [Ansible Galaxy](https://galaxy.ansibleworks.com/intro) about page.

Example Playbook
-------------------------

Example playbook for installing GitLab database and web servers on separate systems:

    ---
    - hosts: modx
      roles:
      - { role: Ansibles.mysql, mysql_databases: [{name: "{{ modx_database_name }}"}], mysql_users: [{name: "{{ modx_database_user }}", pass: "{{ modx_database_password }}", host: "{{ modx_database_server }}", priv: "{{ modx_database_name }}.*:ALL"}]}
      - { role: modx }

License
-------

MIT

Author Information
------------------

Gary Arnold

[GitHub project page](https://github.com/Dhar/ansible-modx)
