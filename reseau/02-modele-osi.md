# Le modèle OSI

Source : https://youtu.be/2ppV7rpv2XY (chapitre 3)

Le modèle OSI partage le travail en 7 étapes distinctes (7 couches pour une tâche).

![](images/02-modele-osi-01.png)

Décomposition des couches :

![](images/02-modele-osi-02.png)

## Couche 1 : la couche physique

Unité de données : bits.

Toutes les failles possibles à la couche 1 sont des attaques qui nécessitent un accès physique au câble pour pouvoir intercepter et lire le signal brut. Un attaquant muni d'une radio peut brouiller un signal sans fil pour l'interrompre ou le capturer en vol.

![](images/02-modele-osi-03.png)

La sécurité commence à la couche une, alors si quelqu'un a un accès physique, ça compromet les sécurités mises en place des couches supérieures.

## Couche 2 : la liaison des données

**ARP** (Address Resolution Protocol) : au sein d'un réseau local, les appareils utilisent un protocole de confiance simple nommé ARP pour faire correspondre les adresses IP aux adresses MAC.

Un attaquant dans le même réseau peut mentir et envoyer des réponses falsifiées indiquant : « Je suis le routeur. Envoyez-moi votre trafic ». Là, tous les appareils vont lui envoyer leur trafic en le prenant pour le routeur, et lui va renvoyer ça vers le routeur pour faire croire que tout est normal.

Il s'agit d'une attaque de type *man in the middle*, et elle se situe précisément au niveau 2.

## Couche 3 : le réseau

La couche de distribution mondiale : c'est à cette couche que se trouvent l'adresse IP et le routeur. Son rôle : acheminer les paquets à travers les réseaux, d'une adresse IP source à une de destination, en choisissant le chemin le plus court.

Unité de données : packets.

![](images/02-modele-osi-05.png)

