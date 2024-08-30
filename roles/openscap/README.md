Role Name
=========

Deploy and execute OpenScap report tool

Requirements
------------

No requirements. But if you want to expose the result you can add nginx root directory to store openscap reports and results.

Role Variables
--------------

All variables are located in file [defaults/main.yml](./defaults/main.yml).

A Extra variable `debug` add debug message in current Ansible output.

tags
----

There are 2 tags availables :

- `install` : Only install the OpenScap tool on Debian and Windows Server
- `scanning` : Only execute OpenScap reports and results

Dependencies
------------

Need the collections :

- ansible.posix
- ansible.windows
- community.windows

Example Playbook
----------------

Deploy and execute OpenScap reports on develop environment :

```bash
ansible-playbook openscap.yml -i environments/dev -e 'profile=Debian_Average'
```

Deploy and execute OpenScap reports on develop environment with debugs messages :

```bash
ansible-playbook openscap.yml -i environments/dev -e 'debug=true' -e 'profile=Debian_Average'
```

Deploy OpenScap on develop environment :

```bash
ansible-playbook openscap.yml -i environments/dev -t 'install' -e 'profile=Debian_Average'
```

Execute OpenScap reports on develop environment :

```bash
ansible-playbook openscap.yml -i environments/dev -t 'scanning' -e 'profile=Debian_Average'
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
