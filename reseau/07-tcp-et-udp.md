# TCP et UDP

Source : https://youtu.be/2ppV7rpv2XY (chapitre 9)

## 2 manières de transmettre des données

![](images/07-tcp-et-udp-01.png)

- **TCP** (protocole de contrôle de transmission) : fiable, précis, il garantit que nos données arrivent complètes et dans l'ordre.

![](images/07-tcp-et-udp-05.png)

- **UDP** (User Datagram Protocol) : rapide, léger, mais il transmet les données sans certitude ni garantie.

Théoriquement, aucun n'est mieux que l'autre : ce sont 2 outils pour 2 tâches différentes.

## TCP : la fiabilité

![](images/07-tcp-et-udp-02.png)

Avant tout échange, les 2 machines établissent d'abord une connexion formelle. Chaque paquet envoyé doit faire l'objet d'un accusé de réception par le destinataire. Si ce n'est pas le cas, l'expéditeur considère que le paquet est perdu et le renvoie.

### La poignée de main en 3 étapes (handshake)

1. **SYN** : le client envoie un paquet SYN (synchronize) qui dit qu'il veut démarrer une conversation.
2. **SYN-ACK** : le serveur répond qu'il prend note de la demande et qu'il est également prêt.
3. **ACK** : le client renvoie un ACK (OK, commençons).

Après ces 3 messages, une connexion fiable est établie. Ces messages confirment que l'autre est présent, prêt et synchronisé.

### Exemple d'attaque : le déluge de SYN (SYN flood)

Cette attaque abuse de la poignée de main.

![](images/07-tcp-et-udp-03.png)
![](images/07-tcp-et-udp-04.png)

Quand le serveur reçoit une requête SYN et y répond, il réserve un peu de mémoire pour se souvenir de cette connexion semi-ouverte pendant qu'il attend l'ACK final du client.

L'attaque marche si un attaquant envoie des milliers, voire des millions de requêtes SYN mais n'envoie jamais les ACK finaux. Le serveur alloue consciencieusement des ressources à ces requêtes qui n'aboutiront jamais. Ça sature la table des connexions et le serveur devient hors service, y compris pour les utilisateurs légitimes.

## UDP : rapide mais pas fiable

Il établit une connexion sans poignée de main, sans installation ni connexion formelle du tout. Il se contente d'envoyer ses paquets à destination.

Quand on utilise l'un ou l'autre :

![](images/07-tcp-et-udp-06.png)

## QUIC : le nouveau protocole

QUIC est un mélange de la fiabilité de TCP et de la rapidité d'UDP, car il s'émancipe du handshake.

QUIC reprend la base d'UDP (rapide et léger) et y ajoute la fiabilité, l'ordonnancement et même le chiffrement intégrés, le tout d'une manière plus intelligente et plus rapide que TCP classique.

Internet évolue dans ce sens : la version 3 du protocole HTTP (la plus récente version du protocole web) fonctionne sur QUIC, ce qui signifie qu'elle fonctionne sur UDP. 40 % de tous les sites web fonctionnent sur QUIC.

Debunking de mythe :

![](images/07-tcp-et-udp-07.png)

Rappel TCP/UDP :

![](images/07-tcp-et-udp-08.png)

Suite : [HTTPS et TLS](08-https-et-tls.md)
