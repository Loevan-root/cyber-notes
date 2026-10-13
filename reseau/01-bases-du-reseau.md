# Les bases du réseau

Source : https://youtu.be/2ppV7rpv2XY (chapitres 1 et 2)

## Pourquoi le réseau compte en cyber

Là il nous explique ce qu'il se passe quand on fait une recherche sur Google.

![](images/01-bases-du-reseau-01.png)

![](images/01-bases-du-reseau-02.png)

Dans la vidéo, il explique que toutes les attaques dont on a entendu parler utilisent le réseau.

![](images/01-bases-du-reseau-04.png)

Ma remarque : je trouve ce qu'il dit faux, car il y a des attaques physiques qui peuvent être effectuées dans le monde, tel un hacker qui passe avec une USB Rubber Ducky et qui peut collecter des données confidentielles d'une entreprise hors ligne (hors network). Mais bon, je sais qu'il dit ça pour la vidéo.

![](images/01-bases-du-reseau-03.png)

À quoi ça sert de regarder sa vidéo ?

![](images/01-bases-du-reseau-05.png)

Le voc à retenir :

![](images/01-bases-du-reseau-06.png)

## C'est quoi un réseau ?

Un réseau est simplement constitué de deux appareils ou plus capables de communiquer et de partager des données.

![](images/01-bases-du-reseau-07.png)

![](images/01-bases-du-reseau-08.png)

## Switch et routeur

- **Switch** : déplace les données dans un même réseau et utilise l'adresse MAC. C'est le connecteur central au sein d'un réseau local uniquement.

![](images/01-bases-du-reseau-09.png)

- **Routeur** : déplace des données entre les réseaux, comme une poste qui s'occuperait de distribuer nos colis à la bonne adresse (adresse IP).

![](images/01-bases-du-reseau-11.png)

![](images/01-bases-du-reseau-12.png)

## LAN et WAN

- **LAN** (Local Area Network) : un groupe d'appareils qui se situent au même lieu physique et qui partagent un même réseau local. Exemple : mon bureau, mon réseau domestique.
- **WAN** (Wide Area Network, "étendu") : même chose que le LAN mais étendu, longue distance, ville à ville, continent à continent. Le WAN le plus connu, c'est Internet : des petits réseaux locaux interconnectés pour former des réseaux toujours plus vastes jusqu'à arriver à Internet.

![](images/01-bases-du-reseau-10.png)

## Client et serveur

- Le client, c'est celui qui envoie des requêtes (des demandes).
- Le serveur, c'est celui qui répond à ce qui lui est demandé.

Exemple : lorsque j'ouvre un site web, mon appareil est client, c'est lui qui effectue la requête. La machine qui stocke et envoie le site web est serveur, c'est elle qui fournit la réponse.

![](images/01-bases-du-reseau-13.png)

**client → demande / serveur → répond**

## C'est quoi Internet ?

Internet : un réseau de réseaux. Il contient des centaines de milliers de réseaux indépendants gérés par les fournisseurs d'accès à Internet, universités, entreprises…

![](images/01-bases-du-reseau-14.png)

L'indépendance c'est cool, mais c'est plus vulnérable.

## Le voyage des données en paquets

Un paquet, c'est comme l'extérieur d'une enveloppe.

![](images/01-bases-du-reseau-15.png)

- **L'en-tête** : au début, il y a les infos d'adressage. D'où vient le paquet, où il va, quelle adresse IP et quel port (de la source et de la destination), et le combientième paquet il est dans la séquence.
- **Le payload** : c'est le contenu de l'enveloppe.

![](images/01-bases-du-reseau-16.png)

Il est important de séparer le payload et l'en-tête, car l'en-tête doit être public et visible par tous pour que le paquet puisse arriver à la bonne destination, sans que le contenu de l'enveloppe soit lu : seul le destinataire doit pouvoir lire le payload.

Pour protéger le payload, il faut le chiffrer.

Les acteurs physiques qui font tourner tout ça :

![](images/01-bases-du-reseau-17.png)

## La suite

Le modèle OSI, c'est le concept le plus important du réseautage. En fait, le réseau est partagé en plusieurs couches qui séparent les tâches pour effectuer un objectif.

Suite : [Le modèle OSI](02-modele-osi.md)

