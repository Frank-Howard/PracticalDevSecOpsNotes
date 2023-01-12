pip3 install ansible==6.4.0  

```
cat > inventory.ini <<EOL

[devsecops]
devsecops-box-xioqjd4c

[sandbox]
sandbox-xioqjd4c

[prod]
prod-xioqjd4c

EOL
```
#### ad hoc commands 

ansible -i inventory.ini prod --list-hosts

ansible --version

Config file below
```
cat > /etc/ansible/ansible.cfg <<EOF
[defaults]
stdout_callback = yaml
deprecation_warnings = False
host_key_checking = False
retry_files_enabled = False
inventory = /inventory.ini
EOF
```

ssh-keyscan -t rsa devsecops-box-xioqjd4c sandbox-xioqjd4c prod-xioqjd4c >> ~/.ssh/known_hosts  

ansible -i inventory.ini all -m ping  

ansible -i inventory.ini all -m shell -a "hostname"  
ansible-doc -l | egrep "add_host|amazon.aws.aws"  
ansible -i inventory.ini all -m copy -a "src=/root/notes dest=/root"  
#### Hardening
pip3 install ansible==6.4.0 ansible-lint==6.8.1
```
cat > inventory.ini <<EOL

# DevSecOps Studio Inventory
[devsecops]
devsecops-box-xioqjd4c

[prod]
prod-xioqjd4c

EOL
```
Capture key sigs to allow for automation using ssh commands  
`ssh-keyscan -t rsa prod-xioqjd4c devsecops-box-xioqjd4c >> ~/.ssh/known_hosts`
`ansible -i inventory.ini prod -m apt -a "name=ntp state=present`
`ansible -i inventory.ini all -m command -a "bash --version"`
`ansible-doc -l | grep shell`
`ansible -i inventory.ini prod -m shell -a "uptime"`




