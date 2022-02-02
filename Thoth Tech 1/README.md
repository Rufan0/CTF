# Thoth Tech 1 CTF Həlli

### CTF ətraflı izah [Link](https://rufan0.github.io/blog/Thoth-Tech1)

- Salam hər kəsə

- Bu gün sizinlə Thoth Tech: 1 adlı ctfi həll edəcəyik

[Yükləmə linki](https://www.vulnhub.com/entry/thoth-tech-1,734/)

- .ova faylını Virtualbox-a İMPORT edirik.

- ip adresi tapdıqdan sonra nmap ilə port scan edirik.
```
sudo netdiscover -r 192.168.1.0/24
```

```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
```

- İlk olaraq 80 portu açıq olduğuna görə web sayta daxil oldum və düz əməlli heçnə tapa bilmədim :D daha sonra nmap axtarışda ftp portunun açıq olduğunu və Anonymous olaraq daxil olmağın mümkün olduğunu gördüm

- ftp portuna bağlanmaq üçün terminal üzərindən

` ftp <IP adress>`


`ftp 192.168.1.105`

- `ls` əmrini icra edək görəciyik ki, `note.txt` adlı bir fayl var daha sonra more əmri ilə faylın içini oxuyaq.

`more note.txt`

- Dear pwnlab,
- My name is jake. Your password is very weak and easily crackable, I think change your password



- Bu qeydə nəzər salsaq istifadəçi adının pwnlab və parolunun zəif olduğunu görərik, elə isə bruteforce edə bilərik. Həm FTP, həm də SSH xidmətlərinin açıq olduğu bu hallarda mən FTP parolunu sındırmağa və onu SSH xidmətində təkrar istifadə etməyə üstünlük verirəm. Bunun səbəbi, SSH serverlərinin bruteforcing-ə məhdudiyyətlər qoyması, yəni sorğuları məhdudlaşdırmasıdır.

```
hydra -l pwnlab -P /usr/share/wordlists/rockyou.txt 192.168.1.105 ftp
```

- İndi biz SSH serverinə daxil ola bilərik.

```
ssh istiadəçi adı @ ip

ssh username @ ip

ssh pwnlab@192.168.1.105
```

- User flag əldə etdik root folderinə daxil olmaq istəfim ancaq alınmadı, indi isə Privilege Escalation edib root olmalıyıq ki, root flagini əldə edək.

- Sistemdə git olub olmadığını yoxladım və var.

- Elə isə /tmp/ faylına keçib [LinEnum.git](https://github.com/rebootuser/LinEnum) yükləyək və işə salaq.


- Və boom boşluğu tapdıq!!

```
sudo find . -exec /bin/bash \; -quit
```

- Bu əmr ilə artıq biz root olduq
