Role Name
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
`gpg_user`: < Name of the User >
`gpg_group`: < Name of the group >
`gpg_email`: < Email of gpg key >
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

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
