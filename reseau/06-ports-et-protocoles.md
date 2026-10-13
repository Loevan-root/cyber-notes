# Les ports et les protocoles

Source : https://youtu.be/2ppV7rpv2XY (chapitre 8)

## C'est quoi un port ?

![](images/06-ports-et-protocoles-01.png)

Un port = une porte sur la machine. Une machine possède 65 535 ports / portes.

- L'adresse IP correspond à l'adresse postale du bâtiment.
- Le port correspond au numéro de porte ou de pièce d'un service particulier à l'intérieur.

Chaque service écoute sur son propre numéro de port en attente de connexions : le trafic web frappe à une porte, les mails à une autre, SSH à une autre…

La combinaison d'une IP et d'un numéro de port permet d'identifier la machine mais aussi un service précis sur cette machine. Ce couplage est la coordonnée fondamentale de toute connexion réseau.

## Les 3 plages de ports

Si on connaît ces plages, ça permet de lire instantanément n'importe quel réseau.

![](images/06-ports-et-protocoles-02.png)

| Plage | Nom | Usage |
|---|---|---|
| 0 - 1023 | Ports réservés (bien connus) | Services essentiels standards : le web, le courrier électronique, la connexion à distance. C'est la zone qui compte le plus pour la sécurité |

![](images/06-ports-et-protocoles-09.png)

| 1024 - 49151 | Ports d'enregistrement | Applications spécifiques (MySQL, RDP) |
| 49152 - 65535 | Ports dynamiques ou éphémères | Temporaires : mon PC les utilise à la volée pour les connexions sortantes, brièvement, puis les libère |

Quand mon navigateur se connecte à un site web, il utilise un port connu côté serveur et un port éphémère aléatoire côté client (sur mon appareil). La plupart des services vulnérables intéressants se trouvent dans les ports bien connus.

## Les ports critiques

Ce sont les ports que tous les pros en cyber ont mémorisés. Je les complète dans mes notes de cours.

![](images/06-ports-et-protocoles-03.png)

![](images/06-ports-et-protocoles-04.png)

![](images/06-ports-et-protocoles-10.png)

Exemple de comparaison ancien / nouveau : Telnet (en clair) remplacé par SSH (chiffré).

![](images/06-ports-et-protocoles-05.png)

## Le scan de ports (le repérage)

Avant une attaque, un attaquant commence toujours par faire de la reconnaissance. Il cartographie la cible, et l'outil fondamental pour ça est le **scan de ports**.

Un scanner de ports teste systématiquement les ports d'une machine un par un pour voir lesquels sont ouverts, car **un port ouvert = une entrée potentielle**.

L'outil le plus connu s'appelle **Nmap** (utilisé aussi bien par les attaquants que par les défenseurs).

IRL, ce serait comme un cambrioleur qui fait le tour d'un bâtiment pour voir s'il y a une entrée.

![](images/06-ports-et-protocoles-06.png)

## Shodan, l'X-ray d'Internet

Les attaquants utilisent Shodan, qui a déjà fait la cartographie d'Internet.

![](images/06-ports-et-protocoles-07.png)

## Minimiser la surface d'attaque

Pour éviter les attaques, un défenseur ferme les ports dont on n'a pas besoin. C'est un modèle de sécurité périmétrique classique : on construit un mur et on garde les portes.

![](images/06-ports-et-protocoles-08.png)

Suite : [TCP et UDP](07-tcp-et-udp.md)
