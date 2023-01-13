get Inspec
wget https://packages.chef.io/files/stable/inspec/4.37.8/ubuntu/18.04/inspec_4.37.8-1_amd64.deb  
dpkg -i inspec_4.37.8-1_amd64.deb  

Prevent SSH Agent from prompting YES or NO  
echo "StrictHostKeyChecking accept-new" >> ~/.ssh/config  

Run Inspec against the production server
inspec exec https://github.com/dev-sec/linux-baseline -t ssh://root@prod-xioqjd4c -i ~/.ssh/id_rsa --chef-license accept  

-t = target machine
-i is the ssh-key since login is via ssh
--chef-license tells that we are accepting license, prevents asking YES/NO

