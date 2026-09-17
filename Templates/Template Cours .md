<%*
/* TEMPLATE COURS - Templater
   Cree la note, la range dans Cours/<Matiere>/ et la renomme. */

const RACINE = "Cours";

// Adapte cette liste a tes modules
const MATIERES = [
  "Angular",
  "SolidJS",
  "Java / Spring Boot",
  "TypeScript",
  "Architecture logicielle",
  "UX / UI",
  "Gestion de projet",
  "Anglais",
  "Flutter"
  "Memoire",
];

const TYPES = ["Cours", "TD", "TP", "Projet", "Conference", "Revision"];

const BAD = ["\\", "/", ":", "*", "?", "<", ">", "|", "#", "^", "[", "]", String.fromCharCode(34)];
const clean = function (s) {
  let out = String(s);
  for (const c of BAD) { out = out.split(c).join("-"); }
  return out.trim();
};

/* --- Saisie --- */
let matiere = await tp.system.suggester(
  (m) => m,
  MATIERES.concat("+ Autre..."),
  false,
  "Matiere ?"
);
if (!matiere) { return; }
if (matiere === "+ Autre...") {
  matiere = await tp.system.prompt("Nom de la matiere");
  if (!matiere) { return; }
}

let type = await tp.system.suggester((t) => t, TYPES, false, "Type de seance ?");
if (!type) { type = "Cours"; }

let sujet = await tp.system.prompt("Sujet de la seance (optionnel)");
if (!sujet) { sujet = ""; }

let prof = await tp.system.prompt("Intervenant (optionnel)");
if (!prof) { prof = ""; }

/* --- Dates et chemins --- */
const date = window.moment().format("YYYY-MM-DD");
const jour = window.moment().locale("fr").format("dddd DD MMMM YYYY");
const slug = clean(matiere);
const dossier = RACINE + "/" + slug;
const titre = sujet ? clean(date + " - " + slug + " - " + sujet) : clean(date + " - " + slug);

/* --- Tag a partir de la matiere --- */
let brut = "";
for (const ch of slug.toLowerCase()) {
  const ok = (ch >= "a" && ch <= "z") || (ch >= "0" && ch <= "9");
  brut += ok ? ch : "-";
}
const tag = brut.split("-").filter(Boolean).join("-");

/* --- Dossier --- */
if (!app.vault.getAbstractFileByPath(dossier)) {
  try { await app.vault.createFolder(dossier); } catch (e) {}
}

/* --- Seance precedente de la meme matiere --- */
const precedentes = app.vault
  .getMarkdownFiles()
  .filter((f) => f.path.startsWith(dossier + "/") && f.basename !== titre)
  .sort((a, b) => b.basename.localeCompare(a.basename));
const lienPrec = precedentes.length
  ? "[[" + precedentes[0].basename + "]]"
  : "_aucune seance anterieure_";

/* --- Lignes calculees --- */
const h1 = sujet ? sujet : matiere;
const ligneProf = prof ? "\n> Intervenant : " + prof : "";

await tp.file.move(dossier + "/" + titre);
-%>
---
matiere: <% matiere %>
type: <% type %>
date: <% date %>
intervenant: <% prof %>
statut: brouillon
tags:
  - cours
  - <% tag %>
---

# <% h1 %>

> [!abstract] <% type %> - <% matiere %>
> 📆 <% jour %><% ligneProf %>
> ⬅️ Séance précédente : <% lienPrec %>

## 🎯 Objectifs de la séance

- 

## 📝 Notes

### 

## 💡 Points clés à retenir

- 

## ❓ Questions / à revoir

- [ ] 

## ✅ Autres tâches

- [ ] 

## 📤 Rendus & deadlines

- [ ] 

## 🔗 Ressources

- 
