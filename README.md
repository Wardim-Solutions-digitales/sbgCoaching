# SBG Coaching — Site web officiel

Site web professionnel de **Samuel Billa-Garcia**, coach sportif personnel et coach bien-être en entreprise basé à Engis (Liège), Belgique.

🌐 [sbgcoaching.be](https://sbgcoaching.be)

---

## Stack technique

| Catégorie | Technologie |
|---|---|
| Framework | [Astro 5](https://astro.build) (SSR) |
| UI | [React 19](https://react.dev) |
| Langage | TypeScript 5 |
| Styles | SCSS (Sass 1.87) — architecture 7-1 + BEM |
| Bundler | Vite 6 + Terser |
| Email | Nodemailer (SMTP) |
| Déploiement | Vercel / Netlify / Node.js standalone |
| Linting | ESLint 9 + Stylelint + Prettier |

---

## Prérequis

- Node.js ≥ 18
- npm ≥ 9

---

## Installation

```bash
git clone https://github.com/ton-compte/sbgCoaching.git
cd sbgCoaching
npm install
```

### Variables d'environnement

Créer un fichier `.env` à la racine du projet :

```env
SMTP_HOST=ton-serveur-smtp
SMTP_PORT=465
SMTP_USER=ton-email@domaine.com
MAIL_SMTP_PASS=ton-mot-de-passe
```

Ces variables sont nécessaires pour que le formulaire de contact envoie les emails via `/api/contact`.

---

## Commandes disponibles

| Commande | Description |
|---|---|
| `npm run dev` | Démarre le serveur de développement |
| `npm run build` | Build de production |
| `npm run preview` | Prévisualise le build local |
| `npm run refresh` | Vide le cache Vite et relance le dev |
| `npm run lint:ts` | Lint TypeScript avec ESLint |
| `npm run lint:scss` | Lint SCSS avec Stylelint |

---

## Structure du projet

```
sbgCoaching/
├── public/
│   ├── favicon/
│   └── img/                    # Images (hero, témoignages, résultats…)
├── src/
│   ├── hooks/                  # Hooks React personnalisés (useInView)
│   ├── js/
│   │   ├── data/               # Données statiques (témoignages, vidéos…)
│   │   └── global/             # Utilitaires partagés (FAQ, footer, form)
│   ├── layouts/
│   │   └── BaseLayout.astro    # Shell HTML commun à toutes les pages
│   ├── pages/
│   │   ├── api/contact.ts      # Endpoint POST — envoi d'email SMTP
│   │   ├── index.astro
│   │   ├── a-propos.astro
│   │   ├── coaching-entreprise.astro
│   │   ├── coaching-general.astro
│   │   ├── coaching-sportif-video.astro
│   │   ├── contact.astro
│   │   ├── rdv.astro
│   │   ├── temoignages.astro
│   │   └── ...
│   ├── partials/               # Composants Astro + React réutilisables
│   │   ├── components/         # Menu, Footer, SEO, ContactForm…
│   │   ├── index/              # Sections de la page d'accueil
│   │   ├── about/
│   │   ├── entreprise/
│   │   ├── general/
│   │   └── performance/        # Wrapper LazyFadeIn (scroll reveal)
│   └── scss/
│       ├── abstracts/          # Variables, mixins, fonts
│       ├── base/               # Reset, typographie, animations
│       ├── components/         # Menu, footer, boutons…
│       ├── layout/             # Containers, grille
│       └── pages/              # Styles par page
├── astro.config.ts
├── vite.config.ts
├── netlify.toml
├── vercel.json
├── render.yaml
└── Dockerfile
```

---

## Pages

| Page | Route | Description |
|---|---|---|
| Accueil | `/` | Hero slider, présentation des offres, FAQ |
| À propos | `/a-propos` | Biographie du coach, parcours |
| Coaching général | `/coaching-general` | Coaching individuel et collectif |
| Coaching entreprise | `/coaching-entreprise` | Sessions en entreprise (100% déductibles fiscalement) |
| Coaching vidéo | `/coaching-sportif-video` | Bibliothèque de vidéos d'exercices |
| Témoignages | `/temoignages` | Avis clients filtrables (général / entreprise) |
| Contact | `/contact` | Formulaire + Google Maps |
| Rendez-vous | `/rdv` | Prise de rendez-vous |
| Mentions légales | `/mentions-legales` | |
| Politique de confidentialité | `/politique-de-confidentialite` | |

---

## Fonctionnalités notables

- **Formulaire de contact** — validation en temps réel, protection anti-spam (honeypot), sauvegarde automatique en `localStorage`, délai de soumission de 3 secondes
- **Scroll reveal** — composant `LazyFadeIn` basé sur `IntersectionObserver`
- **SEO avancé** — Open Graph, Twitter Card, canonical URLs, JSON-LD Schema.org (`LocalBusiness`, `Review`, `Article`)
- **Multi-adapter** — le même build peut être déployé sur Vercel, Netlify ou Node.js standalone selon la variable d'environnement `DEPLOY_TARGET`

---

## Déploiement

### Vercel

```bash
DEPLOY_TARGET=vercel npm run build
```

### Netlify

```bash
DEPLOY_TARGET=netlify npm run build
```

### Node.js standalone / Docker

```bash
npm run build
docker build -t sbgcoaching .
docker run -p 8080:8080 sbgcoaching
```

---

## Alias de chemins (Vite)

| Alias | Chemin réel |
|---|---|
| `@` | `src/` |
| `@js` | `src/js/` |
| `@scss` | `src/scss/` |
| `@partials` | `src/partials/` |
| `@layouts` | `src/layouts/` |

---

## Contact

**SBG Coaching — Samuel Billa-Garcia**
📍 Route de Yernée 264, 4480 Engis (Liège), Belgique
📧 info@sbgcoaching.be
📞 +32 494 20 50 75
