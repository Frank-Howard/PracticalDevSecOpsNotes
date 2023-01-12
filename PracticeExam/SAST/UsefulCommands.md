Use docker image that can be used for install and running, see master file

#### pip-audit
pip3 install pip-audit==1.1.2 
pip-audit -r ./requirements.txt -f json | tee pip-audit-output.json 

#### detect-secrets
pip3 install detect-secrets==1.3.0 
detect-secrets scan > secrets-output.json 
echo "q\n" | detect-secrets audit secrets-output.json 
 
#### Talisman
curl --silent https://raw.githubusercontent.com/thoughtworks/talisman/master/global_install_scripts/install.bash > /tmp/install_talisman.bash && /bin/bash /tmp/install_talisman.bash pre-commit 
curl --silent https://raw.githubusercontent.com/thoughtworks/talisman/master/global_install_scripts/install.bash > /tmp/install_talisman.bash && /bin/bash /tmp/install_talisman.bash pre-push 
source ~/.bashrc 
^ Adds it to the bash environment so you can call talisman -h 
talisman --scan\n 

#### SemGrep
pip3 install semgrep==0.108.0
semgrep --help\n
semgrep --lang python -e "os.system(...)" . --json | jq 
semgrep --lang python -e "DEBUG =True" --include settings.py . 
Scan all declarations of variables  
semgrep --lang python -e '$X = $Y' .
Scan all function calls that have request as an argument 
semgrep --lang python -e '$FUNC(request)' . 
