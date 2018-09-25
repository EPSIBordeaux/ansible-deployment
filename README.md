# Ansible server setup

## Usage

1. Copy `inventory.example` as `inventory` and edit it to fit your needs.

2. Copy `group_vars/all.example` as `group_vars/all` and edit it to fit your needs.

### Root Setup

- Check Server fingerprint, accept it if it match and exit

    ```bash
    ssh USER@SERVER
    ```

- Run root playbook

    ```bash
    ansible-playbook playbooks/root_setup.yml -k
    ```

    This command will run the `root_setup` playbook and ask for your root password.

    After this playbook succed, you'll no longer be able to run it again, because password authentication is now forbidden.

- You'll need to use the `setup` playbook with the user you just created

    ```bash
    ssh USER@SERVER
    # change your password
    ```

    > Your password is your username, so you better change it fast, even if you still need your SSH key to connect !

### Basic Setup

```bash
ansible-playbook playbooks/setup.yml -K
```

> Precise your SUDO password.

### Install an application

**Make sure you've runned the `Basic Setup` first, otherwise

```bash
ansible-playbook playbooks/applications/monit.yml -K
```

> Precise your SUDO password.

### Install all

```bash
ansible-playbook playbooks/all.yml -K
```

> Precise your SUDO password.
