Role ssh_server
=========

Role to set SSH server settings, with options for bastionhost with YubiKey authentication.

Requirements
------------

- Ensure required files are present as defined by variables.

Role Variables
--------------

- `sshca_root_pubkey_file`: Public key file of SSH root CA. (*Required*)
- `sshca_host_pubkey_folder`: Folder, where to save fetched SSH host public keys from servers to assist SSH certificate issuing. (*Required*)
- `sshca_host_pubkey_cert_file`: Path to certificate file for each host, signed by SSH CA. (*Required*)
- `bastionhost`: Defaults to "no". Set "yes" together with "yubico_api_id" and "yubikey_mappings.j2" template to enable YubiKey authentication.
- `yubico_api_id`: Get it from https://upgrade.yubico.com/getapikey/.
- `principals`: List of security principals to set in /etc/ssh/auth_principals
- `clean_authorized_keys`: Clean / delete authorized_keys file of adminuser to ensure SSH CA authentication only. Default / undefined is no.

Dependencies
------------

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: ssh_servers
      roles:
        - ssh_server

License
-------

MIT
