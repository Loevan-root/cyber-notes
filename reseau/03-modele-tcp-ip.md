# Le modèle TCP/IP

Source : https://youtu.be/2ppV7rpv2XY (chapitre 4)

Le modèle qui fait réellement fonctionner Internet. Il fonctionne grâce à 4 couches.

![](images/03-modele-tcp-ip-01.png)

Ce modèle tire son nom des 2 protocoles les plus importants : TCP et IP.

- Le modèle OSI est le schéma pédagogique.
- Le modèle TCP/IP, c'est la réalité technique.

Les 2, c'est à peu près la même chose mais ils décrivent la chose avec des résolutions différentes. Le modèle TCP/IP regroupe juste quelques couches du modèle OSI en passant de 7 à 4 couches.

**OSI = théorique / TCP/IP = pratique**

## Les 4 couches de TCP/IP

![](images/03-modele-tcp-ip-02.png)

| Couche | Rôle |
|---|---|
| 4. Application | Tout ce avec quoi on interagit (HTTPS, DNS, email, SSH et le chiffrement TLS) |
| 3. Transport | TCP et UDP gèrent la connexion et les ports |
| 2. Internet | IP gère l'adressage et le routage sur les réseaux |
| 1. Liaison | La transmission physique et la distribution locale : les câbles, le wifi et les adresses MAC |

Correspondance entre OSI et TCP/IP :

![](images/03-modele-tcp-ip-03.png)

## Les protocoles de la couche application

- **HTTP/HTTPS** : permet d'afficher des pages web.
- **DNS** : résout les noms en adresses.
- **SMTP, POP3, IMAP** : permettent de déplacer les mails.
- **SSH** : accès à distance sécurisé.
- **TLS** : assure le chiffrement.

![](images/03-modele-tcp-ip-04.png)

## Le cœur : TCP + IP

Les 2 couches intermédiaires constituent le moteur de ce modèle.

- La couche **transport** exécute TCP et UDP : ça gère la conversation proprement entre 2 machines en garantissant une livraison fiable.
- La couche **Internet** exécute le protocole IP (le système d'adressage et de routage), ce qui permet d'acheminer des paquets à n'importe quel appareil sur terre.

![](images/03-modele-tcp-ip-05.png)

Ensemble, TCP et IP forment le duo TCP/IP, ce qui compose le réseautage mondial. Si on comprend ça, on comprend littéralement le cœur d'Internet.

Le passage de réseau local à Internet :

![](images/03-modele-tcp-ip-06.png)

## Aparté

J'ai vu brièvement les différents chapitres de la vidéo et je me suis rendu compte que j'ai déjà vu le reste, ou du moins aperçu le concept en cours (broadcast, masque de sous-réseau…). Pour la suite, je ne prends en note que ce que je ne connais pas, mais en suivant le fil des chapitres. Mes notes sont donc moins complètes que la vidéo entière : le lien est en haut de chaque fichier si tu veux voir les principes en profondeur.

Suite : [IPv4, NAT et sous-réseaux](04-ipv4-nat-sous-reseaux.md)

![](images/03-modele-tcp-ip-07.png)
