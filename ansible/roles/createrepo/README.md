Createrepo Role
===============

The dcaf-abe createrepo role will prepare an http repository on abe when it used in offline mode. This is determined by the value of the 'offline' variable in group_vars/all.yml. If it is set to true the createrepo role is called, if set to false it is not.

If dcaf-abe is used in offline mode all the necessary packages are downloaded to the /opt/autodeploy/resources/rpms directory. This directory is used for both a local and an apache based http repository.

The role will do the following:
  * Create an offline repo file in the repository that can be distributed to any hosts /etc/yum.conf directory.

  * Create an offline repo config for apache and puts it in the /etc/httpd/conf.d directory.

  * Restart the httpd service so the changes take effect.

Requirements
------------

The role requires a pre-installed version of RHEL on the dcaf-abe autodeploy node.

Role Variables
--------------

The variables for this role come from facts gathered by ansible and group_vars/all.yml. The group_vars/all.yml variables need to be edited as needed.

group_vars/all.yml
 * offline: (true or false)

Dependencies
------------

The role depends on the requirements listed above.

Playbook
--------

The role is called in the dcaf-abe/ansible/main.yml playbook.

Run the playbook from the dcaf-abe/ansible directory

    ansible-playbook ansible/main.yml
