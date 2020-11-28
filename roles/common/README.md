Role Common
=========

Common settings for servers (hostname, timezone, locales, ntp, unattended-upgrades).

Requirements
------------

- Make sure your current user can login to every server by SSH public-private-key.
- Caution: This role can change the hostnames, so update your inventory accorindly.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

- `community.general`: For setting locale and timezone.
- `ansible.posix`

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
        - common

License
-------

MIT
