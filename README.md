agency
======



Installation
------------

From your local machine create a SSH Key 
for `agency` user into your remote server 
```bash
$ ssh-keygen -t rsa -f ~/.ssh/agency -C agency
```

Copy and paste the following output 
into your remote server metadata 
for grant SSH authentication
```bash
$ cat ~/.ssh/agency.pub
```

Edit and add the following code 
into your `/etc/ansible/hosts` files
then replace `X.X.X.X` with IP of the remote server
and `admin@example.com` with administrator email and other variables like smtp, etc...
```ini
[Agency]
X.X.X.X
[Agency:vars]
http_port=80
admin_email=admin@example.com
gmail_user=myusername@gmail.com
gmail_password=mypassword
ansible_user=agency
ansible_ssh_private_key_file=~/.ssh/agency
```

Download on your local machine the agency ansible playbook
```bash
$ curl -O https://javanile.github.io/agency/agency.yml 
```

Build your agency infrastructure to handle your business
```bash
$ ansible-playbook agency.yml
```

Authenticate Google Drive for backup
```bash
$ ssh -i ~/.ssh/agency agency@X.X.X.X ./agency/auth-gdrive
```
