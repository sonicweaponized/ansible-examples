### 1. Make sure machine is up to date

- `apt update`

- `apt upgrade`


### 2. Install ansible

- `apt-add-repository --yes --update ppa:ansible/ansible`

- `apt install ansible`


### 3. Install dependencies for Juniper NETCONF connections

- `apt install python-pip`

- `pip install junos-eznc`

- `pip install jxmlease`


### 4. Create ansible user and ssh keys

- `useradd -m -s /bin/bash ansible`

- `passwd ansible`

- `echo  -e 'ansible\tALL=(ALL)\tNOPASSWD:\tALL' > /etc/sudoers.d/ansible`

- `apt install whois`

- `su - ansible`

- `ssh-keygen -t rsa` <-- No passphrase


### 5. Clone ansible-examples repository

- `git clone https://github.com/sonicweaponized/ansible-examples.git`
