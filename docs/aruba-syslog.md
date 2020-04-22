### 1. Modify inventory file in `ansible-examples`

- `vi inventory`

- In line `core ansible_host=XXX.XXX.XXX.XXX`, replace `XXX.XXX.XXX.XXX` with the ip of your aruba switch.  You can also change the name `core` to whatever you desire.  `foo` or `bar` for example.  If you do this, also make sure to change the name under the `[arubaos_2930]` group to match.

- In line `ansible_password=PASSWORD`, replace `PASSWORD` with the password for the `manager` account on your aruba switch.


### 2. Modify `set_syslog_aruba.yml`

- `vi set_syslog_aruba.yml`

- In line `lines: logging XXX.XXX.XXX.XXX`, replace `XXX.XXX.XXX.XXX` with the ip of your syslog server (or a dummy ip if you don't have one.)


### 3. Run `set_syslog_aruba.yml` playbook

- `ansible-playbook set_syslog_aruba.yml`

- Your output should be:

```
ansible@ansible-test:~/ansible-examples$ ansible-playbook set_syslog_aruba.yml

PLAY [arubaos_2930] ************************************************************************************************************************

TASK [Set syslog server] *******************************************************************************************************************
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host core should use /usr/bin/python3, but is using /usr/bin/python for backward
compatibility with prior Ansible releases. A future Ansible release will default to using the discovered platform python for this host. See
 https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information. This feature will be removed in
 version 2.12. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
changed: [core]

TASK [Save running config to startup] ******************************************************************************************************
changed: [core]

PLAY RECAP *********************************************************************************************************************************
core                       : ok=2    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
