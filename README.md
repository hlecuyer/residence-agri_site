# Template site presta — mode d'emploi

Squelette à dupliquer pour chaque nouveau client.

## Usage

```bash
cp -r ~/workspace/template-site-presta ~/workspace/site-{nom-client}
cd ~/workspace/site-{nom-client}
```

Puis remplir au fur et à mesure des étapes.

## Structure

```
site-{client}/
├── docs/                    # Site web production — déployé tel quel sur GH Pages
│   ├── index.html
│   ├── styles.css
│   ├── script.js
│   └── assets/
├── 00-commercial/           # Devis, CGV, factures (privé, gitignored)
├── 01-brief/                # Notes entretien, mail brief, réponses (privé)
├── 02-design/               # Prompts Claude Design, sorties, design-system (privé)
├── 03-livraison/            # QA, passation (privé)
├── 99-retrospective.md      # Debrief fin de projet (privé)
├── .gitignore               # Ignore tous les dossiers privés
└── README.md                # README public du site
```

## Convention clé

**`docs/` est à la racine** car GitHub Pages déploie depuis `/` ou `/docs` d'une branche — pas de subdir custom. En mettant `docs/` directement à la racine, on évite toute étape de déplacement au moment du déploiement.

Le `.gitignore` à la racine du template **ignore tous les dossiers de tracking projet** (`00-commercial/`, `01-brief/`, etc.). Donc quand on fait `git init` + push vers GitHub, seuls `docs/` + `README.md` + assets publics se retrouvent sur le repo public. Le tracking reste local et privé.

## Étape par étape

| Étape | Fichier(s) à remplir |
|---|---|
| Entretien initial | `01-brief/entretien-initial.md` |
| Devis + signature | `00-commercial/devis.md` |
| Mail brief envoyé | `01-brief/mail-brief-envoye.md` |
| Réponse client | `01-brief/reponse-client.md` |
| 2e entretien (si besoin) | `01-brief/second-entretien.md` |
| Pilotage Claude Design | `02-design/prompts-utilises.md`, outputs dans `02-design/wireframe/` et `02-design/highfi/` |
| Design system retenu | `02-design/design-system.md` |
| Code | `docs/` (à la racine) |
| QA pré-livraison | `03-livraison/qa-rapport.md` |
| Passation client | `03-livraison/passation.md` |
| Rétrospective fin de projet | `99-retrospective.md` |

## Référentiel

Le **référentiel méthodologique** (méthodos, prompts génériques, CGV, checklists) est dans `~/workspace/framework-presta/`. Ne pas copier — référencer par chemin absolu si besoin.

## Init Git + déploiement GH Pages

Au moment de créer le repo de production :

```bash
cd ~/workspace/site-{client}
git init
git add .
git commit -m "feat: initial site {client}"
gh repo create {client}_site --public --source=. --remote=origin --push
gh api -X POST 'repos/hlecuyer/{client}_site/pages' \
  -f 'source[branch]=master' \
  -f 'source[path]=/docs'
```

Le `.gitignore` du template empêche les dossiers privés d'être pushés. Le repo public ne contiendra que `docs/` + README.

## Convention

- Pas de date dans les noms de fichiers (la date va dans le contenu)
- Si plusieurs versions d'un artefact : `mail-brief-envoye-v2.md` etc.
- Tout en markdown sauf le code dans `docs/` et les binaires
