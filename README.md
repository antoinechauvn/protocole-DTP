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
| dynamic desirable |  Dans ce mode, le port est en mode `access` mais il écoute et envoi des annonces DTP afin d'établir un Dynamic Trunk. Si la négociation réussie avec un port voisin en Trunk ou Auto, le port devient trunk. |
| dynamic auto | L'interface DTP `dynamic auto` n'écoutera passivement que les messages DTP provenant de l'interface de l'autre commutateur. Si l'interface `dynamic auto` DTP reçoit un message DTP de l'interface de l'autre commutateur, une liaison trunk sera formée. |
| trunk | Ce mode place de manière statique le port dans un trunk et annonce des paquets  DTP au voisin afin d'établir une liaison trunk dynamique. |
| nonegotiate | Le mode `nonegotiate` désactive l'envoi de paquets DTP à partir d'une interface. Le mode `nonegotiate` n'est possible que lorsque le mode de port de commutation de l'interface est « access » ou « trunk ». |
| access | Une interface de commutateur configurée en mode `access` convertit l'interface du commutateur en mode `access`. Le mode "access" empêche l'utilisation du DTP et fait du port un port d'accès pur. |

### Exemple:
![image](https://user-images.githubusercontent.com/83721477/165760428-7557fb30-291e-4e73-9f2e-9e283c074837.png)
![image](https://user-images.githubusercontent.com/83721477/165760475-01b83a69-e8d3-4d7a-b19c-e7d749567f07.png)
![image](https://user-images.githubusercontent.com/83721477/165760527-4f4c9307-61a3-4292-9277-45c3a10c7efd.png)
