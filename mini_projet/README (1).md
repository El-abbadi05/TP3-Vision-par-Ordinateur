# Mini-projet : Floutage automatique des visages

## Objectif
Détecter les visages (dlib, détecteur HOG) puis appliquer `cv2.GaussianBlur` sur chaque zone pour **anonymiser** une image ou un flux webcam (conformité vie privée).

## Installation
```bash
pip install opencv-python dlib-bin   # Windows
pip install opencv-python dlib       # Linux / macOS (cmake requis)
```

## Utilisation
```bash
# Sur une image
python flou_visages.py --image people.jpg --sortie people_flou.jpg

# Sur la webcam (touche q pour quitter)
python flou_visages.py --webcam
```

## Principe
1. Conversion en niveaux de gris, détection des visages avec `dlib.get_frontal_face_detector()`.
2. Pour chaque visage : découpe de la zone, `GaussianBlur` avec un noyau impair proportionnel à la taille du visage.
3. Affichage / sauvegarde du résultat.

## Limites
Le détecteur HOG de dlib ne détecte bien que les visages **de face** : les visages de profil ou très petits peuvent ne pas être floutés.
