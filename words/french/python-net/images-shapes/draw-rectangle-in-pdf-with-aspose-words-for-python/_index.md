---
category: general
date: 2026-08-07
description: Dessiner un rectangle dans un PDF en utilisant Aspose.Words pour Python
  et apprendre comment ajouter une ombre à la forme, configurer l'ombre de la forme,
  puis enregistrer le document au format PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: fr
lastmod: 2026-08-07
og_description: Tracer un rectangle dans un PDF avec Aspose.Words pour Python. Ce
  tutoriel montre comment ajouter une ombre à une forme, configurer l’ombre de la
  forme et enregistrer le document au format PDF pour une génération professionnelle
  de documents.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Dessiner un rectangle dans un PDF avec Aspose.Words pour Python – guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Dessiner un rectangle dans un PDF avec Aspose.Words pour Python
url: /fr/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dessiner un rectangle dans un PDF avec Aspose.Words pour Python

Si vous devez **dessiner un rectangle dans un PDF** en travaillant avec Python, ce guide vous fournit une solution complète, prête à l'emploi. Vous verrez exactement comment **ajouter une ombre à une forme**, configurer cette ombre, et enfin **enregistrer le document au format PDF** pour la distribution ou l'archivage.

Créer un rectangle ombré est une exigence courante pour les rapports, factures ou annotations visuelles. À la fin de ce tutoriel, vous disposerez d'un script unique qui produit un PDF contenant un rectangle avec une ombre réaliste, et vous comprendrez comment ajuster la taille, la couleur et le décalage pour s'adapter à n'importe quel design.

## Prérequis

Avant de commencer, assurez-vous d'avoir :

* Python 3.8+ installé.
* Le package Aspose.Words for Python via .NET (`aspose-words`) – installer avec :

```bash
pip install aspose-words
```

* Permission d'écriture sur le dossier où vous prévoyez d'enregistrer le PDF.

Aucune bibliothèque supplémentaire n'est requise ; Aspose.Words gère la création de formes, la configuration des ombres et l'exportation PDF en interne.

## Étape 1 : Créer un nouveau document vierge (dessiner un rectangle dans un PDF – initialisation)

La première étape consiste à instancier un objet `Document`. Cet objet représente l'intégralité du fichier PDF et fournit un conteneur pour les sections, paragraphes et formes.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Pourquoi c’est important :** Aspose.Words traite la génération de PDF comme une conversion à partir d’un modèle de document Word, nous commençons donc avec un `Document` même si le résultat final est un PDF.

## Étape 2 : Insérer une forme rectangle dans le corps du document

Un rectangle est un `ShapeType` spécifique. Nous l’ajoutons au corps de la première section, ce qui crée automatiquement une nouvelle page lors de l’enregistrement en PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Explication :** Les propriétés `width` et `height` contrôlent la taille visuelle de la forme dans le PDF. Ajouter du texte rend le rectangle plus facile à vérifier pendant les tests.

## Étape 3 : Ajouter une ombre à la forme – activer et personnaliser

Nous activons maintenant l’effet d’ombre et ajustons finement son apparence. C’est ici que le mot‑clé **add shadow to shape** entre en jeu.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Pourquoi configurer l’ombre de la forme ?** Ajuster `blur`, `distance` et `angle` vous permet de simuler un éclairage réaliste, ce qui améliore la lisibilité et la hiérarchie visuelle dans les PDF générés.

## Étape 4 : Enregistrer le document au format PDF – sortie finale

Avec le rectangle et son ombre définis, la dernière étape consiste à exporter le document Word en PDF. Cela satisfait le besoin **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Lorsque vous ouvrez `shadow_rectangle.pdf`, vous verrez une page unique contenant un rectangle à bord gris intitulé « Shadow demo » avec une ombre diagonale nette.

### Résultat attendu

* Un fichier PDF nommé `shadow_rectangle.pdf`.
* Une page avec un rectangle de 200 pt × 100 pt.
* Une ombre visible décalée de 5 pt à un angle de 45°, floutée de 8 pt.

## Étape 5 : Explorer les variantes et cas limites (optionnel)

Voici des ajustements courants que vous pourriez nécessiter dans des projets réels :

| Variation | Extrait de code | Quand l’utiliser |
|-----------|----------------|------------------|
| **Type de forme différent** (par ex., ellipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Pour des graphiques arrondis ou des badges |
| **Couleur d'ombre personnalisée** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Lorsqu'une ombre grise ou spécifique à la marque est requise |
| **Formes multiples** | Repeat the shape‑creation block and adjust `left`/`top` properties | Pour créer des diagrammes complexes |
| **Pas de texte à l'intérieur de la forme** | Omit `rectangle.text = "..."` | Lorsque la forme est purement décorative |
| **Sortie à DPI plus élevé** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Pour des PDF prêts à l'impression |

**Astuce pro :** Toujours définir `shadow.visible = True` avant d’ajuster les autres propriétés ; sinon les modifications sont ignorées silencieusement.

## Script complet – copier, coller et exécuter

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Exécutez le script depuis votre terminal ou votre IDE. Remplacez `YOUR_DIRECTORY` par un chemin de dossier réel, tel que `"/tmp"` ou `"C:\\Users\\Me\\Documents"`.

## Conclusion

Vous savez maintenant comment **dessiner un rectangle dans un PDF** en utilisant Aspose.Words pour Python, **ajouter une ombre à une forme**, **configurer l’ombre de la forme**, et **enregistrer le document au format PDF**. L’exemple complet montre chaque étape, de la création du document à l’exportation finale, et les variantes optionnelles illustrent comment adapter le code à des scénarios plus complexes.

Ensuite, vous pourriez explorer :

* Ajouter d'autres types de formes (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Appliquer des remplissages en dégradé ou des bordures pour améliorer l'attrait visuel.
* Utiliser `PdfSaveOptions` pour incorporer des polices ou contrôler la compression des images.

N’hésitez pas à expérimenter avec les paramètres pour correspondre à votre identité visuelle ou à vos directives de conception. Bon scripting PDF !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Optimiser les signets PDF avec Aspose.Words pour Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimiser le chargement PDF Python Aspose Words Ignorer les images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Manipulation PDF Aspose Words Python](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}