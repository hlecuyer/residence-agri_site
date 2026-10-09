# CLAUDE.md — atelier site résidence agricole « En quête d'avenir »

Site one-page statique pour la résidence agricole « En quête d'avenir ».
Cliente : Lou Lecuyer (la sœur d'Hugo). Bénévolat, pas de devis sur ce projet.

**Contexte, statut, échéance et prochaine action : voir `ETAT.md` à la racine.**

---

## Lire dans cet ordre en début de session

1. `ETAT.md` — où on en est, prochaine action
2. `01-brief/brief.md` — tout ce que la cliente a dit (WhatsApp + vocaux transcrits)
3. `01-brief/materia/maquette-actuelle-lou.jpg` — SA maquette (le contenu est dedans,
   le design est à refaire)
4. `01-brief/materia/variantes-design-A-B-C.jpg` — les 3 pistes design avec elle
5. `01-brief/questions-ouvertes.md` — ce qui reste flou

## Périmètre validé (ne pas dériver)

- **Une seule page** (`docs/index.html`), scroll down, mobile-first
- Passe **contenu** : reprendre fidèlement les textes de sa maquette et du rapport
  (`01-brief/materia/invitation-texte.md`) — le contenu est déjà bien, ne pas réécrire
  sans raison ; trancher le « trop de texte » que Lou ressent
- Passe **design** : sortie du « ChatGPT-like » — direction probablement A (naturelle
  et épurée, photographique immersive) ou un mix A/B ; inspirations : Symfaunia,
  Zealandia. Itérer par maquettes HTML validées dans le navigateur par Hugo
- **Section « prochaine résidence »** : la date (ex. 14-15 janvier) doit être
  affichable quand elle existe, masquable sinon, et modifiable facilement par Lou
  (à trancher : fichier de données simple édité par Hugo vs mini-CMS — voir
  `01-brief/questions-ouvertes.md` n°4)
- Contact : `residence.agri@mail.com` (mailto simple en v1, sauf avis contraire)
- Pas de tracker, pas de dépendance lourde. HTML/CSS/JS minimal, GH Pages possible

## Règles de travail

- Les photos de la maquette ChatGPT sont des placeholders : Ne PAS les utiliser comme
  vraies photos. Emplacements marqués `[PHOTO À FOURNIR : …]`
- Les personnes citées (Juliette Young, Estelle Baillan, Emmanuel Ogier) : contenu
  gelé tant que Lou n'a pas confirmé leur accord
- Toute info nouvelle (appel, message, décision prise ailleurs) va dans `ETAT.md`
  tout de suite
- À la fin de toute session, **mettre à jour `ETAT.md`** — systématiquement, comme
  un commit, sans demander

## Hors périmètre (ne pas mélanger)

- Restauration de l'ancien site loulecuyer.com → `~/workspace/site-lou-lecuyer/`
- Devis site Power Shift → autre dossier à créer le moment venu
- L'outil IA POWERSHIFT (8 chercheurs, API open source) → autre sujet

Protocole complet : `/home/hugo/workspace/CLAUDE.md`.

*Maj : 2026-10-09*
