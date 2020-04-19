GPG key import
=========

Importing a gpg key to a specific host.

## Features

- Tests if your gpg key is present
- Easy to use: you have only to supply your key files
- Idempotency is present in all actions
- Key is added to a specific user

Requirements
------------
Before running the role you should update `defaults/main.yml` with your personal informations and add your gpg key in `files/`.

### How to add the gpg keys
- public.key -> `gpg -a --export username@email > files/public.key`

- signing.key -> `gpg -a --export-secret-keys username@email > files/signing.key`

- ultimate.trust -> `gpg --export-ownertrust > files/ultimate.trust`

Role Variables
--------------
`gpg_user`: Name of the user <br />
`gpg_group`: Name of the group <br />
`gpg_email`: Email of gpg key <br />
`gpg_home`: Where GPG will be located

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
        - role: gpg_key_import
```

License
-------
MIT

Author Information
------------------
Alexis Miles Oortmann (@MisterMiles) <mister_dev@mailbox.org>
