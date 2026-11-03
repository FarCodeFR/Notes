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
⬅️ Séance précédente : aucune séance antérieure

## 🎯 Objectifs de la séance
- 

## 📝 Notes

## 💡 Points clés à retenir
- Bonjourlafuite.eu.org pour voir les derniers sites ou les données ont fuitées 


<font color="#00b050">DITC</font>

	D : Disponibilité
	I : Intégrité
	T : Confidentialité
	C : Traçabilité


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

Robot qui navigue et cherche des failles ou avec SBM viewer


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
	Tampering / Intégrité
	Repudiation / Non-répudiation
	Information disclosure / Confidentialité
	Denial of service / Disponibilité
	Elevation of privilege / Autorisation


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



## ❓ Questions / à revoir
- Vérifier comment son stocker les secrets/Token 
- Vérifier les vulnérabilités avec npm audit ou SonarQube

## ✅ Autres tâches
- [ ] 

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
