### 1. Make sure machine is up to date

- `apt update`

- `apt upgrade`


### 2. Install python, ansible, and sshpass

- `apt install python ansible sshpass`


### 3. Create ansible user and ssh keys

- `useradd -m -s /bin/bash ansible`

- `passwd ansible`

- `echo  -e 'ansible\tALL=(ALL)\tNOPASSWD:\tALL' > /etc/sudoers.d/ansible`

- `apt install whois`

- `su - ansible`

- `ssh-keygen -t rsa` <-- No passphrase


### 4. Clone ansible-examples repository

- `git clone https://github.com/sonicweaponized/ansible-examples.git`
