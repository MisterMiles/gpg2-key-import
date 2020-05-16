GPG2 key import
=========

Importing a gpg2 key to a specific host.

## Features

- Tests if your gpg2 key is present
- Easy to use: you have only to supply your key files
- Idempotency is present in all actions
- Key is added to a specific user

Requirements
------------
Before running the role you should update `defaults/main.yml` with your gpg informations.

### How to add the gpg keys

- public.key -> `gpg -a --export username@email`

- signing.key -> `gpg -a --export-secret-keys username@email`

- ultimate.trust -> `gpg --export-ownertrust`

Role Variables
--------------
`gpg_user`: Name of the user <br />
`gpg_group`: Name of the group <br />
`gpg_email`: Email of the gpg key <br />
`gpg_home`: Where GPG will be located

`gpg_sign_passwd`: Password for GPG private key <br />
`gpg_ownertrust`: Trust the implemented sign key<br />
`gpg_signkey`: GPG private key <br />
`gpg_signwith`: Hash id of GPG private key <br />
`gpg_pubkey`: GPG public key

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
        gpg_group: repo_group
        gpg_email: repo@mail.com
        gpg_home: /var/lib/repo
        gpg_sign_passwd: {{ lookup('hashi_vault', ... }}
        gpg_signkey: {{ lookup('hashi_vault', ... }}
        gpg_signwith: << your_hash >>
        gpg_ownertrust: <hash_sequence>:6:
        gpg_pubkey: |
         foo
     roles:
        - role: gpg2_key_import
```

License
-------
MIT

Author Information
------------------
Alexis Miles Oortmann (@MisterMiles) <mister_dev@mailbox.org>
