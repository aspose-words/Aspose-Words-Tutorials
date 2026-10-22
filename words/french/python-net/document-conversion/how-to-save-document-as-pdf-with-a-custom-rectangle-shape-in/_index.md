---
category: general
date: 2026-10-07
description: Apprenez à enregistrer un document au format PDF tout en ajoutant une
  forme rectangulaire et une ombre personnalisée à l'aide d'Aspose.Words pour Python.
  Code étape par étape inclus.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: fr
lastmod: 2026-10-07
og_description: Enregistrez le document au format PDF avec une forme rectangulaire
  personnalisée en utilisant Aspose.Words pour Python. Suivez l’exemple complet pour
  dessiner, styliser et exporter Word en PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Enregistrer le document au format PDF avec une forme rectangulaire – guide
  complet Python
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Comment enregistrer un document au format PDF avec une forme rectangulaire
  personnalisée en Python
url: /fr/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment enregistrer un document au format PDF avec une forme de rectangle personnalisée en Python

Si vous devez **save document as PDF** tout en ajoutant des graphiques personnalisés, ce guide vous montre comment. Nous allons parcourir la création d'un fichier Word vierge, **drawing a rectangle shape**, définir sa taille, appliquer une ombre visible, et enfin **export Word to PDF** en utilisant la bibliothèque Aspose.Words pour Python.

Vous obtiendrez un PDF contenant un rectangle parfaitement positionné, prêt pour les rapports, factures ou tout scénario d'automatisation de documents. Aucun outil externe n'est requis — uniquement Python et le package Aspose.Words.

## Ce dont vous aurez besoin

| Exigence | Pourquoi c’est important |
|----------|--------------------------|
| Python 3.8+ | L'API Aspose.Words pour Python cible les interprètes modernes. |
| `aspose-words` package (`pip install aspose-words`) | Fournit l'espace de noms `aw` utilisé dans les exemples de code. |
| Familiarité de base avec Python et la programmation orientée objet | Le tutoriel manipule des objets comme `Document` et `Shape`. |
| Permission d'écriture sur un dossier où le PDF sera enregistré | L'étape `save document as pdf` écrit un fichier sur le disque. |

> **Astuce :** Utilisez un environnement virtuel (`python -m venv venv`) pour isoler les dépendances.

## Comment enregistrer un document au format PDF avec une forme de rectangle

Voici un exemple complet et exécutable. Chaque étape est expliquée afin que vous compreniez **pourquoi** nous effectuons l'action, et pas seulement **ce que** le code fait.

### Étape 1 : Initialiser un nouveau document vierge

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Créer un nouvel objet `Document` vous fournit une collection de pages vierge. Vous pourriez également charger un *.docx* existant si vous souhaitiez **export Word to PDF** plus tard, mais commencer avec un document vierge maintient l'exemple ciblé.

### Étape 2 : Ajouter une forme de rectangle au document

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

L'étape `add rectangle shape` utilise `ShapeType.RECTANGLE`. En ajoutant la forme à un paragraphe, Aspose.Words sait où la rendre dans le PDF final.

### Étape 3 : Définir les dimensions du rectangle

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Définir explicitement les **dimensions du rectangle** garantit que la forme reste cohérente sur toutes les plateformes. Vous pouvez également utiliser les assistants `convert_to_inches` si vous préférez les unités impériales.

### Étape 4 : (Facultatif) Appliquer une ombre personnalisée visible

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Une ombre fait ressortir le rectangle dans le PDF. Le drapeau `shadow.visible` est requis ; sans lui, les autres propriétés n'ont aucun effet.

### Étape 5 : Enregistrer le document au format PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Appeler `document.save` avec une extension **.pdf** déclenche automatiquement **save document as pdf** en utilisant le moteur PDF intégré d'Aspose.Words. Aucune étape de conversion supplémentaire n'est nécessaire, ce qui explique pourquoi cette méthode est la façon recommandée de **export Word to PDF**.

> **Pourquoi cela fonctionne :** Aspose.Words écrit la mise en page du document, y compris le rectangle et son ombre, directement dans le flux PDF. Le processus est sans perte et conserve la qualité vectorielle.

## Code source complet (script unique)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

L'exécution de ce script produit `shadow_rectangle.pdf` qui ressemble à ceci :

![Diagramme du PDF généré montrant la forme du rectangle après save document as pdf](placeholder-image.png)

*Le PDF contient une seule page avec un rectangle à ombre noire centré dans le document.*

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|---------|
| **Puis-je placer le rectangle à un emplacement spécifique ?** | Oui. Définissez `rectangle.left` et `rectangle.top` (en points) avant d'enregistrer. |
| **Et si j’ai besoin de plusieurs formes ?** | Créez des objets `Shape` supplémentaires, configurez chacun, et ajoutez‑les au même paragraphe ou à des paragraphes différents. |
| **L'ombre affecte‑t‑elle la taille du PDF ?** | Seulement marginalement ; l'ombre est stockée comme métadonnées vectorielles, pas comme image raster. |
| **Puis‑je utiliser cela pour convertir des fichiers *.docx* existants ?** | Absolument. Remplacez `aw.Document()` par `aw.Document("input.docx")` et le reste des étapes reste inchangé. |
| **Existe‑t‑il un moyen de changer la couleur de remplissage du rectangle ?** | Définissez `rectangle.fill_color = aw.drawing.Color.light_blue` (ou toute `Color` que vous préférez). |

## Prochaines étapes

Maintenant que vous savez comment **save document as PDF** avec un rectangle personnalisé, vous pourriez explorer :

* **Export Word to PDF** avec en‑têtes, pieds de page et numéros de page.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) en utilisant la même classe `Shape`.  
* **Batch process** un dossier de fichiers Word, en appliquant la même superposition de rectangle à chacun.  

Ces extensions suivent le même schéma : créer une forme, configurer ses propriétés, et **save document as pdf**.

---

**Résumé :** Ce tutoriel vous a montré comment **save document as PDF** tout en **add rectangle shape**, **set rectangle dimensions**, et appliquer une ombre personnalisée avec Aspose.Words pour Python. Le script complet est prêt à être copié, exécuté et adapté à vos propres pipelines d'automatisation de documents. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme de rectangle, ajouter une ombre et enregistrer en PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Ajouter un rectangle au PDF avec Aspose.Words – Guide étape par étape](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Enregistrer le document au format PDF avec Aspose.Words – Guide complet C#](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}