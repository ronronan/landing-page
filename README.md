# landing-page

Site personnel de [ronronan](https://github.com/ronronan), accessible sur [3rm.fr](https://3rm.fr).

Un blog statique construit avec [Hugo](https://gohugo.io) et le thème [PaperMod](https://github.com/adityatelange/hugo-PaperMod). Pas de base de données, pas de runtime — juste du Markdown transformé en HTML.

## Stack

| Composant  | Choix                    |
| ---------- | ------------------------ |
| Générateur | Hugo                     |
| Thème      | PaperMod (submodule git) |
| Contenu    | Markdown                 |
| Langue     | Français                 |

## Prérequis

- [Hugo](https://gohugo.io/installation/) (version étendue recommandée)
- Git

## Démarrage rapide

```bash
# Cloner avec le submodule du thème
git clone --recurse-submodules https://github.com/ronronan/landing-page.git
cd landing-page

# Lancer le serveur de développement
hugo server -D

# Ouvrir http://localhost:1313
```

> Si le dépôt a déjà été cloné sans `--recurse-submodules` :
>
> ```bash
> git submodule update --init --recursive
> ```

## Contenu

Les articles sont dans `content/posts/`. Pour en créer un nouveau :

```bash
hugo new posts/mon-article.md
```

Éditer ensuite le fichier généré dans `content/posts/`.

## Build

```bash
hugo --minify
```

Le site généré est dans `public/`. Ce dossier est exclu du dépôt (`.gitignore`).

## Structure

```
.
├── content/
│   └── posts/        # Articles du blog
├── themes/
│   └── PaperMod/     # Thème (submodule git)
├── static/           # Fichiers statiques (images, fonts…)
├── layouts/          # Surcharges de templates
├── i18n/             # Traductions
└── hugo.yaml         # Configuration Hugo
```

## Configuration

Tout se passe dans `hugo.yaml`. Les paramètres notables :

- `baseURL` — à ajuster si le domaine change
- `params.defaultTheme` — `auto`, `light` ou `dark`
- `params.socialIcons` — liens vers les profils externes
