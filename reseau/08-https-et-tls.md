# Le chiffrement : HTTPS et TLS

Source : https://youtu.be/2ppV7rpv2XY (chapitre 10, numéroté ainsi dans mes notes)

![](images/08-https-et-tls-01.png)

## HTTPS = HTTP + TLS

![](images/08-https-et-tls-02.png)

TLS (Transport Layer Security) = couche de transport sécurisée.

Quand on se connecte en HTTPS, TLS offre 3 garanties :

- **Confidentialité** : le contenu est chiffré, donc les personnes qui écoutent ne voient que des caractères brouillés et incompréhensibles.
- **Intégrité** : les données ne peuvent pas être altérées secrètement pendant la transmission sans être détectées.
- **Authenticité** : on peut vérifier que l'on parle bien au bon serveur et non à un imposteur.

## La poignée de main TLS

![](images/08-https-et-tls-03.png)

Quand notre navigateur se connecte de manière sécurisée à un serveur, avant tout échange de données, les 2 machines font un TLS handshake. Cette procédure rapide vise à établir une communication chiffrée.

1. Les 2 parties se mettent d'accord sur la version de TLS et la méthode de chiffrement.
2. Le serveur présente son certificat, une preuve de son authenticité qui atteste son identité.
3. Les 2 font un échange de clés (astucieux) qui leur permet de s'accorder sur une clé secrète partagée sans jamais envoyer cette clé sur le réseau, où elle pourrait être volée.
4. À partir de là, ils utilisent la clé de session pour chiffrer toutes les données.

La version moderne TLS 1.3 fait ça très rapidement, en un seul aller-retour (une fraction de seconde), à chaque fois qu'une connexion sécurisée est établie.

## La garantie d'authenticité

![](images/08-https-et-tls-04.png)

Pour vérifier l'authenticité d'un site, on utilise les **CA** (autorités de certification). C'est une liste de certificats fiables livrée dans notre OS et notre navigateur, qui sert à savoir si un certificat est valide ou non.

Si le certificat est invalide, expiré ou correspond à un nom incorrect, le navigateur affiche un avertissement. C'est parfois la seule chose qui sépare la victime d'une catastrophe.

**Let's Encrypt : le HTTPS partout.** Aujourd'hui 95 % du trafic est en HTTPS, contre seulement 25 % en 2014.

![](images/08-https-et-tls-05.png)

## TLS simplement

![](images/08-https-et-tls-06.png)

TLS, c'est comme un tube blindé et étanche reliant directement notre machine au serveur. Nos données passent à l'intérieur. Tout ce qui se trouve autour du tube peut voir qu'un tube existe et que du trafic circule, mais personne ne peut l'ouvrir pour lire ce qu'il contient. Le tube est bien accroché au bâtiment que l'on souhaite atteindre, comme l'atteste son certificat.

Voilà la confidentialité, l'intégrité et l'authenticité en une image. C'est une protection efficace pour les données en transit, et c'est pour ça qu'on peut se connecter à sa banque en toute sécurité.

## Mythe : HTTPS veut dire site web sûr

Faux. HTTPS ne veut pas dire « de confiance » ou « sûr », ça veut juste dire que le trafic entre moi et le serveur est chiffré.

![](images/08-https-et-tls-07.png)

**HTTPS sécurise la transmission, pas la destination.**

## Ce que TLS ne protège pas

![](images/08-https-et-tls-08.png)

1. Les métadonnées.
2. Ça cache ce que l'on fait, mais pas les sites que l'on visite. TLS protège la transmission mais ne protège en rien le serveur contre le piratage : si la société qui stocke nos données se fait hacker, nos données chiffrées en transit se retrouvent déchiffrées sur son système compromis.
3. TLS protège uniquement les données en mouvement. Les données stockées sur un disque nécessitent un style de chiffrement totalement différent.

**Mon aparté pour le point 2 :** pas vraiment, d'après ce que j'avais vu, certains sites (pas tous, mais les plus gros) hashent nos mots de passe, donc ils ne sont pas en clair. En plus, ils ajoutent des caractères aléatoires à notre mot de passe pour améliorer sa sécurité.

TLS en action — sur un wifi public :

![](images/08-https-et-tls-09.png)

## Une attaque réelle : le détournement BGP de myetherwallet.com

![](images/08-https-et-tls-10.png)

Combinaison de hack sophistiquée : les attaquants ont abusé du système de routage d'Internet (BGP) pour détourner tout le trafic destiné à un site populaire de portefeuilles crypto (myetherwallet.com) en le redirigeant vers un serveur qu'ils contrôlaient. Les victimes entraient la bonne adresse mais se retrouvaient sur la fausse copie faite par l'attaquant.

Comme les attaquants ne possédaient pas le certificat légitime du vrai domaine, le navigateur de chaque victime affichait un avertissement de certificat. Le protocole TLS avait bien fonctionné et avait signalé le problème, mais de nombreux utilisateurs n'ont pas écouté l'avertissement et ont tenté de se connecter. Résultat : en environ 2 h, 150 000 $ de crypto ont été volés par les pirates.

**Leçon :** ne jamais ignorer un avertissement de certificat.

Résumé de HTTPS/TLS :

![](images/08-https-et-tls-11.png)

Suite : [Le trajet d'une requête](09-trajet-dune-requete.md)
