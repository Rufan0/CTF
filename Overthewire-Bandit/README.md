# OverTheWire Bandit CTF Həlləri



**CTF haqqında ətraflı-[link](https://overthewire.org/wargames/bandit/)**


SSH bağlantısı etmək üçün 1 neçə proqramdan istifadə edə bilərsiniz mənim istifadə etdiyim əməliyyat sistemi Windows 11-dir və mən WSL-Linux vasitəsilə bağlanıram

[Putty](https://putty.org/) vasitəsilə də bağlana bilərsiniz 

**Bandit [LEVEL 0](https://overthewire.org/wargames/bandit/bandit0.html)** 

![bandit level-0](https://i.imgur.com/1EyLY3l.png)

- Portu 2220-yə təyin etməklə istənilən SSH proqramı ilə bağlana bilərsiniz.
```
 ssh bandit.labs.overthewire.org -p 2220 -l bandit0
```
> və ya terminalda ilk olaraq belə yazıb `ssh bandit0@bandit.labs.overthewire.org -p 2220` daha sonra parolu daxil edə bilərsiniz

- Parol `bandit0` 

**Bandit [LEVEL 0->1](https://overthewire.org/wargames/bandit/bandit1.html)** 
![bandit level-1](https://i.imgur.com/BadC8Ut.png)
- `ls`
- `cat readme`
- parolu copy edib çıxırıq `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`
- cat command ətraflı [link](https://linuxize.com/post/linux-cat-command/)

**Bandit [LEVEL 1->2](https://overthewire.org/wargames/bandit/bandit2.html)**
![bandit level-1](https://i.imgur.com/OvZ1tVX.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit1
```
- `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`
- `ls`
- faylı oxumaq üçün `cat ./-`
- parolu copy edib çıxırıq `CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`

**Bandit [LEVEL 2->3](https://overthewire.org/wargames/bandit/bandit3.html)**
![bandit leve2-3](https://i.imgur.com/Eqfq7PZ.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit2
```
- `CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`
- `ls`
- faylı oxumaq üçün `cat 'spaces in this filename'`
>və ya `cat spaces\ in\ this\ filename`   
- parolu copy edib çıxırıq `UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`

**Bandit [LEVEL 3->4](https://overthewire.org/wargames/bandit/bandit4.html)**
![bandit leve3-4](https://i.imgur.com/WxEdl0x.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit3
```
- `UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`
- `ls`
- `cd inhere`
- `ls -la`
- faylı oxumaq üçün `cat .hidden`   
- parolu copy edib çıxırıq `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`

**Bandit [LEVEL 4->5](https://overthewire.org/wargames/bandit/bandit5.html)**
![bandit leve4-5](https://i.imgur.com/eYE0yMQ.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit4
```
- `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`
- `ls`
- `cd inhere`
- `ls -la`
- faylı oxumaq üçün `cat ./-file07`   
- parolu copy edib çıxırıq `koReBOKuIDDepwhWk7jZC0RTdopnAYKh`

**Bandit [LEVEL 5->6](https://overthewire.org/wargames/bandit/bandit6.html)**
![bandit leve5-6](https://i.imgur.com/GCxla05.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit5
```
-`koReBOKuIDDepwhWk7jZC0RTdopnAYKh`
- `ls`
- `cd inhere` və `ls -la`
- Beləliklə, göstərişlər verilir ki, fayl "insan tərəfindən oxuna bilər, ölçüsü 1033 baytdır, icra edilə bilməz"
- `find . -type f -size 1033c -exec cat {} \;`
- parolu copy edib çıxırıq `DXjZPULLxYr17uwoI01bNLQbtFemEgo7`
- 
**Bandit [LEVEL 6->7](https://overthewire.org/wargames/bandit/bandit7.html)**
![bandit leve6-7](https://i.imgur.com/mBCqcYL.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit6
```
- `DXjZPULLxYr17uwoI01bNLQbtFemEgo7`
- `ls`
- Beləliklə, faylın 33 bayt ölçüsündə bandit6 qrupuna, bandit7 istifadəçisinə məxsus olacağına dair göstərişlər verilir
- `find / -user bandit7 -group bandit6 -size 33c -exec cat {} \; 2>/dev/null`
- parolu copy edib çıxırıq `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`

**Bandit [LEVEL 7->8](https://overthewire.org/wargames/bandit/bandit8.html)**
![bandit leve7-8](https://i.imgur.com/EnjfjKw.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit7
```
- `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`
- `ls`
- İpucu verildiyi kimi data.txt-də olan parol “milyonuncu” ilə eyni sətirdədir.
- `cat data.txt | grep "millionth"`
- parolu copy edib çıxırıq `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`

**Bandit [LEVEL 8->9](https://overthewire.org/wargames/bandit/bandit9.html)**
![bandit leve8-9](https://i.imgur.com/fpoDHII.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit8
```
- `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`
- `ls`
- `cat data.txt | sort | uniq -c` və 1 olan sətirdədir parol
- parolu copy edib çıxırıq `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`

**Bandit [LEVEL 9->10](https://overthewire.org/wargames/bandit/bandit10.html)**
![bandit leve9-10](https://i.imgur.com/Jz0LrEp.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit9
```
- `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`
- `ls`
- `string data.txt`
- parolu copy edib çıxırıq `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`
- [Strings haqqında ətraflı](https://www.howtogeek.com/427805/how-to-use-the-strings-command-on-linux/)


**Bandit [LEVEL 10->11](https://overthewire.org/wargames/bandit/bandit11.html)**
![bandit leve10-11](https://i.imgur.com/qowjje8.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit10
```
- `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`
- `ls`
- `cat data.txt | base64 -d`
- parolu copy edib çıxırıq `IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`

**Bandit [LEVEL 11->12](https://overthewire.org/wargames/bandit/bandit12.html)**
![bandit leve11-12](https://i.imgur.com/ZhtKVhd.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit11
```
- `IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`
- `ls`
- `cat data.txt`
- Göründüyü kimi, bizdən verilən faylda ROT13 decode yerinə yetirməliyik.
- İndi biz bunu istədiyiniz hər hansı deşifrə alətindən istifadə edərək deşifrə edə bilərik. Mən özüm [CyberChef](https://gchq.github.io/CyberChef/)-dən CTF-lər üçün əsas vasitə kimi istifadə edirəm.
- Bununla belə, daxili Linux əmrindən istifadə edərək bu problemi həll etmək mümkündür.
- `cat data.txt| tr [A-Za-z] [N-ZA-Mn-za-m]`
- parolu copy edib çıxırıq `5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`

**Bandit [LEVEL 12->13](https://overthewire.org/wargames/bandit/bandit13.html)**
![bandit leve12-13](https://i.imgur.com/k2lcLGR.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit12
```
- `5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`
- `ls`
- `cat data.txt` vər görürük ki faylımız hexdump formatindadir
 ```
 mkdir /tmp/rufan/
 cp data.txt /tmp/rufan/data.txt
 cd /tmp/rufan/
 xxd -r data.txt > password
 
 file password
 password: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```
- və faylımızın gzip compressed olduğunu görürük ctf in açıqlama hissəsində də deyilmişdi bir neçə dəfə compress edilmiş faylın içərisindədir növbəti parol
```
mv password password.gz
gunzip password.gz

file password
bzip2 compressed data, block size = 900k
mv password password.bz2
bzip2 -d password.bz2 

file password 
password: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix

mv password password.gz
gunzip password.gz 

file password 
password: POSIX tar archive (GNU)

mv password password.tar
tar xvf password.tar data5.bin
data5.bin

file data5.bin 
data5.bin: POSIX tar archive (GNU)

mv data5.bin data5.tar
tar xvf data5.tar data6.bin 
data6.bin

file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k

mv data6.bin data6.bz2
bzip2 -d data6.bz2 

file data6
data6: POSIX tar archive (GNU)

mv data6 data6.tar
tar xvf data6.tar data8.bin
data8.bin

file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix

mv data8.bin data8.gz
gzip -d data8.gz 

file data8 
data8: ASCII text

cat data8
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
- parolu copy edib çıxırıq `8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL `

**Bandit [LEVEL 13->14](https://overthewire.org/wargames/bandit/bandit14.html)**
![bandit leve13-14](https://i.imgur.com/u6LGJ6R.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit13
```
- `8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL`
- ls etdikdən sonra görürük ki private key var və bunundab istifadə edib bandit 14 istifadəçisinə bağlanacağıq
```
bandit13@bandit:~$ ls
sshkey.private

bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
```
- Daha sonra isə `cat /etc/bandit_pass/bandit14` -edib bandit14 istifadəçisinin parolunu əldə edirik

- parolu copy edib çıxırıq `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`

**Bandit [LEVEL 14->15](https://overthewire.org/wargames/bandit/bandit15.html)**
![bandit leve14-15](https://i.imgur.com/7WDGiIN.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit14
```
- `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`
```
bandit14@bandit:~$ echo "4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e" | nc localhost 30000
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
- parolu copy edib çıxırıq `BfMYroe26WYalil77FoDi9qh59eK5xNr`

**Bandit [LEVEL 15->16](https://overthewire.org/wargames/bandit/bandit16.html)**
![bandit leve15-16](https://i.imgur.com/KLaYYbP.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit15
```
- `BfMYroe26WYalil77FoDi9qh59eK5xNr`
```
bandit15@bandit:~$ echo "BfMYroe26WYalil77FoDi9qh59eK5xNr" | openssl s_client -connect localhost:30001 -ign_eof
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIEZOzuVDANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjEwOTMwMDQ0NTU0WhcNMjIwOTMwMDQ0NTU0WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAM9En7CC
uPr6cVPATLAVhWMU1hggfIJEp5sZN9RPUbK0zKBv802yD54ObHYmIge6lqqkgXOz
2AuI4UfCG4iMb0UYUCA/wISwNqUQrjcja0OnqzCTRscXzzoIsHbC8lGFzMDRz3Jw
8nBD6/2jvFt1rnBtZ4ghibNn5rFHRi5EC+K/AgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAD7/moj14DUI6/D6imJ8pQlAy/8lZlsrbyRnqpzjWaATShDYr7k3
umdRg+36MciNFAglE7nGYZroTSDCm650D81+797owSXLPAdp1Q6JfQH5LOni2kbw
UHcO9hwQ+rJzEgIlfGOic7dC5lj8DBU5tugY87RZGKiZ2GG77WXas9Iz
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: 481E019975293D69DF40FADFA3F46C3CE7A52B2B4BF3F5202EBC69C820B1E94A
    Session-ID-ctx:
    Master-Key: 678BDFB9E5A5AC6F67CC36EB6F0D2FF9A68A37753F419E442835DF4B3F0FC5DFD8047BEF5E5D8BF01707E951D841A884
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 8a eb e8 f5 31 15 46 ad-b2 a8 10 c1 51 b9 66 14   ....1.F.....Q.f.
    0010 - 08 a7 af 89 15 e3 60 f5-92 78 8a 2a 4c 52 d6 a4   ......`..x.*LR..
    0020 - 42 3a c0 43 b5 12 53 db-3c bd 09 1a f0 39 fd 50   B:.C..S.<....9.P
    0030 - 89 73 4b 8b 49 c9 c0 ec-d7 a0 ba d0 08 17 bc 5b   .sK.I..........[
    0040 - c1 83 78 18 df 53 67 ff-ba 0e 83 d2 36 6c 2a 19   ..x..Sg.....6l*.
    0050 - 95 81 82 81 48 9e 0b 8e-34 82 b6 21 bc fc e2 12   ....H...4..!....
    0060 - 82 d2 96 79 32 86 d6 f5-2d c0 60 08 1b 32 46 9b   ...y2...-.`..2F.
    0070 - b6 d2 eb dc ad 9a cf 33-f0 28 a2 61 5a 1d bc 68   .......3.(.aZ..h
    0080 - 5f 99 60 44 1c e1 30 0c-20 96 d9 24 05 95 3d 66   _.`D..0. ..$..=f
    0090 - 53 c0 b5 c5 10 21 bd 21-6c 1a b2 ac 44 16 cc a1   S....!.!l...D...

    Start Time: 1642619404
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed

```
- parolu copy edib çıxırıq `cluFn7wTiGryunymYOu4RcffSxQluehd`

**Bandit [LEVEL 16->17](https://overthewire.org/wargames/bandit/bandit17.html)**
![bandit leve16-17](https://i.imgur.com/S8NLUYz.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit16
```
- `cluFn7wTiGryunymYOu4RcffSxQluehd`

- #Səviyyə 16 bizi hər haker alət dəstinin ən vacib hissələrindən biri ilə tanış edir: nmap


```
bandit16@bandit:~$ nmap -p31000-32000 localhost

Starting Nmap 7.40 ( https://nmap.org ) at 2020-01-17 14:49 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00024s latency).
Not shown: 999 closed ports
PORT STATE SERVICE
31518/tcp open unknown
31790/tcp open unknown


bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIERp0H3zANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjExMjA1MTkxNjIwWhcNMjIxMjA1MTkxNjIwWjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBANKk71YL
CHrcxjGkDZ52qTgeK3UsA5fQMfY+QrvJfGyvybJ2aWEOLv44Tz/V6XQ3K9WWltMR
v1e7+y9RWje/CmgJ/eeYUoAslcbHW5M3AOyoolDyazod4ddFkQdcLU4DzD0AAVb5
OsQ9FriQCtSjmdv/DXDB1oi8Di9dEs5vpeOzAgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAH/R4xbuO92i9pVbZ9A82wNkDZ6yz0wY+h5ft7Z2rWhV8bc6jriA
wlLToiVB5zB7SEflrcUXI4y8A4pXocxn26wpGoITRFCiNZJecBPsgkjSqBwJ5RMB
zCQ4OTg/oPgIBSNxYZcasR4/0cks+haWBDV9V/Y0OxeU1OKCKzcWtKvI
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: 192DEE22B19B9CCCBC112C94625151157C4DABD4118E27F4FE2E63F6CDCE5D8E
    Session-ID-ctx:
    Master-Key: A2B19ABC41C539127F177AA531CBC14B17464FAE1DF912C9AF8E73AF997AB1B3C0D93551B52E7CE40E89833702F43CCB
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - a9 7b f8 63 21 5b c5 4e-f5 18 97 8e 5e d5 c7 43   .{.c![.N....^..C
    0010 - bf 71 63 ca 7f de e7 9b-a7 a8 69 17 f0 79 fb 98   .qc.......i..y..
    0020 - 71 01 28 9a 36 92 52 dd-26 4e c5 9a ab ee 19 0c   q.(.6.R.&N......
    0030 - 1a 28 3c 85 17 a8 2b 00-b0 0d 9c e3 52 41 0d 86   .(<...+.....RA..
    0040 - 12 6f 32 74 a0 5c d8 4a-8d 8e 9c 60 81 c0 46 ba   .o2t.\.J...`..F.
    0050 - 01 43 24 15 ec 67 ff cd-b6 b9 1e 66 89 e6 a2 88   .C$..g.....f....
    0060 - 1e 33 44 e2 c9 5c e6 46-37 b8 31 e4 73 16 9f 71   .3D..\.F7.1.s..q
    0070 - f0 f0 67 a7 08 96 7e 56-36 0f 0f 4f 53 44 e1 24   ..g...~V6..OSD.$
    0080 - 31 ef 56 a2 ea ce 5c 72-b2 9e c5 79 9e 0d 72 8d   1.V...\r...y..r.
    0090 - f9 b8 18 ea eb c1 c6 17-2a 90 ec 11 98 06 ba dd   ........*.......

    Start Time: 1642823862
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----


LAZIMLI HISSE:

-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

```
- Daha sonra isə bu private key-i lokal maşınımızda bir text olaraq qeyd edirik və `chmod 400 privatekey17` edirik.
- `ssh -i privatekey17 bandit17@bandit.labs.overthewire.org -p 2220` və bandit 17 yə bağlandıq.
- `cat /etc/bandit_pass/bandit17` bu command ilə bandit 17 nin parolunu eldə etmiş olduq. 
- parolu copy edib çıxırıq `xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn`

**Bandit [LEVEL 17->18](https://overthewire.org/wargames/bandit/bandit18.html)**
![bandit leve17-18](https://i.imgur.com/BJae1wK.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit17

xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn
```
- Səviyyə 17 -> Səviyyə 18 səhifəsi bizə deyir ki, “passwords.new” və passwords.old” arasında fərqli olan yalnız bir sətir var və o, növbəti səviyyə üçün paroldur. Diff aləti ilə biz faylları asanlıqla müqayisə edə və onların fərqlərini tapa bilərik:
```
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
---
> kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
bandit17@bandit:~$
```

- parolu copy edib çıxırıq `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`


**Bandit [LEVEL 18->19](https://overthewire.org/wargames/bandit/bandit15.html)**
![bandit leve18-19](https://i.imgur.com/7WDGiIN.png)
```
ssh bandit.labs.overthewire.org -p 2220 -l bandit18
```
 `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`
```
-→ ~ ssh bandit18@bandit.labs.overthewire.org -p 2220
Byebye !
Connection to bandit.labs.overthewire.org closed.
hackinganarchy@kali:~/Bandit#
```
- SSH vasitəsilə qoşulmağa cəhd etsək, dərhal sistemdən çıxırıq. Xoşbəxtlikdən, səhifə də bizə parolun hansı faylda olduğunu söyləyir VƏ ssh bizə shell olmadan əmrləri yerinə yetirmək imkanı verir. Bundan istifadə edərək parolu əldə etməyə çalışaq.
```
-→ ~ ssh bandit.labs.overthewire.org -p 2220 -l bandit18 cat readme
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

- parolu copy edib çıxırıq `IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x`
