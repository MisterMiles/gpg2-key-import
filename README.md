Import gpg key
=========

Adds your personal gpg key to a given host.

## Features

- Tests if your gpg key is present
- Easy to use: you have only to supply your key files
- Idempotency is present in all actions
- Key is added user base

Requirements
------------

Before running the role you should update `defaults/main.yml` with your personal informations and add your gpg key in `files/`.

### How to add the gpg keys
- public.key -> `gpg -a --export username@email > files/public.key`

- signing.key -> `gpg -a --export-secret-keys username@email > files/signing.key`

- ultimate.trust -> `gpg --export-ownertrust > files/ultimate.trust`

Role Variables
--------------
`gpg_user`: < Name of the User ><br />
`gpg_group`: < Name of the group ><br />
`gpg_email`: < Email of gpg key ><br />
`gpg_home`: < Where GPG will be located >

Dependencies
------------

The role is modular and has no dependencies

Example Playbook
----------------
```
   - hosts: reposerver
     become: yes
     vars:
        gpg_user: repo_user
        gpg_group: repo_grou`
        gpg_email: repo@mail.com
        gpg_home: /var/lib/repo
     roles:
        - role: import_gpg_key
```
License
-------

MIT

Author Information
------------------
Alexis Miles Oortmann < mistermiles_ansible_hacks@mailbox.org >
