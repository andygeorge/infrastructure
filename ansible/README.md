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

## Updating

```shell
ansible-playbook -i inventory/ playbooks/wsl/update.yml --ask-become-pass
```

```
BECOME password:

PLAY [Update/setup WSL hosts] ************************************************************************************************************************************************************************************

TASK [Gathering Facts] *******************************************************************************************************************************************************************************************
[WARNING]: Platform linux on host localhost is using the discovered Python interpreter at /usr/bin/python3.11, but future installation of another Python interpreter could change the meaning of that path. See
https://docs.ansible.com/ansible-core/2.15/reference_appendices/interpreter_discovery.html for more information.
ok: [localhost]

TASK [Install dnf packages] **************************************************************************************************************************************************************************************
changed: [localhost]

TASK [Show install_output] ***************************************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": [
        "Installed: flatpak-1.15.4-1.fc38.x86_64",
        "Installed: flatpak-selinux-1.15.4-1.fc38.noarch",
        "Installed: flatpak-session-helper-1.15.4-1.fc38.x86_64",
        "Installed: p11-kit-server-0.24.1-6.fc38.x86_64",
        "Installed: ripgrep-13.0.0-10.fc38.x86_64"
    ]
}

TASK [Install flatpak packages] **********************************************************************************************************************************************************************************
ok: [localhost]

TASK [Update installed flatpaks] *********************************************************************************************************************************************************************************
changed: [localhost]

TASK [Flatpak output] ********************************************************************************************************************************************************************************************
ok: [localhost] => (item={'changed': False, 'command': '/usr/bin/flatpak list --system', 'rc': 0, 'stdout': '', 'stderr': '', 'stdout_lines': [], 'stderr_lines': [], 'failed': False}) => {
    "msg": ""
}
ok: [localhost] => (item={'changed': True, 'stdout': '\nNothing to do.', 'stderr': '', 'rc': 0, 'cmd': ['flatpak', 'update', '--noninteractive'], 'start': '2023-06-10 09:43:31.201452', 'end': '2023-06-10 09:43:31.212761', 'delta': '0:00:00.011309', 'msg': '', 'stdout_lines': ['', 'Nothing to do.'], 'stderr_lines': [], 'failed': False}) => {
    "msg": "\nNothing to do."
}

PLAY RECAP *******************************************************************************************************************************************************************************************************
localhost                  : ok=6    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
