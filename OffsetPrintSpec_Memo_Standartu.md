Spécifications techniques des fichiers d'impression
=============

<details>
<summary>About</summary>
   <p>
      
| Author | Kal (UCDP - It-Mgt) <br /> kal@wyld.lol |
| :--------------- |:---------------:| 
| Creation date  | 03-11-2022 |
| Last modifier  | 03-11-2022 | 
| Intent | Fix \|\| Feat. <br />
|| BREAKING CHANGE <br />
|| chore, docs, style, refactor <br /> perf, test, others <br /> |    
| Context | Generic || ~~Custom~~ |

   </p>
</details>

| Imprimeur | [Standartų spaustuvė](https://www.standart.lt/) <br /> ___Note: this documentation is only based on print house spec___ |
| :--------------- |:---------------:| 

   ##    Sommaire
   - [1. Fichiers](#fichiersPDF)
   - [2. Colorimétrie](#colorimetry)

<br /> <br /> <br /> <br /> 



# 1. Fichiers PDF <a id="fichiersPDF"></a>
## 1.1. Format
- versions 1.3 – 1.6
## 1.2. Norme
- PDF/X-3 ou PDF/X-4
## 1.3. Séparations des fichiers
1. Couverture
   - 1 fichier: 4 pages en 2 planches (recto/verso + largeur dos)
   - ø traits de coupes || croix de repérage || autres éléments
   - marge int: min 3mm
   - fond perdu  (illustré): 3-5mm couv souple || 20mm (couv rigide)
2. Pages de garde 
3. Intérieur:
- 1 fichier = max 1Gb
- X fichiers
   - n° + titre: *001-006_titre.pdf*
      > Regex: ^[\w,\s-]+\.[A-Za-z]{3}$
   - pages identiques: zone de rogne/orientation/trimbox (à indiquer dans le fichier)
   - génération en pages simples (ø double-pages)
4. Vernis sélectif (Marquage à chaud, embossage):
- Fichier vectorisé
- Format: correspondance avec le format du doc (superposable)
- Aplats N100%
- ø de détails: taille réduite, éléments précis || complexes
## 1.4. Résolution d'images
- Couleurs || Niveau de gris: mini 240-300dpi
- Bitmap: min 450.2540dpi
## 1.5. Fonts
- Polices spéciales:
   - [✓] Incorporer toutes les polices
   - [✕] ~~Jeux partiels de polices~~
   - [✓] Si *Subset*: config *% caractères utilisé < à...*: **0 (zéro)**
- Marge: min 5mm

# 2. Colorimétrie <a id="colorimetry"></a>
## 2.1. Mode
CMJN || Niveau de gris || Bichromie || Pantone
- Check: convertir les image non conformes
   -  Acrobat Pro: *afficher un aperçu des séparations de couleurs*
## 2.2. Profils
- ISO Coated v2 300% (papier couché (ECI))
- PSO Uncoated ISO12647 (papier non couché (ECI))

## 2.3. Options obligatoires
- [✓] *Supprimer la surimpression de blanc*

## 2.4. Encrage
- Max 300% || 330% (si papiers couchés)
Check: simuler l'affichage offset sur écran
   - profils ICC: *Couleurs d’épreuve /Aperçu de la sortie*
   - surimpression: *Aperçu de la surimpression)
- Gradients || Tons clairs: >2%
- Gris clair (aplat < 40%): N100%
- Gris foncé (aplat > 40%): C30/M20/J20/N100
- Encre métallique (arrière-plan): C50-M40-J40-100 (mélange couleur) (ø N100)
## 2.5. Fonts
- Size > 24pt: C40/M20/J0/N100 (max encrage: 240%)
- Size < 18pt: N100% (en surimpression)
- Size < 7pt: [CMJN]100% (1 couleur)
## 2.6. Elements
- Lignes fines (< 1mm) : N100% (en surimpression)
- Lignes > 2mm: C40/M20/J0/N100 (max encrage: 240%)
- Traits et contours:
   - [CMJN]100% = épaisseur min 0.04mm (~0.11 pt)
   - [CMJN]90% = épaisseur min 0.08mm (~0.23 pt)
   - Si >2 couleurs = épaisseur min 0.2mm (~0.6 pt)

# 3. Modifications post-envoi
- Format: vérifier la correspondance du doc
- Pagination: n° imprimé ET n° de page logique
- Si modif > 3-5 pages: nouveau fichier à fournir (new BAT)
- Emplacement des images: strictement identique à chaque version