- **IP spoofing** : usurper l'IP d'une personne (l'IP source).
- **BGP hijacking** : quand l'attaquant ment au système de routage d'Internet lui-même, ce qui lui permet de convaincre les routeurs du monde entier d'envoyer le trafic d'une victime au mauvais endroit.

Résumé : la couche 3, c'est là où les données deviennent mondiales et où les attaquants peuvent rediriger le trafic de pays entiers.

![](images/02-modele-osi-04.png)

## Couche 4 : le transport

C'est ici que l'on va gérer la communication entre deux programmes spécifiques. C'est ici que résident les protocoles TCP et UDP, que les ports entrent en jeu et que la fiabilité est gérée.

L'unité de données ici est le segment.

La couche 4, c'est quand mon navigateur communique avec un serveur web : c'est elle qui établit cette connexion spécifique sur un port et qui s'assure que les données arrivent correctement.

Les menaces à la couche 4 sont basées sur la connexion :

- **SYN flood** : une attaque par inondation de requêtes, qui est une attaque par déni de service. Elle exploite les processus d'établissement de la connexion TCP (le handshake) pour épuiser les ressources d'un serveur.
- **Scan de ports** : il permet à un attaquant de cartographier les portes ouvertes d'une machine. C'est une étape de reconnaissance essentielle avant presque toutes les attaques.

C'est à ce niveau que se forment les conversations, ce qui en fait l'endroit où les attaquants cherchent des failles et submergent le système.

![](images/02-modele-osi-06.png)

## Couche 5 : les sessions

C'est ici qu'est gérée l'ouverture et la fermeture de conversations en cours, les sessions entre deux systèmes.

![](images/02-modele-osi-07.png)

Métaphore : c'est comme fonder le dialogue, initier l'appel, le maintenir et raccrocher proprement.

Dans la réalité, les responsabilités de cette couche sont gérées conjointement avec celles des couches environnantes. Ce qui explique pourquoi le modèle OSI est plus un outil pédagogique qu'un plan à suivre à la lettre.

![](images/02-modele-osi-12.png)

Menace principale : le **détournement de session** (session hijacking). C'est le vol du jeton, ou de l'identifiant, qui représente la session active. L'attaquant peut alors se connecter à notre compte et usurper notre session sans notre mot de passe.

Une session permet de se connecter à notre compte sans avoir à se reconnecter à chaque fois que nous repartons sur un site.

## Couche 6 : la présentation

![](images/02-modele-osi-08.png)

Son rôle est de collecter les données et de les formater de manière à ce que les deux parties comprennent. C'est le traducteur : il traduit les chiffrements et les encodages, et il transforme les données chiffrées à nouveau en données lisibles.

L'idée clé : les données lisibles sont chiffrées pendant le transport pour la sécurité des données, puis sont rendues de nouveau lisibles (déchiffrées).

**lisible → illisible → lisible**

Attaques :

- **SSL striping** : une attaque qui force discrètement notre connexion à utiliser HTTP au lieu de HTTPS afin de pouvoir lire toutes les données que l'on envoie.
- **Downgrade** : l'attaquant intercepte la connexion afin de forcer le serveur et la victime à utiliser un protocole de chiffrement obsolète ou faible, pour le rendre facile à casser et lire les données échangées.

C'est approximativement ici que se situe TLS (la technologie qui sous-entend HTTPS).

Petite info bonus par moi-même : le S de HTTPS signifie sécurité et il est associé à une couche de chiffrement SSL/TLS.

## Couche 7 : application

![](images/02-modele-osi-09.png)

C'est la couche qu'un attaquant cherche réellement à atteindre. C'est dans cette couche que se situent les protocoles HTTP, HTTPS, SMTP, DNS, SSH.

| Usage | Protocole |
|---|---|
| Le web | HTTP, HTTPS |
| Le courrier électronique | SMTP |
| La gestion des noms de domaine | DNS |
| L'accès à distance | SSH |

Lorsque l'on charge une page web, la couche 7 est le langage que notre navigateur web et le serveur utilisent pour échanger. Comme c'est la couche la plus proche de l'humain, c'est ici que l'on retrouve le plus grand nombre d'attaques (phishing, requête web malveillante, attaque par injection, exploitation des failles des applications).

Les attaques dont on entend le plus parler se situent en couche 7. Plus on monte dans les couches, plus on est proche de l'humain, et l'humain est la couche la plus attaquée de toutes.

## L'encapsulation

**À l'envoi** : l'encapsulation se fait de la couche 7 à 1 et chaque couche agit comme une protection. Ça serait comme une enveloppe dans une enveloppe dans une enveloppe, dans un carton, dans un camion de la poste.

![](images/02-modele-osi-10.png)

**À la réception** : ça marche pareil mais dans le sens inverse.

1. La machine reçoit les données de manière brute à la couche 1.
2. Elle les rassemble en une trame au niveau 2 et lit l'adresse MAC.
3. Elle extrait ces infos pour trouver le paquet au niveau 3 et lit l'adresse IP.
4. Elle extrait ces données pour trouver le segment à la couche 4 et lit le port.
5. Elle continue le déballage jusqu'à la couche 7 : les données d'application d'origine apparaissent et sont livrées au programme approprié.

![](images/02-modele-osi-11.png)

Chaque couche du récepteur ne communique qu'avec sa couche correspondante du côté émetteur, ce qui permet à 2 machines très différentes d'interagir parfaitement.

## Pourquoi les pros connaissent ce modèle par cœur

Il permet aux pros de se comprendre plus rapidement : quand quelqu'un dit « c'est une erreur de couche 7 », celui qui l'écoute sait qu'il parle de la partie logicielle, de l'app, ou du serveur web.

Ça marche pareil pour la classification des attaques. Par exemple, une attaque de déni de service de couche 3 ou 4 inonde le serveur de données brutes, alors qu'une de couche 7 l'inonde de données classées comme légitimes. En parlant par couche, on sait exactement où se situe l'attaque ou le problème. La précision est tout l'intérêt de ce modèle.

## Attention : ce modèle est un peu erroné

C'est un outil pédagogique, pas une science exacte.

![](images/02-modele-osi-13.png)

Dans la réalité :

- Les 3 couches supérieures (7-6-5) se confondent.
- Le chiffrement s'effectue sur plusieurs niveaux et non un seul.
- Le protocole qui fait réellement fonctionner Internet ne se comporte pas réellement sur 7 couches.

Le modèle OSI est un bon résumé, mais la réalité est un peu plus chaotique que 7 boîtes bien rangées. Mais bon, malgré tout, le modèle OSI reste la base.

![](images/02-modele-osi-14.png)

Suite : [Le modèle TCP/IP](03-modele-tcp-ip.md)
