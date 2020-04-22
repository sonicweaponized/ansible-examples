### 1. Modify inventory file in `ansible-examples`

- `vi inventory`

- In line `tig-stack ansible_host=XXX.XXX.XXX.XXX`, replace `XXX.XXX.XXX.XXX` with your machine's IP address


### 2. Generate hashed password for `ansible` user on target machine

- This is the password for the `ansible` user on the machine where the tig-stack will be installed

- `mkpasswd --method=SHA-512`


### 3. Modify `linux_deploy-ssh.yml`

- `vi linux_deploy-ssh.yml`

- In line `remote_user: yourdefaultuser` replace `yourdefaultuser` with the user on the target machine 

(* **Note: this is the user that you created when initially setting up the target machine, NOT the ansible user we are creating**)

- In line `password=your$$hashedpassword` replace `your$$hashedpassword` with the output from the `mkpasswd --method=SHA-512` command in step 2.

### 4. Run `linux_deploy-ssh.yml` playbook

- `ansible-playbook linux_deploy-ssh.yml --ask-pass --ask-become-pass`

- When prompted enter the password for the user that you created when initially setting up the target machine.

- Your output should be:

```
ansible@ansible-test:~/ansible-examples$ ansible-playbook linux_deploy-ssh.yml --ask-pass --ask-become-pass
SSH password:
BECOME password[defaults to SSH password]:

PLAY [linux_ubuntu1804] ********************************************************************************************************************

TASK [Add a new user named ansible] ********************************************************************************************************
changed: [tig-stack]

TASK [Add ansible user to the sudoers] *****************************************************************************************************
changed: [tig-stack]

TASK [Deploy SSH Key] **********************************************************************************************************************
changed: [tig-stack]

PLAY RECAP *********************************************************************************************************************************
tig-stack                  : ok=3    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
