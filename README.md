# protocole-DTP
Découverte du protocole DTP

### Qu'est-ce que le protocole DTP?
Le Dynamic Trunk Protocol ou DTP est un protocole réseau propriétaire de Cisco Systems, permettant de gérer dynamiquement l'activation/désactivation du mode trunk d'un port sur un commutateur réseau.

## Principe de fonctionnement
Le principe est assez simple:

* Les annonces DTP sont effectué toutes les 30 secondes afin que le voisin soit toujours tenu au 
courant du statuts de la liaison. DTP a besoin que les deux switches soient dans le même domaine VTP.
* Si le port est connecté à un switch voisin, ce dernier va recevoir l’annonce DTP et y répondre. Des deux côtés, l’activation du Trunk s’effectue.
* Si le port est connecté à un pc, ce dernier ne répondra pas à l’annonce, car il comprend pas le protocole. Sur le port du switch, le Trunk n’est pas activé et donc reste en mode Access.

| Mode | Description |
| --- | --- |
| dynamic desirable | Un port de commutateur configuré en mode `dynamic desirable` DTP tentera activement de convertir la liaison en une liaison trunk à l'aide du protocole DTP (Dynamic Trunking Protocol). Si le port connecté à un autre port est capable de former un trunk, une liaison trunk sera formée. <br>L'interface qui est configurée en mode `dynamic desirable` DTP générera des messages DTP sur l'interface. Si le commutateur reçoit des messages DTP de l'autre commutateur, il supposera que l'autre port est capable de gérer des trames étiquetées et une liaison trunk sera formée entre deux commutateurs. |
| dynamic auto | Un port de commutateur configuré en tant que DTP `dynamic auto` est capable de former une liaison trunk si l'autre interface de commutateur est configurée pour former une interface trunk et peut négocier à l'aide de DTP. <br>Une interface de commutation configurée en mode DTP `dynamic auto` ne générera pas de messages DTP sur l'interface. L'interface DTP `dynamic auto` n'écoutera passivement que les messages DTP provenant de l'interface de l'autre commutateur. Si l'interface `dynamic auto` DTP reçoit un message DTP de l'interface de l'autre commutateur, une liaison trunk sera formée. |
| trunk | Une interface de commutateur configurée en mode trunk convertit l'interface du commutateur en mode trunking pur. Une interface en mode trunk peut également négocier avec l'interface de commutateur de l'autre côté pour former une liaison trunk entre deux commutateurs. |
| nonegotiate | Le mode `nonegotiate` désactive l'envoi de paquets DTP à partir d'une interface. Le mode `nonegotiate` n'est possible que lorsque le mode de port de commutation de l'interface est « access » ou « trunk ». |
| access | Une interface de commutateur configurée en mode `access` convertit l'interface du commutateur en mode `access`. Le mode "access" empêche l'utilisation du DTP et fait du port un port d'accès pur. |

![image](https://user-images.githubusercontent.com/83721477/165760428-7557fb30-291e-4e73-9f2e-9e283c074837.png)
![image](https://user-images.githubusercontent.com/83721477/165760475-01b83a69-e8d3-4d7a-b19c-e7d749567f07.png)
![image](https://user-images.githubusercontent.com/83721477/165760527-4f4c9307-61a3-4292-9277-45c3a10c7efd.png)
