### 1. Run `build_tig-stack.yml`

- `ansible-playbook build_tig-stack.yml`

- Your output should be:

```
ansible@ansible-test:~/ansible-examples$ ansible-playbook build_tig-stack.yml

PLAY [tig-stack] ***************************************************************************************************************************

TASK [Install Python for Ansible] **********************************************************************************************************
ok: [tig-stack]

TASK [Upgrade packages] ********************************************************************************************************************
[WARNING]: Updating cache and auto-installing missing dependency: python-apt
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host tig-stack should use /usr/bin/python3, but is using /usr/bin/python for backward
compatibility with prior Ansible releases. A future Ansible release will default to using the discovered platform python for this host. See
 https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information. This feature will be removed in
 version 2.12. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
ok: [tig-stack]

TASK [Check if a reboot is required] *******************************************************************************************************
ok: [tig-stack]

TASK [Restart Machine] *********************************************************************************************************************
skipping: [tig-stack]

TASK [Waiting for Server to come back] *****************************************************************************************************
ok: [tig-stack -> localhost]

TASK [Add influxDB Repo Key] ***************************************************************************************************************
changed: [tig-stack]

TASK [Add influxDB Repo] *******************************************************************************************************************
changed: [tig-stack]

TASK [Install influxDB] ********************************************************************************************************************
changed: [tig-stack]

TASK [Install pip] *************************************************************************************************************************
changed: [tig-stack]

TASK [Enable service for influxDB] *********************************************************************************************************
ok: [tig-stack]

TASK [Make sure influxDB is running] *******************************************************************************************************
changed: [tig-stack]

TASK [Prerequests for influxDB Database Steps] *********************************************************************************************
changed: [tig-stack]

TASK [Add User to influxDB] ****************************************************************************************************************
ok: [tig-stack]

TASK [Create telegraf Database] ************************************************************************************************************
ok: [tig-stack]

TASK [Install telegraf] ********************************************************************************************************************
changed: [tig-stack]

TASK [Enable Service for telegraf] *********************************************************************************************************
ok: [tig-stack]

TASK [Make sure telegraf is running] *******************************************************************************************************
ok: [tig-stack]

TASK [Copy telegraf.conf] ******************************************************************************************************************
changed: [tig-stack]

TASK [Manage telegraf configuration] *******************************************************************************************************
changed: [tig-stack]

TASK [Restart telegraf Service] ************************************************************************************************************
changed: [tig-stack]

TASK [Add Grafana repo key] ****************************************************************************************************************
changed: [tig-stack]

TASK [Add Grafana repo] ********************************************************************************************************************
changed: [tig-stack]

TASK [Install Grafana] *********************************************************************************************************************
changed: [tig-stack]

TASK [Enable Service for Grafana] **********************************************************************************************************
changed: [tig-stack]

TASK [Make sure Grafana is running] ********************************************************************************************************
changed: [tig-stack]

PLAY RECAP *********************************************************************************************************************************
tig-stack                  : ok=24   changed=15   unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
```
