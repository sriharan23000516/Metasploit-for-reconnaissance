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
<img width="758" height="407" alt="image" src="https://github.com/user-attachments/assets/87873d52-eb34-41a6-8c23-26738bcd7cc0" />


Invoke msfconsole:
## OUTPUT:
<img width="731" height="794" alt="image" src="https://github.com/user-attachments/assets/9f29fc51-95fc-44ee-8ff1-2b10e59b5280" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT

<img width="813" height="859" alt="image" src="https://github.com/user-attachments/assets/2e529053-a5a6-4f0a-b7c0-20915a440240" />




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="896" height="404" alt="Screenshot 2026-02-06 133154" src="https://github.com/user-attachments/assets/5b1f239c-46d9-4145-a2da-ae8dbea8f3d4" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="716" height="382" alt="image" src="https://github.com/user-attachments/assets/d98d6644-67c9-4c3c-943d-7dca62c47ea0" />




Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="752" height="506" alt="image" src="https://github.com/user-attachments/assets/1a16c11e-ba67-4fa4-8232-7af632934d9c" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="945" height="881" alt="image" src="https://github.com/user-attachments/assets/852aa389-b2a9-4968-b3cd-2016c80068c4" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="940" height="854" alt="image" src="https://github.com/user-attachments/assets/c02f683c-ab40-4d1e-a048-4d5ab449a560" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="900" height="169" alt="image" src="https://github.com/user-attachments/assets/1d7d655c-d5a6-4bd9-a7c4-e369af2c3d7e" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="952" height="665" alt="image" src="https://github.com/user-attachments/assets/6e753ddf-e72f-4a5e-9b63-ad416132d062" />



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="952" height="665" alt="image" src="https://github.com/user-attachments/assets/6e753ddf-e72f-4a5e-9b63-ad416132d062" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="684" height="125" alt="image" src="https://github.com/user-attachments/assets/16f94ab2-be45-46d7-ba96-905758789ec1" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="762" height="538" alt="image" src="https://github.com/user-attachments/assets/56e3eb93-10ca-417c-b1ba-72e04ebe4a10" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="796" height="165" alt="image" src="https://github.com/user-attachments/assets/b6df67b3-1261-425f-bc42-f35ec78d2705" />




![WhatsApp Image 2026-02-06 at 2 16 48 PM](https://github.com/user-attachments/assets/5c63f38e-e63a-469f-ab4b-3bba9b8fd18e)






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
