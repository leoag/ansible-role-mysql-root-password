Role Name
=========

 A very simple role to reset the mysql or mariadb server root password

Requirements
------------

- MySQL or MariaDB Server must be installed.
- The role checks for the /etc/init.d/mysql file to proceed.
- You should have sudo or root for the role to work due to become (see example below)
- python-mysqldb or python3-mysqldb is needed depending on python version

Role Variables
--------------

Right now it only has 2 variables:

    mysql_root_username: root
    mysql_root_password: "{{ mysql_root_password }}"

They have default values in defaults/main.yml, so they are not mandatory.
You have the option to pass the mysql_root_password variable inline, in the
vars/main.yml or with a ansible-vault file /vars/vault.yml

If you pass it with a vault file, keep in mind you should enter the vault password inline. Examples below.

Vault support is a work in progress.


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

    - hosts: dbservers
      become: true
      vars_files:
        - vars/main.yml
        - vars/vault.yml
      roles:
        - role: leogallego.mysql-root-password

Run it with the mysql password inline and ask for sudo password:

    ansible-playbook -i mysql.hosts playbook-mysql-reset.yml -e "mysql_root_password=INLINEPASS" --ask-pass --ask-become-pass

Run it with variables in vars/main.yml:

    ansible-playbook -i mysql.hosts playbook-mysql-reset.yml --ask-pass  --ask-become-pass

Run it with {{ mysql_root_password }} defined in vars/vault.yml:

    ansible-playbook -i mysql.hosts playbook-mysql-reset.yml --ask-pass --ask-vault-pass --ask-become-pass


License
-------

GPLv3

Author Information
------------------

Leonardo Gallego
