# Le trajet d'une requête, du début à la fin

Source : https://youtu.be/2ppV7rpv2XY (dernier chapitre)

Pour finir, on traque une requête du début à la fin : tout ce qu'on a vu se met bout à bout.

![](images/09-trajet-dune-requete-01.png)

1. **La recherche DNS** : mon PC trouve l'IP qui correspond au nom du site. ([notes DNS](05-dns.md))

![](images/09-trajet-dune-requete-02.png)

2. **La poignée de main TCP** : ouverture du tunnel (SYN, SYN-ACK, ACK). ([notes TCP](07-tcp-et-udp.md))

![](images/09-trajet-dune-requete-03.png)

3. **La poignée de main TLS** : verrouillage du tunnel. ([notes TLS](08-https-et-tls.md))

![](images/09-trajet-dune-requete-04.png)

4. **La requête voyage** : toutes les couches prennent vie (encapsulation, routeurs, NAT…). ([notes OSI](02-modele-osi.md))

![](images/09-trajet-dune-requete-05.png)

5. **La réponse retourne** : 1 clic complété.

![](images/09-trajet-dune-requete-06.png)

## La vision cybersécurité

![](images/09-trajet-dune-requete-07.png)

Chaque étape est une cible possible pour un attaquant :

- DNS : fausses réponses, détournement
- TCP : SYN flood
- TLS : downgrade, SSL striping, faux certificats
- Routage : BGP hijacking
- Réseau local : ARP spoofing

Comprendre le trajet complet, c'est savoir où chercher quand quelque chose ne va pas, côté attaque comme côté défense.

La map :

![](images/09-trajet-dune-requete-08.png)

---

Retour au [sommaire](../README.md)
