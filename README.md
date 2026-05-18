# Déployer cette page sur GitHub Pages (sécurisé)

Ce dépôt contient une page statique (`index.html`, `styles.css`). Voici les étapes recommandées pour déployer et sécuriser.

Commandes locales (si Git n'est pas initialisé) :

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
```

Créer le repo distant et pousser (option A — avec GitHub CLI) :

```bash
# installez GitHub CLI depuis https://cli.github.com/
gh repo create <OWNER>/<REPO> --public --source=. --remote=origin --push
```

Option B — sans `gh` :

```bash
# créez un repo sur github.com (New repository), puis :
git remote add origin git@github.com:USERNAME/REPO.git
git push -u origin main
```

Après push, GitHub Actions déploiera automatiquement sur GitHub Pages (branch `main`).

Bonnes pratiques sécurité (résumé) :
- Ne jamais committer de secrets (clé API, `.env`).
- Utiliser les *GitHub Secrets* pour les clés nécessaires aux workflows.
- Activer *Dependabot* et *vulnerability alerts* dans les settings.
- Activer *Branch protection* pour `main` (requérir PRs et revues).
- Activer *Secret scanning* et *Push protection* si disponible.

Fichiers ajoutés ici pour automatiser et guider le déploiement :
- [.gitignore](.gitignore)
- [.github/workflows/pages.yml](.github/workflows/pages.yml#L1-L40)
- [.github/dependabot.yml](.github/dependabot.yml#L1-L20)
- [SECURITY.md](SECURITY.md)

Si vous voulez, je peux créer aussi un domaine personnalisé (`CNAME`) ou configurer des protections précises dans l'UI GitHub.
