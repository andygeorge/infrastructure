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

PLAY [Update/setup WSL hosts] **********************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************
Saturday 10 June 2023  09:47:46 -0500 (0:00:00.047)       0:00:00.047 *********
ok: [localhost]

TASK [Install dnf packages] ************************************************************************************************************
Saturday 10 June 2023  09:47:47 -0500 (0:00:00.702)       0:00:00.750 *********
changed: [localhost]

TASK [Show install_output] *************************************************************************************************************
Saturday 10 June 2023  09:47:54 -0500 (0:00:07.315)       0:00:08.066 *********
ok: [localhost] =>
  msg:
  - 'Installed: flatpak-1.15.4-1.fc38.x86_64'
  - 'Installed: flatpak-selinux-1.15.4-1.fc38.noarch'
  - 'Installed: flatpak-session-helper-1.15.4-1.fc38.x86_64'
  - 'Installed: p11-kit-server-0.24.1-6.fc38.x86_64'
  - 'Installed: ripgrep-13.0.0-10.fc38.x86_64'

TASK [Install flatpak packages] ********************************************************************************************************
Saturday 10 June 2023  09:47:54 -0500 (0:00:00.034)       0:00:08.100 *********
ok: [localhost]

TASK [Update installed flatpaks] *******************************************************************************************************
Saturday 10 June 2023  09:47:54 -0500 (0:00:00.223)       0:00:08.323 *********
changed: [localhost]

TASK [Flatpak output] ******************************************************************************************************************
Saturday 10 June 2023  09:47:54 -0500 (0:00:00.211)       0:00:08.535 *********
ok: [localhost] => (item={'changed': False, 'command': '/usr/bin/flatpak list --system', 'rc': 0, 'stdout': '', 'stderr': '', 'stdout_lines': [], 'stderr_lines': [], 'failed': False}) =>
  msg: ''
ok: [localhost] => (item={'changed': True, 'stdout': '\nNothing to do.', 'stderr': '', 'rc': 0, 'cmd': ['flatpak', 'update', '--noninteractive'], 'start': '2023-06-10 09:47:54.770201', 'end': '2023-06-10 09:47:54.777789', 'delta': '0:00:00.007588', 'msg': '', 'stdout_lines': ['', 'Nothing to do.'], 'stderr_lines': [], 'failed': False}) =>
  msg: |2-

    Nothing to do.

PLAY RECAP *****************************************************************************************************************************
localhost                  : ok=6    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

Saturday 10 June 2023  09:47:54 -0500 (0:00:00.095)       0:00:08.631 *********
===============================================================================
Install dnf packages ------------------------------------------------------------------------------------------------------------ 7.32s
Gathering Facts ----------------------------------------------------------------------------------------------------------------- 0.70s
Install flatpak packages -------------------------------------------------------------------------------------------------------- 0.22s
Update installed flatpaks ------------------------------------------------------------------------------------------------------- 0.21s
Flatpak output ------------------------------------------------------------------------------------------------------------------ 0.10s
Show install_output ------------------------------------------------------------------------------------------------------------- 0.03s
```
