# Reg No: 212224040232
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

![1config](https://github.com/user-attachments/assets/8782326f-1dce-4231-86d0-9fef6087918a)

Invoke msfconsole:

## OUTPUT:

![2msf](https://github.com/user-attachments/assets/a1c719d1-20c2-4212-a048-94a2ec509f45)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:

![3help](https://github.com/user-attachments/assets/1b854ae9-b533-46bf-9fce-d8b1200e8ab2)

Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).

msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![4nmap](https://github.com/user-attachments/assets/c9154807-3823-4bfa-b19d-8bd18f93b42c)


use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

## OUTPUT:

![5db](https://github.com/user-attachments/assets/6c203b16-8f01-40fc-8593-e66b1c338e43)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.

cd /usr/share /metasploit-framework/modules/auxiliary

kali > ls -l

## OUTPUT:

![6path](https://github.com/user-attachments/assets/cfa43a55-99f7-4441-9233-184cc2766300)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 

msf >search name:Microsoft type:exploit

## OUTPUT:

![7search](https://github.com/user-attachments/assets/14582591-a828-4b5d-aefd-903f5371ccbc)

The info command provides information regarding a module or platform

## OUTPUT:

![8info](https://github.com/user-attachments/assets/ad1cc872-f670-4e4f-b3d5-db92b156cf7c)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

systemctl start postgresql

msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.

db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

![9db](https://github.com/user-attachments/assets/a16e833b-c660-448d-81fc-8b7eb0719aa3)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

## OUTPUT:

![10sea](https://github.com/user-attachments/assets/d035c320-df80-4d1d-8685-d649e31f7bfc)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

## OUTPUT:

![11use](https://github.com/user-attachments/assets/c0653b81-1879-4bf1-8d1a-547eaf74f91a)


Use the set rhosts command to set the parameter and run the module, as follows:

## OUTPUT:

![12rhost](https://github.com/user-attachments/assets/f9069e93-2089-46b8-8750-d570c120d341)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT: 

![13use](https://github.com/user-attachments/assets/eaa45564-75d6-4304-9ba5-4db9355d81a5)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

## OUTPUT: 

![14brute](https://github.com/user-attachments/assets/b5a2a7b0-0913-43f0-93ce-c2ab05462033)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
