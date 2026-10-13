# IPv4, NAT et sous-réseaux

Source : https://youtu.be/2ppV7rpv2XY (chapitres 5 et 6)

## Contourner la limite de l'IPv4

L'IPv4 :

![](images/04-ipv4-nat-sous-reseaux-01.png)

![](images/04-ipv4-nat-sous-reseaux-02.png)

Les adresses IPv4 sont limitées et elles se sont épuisées.

![](images/04-ipv4-nat-sous-reseaux-03.png)

Pour contourner ça, on a séparé les IP entre réseau **public** et **privé**.

![](images/04-ipv4-nat-sous-reseaux-04.png)

Pour un réseau privé, il y a 3 grosses plages d'IP locales, mais non routables sur l'Internet public :

- Le premier bloc commence par **10**
- Le deuxième bloc va de **172.16 à 172.31**
- Le troisième bloc, le plus courant : **192.168**

Ce sont des plages d'adresses privées réutilisées au sein de milliers de réseaux distincts à travers le monde. Ces adresses n'apparaissent jamais en ligne : seul notre routeur possède une adresse IP publique.

## NAT (Network Address Translation)

C'est grâce au NAT qu'Internet ne s'est pas arrêté brutalement en 2011.

![](images/04-ipv4-nat-sous-reseaux-05.png)

En gros, quand mon PC envoie un paquet à un serveur, mon routeur le réécrit en y mettant son adresse IP publique. Quand il reçoit la réponse, il se souvient de quel appareil interne l'avait envoyé et lui renvoie la réponse.

**Métaphore : le réceptionniste.** Dans cette métaphore, la table de routage serait le journal de bord.

![](images/04-ipv4-nat-sous-reseaux-06.png)

### Le NAT n'est pas un firewall

Le NAT cache les adresses privées, mais il ne remplace pas un pare-feu.

![](images/04-ipv4-nat-sous-reseaux-07.png)

L'adressage à connaître :

![](images/04-ipv4-nat-sous-reseaux-08.png)

### Les IP publiques sont constamment scannées

Tout Internet est constamment scanné par des botnets qui ne font que cartographier le web à la recherche de ports ouverts.

![](images/04-ipv4-nat-sous-reseaux-09.png)

Récap IPv4 :

![](images/04-ipv4-nat-sous-reseaux-10.png)

![](images/04-ipv4-nat-sous-reseaux-11.png)

## Le subnetting (sous-réseaux)

Le subnetting, c'est la division d'un réseau en plusieurs sous-réseaux, avec les masques de sous-réseau et la notation CIDR (par exemple /24).

![](images/04-ipv4-nat-sous-reseaux-12.png)
![](images/04-ipv4-nat-sous-reseaux-13.png)
![](images/04-ipv4-nat-sous-reseaux-14.png)

**Simplification :** imagine une organisation comme une ville et les sous-réseaux comme des quartiers fortifiés. À l'intérieur d'un quartier (par exemple le quartier ingénieur), tout le monde peut communiquer. Pareil pour les autres quartiers. Mais quand il s'agit de passer d'un quartier à un autre, il faut passer par la porte et donc respecter certaines règles qui disent si c'est autorisé ou non. C'est ici qu'intervient le pare-feu.

C'est ce qu'on appelle la **segmentation** : elle limite les dégâts en cas de brèche.

![](images/04-ipv4-nat-sous-reseaux-15.png)

## IPv6 — le réglage permanent

![](images/04-ipv4-nat-sous-reseaux-16.png)

![](images/04-ipv4-nat-sous-reseaux-17.png)

IPv6 rend le NAT obsolète :

![](images/04-ipv4-nat-sous-reseaux-18.png)

L'usage de l'IPv6 en 2026 :

![](images/04-ipv4-nat-sous-reseaux-19.png)

Les avantages et inconvénients de l'IPv6 niveau cybersécurité :

![](images/04-ipv4-nat-sous-reseaux-20.png)

Récap adressage :

![](images/04-ipv4-nat-sous-reseaux-21.png)

Suite : [Le DNS](05-dns.md)
