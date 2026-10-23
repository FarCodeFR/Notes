---
matiere: Stratégie technique
type: Cours
date: 2026-10-23
intervenant: 
statut: brouillon
tags:
  - cours
  - strat-gie-technique
---

# Stratégie technique
Cours - Stratégie technique
📆 vendredi 23 octobre 2026
⬅️ Séance précédente : aucune seance anterieure

## 🎯 Objectifs de la séance
- 

## 📝 Notes

## 💡 Points clés à retenir
**ADR (Architecture Decision Record)** : document court, versionné avec le code, qui enregistre une décision et son contexte. Il permet à la prochaine équipe de comprendre _pourquoi_ ce choix a été fait.

Structure d’un ADR :

- Titre et numéro
- Statut : Proposé, Accepté, Remplacé (ou Déprécié)
- Date
- Contexte et contraintes
- Options envisagées
- Décision retenue
- Conséquences, positives et négatives

**Architecture hexagonale** : on place le métier au centre, isolé de tout le reste (base de données, framework, API externes). Le métier ne dépend que de « ports » (interfaces), et les « adaptateurs » les implémentent. On peut ainsi tester ou changer une brique technique sans tout casser.

**Principe** : on choisit un seul style d’architecture pour le projet, mais on peut combiner plusieurs design patterns selon les besoins.

**Organisation** :

- Dossier `docs/adr/`
- Nommage : `0001-choix-de-la-stack-technique.md`, `0002-…`
- Un ADR par décision structurante. Un ADR accepté n’est jamais modifié : on en écrit un nouveau qui le remplace, avec la date et le lien entre les deux.

## ❓ Questions / à revoir

## ✅ Autres tâches
- [ ] Choix d'architecture + créer les ADR
- [ ] Concevoir l'architecture cible du cas 6mois 1an 3ans ( budget, loyer : pas aller trop loin), l'évolution au bout d'un an puis à 3 ans une cible plutôt assumé microservice et l'organisation, nombre de dev, salaire brute pour l'employeur, ce que l'on expert même si il y'aura des modifications, ADR sur 1 et 3 ans car 6 mois sont déjà réalisé

- [ ] 6 mois ce que vous construisez maintenant, avec l'équipe et le budget réels 
- [ ] 1 ans les extractions et renforts prévus, et leurs conditions de déclenchement.
- [ ] 3 ans La cible assumée, est ce que l'architecture d'aujourd'hui doit lui laisser ouvert

## 📌 Tâches non terminées (séances précédentes)
```tasks
not done
path includes Cours/Stratégie technique
path does not include 2026-10-23 - Stratégie technique
heading does not include Rendus
sort by due
hide toolbar
```

## 📤 Rendus & deadlines
```tasks
not done
path includes Cours/Stratégie technique
path does not include 2026-10-23 - Stratégie technique
heading includes Rendus
sort by due
hide toolbar
```

## 🔗 Ressources
- 
