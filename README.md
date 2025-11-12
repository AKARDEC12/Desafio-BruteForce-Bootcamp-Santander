# Desafio-BruteForce-Bootcamp-Santander
### Repositorio contendo um desafio de bruteforce utilizando plataforma tryhackme. 

---
Eu comecei o desafio utilizando o nmap para fazer a varredura das portas e detecar os serviços e versões.

Utilizei os comando -Pn (para nao pingar a maquina alvo) e -sV para identificar a versão e o software que está rodando em cada porta aberta.

### NMAP:

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


---

### PORTAS ABERTAS:

22 - SSH  OpenSSH 7.6p1 

80 - HTTP Apache 2.4.29

---

Após identificar as portas abertas, eu realizei um Gobuster para identificar os subdomínios que poderiam me levar a alguma página com vulnerabilidade. 


### ENUMERAÇÃO DE SUBDOMÍNIOS (GOBUSTER)

Starting gobuster in directory enumeration mode

/.htaccess            (Status: 403) [Size: 278]

/.hta                 (Status: 403) [Size: 278]

/.htpasswd            (Status: 403) [Size: 278]

/admin                (Status: 301) [Size: 314] [--> http://10.201.56.120/admin/]                                             

/index.html           (Status: 200) [Size: 10918]

/server-status        (Status: 403) [Size: 278]


Progress: 4613 / 4613 (100.00%)


Finished
---


Encontrei esse /admin que me levou para uma pagina onde pedia um login e senha. (imagem 1)

Entao eu abri o codigo fonte da pagina para tentar encontrar algo e lá havia um comentário bem descuidado avisando um tal de John que o login era "admin". (imagem 2)

---

A partir dai, eu ja tinha dois nomes que eu poderia rodar um bruteforce para encontrar as suas senhas. 
Comecei com o usuário "admin":
Rodei um hydra no usuario "admin" utilizando a wordlist rockyou.txt e encontrei a senha "xavier" (imagem 3)

coloquei o login "admin" e a senha "xavier" na pagina web e consegui acesso a uma RSA Private Key. (imagem 4 e imagem 5)

Joguei essa RSA Private Key no nano e depois apliquei um ssh2john para transformar em hash. 

Depois disso tudo, usei a wordlist rock novamente para quebrar a hash. E entao encontrei a senha "rockinroll"  para o usuario "john". (imagem 6)

Depois disso, a continuacao do desafio na tryhackme era entrar no usuario john via ssh e depois escalar privilegios para o root. (imagem 7, imagem 8, imagem 9 e imagem 10)

---
USUÁRIOS E SENHAS ENCONTRADAS: 

jhon:rockinroll

admin:xavier

root:football
