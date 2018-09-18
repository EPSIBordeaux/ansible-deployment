# Ansible server setup

## Usage

1. Copy `inventory.example` as `inventory` and edit it to fit your needs.

2. Copy `group_vars/all.example` as `group_vars/all` and edit it to fit your needs.

### From a new server with root access

```bash
ssh USER@SERVER
# Check key authentication and exit
```

```bash
ansible-playbook playbooks/root_setup.yml -k
```

This command will run the `root_setup` playbook and ask for your root password. 

Tasks that will be executed with this playbook are :

- Install required packages
- Enabled unattended updates
- Setup locale
- Create users
- Add custom bin folder
- Setup hostname

After this playbook succed, you'll no longer be able to run it again, because password authentication is not forbidden.

You'll need to use the `setup` playbook with the user you just created

```bash
ssh USER@SERVER
# change your password
```

### Next usage

```bash
ansible-playbook playbooks/root_setup.yml -K
```

Precise your SUDO password.

### Install monit

```bash
ansible-playbook playbooks/monit.yml -K
```

Precise your SUDO password.
