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

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_13_40_09](https://github.com/MaheshS03/EH-EX-5/assets/128498431/549d9a97-87db-4e89-9410-4d875d7386e2)

Invoke msfconsole:
## OUTPUT:

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_13_39_39](https://github.com/MaheshS03/EH-EX-5/assets/128498431/cefff48d-99e2-46cd-8f86-ebe7906b38fa)

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_13_40_09](https://github.com/MaheshS03/EH-EX-5/assets/128498431/f02dbf89-8ebe-4cf0-8886-57b9bc687a31)

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_13_42_05](https://github.com/MaheshS03/EH-EX-5/assets/128498431/50eb7e77-0f6e-4db8-99f6-7efaf523e57c)

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_13_53_35](https://github.com/MaheshS03/EH-EX-5/assets/128498431/ea62aaa6-5246-4c75-bcf3-c609c376f285)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_19_46](https://github.com/MaheshS03/EH-EX-5/assets/128498431/82bac371-c6e9-441c-a99d-b604c46eca7f)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

## OUTPUT:

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_07_00](https://github.com/MaheshS03/EH-EX-5/assets/128498431/bbbfc199-35cc-4fe7-9b13-9bfb414808a6)

The info command provides information regarding a module or platform,

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_13_20](https://github.com/MaheshS03/EH-EX-5/assets/128498431/6cb1c219-af75-4643-85ed-b763a58f2359)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_10_42](https://github.com/MaheshS03/EH-EX-5/assets/128498431/efa35bbf-1ff9-48ec-986a-71d36b7dbc1f)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_11_32](https://github.com/MaheshS03/EH-EX-5/assets/128498431/a041266c-2289-47b6-960c-62dc6b84539a)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_12_15](https://github.com/MaheshS03/EH-EX-5/assets/128498431/9c62919f-b699-4b6a-860b-01e0ab622829)

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_13_02](https://github.com/MaheshS03/EH-EX-5/assets/128498431/f15e38a9-99de-46c0-80ac-06cd985dc387)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_14_49](https://github.com/MaheshS03/EH-EX-5/assets/128498431/29bc5c89-750e-4629-8722-9562eef605c5)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

![VirtualBox_kali-linux-2023 4-virtualbox-amd64_27_04_2024_14_18_28](https://github.com/MaheshS03/EH-EX-5/assets/128498431/9d79739f-1769-48e6-a898-43931c69ead1)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
