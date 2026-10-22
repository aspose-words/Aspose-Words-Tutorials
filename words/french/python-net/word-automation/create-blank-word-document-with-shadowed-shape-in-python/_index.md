---
category: general
date: 2026-10-16
description: Créer un document Word vierge, insérer une forme dans Word, ajouter une
  ombre extérieure et enregistrer en PDF à l'aide de Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: fr
lastmod: 2026-10-16
og_description: Créez un document Word vierge avec une forme d’ombre extérieure en
  utilisant Aspose.Words pour Python. Ce guide montre comment insérer la forme, appliquer
  l’ombre et enregistrer le fichier au format PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Créer un document Word vierge avec ombre de forme – Guide Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Créer un document Word vierge avec une forme ombrée en Python
url: /fr/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec forme ombrée en Python

Si vous devez **créer un document Word vierge** et ajouter un graphique personnalisé, ce guide vous couvre. Nous allons parcourir comment **insérer une forme dans Word**, appliquer une **forme d'ombre extérieure**, et enfin **enregistrer en PDF avec Python**.

Vous apprendrez à configurer Aspose.Words pour Python, créer un rectangle, styliser son ombre et générer un PDF qui conserve l'effet visuel. Aucune expérience préalable avec l'API Aspose n'est requise, mais vous devez posséder des connaissances de base en Python et une installation fonctionnelle de Python 3.10 ou ultérieure.

## Prérequis

* Python 3.10 ou une version plus récente installé.
* Une licence active d'Aspose.Words pour Python (un essai gratuit fonctionne pour l'évaluation).
* Accès à `pip` pour installer le package `aspose-words`.
* Permission d'écriture dans le répertoire où le PDF sera enregistré.

Vous pouvez installer la bibliothèque avec une seule commande :

```bash
pip install aspose-words
```

## Créer un document Word vierge – configuration de l'environnement

La première étape consiste à créer un fichier Word vide qui servira de toile pour la forme.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` représente un fichier Word complètement vierge. En utilisant `DocumentBuilder`, vous avez accès à des méthodes comme `insert_shape`, que nous utiliserons à l'étape suivante.

## Insérer une forme dans Word et définir les dimensions

Nous ajoutons maintenant un rectangle qui recevra plus tard une ombre extérieure. La taille est exprimée en points (1 pt ≈ 1/72 pouce).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

L'appel `insert_shape` renvoie un objet `Shape` que vous pouvez personnaliser davantage. À ce stade, le document contient déjà un rectangle visible lorsqu'il est ouvert dans Microsoft Word.

## Ajouter une ombre extérieure – personnalisation de l'effet

Aspose.Words fournit une classe `ShadowEffect` pour définir les propriétés de l'ombre telles que le style, le flou, la distance et la couleur.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Définir `style` à `OUTER` garantit que l'ombre apparaît à l'extérieur de la bordure du rectangle, offrant un rendu 3 D subtil. Vous pouvez expérimenter avec `blur` et `distance` pour obtenir une ombre plus serrée ou plus diffusée.

## Enregistrer en PDF avec Python – finalisation du document

Après avoir stylisé la forme, le document peut être enregistré directement en PDF. Aspose.Words gère la conversion en interne, préservant l'effet d'ombre.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Lorsque vous ouvrez `shape_with_shadow.pdf` dans n'importe quel lecteur PDF, vous verrez le rectangle avec l'ombre extérieure exactement comme il apparaissait dans Word.

## Exemple complet fonctionnel

Ci-dessous le script complet qui combine toutes les étapes. Copiez-le dans un fichier nommé `create_word_with_shadow.py` et exécutez-le.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Sortie attendue**

L'exécution du script affiche une ligne de confirmation, par exemple :

```
PDF generated at: output/shape_with_shadow.pdf
```

L'ouverture du PDF résultant montre une seule page contenant un rectangle de 200 pt × 100 pt avec une ombre extérieure noire douce.

## Variantes courantes et cas particuliers

* **Changer la couleur de l'ombre** – Remplacez `aw.Color.black` par toute autre valeur `aw.Color`, comme `aw.Color.red` ou `aw.Color.from_argb(255, 0, 120, 215)`.
* **Utiliser une forme différente** – Changez `aw.drawing.ShapeType.RECTANGLE` en `OVAL`, `DIAMOND`, ou toute autre valeur d'énumération prise en charge.
* **Enregistrer en DOCX au lieu de PDF** – Appelez `doc.save("output/shape.docx")` pour conserver le format Word.
* **Plusieurs formes** – Créez des formes supplémentaires en appelant à nouveau `builder.insert_shape` ; chaque forme peut avoir son propre `ShadowEffect`.

**Astuce :** Si vous devez placer la forme à un emplacement précis, définissez `rectangle.left` et `rectangle.top` après l'insertion. Cela vous donne un contrôle pixel‑parfait sur le positionnement.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer une forme dans Word**, **ajouter une forme d'ombre extérieure**, et **enregistrer en PDF avec Python**. L'exemple complet de code montre le flux de travail de bout en bout, et les explications clarifient pourquoi chaque appel d'API est nécessaire.

À partir de là, vous pouvez explorer des options de style plus avancées, ajouter du texte à l'intérieur de la forme, ou combiner plusieurs formes pour créer des diagrammes complexes. Expérimentez avec différents paramètres d'ombre pour correspondre au langage visuel de votre marque, et intégrez cette approche dans des pipelines de génération de documents plus larges.

Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme rectangle, ajouter une ombre & enregistrer en PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Créer un PDF à partir de Word – Guide complet Python avec Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Ajouter une ombre à une forme dans Word avec Aspose.Words – Étape par étape](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}