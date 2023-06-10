# Ansible

## Requirements

On Ansible driver:

```shell
# install
pip install ansible==8.0.0
pip install ansible-lint==6.17.0
pip install prettytable

# verify versions
pip list | grep ansible
ansible            8.0.0
ansible-compat     4.1.2
ansible-core       2.15.0
ansible-lint       6.17.0
```

```shell
# update
ansible-playbook -i inventory/ playbooks/wsl/update.yml --ask-become-pass

# output
BECOME password:

PLAY [Update/setup WSL hosts] ************************************************************************************************************************************************************************************

TASK [Gathering Facts] *******************************************************************************************************************************************************************************************
ok: [localhost]

TASK [Install dnf packages] **************************************************************************************************************************************************************************************
changed: [localhost]

TASK [Show install_output] ***************************************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": [
        "Installed: ripgrep-13.0.0-10.fc38.x86_64"
    ]
}

PLAY RECAP *******************************************************************************************************************************************************************************************************
localhost                  : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
