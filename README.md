meruplaybook
============

This is the role for setting up some mail server.

I would not recommend using this at this time.

## Usage

First, setup an ubuntu 14.04 host (todo, support centos / debian 7). We'll
assume your host is named 'meru' and that your mail server has an MX record for
example.com and an A record for mx.example.com pointing to it.

```
git clone https://github.com/euank/meruplaybook.git roles/meru
cat <<EOF > roles.yml
---
- hosts: meru
  roles: meru
EOF
mkdir group_vars
cat <<EOF > group_vars/all
---
server_hostname: mx.example.com
server_domainname: example.com
mysql_root_password: password
mysql_mail_user: meru
mysql_mail_password: strong-password
mysql_mail_db: meru
EOF
```

After that, running `ansible-playbook roles.yml` should work. Probably.
