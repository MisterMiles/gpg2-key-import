# import-gpg-with-ansible

The role adds your personal gpg key to a given host. 

## Features

- Tests if your gpg key is present
- Easy to use: you have only to supply your key files
- Idempotency is present in all actions
- Key is added user based

## Usage of the role
Before running the role you should update `defaults/main.yml` with your personal informations and add your gpg keys in `files/`. 

### How to export the gpg keys to files
- public.key -> `gpg -a --export username@email > files/public.key`

- signing.key -> `gpg -a --export-secret-keys username@email > files/signing.key`

- ultimate.trust -> `gpg --export-ownertrust > files/ultimate.trust`

## Steps to perform

1. Prepare and export a gpg signing key
2. Add these keys to `files/` and update `defaults/main.yml` with your personal preferences
3. Use at least Ansible version 2.9.0
4. You can run the role as follows `ansible-playbook ../setup.yml --ask-become-pass`
```
cat ../setup.yml
 - name: Export your gnupg key to hosts
   hosts: localhost
   connection: local
   become: yes
   vars:
     gpg_user: name_of_user
     gpg_group: name_of_usergroup
     gpg_email: your_email_of_your_gpg_key
     gpg_home: where_keys_will_be_installed
   roles:
     - role: import_gpg
```
