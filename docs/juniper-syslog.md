## Prerequsite

- You must have setup an ssh key for the ansible user on your juniper switch(es) with username `ansible`.  This key pair is created in the [deploy-ssh-key.md](deploy-ssh-key.md) guide.  Adding this public key to your switch(es) is beyond the scope of this guide.


### 1. Modify inventory file in `ansible-examples`

- `vi inventory`

- In line `sw1 ansible_host=XXX.XXX.XXX.XXX`, replace `XXX.XXX.XXX.XXX` with the ip of your juniper switch.

- In line `sw1-server ansible_host=XXX.XXX.XXX.XXX`, replace `XXX.XXX.XXX.XXX` with the ip of your second juniper switch.  If you do not have a second switch, you can delete this line.

- You can also change the name `sw1` and `sw1-server` to whatever you desire. `foo` or `bar` for example. If you do this, also make sure to change the name under the [juniper_ex2200] group to match.


### 2. Modify `juniper_config_syslog.set`

- `vi juniper_config_syslog.set`

- In line `set system syslog host XXX.XXX.XXX.XXX any any`, replace `XXX.XXX.XXX.XXX` with the ip of your syslog server, or a dummy ip if you don't have one.


### 3. `Run set_syslog_juniper.yml` playbook

- `ansible-playbook set_syslog_juniper.yml`

- Your output should be similar to:

```
ansible@ansible-test:~/ansible-examples$ ansible-playbook set_syslog_juniper.yml

PLAY [Set syslog server] *******************************************************************************************************************

TASK [Setting syslog server...] ************************************************************************************************************
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host sw1 should use /usr/bin/python3, but is using /usr/bin/python for backward
compatibility with prior Ansible releases. A future Ansible release will default to using the discovered platform python for this host. See
 https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information. This feature will be removed in
 version 2.12. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
changed: [sw1]
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host sw1-server should use /usr/bin/python3, but is using /usr/bin/python for backward
compatibility with prior Ansible releases. A future Ansible release will default to using the discovered platform python for this host. See
 https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information. This feature will be removed in
 version 2.12. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
changed: [sw1-server]

PLAY RECAP *********************************************************************************************************************************
sw1                        : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
sw1-server                 : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
