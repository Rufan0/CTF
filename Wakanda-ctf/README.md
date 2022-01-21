#Wakanda writeup CTF

**Wakanda.ova yükləmə [linki](https://www.vulnhub.com/entry/wakanda-1,251/)**

Bu, çətin VM deyil və yaradıcı tərəfindən orta səviyyəli olaraq sıralanır. Beləliklə, bu yazı yeni başlayanlar və əlbəttə hakerlik və pentestinq haqqında daha çox öyrənmək istəyənlər üçündür. Sizə lazım olan tək şey Wakanda VM və Kali Linux-dur

![Wakanda](https://i.imgur.com/0ViToK8.png)

- Qeyd: Açıqlama hissəsinə nəzər salsaq görərik ki 3 dənə flag-imiz var.

- İlk olaraq .ova faylını yükləyib [Virtualbox](https://www.virtualbox.org/) ilə açırıq
- Kali linux və Wakanda VM eyni şəbəkəyə (Nat Networka ayarlayırıq)
![Wakanda1](https://i.imgur.com/jqnq1qN.png)
![Wakanda2](https://i.imgur.com/ZMvQRwr.png)

- Daha sonra isə VM-nı işə salırıq

![Wakanda3](https://i.imgur.com/s4Uu6ta.png)

```
┌──(kali㉿kali)-[~]
└─$ sudo netdiscover -r 10.0.2.0/24
```
> Bunu nmap vasitəsilə də edə bilərsiniz

- netdiscover -dən istifadə edərək Wakanda-nın ip adresini tapırıq.

```
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                                                        
                                                                                                                                                                   
 9 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 540                                                                                                      
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------                                                                                            
 10.0.2.27       08:00:27:08:80:9d      4     240  PCS Systemtechnik GmbH
```
- İP-10.0.2.27
- Açıq portlar və işləyən xidmətlər haqqında fikir əldə etmək üçün nmap istifadə edərək tam portscana başlayaq.
```
┌──(root💀kali)-[/home/kali]
└─# nmap -sS -sV -A -p- 10.0.2.27
Starting Nmap 7.92 ( https://nmap.org ) at 2022-01-20 11:03 EST
Nmap scan report for 10.0.2.27
Host is up (0.0023s latency).
Not shown: 65531 closed tcp ports (reset)
PORT      STATE SERVICE VERSION
80/tcp    open  http    Apache httpd 2.4.10 ((Debian))
|_http-title: Vibranium Market
|_http-server-header: Apache/2.4.10 (Debian)
111/tcp   open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          37624/udp6  status
|   100024  1          37669/tcp6  status
|   100024  1          50586/tcp   status
|_  100024  1          59892/udp   status
3333/tcp  open  ssh     OpenSSH 6.7p1 Debian 5+deb8u4 (protocol 2.0)
| ssh-hostkey: 
|   1024 1c:98:47:56:fc:b8:14:08:8f:93:ca:36:44:7f:ea:7a (DSA)
|   2048 f1:d5:04:78:d3:3a:9b:dc:13:df:0f:5f:7f:fb:f4:26 (RSA)
|   256 d8:34:41:5d:9b:fe:51:bc:c6:4e:02:14:5e:e1:08:c5 (ECDSA)
|_  256 0e:f5:8d:29:3c:73:57:c7:38:08:6d:50:84:b6:6c:27 (ED25519)
50586/tcp open  status  1 (RPC #100024)
MAC Address: 08:00:27:08:80:9D (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   2.30 ms 10.0.2.27

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 21.27 seconds
```
- Açıq port və işləyən xidmətlər var. 80 nömrəli portda Apache web serveri, 3333 nömrəli portda OpenSSH serveri və RPC ilə işləyən portlar var.(Bunları bir qırağa qeyd edək.

- Daha sonra isə [Gobuster](https://github.com/OJ/gobuster)-dən istifadə edərək directoryləri axtarırıq
```
──(root💀kali)-[/home/kali]
└─# gobuster dir -u http://10.0.2.27 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x html,txt,php
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.0.2.27
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              html,txt,php
[+] Timeout:                 10s
===============================================================
2022/01/20 11:39:12 Starting gobuster in directory enumeration mode
===============================================================
/index.php            (Status: 200) [Size: 1527]
/fr.php               (Status: 200) [Size: 0]   
/admin                (Status: 200) [Size: 0]   
/backup               (Status: 200) [Size: 0]   
/shell                (Status: 200) [Size: 0]   
/secret               (Status: 200) [Size: 0]   
/secret.txt           (Status: 200) [Size: 40]  
/troll                (Status: 200) [Size: 0]   
/server-status        (Status: 403) [Size: 297] 
/hahaha               (Status: 200) [Size: 0]   
/hohoho               (Status: 200) [Size: 0]   
                                                
===============================================================
2022/01/20 11:51:05 Finished
===============================================================
```

- Web sayta nəzər salaq. Burp Suite -toolu da bir qıraqda işləsin :)

![Wakanda4](https://i.imgur.com/iq3VXBQ.png)

- Veb saytın HTML kodlarına nəzər salın.
> CTRL+U

![Wakanda5](https://i.imgur.com/8lvUcp3.png)

- Şərh edilmiş bir kod var. Bu, fransız dilinə dil dəyişdirici kimi görünür, lakin vebsaytda görünmür.

- Saytın URL hissəsinə `?lang=fr` əlavə edirik 

![Wakanda6](https://i.imgur.com/ZDJDPxq.png)

- Gördüyünüz kimi məzmunun bir hissəsi indi fransız dilində göstərilir.

- Bunu gördükdə ağlıma ilk olaraq heçnə gəlmədi :D daha sonra araşdırdım və Directory Traversal ola biləcəyini gördüm.



Davamina sabah baxacam

<!-- Ola bilərmi ki, lang parametrinin dəyəri PHP skriptinə daxil edilmiş tərcüməni ehtiva edən PHP faylıdır? Və əgər bu doğrudursa, yerli faylları (LFI) daxil etmək və PHP skriptlərinə baxmaq və ya kodu icra etmək üçün ondan istifadə edə bilərikmi? 

![Wakanda7](https://i.imgur.com/p81eiL8.png)
![Wakanda7](https://i.imgur.com/gWphPe0.png)

- Server fr.php faylında 200 OK və test.php mövcud olmayan faylda 404 qaytarır.

- Bu, bunun bir fayl olduğunu təsdiqləyir. -->







