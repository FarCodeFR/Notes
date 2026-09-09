# 📆 <%* tR += window.moment().locale("fr").format("dddd DD MMMM YYYY") %>

  
## 🔁 Routine quotidienne

- [ ] Café
- [ ] Mail

  
## 💀 Priorités du jour



## 📤 Autres tâches



  

## ♻️ Tâches non terminées des jours précédents

<%* const DAILY_FOLDER = "Notes"; const EXCLUDE = ["Templates"]; const SECTIONS = ["Autres tâches", "Tâches non terminées"]; const today = window.moment().format("YYYY-MM-DD"); const isDaily = (f) => /^\d{4}-\d{2}-\d{2}$/.test(f.basename) && !EXCLUDE.some((d) => f.path.startsWith(d + "/")) && (DAILY_FOLDER === "" || f.path.startsWith(DAILY_FOLDER + "/")); const last = app.vault.getMarkdownFiles().filter((f) => isDaily(f) && f.basename < today).sort((a, b) => b.basename.localeCompare(a.basename))[0]; if (!last) { tR += "> [!error] Aucune note quotidienne antérieure trouvée."; } else { const content = await app.vault.read(last); let heading = null; const tasks = []; for (const raw of content.split("\n")) { const h = raw.match(/^#{1,6}\s+(.*)$/); if (h) { heading = h[1].trim(); continue; } if (!heading) { continue; } if (!SECTIONS.some((s) => heading.indexOf(s) !== -1)) { continue; } const line = raw.replace(/^>\s?/, "").trim(); if (line.startsWith("- [ ]") && line.length > 6) { tasks.push(line); } } const uniques = [...new Set(tasks)]; if (uniques.length) { tR += "> [!info] Reporté depuis la note du " + last.basename + "\n\n" + uniques.join("\n"); } else { tR += "> [!info] Aucune tâche non terminée dans la dernière note (" + last.basename + ")."; } } %>

## 📒 Notes