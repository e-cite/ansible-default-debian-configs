Role Name
=========

Installiert einen apt-cacher-ng auf einem Debian host.

Kopiert in Teilen von: https://github.com/elnappo/ansible-role-apt-cacher-ng

Requirements
------------

Keine.

Role Variables
--------------

- `apt_cacher_ng_port: 3142`
- `apt_cacher_ng_cache_dir: /var/cache/apt-cacher-ng`

Dependencies
------------

Keine.

Example Playbook
----------------

## Playbook for the Server
```yaml
- hosts: servers
  remote_user: root
  roles:
   - { role: apt_cacher_ng }
```

## Client Configuration
### with ansible
Set apt_proxy as a host var

	[host:vars]
	apt_proxy=http://apt.example.com:3142/

**For the whole system:**

```yaml
- name: Set up apt proxy
  template: src=templates/00aptproxy.conf dest=/etc/apt/apt.conf.d/00aptproxy owner=root group=root mode=0644
    when: ansible_os_family == "Debian" and apt_proxy is defined
```

templates/00aptproxy.conf:

	# {{ ansible_managed }}
	Acquire::http { Proxy "{{ apt_proxy }}"; };
	Acquire::https { Proxy "https://"; };

**Only for one task:**

```yaml
- apt: name=ufw state=installed
  environment:
    http_proxy: "{{ apt_proxy }}"
```

### without ansible
Replace server IP/FQDN!

	$ echo 'Acquire::http { Proxy "http://apt.example.com:3142"; };' > /etc/apt/apt.conf.d/00aptproxy
  $ echo 'Acquire::https { Proxy "https://"; };' >> /etc/apt/apt.conf.d/00aptproxy

License
-------

proprietär
