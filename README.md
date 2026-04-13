# Sorare MLB 2026 — Tier List par Division

Interface web statique listant les joueurs MLB par division Sorare, triés par position et tier (★ à ★★★★★★), basée sur les rosters officiels Opening Day 2026.

## Déploiement rapide

### Option A — Docker Compose classique

```bash
git clone https://github.com/TON_USER/sorare-mlb.git
cd sorare-mlb
docker compose up -d
# → accessible sur http://VOTRE_IP:8573
```

### Option B — Portainer (Stack depuis GitHub)

1. Dans Portainer → **Stacks** → **+ Add stack**
2. Choisir **Repository**
3. Renseigner :
   - **Repository URL** : `https://github.com/TON_USER/sorare-mlb`
   - **Reference** : `main`
   - **Compose path** : `docker-compose.yml`
4. Cliquer **Deploy the stack**
5. Accéder à **http://VOTRE_IP:8573**

### Option C — Portainer (Stack en paste direct)

1. Dans Portainer → **Stacks** → **+ Add stack**
2. Choisir **Web editor**
3. Coller le contenu de `docker-compose.yml`
4. **Attention** : cette option nécessite que les fichiers `app/` soient accessibles sur l'hôte Portainer. Utiliser de préférence l'option Repository.

## Structure du projet

```
sorare-mlb/
├── docker-compose.yml      ← stack Portainer
└── app/
    ├── Dockerfile          ← image Docker (optionnel si build custom)
    ├── index.html          ← application complète
    └── nginx.conf          ← config nginx
```

## Données

- Rosters officiels **MLB Opening Day 2026** (source : MLB.com)
- 6 divisions : NL Est, NL Central, NL West, AL Est, AL Central, AL West
- 30 équipes, ~200 joueurs
- Tiers Sorare estimés sur la base des performances 2025 et projections 2026

## Tier system

| Tier | Description |
|------|-------------|
| ★★★★★★ | Élite mondial (Ohtani, Judge, Acuña, Freeman...) |
| ★★★★★ | Star établie (top 15 à leur position) |
| ★★★★ | Très bon (starter de qualité) |
| ★★★ | Solide (titulaire fiable) |
| ★★ | Correct (rotation/banc) |
| ★ | Profondeur de roster |

## Mise à jour des données

Modifier directement `app/index.html` dans la section `const DATA = { ... }` puis redéployer le stack.
