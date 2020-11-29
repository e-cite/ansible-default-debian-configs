Role ssh_server
=========

Role to set SSH server settings.

Requirements
------------

- Ensure required files as defined by variables are present.

Role Variables
--------------

- `sshca_pubkey_file`: Public key file of SSH root CA. (*Required*)
- `sshca_host_pubkeys_folder`: Folder where to save fetched SSH host public keys from servers to assist SSH certificate issuing. (*Optional*)
- `sshca_host_certificate_file`: Path to certificate file for each host, signed by SSH CA. (*Optional*)
- `bastionhost`: Defaults to "no". Set "yes" together with "yubico_api_id" and "yubikey_mappings.j2" template to enable yubikey authentication.
- `yubico_api_id`: Get it from https://upgrade.yubico.com/getapikey/.

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
