
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
![Screenshot 2025-05-10 102702](https://github.com/user-attachments/assets/3b23aaf5-5c7d-4454-befb-55432fba3e54)

POSTGRESQL msfdb :
![Screenshot 2025-05-10 102728](https://github.com/user-attachments/assets/77c0ac4c-ca48-44b6-8770-67c87367a7a9)

## OUTPUT:
![Screenshot 2025-05-10 102750](https://github.com/user-attachments/assets/48ebd967-6c2e-4038-b8f5-6ce5b69d09d6)
Invoke msfconsole:

## OUTPUT:
![Screenshot 2025-05-10 102814](https://github.com/user-attachments/assets/8273e682-a91d-43bd-b613-ccdc26d7849a)
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![Screenshot 2025-05-10 102842](https://github.com/user-attachments/assets/80fa2715-14ec-461c-9637-d060534203c0)

## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-100## 0
## OUTPUT:
![Screenshot 2025-05-10 102907](https://github.com/user-attachments/assets/d72dd5d2-2e9f-4acb-ad25-e5da4cca8f44)
## Step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later. scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24
## OUTPUT:
![Screenshot 2025-05-10 102929](https://github.com/user-attachments/assets/050161e0-c297-4a97-b1c9-f2ec5e81f42f)
Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l
## OUTPUT:
![image](https://github.com/user-attachments/assets/99d557c1-7eb5-4c3b-81fb-ca8a1416bcbc)
Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

## OUTPUT:
![image](https://github.com/user-attachments/assets/cf8462c0-710f-4e4e-8fa8-58bb0712ea7c)
The info command provides information regarding a module or platform
## OUTPUT:
![image](https://github.com/user-attachments/assets/4aaf370b-c586-430d-b973-140891a2411e)
Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![image](https://github.com/user-attachments/assets/ace43403-3a21-41c0-86c0-dfc3dd74acb7)
Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
## OUTPUT:
![image](https://github.com/user-attachments/assets/04dead85-4553-4876-84ff-134a8d19812b)
use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

## OUTPUT:
![image](https://github.com/user-attachments/assets/72a7d44c-cee2-47c5-a7e7-79ddaf016e06)
Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
![image](https://github.com/user-attachments/assets/0cc1e004-27e6-4c7b-acc4-4b81e3fbbdbf)
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![image](https://github.com/user-attachments/assets/406ad52c-8b3e-4391-8bd2-efd843f37bdb)
set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
## OUTPUT:
![image](https://github.com/user-attachments/assets/77b6563b-3019-4a91-a691-06427617964b)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
