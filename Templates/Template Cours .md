<%*
// TEMPLATE COURS - Templater
const RACINE = "Cours";
const MATIERES = [
  "Angular", "SolidJS", "Java / Spring Boot", "TypeScript",
  "Architecture logicielle", "UX / UI", "Gestion de projet",
  "Anglais", "Flutter", "Memoire", "PFE",
];
const TYPES = ["Cours", "TD", "TP", "Projet", "Conference", "Revision"];
const NL = String.fromCharCode(10);
const BAD = [String.fromCharCode(92), "/", ":", String.fromCharCode(42), "?", "<", ">", "|", "#", "^", "[", "]", String.fromCharCode(34)];
const clean = function (s) {
  let out = String(s);
  for (const c of BAD) { out = out.split(c).join("-"); }
  return out.trim();
};

// --- Saisie ---
let matiere = await tp.system.suggester((m) => m, MATIERES.concat("+ Autre..."), false, "Matiere ?");
if (!matiere) { return; }
if (matiere === "+ Autre...") {
  matiere = await tp.system.prompt("Nom de la matiere");
  if (!matiere) { return; }
}
let type = await tp.system.suggester((t) => t, TYPES, false, "Type de seance ?");
if (!type) { type = "Cours"; }
const sujet = (await tp.system.prompt("Sujet de la seance (optionnel)")) || "";
const prof = (await tp.system.prompt("Intervenant (optionnel)")) || "";

// --- Dates et chemins ---
const date = window.moment().format("YYYY-MM-DD");
const jour = window.moment().locale("fr").format("dddd DD MMMM YYYY");
const slug = clean(matiere);
const dossier = RACINE + "/" + slug;
const titre = sujet ? clean(date + " - " + slug + " - " + sujet) : clean(date + " - " + slug);

// --- Tag ---
let brut = "";
for (const ch of slug.toLowerCase()) {
  const ok = (ch >= "a" && ch <= "z") || (ch >= "0" && ch <= "9");
  brut += ok ? ch : "-";
}
const tag = brut.split("-").filter(Boolean).join("-");

// --- Dossier ---
if (!app.vault.getAbstractFileByPath(dossier)) {
  try { await app.vault.createFolder(dossier); } catch (e) {}
}

// --- Seance precedente (lien cliquable) ---
const precedentes = app.vault.getMarkdownFiles()
  .filter((f) => f.path.startsWith(dossier + "/") && f.basename !== titre)
  .sort((a, b) => b.basename.localeCompare(a.basename));
const OPEN = "[".repeat(2);
const CLOSE = "]".repeat(2);
const lienPrec = precedentes.length
  ? OPEN + precedentes[0].path.slice(0, -3) + "|" + precedentes[0].basename + CLOSE
  : "aucune séance antérieure";

const h1 = sujet ? sujet : matiere;
const ligneProf = prof ? NL + "> Intervenant : " + prof : "";

// --- Requete Tasks (taches non terminees de la matiere) ---
const F = String.fromCharCode(96).repeat(3); 

const requete = F + "tasks" + NL + "not done" + NL + "path includes " + dossier + NL + "path does not include " + titre + NL + "heading does not include Rendus" + NL + "sort by due" + NL + "hide toolbar" + NL + F;

const requete2 = F + "tasks" + NL + "not done" + NL + "path includes " + dossier + NL + "path does not include " + titre + NL + "heading includes Rendus" + NL + "sort by due" + NL + "hide toolbar" + NL + F;

await tp.file.move(dossier + "/" + titre);

tR += `---
matiere: ${matiere}
type: ${type}
date: ${date}
intervenant: ${prof}
statut: brouillon
tags:
  - cours
  - ${tag}
---

# ${h1}
${type} - ${matiere}
📆 ${jour}${ligneProf}
⬅️ Séance précédente : ${lienPrec}

## 🎯 Objectifs de la séance
- 

## 📝 Notes

## 💡 Points clés à retenir
- 

## ❓ Questions / à revoir
- 

## ✅ Autres tâches
- [ ] 

## 📌 Tâches non terminées (séances précédentes)
${requete}

## 📤 Rendus & deadlines
${requete2}

## 🔗 Ressources
- 
`;
-%>