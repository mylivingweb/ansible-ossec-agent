mylivingweb.ossec-agent
=========

This role will install and configure an ossec-agent on the server. When there there is an parameter `ossec_server_name` configured, it will delagate an action for automatically authenticate the agent. This role uses wazuh repo for ossec-hids. 

Requirements
------------

This role will work on:
 * Red Hat
 * Debian

So, you'll need one of those operating systems.. :-)

Role Variables
--------------

This role needs 2 parameters:
* `ossec_server_ip`: This is the ip address of the server running the ossec-server.
* `ossec_server_name`: This is the hostname of the server running the ossec-server. 
* `ossec_managed_server`: When set to false, tasks that delegate to ossec server will be skipped

This role has 2 tasks with 'delagation_to' which needs the parameter `ossec_server_name`. When this parameter is not set, you'll need to run manually the `/var/ossec/bin/ossec-authd` on the server and `/var/ossec/bin/agent-auth` on the agent. When this is the case, it will show you an message with the exact command line.

Dependencies
------------

No dependencies.

Example Playbook
----------------

The following is an example how this role can be used:

    - hosts: all:!ossec-server.example.com
      roles:
         - { role: mylivingweb.ossec-agent, ossec_server_ip: 192.168.1.1, ossec_server_name: ossec-server.example.com }

License
-------

GPLv3

Author Information
------------------

Please send suggestion or pull requests to make this role better. 

Github: https://github.com/mylivingweb/ansible-ossec-agent

mail: mylivingweb [ at ] gmail . com
