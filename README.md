# Desafio-BruteForce-Bootcamp-Santander
Repositorio contendo um desafio de bruteforce utilizando plataforma tryhackme. 


NMAP:

nmap -Pn -sV 10.201.56.120
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-12 06:47 EST
Nmap scan report for 10.201.56.120
Host is up (0.37s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.93 seconds


PORTAS ABERTAS:
22 - SSH 
80 - HTTP


ENUMERACAO DE SUBDOMINIOS (GOBUSTER)

Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 278]
/.hta                 (Status: 403) [Size: 278]
/.htpasswd            (Status: 403) [Size: 278]
/admin                (Status: 301) [Size: 314] [--> http://10.201.56.120/admin/]                                             
/index.html           (Status: 200) [Size: 10918]
/server-status        (Status: 403) [Size: 278]
Progress: 4613 / 4613 (100.00%)
===============================================================
Finished

USUARIOS ENCONTRADOS: 
jhon:rockinroll
admin:xavier
root:football
