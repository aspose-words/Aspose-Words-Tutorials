---
category: general
date: 2026-05-04
description: Apprenez à créer une forme rectangulaire, à ajouter une forme avec des
  ombres, à modifier la couleur de l’ombre, à définir la distance de l’ombre et à
  enregistrer le document au format PDF en utilisant Aspose.Words pour Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: fr
og_description: Créez une forme rectangulaire avec Aspose.Words pour Python, apprenez
  comment ajouter une forme, modifier la couleur de l’ombre, définir la distance de
  l’ombre et enregistrer le document au format PDF.
og_title: Créer une forme rectangulaire – Ajouter une ombre, changer la couleur et
  enregistrer en PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Créer une forme de rectangle en Python – Guide complet pour ajouter des ombres
  et enregistrer en PDF
url: /fr/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire – Tutoriel complet pour les développeurs Python

Vous avez déjà eu besoin de **create rectangle shape** dans un document Word et vous vous demandez comment lui donner une ombre soignée ? Peut-être que vous créez un générateur de rapports et que le rendu visuel compte—surtout lorsque le résultat final est un PDF. Bonne nouvelle ? Avec Aspose.Words for Python, vous pouvez non seulement **how to add shape** mais aussi ajuster chaque propriété de l'ombre, de la couleur à la distance, puis **save document as pdf** en un seul flux fluide.

Dans ce guide, nous parcourrons l'ensemble du processus étape par étape. Vous verrez le code exact que vous pouvez copier‑coller, comprendre *why* chaque ligne est importante, et apprendre quelques astuces pour gérer les cas limites (comme les ombres transparentes ou le DPI non standard). À la fin, vous serez capable de **create rectangle shape**, personnaliser son ombre, et exporter un PDF net sans effort.

## Prérequis

- Python 3.8+ installé sur votre machine.  
- Aspose.Words for Python via `pip install aspose-words`.  
- Familiarité de base avec Python orienté objet (rien de spécial).  

Si vous avez déjà un environnement virtuel configuré, exécutez simplement la commande d'installation et vous êtes prêt à partir.

## Étape 1 : Initialise le Document et le Builder

Avant de pouvoir **how to add shape**, vous avez besoin d'un document vierge avec lequel travailler. La classe `Document` représente le fichier complet, et `DocumentBuilder` est votre pinceau.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Pourquoi c'est important :* `Document` contient toutes les sections, pages et ressources. `DocumentBuilder` vous offre une API fluide pour insérer du contenu exactement où vous le souhaitez—considérez‑le comme un curseur dans un traitement de texte.

## Étape 2 : Insérer la forme rectangulaire

Maintenant nous **how to add shape** réellement. La méthode `insert_shape` nécessite le type de forme et ses dimensions (en points). Ici, nous choisissons un rectangle de 200 × 100 pt et lui appliquons un remplissage bleu clair.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Astuce :* Si vous devez aligner la forme avec du texte existant, utilisez `builder.move_to` avant l'insertion, ou ajustez les propriétés `left`/`top` après la création.

## Étape 3 : Activer l'ombre

Une forme sans ombre paraît plate. Pour **set shadow distance** et rendre l'effet visible, récupérez le format d'ombre et activez‑le.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Pourquoi cette étape :* Le format d'ombre est un objet séparé ; basculer `visible` est la première chose à faire, sinon toutes les autres propriétés d'ombre sont ignorées.

## Étape 4 : Styliser l'ombre – Colour, Blur, Distance, Direction

C'est ici que la magie opère. Nous allons **change shadow color**, ajuster le rayon de flou, définir la distance de l'ombre par rapport au rectangle, et la faire pivoter de 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explication de chaque propriété :*

| Propriété | Ce qu'elle fait | Valeurs typiques |
|----------|----------------|------------------|
| `style` | Détermine si l'ombre est *inner* ou *outer*. | `OUTER` (le plus courant) |
| `blur_radius` | Contrôle la douceur ; plus élevé = bords plus flous. | 0–20 px est habituel |
| `distance` | Distance de décalage de l'ombre par rapport à la forme. | 0–10 pt pour subtil, >10 pour dramatique |
| `direction` | Angle de la source lumineuse, mesuré dans le sens des aiguilles d'une montre depuis l'axe x. | 0‑360° |
| `color` | Teinte de l'ombre. | Any `aw.Color` (e.g., `gray`, `dark_red`) |

*Cas limite :* Si vous définissez `distance` à `0`, l'ombre se placera directement sous la forme, masquant efficacement le remplissage de la forme. Gardez‑la au-dessus de `0` pour un décalage visible.

## Étape 5 : Enregistrer le Document en PDF

Enfin, nous **save document as pdf**. Aspose.Words rasterise automatiquement l'ombre, de sorte que le PDF ressemble exactement à la vue Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Pourquoi le PDF ?* Les PDF conservent la mise en page sur toutes les plateformes, ce qui les rend parfaits pour les rapports, factures ou tout autre document imprimable.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="exemple de création de forme rectangulaire avec ombre"}

*L'image ci‑dessus montre le rendu final du PDF – un rectangle bleu clair avec une ombre extérieure gris doux, exactement comme nous l'avons configuré.*

## Questions fréquentes & variantes

### Et si j'ai besoin d'une ombre **transparent** ?

Définissez le canal alpha sur la couleur de l'ombre :

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Puis‑je appliquer la même ombre à plusieurs formes ?

Oui. Extrayez le `ShadowFormat` d'une forme et assignez‑le à une autre :

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Comment changer l'ombre pour un **different shape type** ?

Tous les types de formes partagent les mêmes propriétés `ShadowFormat`, vous pouvez donc réutiliser le même bloc de configuration—remplacez simplement `ShapeType.RECTANGLE` par `ShapeType.OVAL`, `ShapeType.TRIANGLE`, etc.

### Qu'en est‑il des **high‑resolution PDFs** pour l'impression ?

Spécifiez le `PdfSaveOptions` avec un DPI plus élevé :

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Récapitulatif

Nous avons couvert tout ce dont vous avez besoin pour **create rectangle shape**, **how to add shape**, personnaliser sa **shadow colour**, **set shadow distance**, et enfin **save document as pdf**. Le script complet et exécutable ressemble à ceci :

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Exécutez le script, ouvrez le `ShadowedShape.pdf` généré, et vous verrez un rectangle net avec une ombre grise subtile—exactement ce que l’on attend d’un rapport formaté professionnellement.

## Et après ?

- **Explore other shape types** (`ShapeType.OVAL`, `ShapeType.LINE`) pour enrichir vos documents.  
- **Combine multiple shadows** en superposant des formes ; vous pouvez même créer un effet « glow » en utilisant une ombre interne avec une couleur vive.  
- **Automate batch processing** : bouclez sur une collection de lignes de données, générez une forme par ligne, et fusionnez le tout dans un seul PDF.  
- **Integrate with other Aspose libraries** (par ex., Aspose.Slides) si vous devez exporter le même visuel vers PowerPoint.

N'hésitez pas à expérimenter—modifiez le `blur_radius`, jouez avec `direction`, ou remplacez `gray` par une teinte spécifique à votre marque. L'API est suffisamment flexible pour que quelques ajustements modifient radicalement l'impact visuel.

Des questions ou un scénario difficile ? Laissez un commentaire ci‑dessous ou contactez les forums de la communauté Aspose. Bon codage, et profitez de ces rectangles magnifiquement ombrés !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}