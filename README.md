# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:

<img width="619" height="346" alt="image" src="https://github.com/user-attachments/assets/438288e8-fb1d-474f-88d7-6e58c88ee0c6" />

Invoke msfconsole:
## OUTPUT:
<img width="717" height="560" alt="image" src="https://github.com/user-attachments/assets/addd411e-8597-47f7-afba-4a249de8f8af" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="748" height="760" alt="image" src="https://github.com/user-attachments/assets/ff28740c-b1a2-46e6-8145-7893aa9052fb" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="932" height="415" alt="image" src="https://github.com/user-attachments/assets/3840fd44-0a67-42b3-a958-835f2a29e2db" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="746" height="420" alt="image" src="https://github.com/user-attachments/assets/2bdf59df-a576-4ddf-9d3c-0dcdef42d6a6" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="455" height="207" alt="image" src="https://github.com/user-attachments/assets/be37a3a1-bbc4-4e87-9ebd-0bfa8ecba24f" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="954" height="808" alt="image" src="https://github.com/user-attachments/assets/c92b2364-b48d-4b0c-ae34-2aab0a72e832" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:


<img width="944" height="832" alt="image" src="https://github.com/user-attachments/assets/5ba0542f-db7e-43be-acd9-c116da75820e" />


## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="865" height="183" alt="image" src="https://github.com/user-attachments/assets/32d841cc-7d80-4269-9382-43c8ea8e08ed" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="951" height="835" alt="image" src="https://github.com/user-attachments/assets/72c98113-32d0-4e1b-8d94-82bc4a227c5c" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="942" height="480" alt="image" src="https://github.com/user-attachments/assets/07eda892-fb35-4ebe-aeb3-f9796c17f2eb" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="577" height="130" alt="image" src="https://github.com/user-attachments/assets/c9be313a-3755-4460-9cb7-6120989a44b4" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="941" height="730" alt="image" src="https://github.com/user-attachments/assets/274b6735-fa6c-4c91-9560-e561ca20a5a3" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
