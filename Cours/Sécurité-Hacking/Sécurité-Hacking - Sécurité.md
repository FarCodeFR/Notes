---
matiere: Sécurité/Haking
type: Cours
date: 2026-11-02
intervenant:
statut: brouillon
tags:
  - cours
  - sécurité-hacking
---

# Sécurité
Cours - Sécurité/Haking
📆 lundi 02 novembre 2026
⬅️ Séance précédente : [After](obsidian://open?vault=Notes&file=Cours%2FS%C3%A9curit%C3%A9-Hacking%2F2026-11-06%20-%20S%C3%A9curit%C3%A9-Hacking%20-%20D%C3%A9fense)
## 🎯 Objectifs de la séance
- 

## 📝 Notes

## 💡 Points clés à retenir
- Bonjourlafuite.eu.org pour voir les derniers sites ou les données ont fuitées 


<font color="#00b050">DITC</font>

	D : Disponibilité
	I : Intégrité
	T : Traçabilité
	C : Confidentialité


<font color="#00b050">Gold Standard </font>

	Authentification
Sur ce que l'on sait 
Sur ce que l'on a
Sur ce que l'on est

	Autorisation
La personne a-t-elle le droit sur cet objet ? 

	Audit
Qu'a décidé le garde, pour qui, pourquoi ? 


<font color="#00b050">CVE</font> [Lien](https://www.cve.org/)

C'est l'identifiant unique d'une vulnérabilité précise.
Un catalogue public qui attribue des numéros d'identification uniques pour chaque faille de sécurité


<font color="#00b050">CVSS</font> [Lien](https://www.first.org/cvss/calculator/4.0)

Un système de notation numérique et d'évaluation de la gravité
Calculateur du système d'évaluation des vulnérabilités communes (CVSS) version 4.0


<font color="#00b050">Shodan</font>  [Lien](https://www.shodan.io/)  + <font color="#00b050">Exploit-db</font>  [Lien](https://www.exploit-db.com/)

Robot qui navigue et cherche des failles et SBM viewer


<font color="#00b050">SSDLC</font>

<font color="#00b050">SCCTDE</font>
Chaque phase arrête ses propres défauts 

	Spécification
	Conception
	Codage
	Tests
	Déploiement
	Exploitation


<font color="#00b050">Trouver plus tôt avant de merge</font>

	Injection
SAST, Lint, Revue de code

	Dépendance vulnérable
SCA dans la PR

	Faille d'autorisation
Tests d'autorisation, middleware central

	Abus métier
Exigences, threat modeling

	Configuration cloud
Scan de l'Iac


<font color="#00b050">Safe Coding : rendre l'erreur rare et visible</font>

	Entrées
	Requêtes
	Navigateur
	Echapatoire


<font color="#00b050">Métier de la CyberSécurité</font>

	Ingénieur AppSec
	Architecte sécurité
	Security Champion
	Ingénieur DevSecOps
	Pentester, red team
	Analyste SOC
	RSSI


<font color="#00b050">Six menaces, Six propriétés </font>


	Spoofing / Authenticité
Un attaquant se fait passer pour un utilisateur légitime avec un mot de passe volé, ou envoie un faux e-mail de phishing qui imite ta banque.

	Tampering / Intégrité
Modifier le prix d’un article dans la requête HTTP (ex. passer 100 € à 1 €) avant qu’elle n’arrive au serveur.

	Repudiation / Non-répudiation
Un utilisateur supprime un compte client puis nie l’avoir fait, et aucun log n’existe pour prouver le contraire.

	Information disclosure / Confidentialité
Une injection SQL qui expose la table des utilisateurs, ou une API qui renvoie trop de champs (mots de passe hashés, e-mails).

	Denial of service / Disponibilité // DDOS
Un botnet inonde le serveur de requêtes (DDoS) jusqu’à ce que le site ne réponde plus.

	Elevation of privilege / Autorisation
Un utilisateur standard modifie l’ID dans l’URL (`/admin/users/1`) et accède à des fonctions réservées aux administrateurs.


<font color="#00b050">Abuse case : </font>

C'est l'user story d'un acteur malveillant


<font color="#00b050">YesWeHack :</font> [Lien](https://www.yeswehack.com/fr)

Site recherche de bug bounty 

<font color="#00b050">Information Clé PRIVE clé PUBLIC </font>

- **Connexions sécurisées (HTTPS / SSL-TLS) :** Le serveur utilise sa clé privée pour garantir la sécurité de la session, tandis que la clé publique est intégrée au certificat numérique consulté par votre navigateur.

- **Accès aux serveurs (SSH) :** La clé publique est placée sur le serveur distant, et la clé privée reste sur votre ordinateur pour prouver votre identité.

- **Cryptomonnaies :** La clé publique fait office d'adresse pour recevoir des fonds, et la clé privée sert à signer et valider les transactions


<font color="#00b050">Anti-pattern</font>

	Client-Side Enforcement
Le serveur s'en remet au client pour un contrôle qui le protège

	Trust Boundary Violation
Données vérifiées et brutes dans la même structure

	Untrusted Control Sphere
Un composant privilégié agit pour un appelant qui ne l'est pas.

	Confused Deputy
Un tiers décide du code qui s'execute

	Unmaintained Component
Une faille que plus personne ne peut corriger


<font color="#00b050">Deux types de requêtes HTTP </font>

	Les requêtes Top-Level 
	Les requêtes XHR/FETCH


<font color="#00b050">WebStorage / Cookie </font>

> Les cookies sont plus sûrs contre le vol de token par XSS **s’ils ont le flag `HttpOnly`** : le JavaScript ne peut pas les lire, donc un script injecté ne peut pas les récupérer. Le `localStorage`, lui, est accessible à n’importe quel JS exécuté sur la page, y compris un script malveillant injecté par XSS. Dans les deux cas, les données restent propres au navigateur de l’utilisateur et isolées par origine : un autre site ne peut pas les lire.

**À retenir :**

- Un cookie **sans** `HttpOnly` est lisible en JS, comme le `localStorage`.
- Il faut ajouter `Secure` (HTTPS uniquement) et `SameSite` (contre le CSRF).
- `HttpOnly` empêche le **vol** du token, pas les requêtes faites au nom de l’utilisateur pendant la XSS.
- Les cookies exposent au CSRF, pas le `localStorage`.


<font color="#00b050">RLS / Row Level Security </font>

N'accéder qu'a ses propres données par exemple discord chaque chanel accède à leurs données.


<font color="#00b050">Déléguer un accès au Drive </font> OAuth

![[Capture d’écran 2026-11-04 à 10.35.09.png]]

![[Capture d’écran 2026-11-04 à 10.35.40.png]]


<font color="#00b050">OIDC est une surcouche à OAuth </font>

![[Capture d’écran 2026-11-04 à 10.36.35 1.png]]

![[Capture d’écran 2026-11-04 à 10.37.08.png]]


<font color="#00b050">SSO</font>

Permet de se connecter une seule fois pour accéder à plusieurs applicaitons 


<font color="#00b050">SameSite</font> Cookies disponible

	None
Toujours, y compris depuis d’autres sites (iframes, requêtes cross-site)

	Lux
Même site, plus les clics sur un lien depuis un autre site (navigation GET)

	Strict
Uniquement  les requêtes venant du même site


![[Capture d’écran 2026-11-04 à 12.16.35.png]]


<font color="#00b050">Outils FFUF apt </font> [Lien](https://www.kali.org/tools/ffuf/) pour tester different lien avec des mots clé

## ❓ Questions / à revoir
- Vérifier comment son stocker les secrets/Token 
- Vérifier les vulnérabilités avec npm audit ou SonarQube

## ✅ Autres tâches

## 📌 Tâches non terminées (séances précédentes)
```tasks
not done
path includes Cours/Sécurité-Haking
path does not include 2026-11-02 - Sécurité-Haking - Sécurité
heading does not include Rendus
sort by due
hide toolbar
```

## 📤 Rendus & deadlines
```tasks
not done
path includes Cours/Sécurité-Haking
path does not include 2026-11-02 - Sécurité-Haking - Sécurité
heading includes Rendus
sort by due
hide toolbar
```

## 🔗 Ressources
- 
