ANSIBLE-ROLE-USERS
==================

Ansible role create users with ssh pub key. 

**NO PRIVATE KEY**

If you need to create a group, I have separeted this action with [redbeard28.groups galaxy role](https://github.com/redbeard28/ansible-role-groups)

## Howto use this role?
This role need to be include in a playbook. 

Call this **Galaxy** role  like this:

````bash
ansible-galaxy install -r requirements.yml 
````

Inside requirements.yml
````yaml
# from GitHub, overriding the name and specifying a specific tag
- src: redbeard28.users
````

More info => [Ansible Docs](https://docs.ansible.com/ansible-container/roles/access.html)

## Requirements

 * Ansible 2.9+


Role Variables
--------------
state[*](https://docs.ansible.com/ansible/latest/modules/user_module.html) means ansible value: present or absent
```yaml
---
users:
  - { state: 'present', name: 'myname', group: 'mygroup', password: {{ vault_shadow_password }}, key: {{ vault_ssh_pub_key }}, shell: '/bin/ksh', homepath: '/home' }
```

Dependencies
------------

 * redbeard28.groups if group do not exist

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: redbeard28.users, tags: mytags }


Molecule testing framework
--------------------------

You can use molecule to test this role.
```bash
image=debian tag="buster" molecule converge 
image=debian tag="buster" molecule verify 
```

Author Information
------------------

Jeremie CUADRADO[¹](mailto:info@redbeard-consulting.fr) from Redbeard-Consulting
