# Le DNS (l'annuaire d'Internet)

Source : https://youtu.be/2ppV7rpv2XY (chapitre 7)

## L'humain utilise des noms, la machine des nombres

![](images/05-dns-01.png)

C'est comme sur notre téléphone : quand on met le nom de quelqu'un au lieu de garder juste son numéro, ça nous permet, à nous humains, de retenir plus facilement quel nom correspond à qui. Le DNS fait la traduction du nom vers l'IP, comme notre téléphone du nom vers le numéro.

## L'étape 0 de toute connexion

![](images/05-dns-02.png)

L'étape 0, c'est une recherche DNS (invisible et rapide). Le DNS intervient dès que l'on appuie sur Entrée, avant même qu'une seule requête soit envoyée au site. Mon PC ne peut pas entamer la conversation sans savoir quelle IP correspond au nom.

Le DNS est une bonne cible : si un attaquant parvient à corrompre cette première traduction, il peut nous envoyer silencieusement au mauvais endroit avant même que l'on fasse quoi que ce soit.

## La recherche DNS

![](images/05-dns-03.png)

Le DNS est un annuaire hiérarchisé et une recherche est une course de relais à travers cette hiérarchie.

1. Mon appareil parle à son assistant (le **resolver récursif**), géré généralement par mon fournisseur d'accès à Internet ou un service public.
2. S'il ne connaît pas la réponse, il demande au **serveur root** (le sommet de l'arbre DNS). Ce serveur ne connaît pas la réponse précise mais sait qui gère la fin du nom de domaine : pour les .com, il redirige vers les serveurs .com, pareil pour les .net…
3. Les serveurs de domaine de premier niveau (TLD) le dirigent vers le serveur faisant autorité pour ce domaine précis.
4. Le **serveur faisant autorité** détient le nom de domaine et renvoie l'IP réelle.

Un exemple par une recherche réelle :

![](images/05-dns-04.png)

Ça marche en 3 questions, de la plus générale à la plus spécifique. Ce qui est cool, c'est que l'annuaire est décentralisé : aucun PC n'a tout le contenu de l'annuaire, mais n'importe quel nom de domaine peut être résolu en quelques millisecondes.

## En termes simples

Le DNS, c'est comme l'assistance de renseignements téléphonique : on donne un nom à un opérateur, il consulte une chaîne d'annuaires classés de national puis régional puis local, jusqu'à trouver le numéro exact, puis nous le communique.

![](images/05-dns-05.png)

Il existe des astuces pour aller plus vite : l'opérateur note les numéros les plus populaires sur un bloc-notes. La prochaine fois, il n'a plus besoin de faire tout le chemin, il regarde son bloc-notes et répond instantanément. Le bloc-notes, c'est le **cache**.

## Cache, TTL et résolveurs publics

La mise en cache est temporaire et comporte une horloge, le **TTL** (time to live). Il indique le nombre de secondes pendant lesquelles un résolveur a le droit de garder la réponse en cache avant de devoir la rechercher à nouveau.

![](images/05-dns-06.png)

Hormis le FAI, il existe des résolveurs publics : 8.8.8.8 (Google), 1.1.1.1 (Cloudflare) ou encore 9.9.9.9 (Quad9). Ils sont souvent plus rapides et certains ajoutent un filtrage de sécurité.

Les types d'enregistrement DNS et leurs cartes de référence :

![](images/05-dns-07.png)

## Le DNS a été construit sans sécurité

![](images/05-dns-08.png)

C'est central mais aussi fragile. Deux exemples :

### Mirai et Dyn (octobre 2016)

Une attaque contre le fournisseur DNS Dyn, qui a montré que le DNS est un point central fragile.

![](images/05-dns-09.png)

### La tortue de mer (Sea Turtle) : le DNS est espionné

Cela est très effrayant : de 2017 à 2019, un groupe financé par un État a méthodiquement compromis les enregistrements DNS d'une quarantaine d'organisations dans 13 pays, dont des gouvernements et des agences de renseignement. Il redirigeait silencieusement le trafic de ses cibles via des serveurs qu'il contrôlait. Il a même parfois trompé des autorités de certification pour qu'elles lui attribuent des certificats valides pour des sites usurpés. Les victimes qui se connectaient semblaient être sur le bon site légitime, mais c'était juste une imitation.

![](images/05-dns-10.png)

## Comment défendre le DNS : 2 défenses pour 2 problèmes différents

![](images/05-dns-11.png)

- **DNSSEC** : comme un sceau de cire inviolable posé sur la réponse. N'importe qui peut encore la lire, mais on peut être certain qu'elle est authentique et qu'elle n'a pas été altérée.
- **DoH / DoT** : comme envoyer une lettre dans une enveloppe opaque scellée. Personne en chemin ne peut la lire, mais on ne peut pas s'assurer qu'elle n'a pas été altérée, et ça ne prouve pas qui a écrit la lettre à l'intérieur.

Dans l'idéal, on souhaite à la fois l'authenticité et la confidentialité.

La bonne nouvelle : le DNS chiffré se généralise à partir de 2026. Les principaux navigateurs web (Chrome, Firefox…) activeront par défaut le DNS chiffré pour la plupart des utilisateurs.

Récap DNS :

![](images/05-dns-12.png)

Suite : [Ports et protocoles](06-ports-et-protocoles.md)
