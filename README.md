Ansible Role: Users
=========
This ansible role allows adding users, groups and user's
ssh authorized_keys and private keys.

Requirements
------------
None

Variables
------------
Path to new user's shell:
```
users_shell_path: /bin/bash
```

Path to new user's home directory:
```
users_home_directory: /home
```

User definitions:
```
users: []
```

Example Playbook
------------
```
- hosts: all
  vars_files:
    - vars/main.yml
  roles:
    - jamslinger.users
```

With `vars/main.yaml`:
```
users_shell_path: /bin/bash
users_home_directory: /home
users:
  - username: ansible
    group: ansible
    authorized_keys:
      - "{{ lookup('file', '~/.ssh/ansible_rsa.pub') }}"
    ssh_private_keys:
      - name: id_gitlab
        key: "{{ lookup('file', '~/.ssh/git_rsa') }}"
```

License
------------
MIT
