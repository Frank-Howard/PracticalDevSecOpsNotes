`pip3 install bandit==1.7.4`  
`bandit -r .`  

Two ways to do FPA, reading source code or exploiting the vuln

https://www.mysqltutorial.org/sql-concat-in-mysql.aspx/

look at cve, find the location in the file. See the method being called. Find the package being used, search the CVE libary.
Determine if false positive in this instance.
Keep it in the baseline. (the stats don't change) 
then run `bandit -r . --baseline=baseline.json`  

example baseline: 
https://gitlab.practical-devsecops.training/-/snippets/15  

#### Extra FPA notes
Typically SAST traces from user input (sources) to critical security functions (sinks) 


