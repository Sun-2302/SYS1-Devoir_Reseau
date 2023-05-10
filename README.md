# SYS1-Devoir_Reseau

## FTP - Authentification
. Démarrer le challenge (Téléchargement d'un fichier)<br>
. Ouvrir le fichier sur Wireshark<br>
. Clic droit sur un des protocoles FTP<br>
. Suivre son flux tcp<br>
. Le mot de passe est à côté de PASS

```
USER cdts3500
331 Enter password.
PASS c******0
230 CDTS3500 logged on.
SYST
215  OS/400 is the remote operating system. The TCP/IP version is "V5R2M0".
```

## TELNET - Authentification
. Démarrer le challenge (Téléchargement d'un fichier)<br>
. Ouvrir le fichier sur Wireshark<br>
. Clic droit sur un des protocoles Telnet<br>
. Suivre son flux tcp<br>
. Le mot de passe est à côté de password

```
........... ..!.."..'.....#..%..%........... ..!..".."........P. ....".....b........b....	B.
........................"......'.....#..&..&..$..&..&..$.. .....#.....'........... .9600,9600....#.bam.zing.org:0.0....'..DISPLAY.bam.zing.org:0.0......xterm-color.............!.............."............
OpenBSD/i386 (oof) (ttyp1)

login: .."........"ffaakkee
.
Password:u***
.
```

## ETHERNET - trame
. Démarrer le challenge<br>
. Copier l'hexadécimal trouvé et le convertir en texte
```
00 05 73 a0 00 00 e0 69 95 d8 5a 13 86 dd 60 00
00 00 00 9b 06 40 26 07 53 00 00 60 2a bc 00 00
00 00 ba de c0 de 20 01 41 d0 00 02 42 33 00 00
00 00 00 00 00 04 96 74 00 50 bc ea 7d b8 00 c1
d7 03 80 18 00 e1 cf a0 00 00 01 01 08 0a 09 3e
69 b9 17 a1 7e d3 47 45 54 20 2f 20 48 54 54 50
2f 31 2e 31 0d 0a 41 75 74 68 6f 72 69 7a 61 74
69 6f 6e 3a 20 42 61 73 69 63 20 59 32 39 75 5a
6d 6b 36 5a 47 56 75 64 47 6c 68 62 41 3d 3d 0d
0a 55 73 65 72 2d 41 67 65 6e 74 3a 20 49 6e 73
61 6e 65 42 72 6f 77 73 65 72 0d 0a 48 6f 73 74
3a 20 77 77 77 2e 6d 79 69 70 76 36 2e 6f 72 67
0d 0a 41 63 63 65 70 74 3a 20 2a 2f 2a 0d 0a 0d
0a
```
. Le mot de passe est à côté de Authorization basic mais il est codé en base64 (Présence de == vers la fin)
```
s��i��Z��`�@&S`*����� A�B3�tP��}�����Ϡ
	>i��~�GET / HTTP/1.1
Authorization: Basic Y*****************==
User-Agent: InsaneBrowser
Host: www.myipv6.org
Accept: */*
```
. Décoder le mot de passe
```
*****:*******
```
## Authentification twitter
. Démarrer le challenge (Téléchargement d'un fichier)<br>
. Ouvrir le fichier sur Wireshark<br>
. Clic droit sur le protocole HTTP <br>
. Suivre son flux<br>
. Le mot de passe est à côté de Authorization basic mais il est codé en base64 (Présence de == vers la fin)
```
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Authorization: Basic d***********************=
Connection: keep-alive
Host: twitter.com
```
. Décoder le mot de passe (le mot de passe final commence après le : )
```
usertest:p*******
```

## Bluetooth - Fichier inconnu
. Démarrer le challenge (Téléchargement d'un fichier)<br>
. Ouvrir le fichier sur Wireshark<br>
. Aller dans Wireless > Equipement bluetooth  dans la barre d'outil pour trouver le nom et l'adresse MAC du téléphone

![Capture d’écran (223)](https://github.com/Sun-2302/SYS1-Devoir_Reseau/assets/127884950/73f09e0d-43ac-44ee-b025-bbfcbddb4aef)

```
0c:b3:19:b9:4f:c6 SamsungE GT-S7390G
```
. Il faut concaténer  l'adresse MAC (en majuscule) et le nom du téléphone
```
0C:B3:19:B9:4F:C6GT-S7390G 
```
. Puis on encrypte cette concaténation en SHA1 pour obtenir le mot de passe
```
c1************************************2b
```
