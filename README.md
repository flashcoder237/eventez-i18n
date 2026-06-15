# eventez-i18n — Traductions d'interface (hébergement OTA)

Repo **public** qui héberge les fichiers de traduction de l'interface mobile
EventEz, servis par **GitHub Pages** (gratuit). L'app mobile les télécharge à la
demande (OTA) et les met en cache — voir `EventEzMobile/src/i18n/translations.ts`.

> Ne contient **que des chaînes d'interface traduites** (ex. « Buy tickets » →
> « Comprar entradas »). Rien de sensible → public sans risque.

## URL servie

```
https://flashcoder237.github.io/eventez-i18n/
```

Chaque langue : `https://flashcoder237.github.io/eventez-i18n/{lang}.json`
(ex. `/es.json`, `/de.json`).

À mettre dans l'app mobile (`.env` / EAS) :

```
EXPO_PUBLIC_TRANSLATIONS_URL=https://flashcoder237.github.io/eventez-i18n
```

(Le loader concatène `/{lang}.json`. fr/en restent bundlés dans l'app, **pas**
besoin de les héberger ici.)

## Ajouter / mettre à jour des langues

Depuis le repo mobile :

```bash
# 1. Générer les traductions (gratuit, offline — voir scripts/translate_locales.py)
pip install argostranslate
python scripts/translate_locales.py --langs es,pt,de,it --out ../../eventez-i18n

# 2. Publier
cd ../../eventez-i18n
git add . && git commit -m "i18n: es, pt, de, it" && git push
```

GitHub Pages redéploie en ~1 min. L'app prend la nouvelle langue au prochain
choix dans Settings (cache rafraîchi en arrière-plan).

## Structure

```
eventez-i18n/
  .nojekyll        # sert les fichiers tels quels (pas de build Jekyll)
  index.html       # page d'accueil (optionnelle)
  manifest.json    # { "es": <version>, … } généré par le script
  es.json, de.json, …   # une langue par fichier (ajoutés par le script)
```
