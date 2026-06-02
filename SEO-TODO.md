# SEO-TODO — Les Terrasses du Fort
> À compléter une fois le domaine validé par le client

---

## 🔴 Priorité 1 — Dès réception du domaine

### 1. Remplacer le domaine placeholder
Chercher dans ces fichiers et remplacer `les-terrasses-du-fort.fr` par le vrai domaine :
- `index.html` → balises canonical, og:url, JSON-LD
- `sitemap.xml` → toutes les `<loc>`
- `robots.txt` → ligne Sitemap:

```bash
# Commande rapide (remplacer MON-DOMAINE.com) :
find . -type f \( -name "*.html" -o -name "*.xml" -o -name "*.txt" \) \
  -exec sed -i '' 's/les-terrasses-du-fort\.fr/MON-DOMAINE.com/g' {} +
```

### 2. Google Search Console
1. Aller sur https://search.google.com/search-console
2. Ajouter le domaine
3. Vérifier via DNS TXT (chez le registrar du client) ou via balise meta :
   ```html
   <!-- Ajouter dans le <head> de index.html -->
   <meta name="google-site-verification" content="CODE_FOURNI_PAR_GOOGLE" />
   ```
4. Soumettre le sitemap : `https://MON-DOMAINE.com/sitemap.xml`
5. Demander l'indexation de la page principale

### 3. Mise à jour du sitemap
Mettre à jour `<lastmod>` dans sitemap.xml avec la date de mise en ligne réelle.

---

## 🟡 Priorité 2 — Optimisations post-lancement

### 4. Google Analytics (optionnel)
Ajouter avant `</head>` dans index.html :
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### 5. Google Business Profile
- Créer / revendiquer la fiche Google Maps du logement
- URL : https://business.google.com
- Ajouter : photos, horaires, description, lien vers le site

### 6. Images OG (réseaux sociaux)
Idéalement créer une image 1200×630px spécifique pour le partage social :
- `assets/og-image.jpg`
- Remplacer l'URL actuelle dans les balises og:image et twitter:image

### 7. Coordonnées GPS dans le JSON-LD
Vérifier les coordonnées exactes de la propriété (actuellement : 15.9987, -61.7204)
et corriger si besoin dans le bloc JSON-LD de index.html.

---

## 🟢 Priorité 3 — Optimisations avancées (si trafic en croissance)

### 8. PWA / Service Worker
Ajouter un manifest.json pour permettre l'ajout à l'écran d'accueil mobile :
```json
{
  "name": "Les Terrasses du Fort",
  "short_name": "Terrasses du Fort",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#111111",
  "background_color": "#ffffff",
  "icons": [{ "src": "/assets/logos/logo.png", "sizes": "192x192" }]
}
```

### 9. Backlinks locaux
Soumettre le site aux annuaires locaux :
- Guadeloupe Tourisme : https://fr.guadeloupe-tourisme.com
- Lesilesdeguadeloupe.com
- TripAdvisor
- Yelp

### 10. Titre et description Airbnb / Booking
Aligner les titres/descriptions sur les plateformes avec ceux du site pour la cohérence SEO.

---

## ✅ Déjà fait

- [x] `<html lang="fr">` 
- [x] Title SEO + meta description
- [x] Canonical URL
- [x] Robots meta
- [x] Open Graph (7 balises)
- [x] Twitter Cards
- [x] JSON-LD Schema (LodgingBusiness + WebSite + BreadcrumbList)
- [x] Preconnect CDN + Google Fonts
- [x] Preload image LCP (fetchpriority="high")
- [x] Alt text sur toutes les images de contenu
- [x] sitemap.xml
- [x] robots.txt
- [x] vercel.json (cache, sécurité, redirects)
- [x] ARIA labels sections + navigation
- [x] Hiérarchie h1/h2/h3 corrigée (1 seul h1 par page)
- [x] Structure dossier réorganisée (styles/ + assets/)
