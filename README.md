# SoulGoldFR

Traduction française d'un hack ROM Pokémon (base Emerald, "Hide & Seek") — distribuée sous forme de **patch xdelta**, pas de ROM complète (pour rester dans les clous côté droits d'auteur : Nintendo possède le jeu de base, seules les modifications appliquées par-dessus sont partagées ici).

Hack original : [pokemonsoulgold.com](https://pokemonsoulgold.com/)

## Ce qu'il te faut

1. **Une ROM Pokémon Émeraude EU/US non modifiée**, fichier `.gba`, nommé typiquement :
   `Pokemon - Emerald Version (USA, Europe).gba`

   Vérifie que c'est la bonne version en comparant son empreinte SHA1 :
   ```
   f3ae088181bf583e55daf962a92bb46f4f1d07b7
   ```
   (calcul sous macOS/Linux : `shasum -a 1 "ta_rom.gba"`)

   Cette ROM n'est **pas fournie ici** — tu dois te la procurer toi-même à partir d'une cartouche que tu possèdes.

2. **L'outil `xdelta3`** pour appliquer le patch.
   - macOS (Homebrew) : `brew install xdelta`
   - Linux : `apt install xdelta3` (ou équivalent selon la distro)
   - Windows : binaire disponible sur le dépôt officiel [xdelta](https://github.com/jmacd/xdelta), ou passer par un frontend graphique type Delta Patcher / xdelta UI.

3. **L'émulateur [mGBA](https://mgba.io/)** — c'est celui utilisé pour développer et tester ce patch. D'autres émulateurs GBA peuvent fonctionner, mais mGBA est le seul garanti sans souci ici.

## Comment appliquer le patch

Avec `xdelta3` en ligne de commande, dans le dossier où se trouvent ta ROM d'origine et le patch :

```
xdelta3 -d -s "Pokemon - Emerald Version (USA, Europe).gba" pokemonHnS_v1.0-FR.xdelta pokemonHnS.gba
```

Ça crée un nouveau fichier `pokemonHnS.gba` — c'est la ROM patchée, à ouvrir avec mGBA.

Ta ROM d'origine n'est jamais modifiée : le patch lit l'originale et écrit un nouveau fichier à côté.

## Contenu de cette version (v1.0)

- Traduction française complète (menus, objets, talents, attaques, noms d'espèces, quasiment tous les scripts de dialogue).
- Plusieurs bugs de traduction corrigés (textes tronqués qui provoquaient des plantages sur certains Pokémon/objets/baies).
- Correctif d'un plantage intermittent au démarrage d'une nouvelle partie.
- Corrections d'affichage sur l'écran résumé des Pokémon (description de talent, page des stats).

## En cas de souci

- Si le patch refuse de s'appliquer ou que le résultat plante immédiatement : vérifie en premier le hash SHA1 de ta ROM source (ci-dessus) — un mauvais dump (mauvaise région/version) est la cause la plus fréquente.
- Utilise bien mGBA, pas un autre émulateur, en cas de comportement anormal.
