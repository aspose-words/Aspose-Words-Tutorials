---
category: general
date: 2026-08-17
description: Comment enregistrer un PNG avec Aspose.Words pour Python. Apprenez à
  ajouter une ombre à une forme, à enregistrer le document au format PDF et à exporter
  Word en PNG dans un guide complet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: fr
lastmod: 2026-08-17
og_description: Comment enregistrer un PNG avec Aspose.Words. Ce tutoriel montre comment
  ajouter une ombre à une forme, enregistrer le document au format PDF et exporter
  Word en PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Comment enregistrer un PNG et ajouter une ombre à une forme avec Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Comment enregistrer un PNG et ajouter une ombre à une forme avec Aspose.Words
url: /fr/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment enregistrer un PNG et ajouter une ombre à une forme avec Aspose.Words

Si vous avez besoin de **how to save PNG** depuis un fichier Word, ce guide vous fournit une solution complète et exécutable. Vous verrez également comment **add shadow to shape**, **save document as PDF**, et **export Word to PNG** sans quitter l'environnement Aspose.Words.

Le tutoriel couvre tout ce qui est nécessaire pour transformer un document Word vierge en PDF et en image PNG, tout en appliquant un effet d'ombre simple à une forme rectangulaire. Aucun outil externe n'est requis, et le code fonctionne avec Aspose.Words for Python via .NET 7 ou version ultérieure.

## Ce que vous accomplirez

* Créer un nouveau document Word par programmation.  
* Insérer une forme rectangulaire et configurer un effet d'ombre.  
* Enregistrer le même document au format PDF.  
* Exporter le document au format PNG.  

Ces étapes répondent à la requête courante **how to save PNG** tout en gérant **add shadow to shape** et **save document as PDF** dans un seul flux de travail.

## Prérequis

* Python 3.9 ou version supérieure.  
* Aspose.Words for Python via .NET installé (`pip install aspose-words`).  
* Permission d'écriture sur le répertoire de sortie que vous spécifiez.  

Si vous n'avez pas encore installé Aspose.Words, exécutez :

```bash
pip install aspose-words
```

## Comment enregistrer un PNG avec Aspose.Words

La première étape majeure consiste à créer un document et un `DocumentBuilder`. Le builder vous offre une API fluide pour insérer du contenu tel que des formes, des tableaux ou du texte.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` représente l'intégralité du fichier Word en mémoire. `aw.DocumentBuilder` pointe vers l'emplacement d'insertion actuel, qui est initialement le début de la première (et unique) section.

## Ajouter une ombre à la forme avant l'exportation

Une forme peut être n'importe quel objet de dessin — rectangle, ellipse ou polygone personnalisé. Ici, nous créons un rectangle de 100 × 100 points et appliquons une ombre douce.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Pourquoi configurer l'ombre avant l'enregistrement ? Aspose.Words rend l'ombre pendant les phases d'exportation PDF et PNG, de sorte que l'effet visuel est conservé dans les deux formats de sortie.

### Astuce pro
Si vous avez besoin d'une ombre plus nette, réduisez `blur`. Pour un décalage plus prononcé, augmentez `distance`. La classe `Shadow` expose également `angle` et `transparency` pour un contrôle précis.

## Enregistrer le document au format PDF

Enregistrer un document Word au format PDF ne nécessite qu'une seule ligne une fois le contenu prêt. La constante `SaveFormat.PDF` indique à Aspose.Words d'effectuer la conversion.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Le PDF résultant contient le rectangle avec l'ombre exacte que vous avez définie. Aspose.Words gère les graphiques vectoriels, de sorte que la taille du PDF reste modeste.

## Exporter Word en PNG

L'exportation en PNG crée une image raster de chaque page. Par défaut, Aspose.Words utilise 96 DPI ; vous pouvez augmenter cette valeur pour une sortie à plus haute résolution en fournissant un objet `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Lorsque vous **export Word to PNG**, chaque page est enregistrée comme un fichier PNG distinct. Comme notre document d'exemple ne comporte qu'une seule page, un seul fichier PNG apparaît.

### Optionnel : PNG à haute résolution

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Un DPI plus élevé est utile lorsque le PNG sera utilisé pour l'impression ou lorsque vous avez besoin d'une vignette nette.

## Script complet – copier, coller et exécuter

Ci-dessous se trouve le script complet et autonome qui implémente chaque étape décrite ci‑dessus. Enregistrez‑le sous le nom `generate_assets.py` et exécutez‑le depuis la ligne de commande.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Sortie attendue

L'exécution du script crée trois fichiers :

* `output/output.pdf` – un PDF avec un rectangle projetant une ombre noire.  
* `output/output.png` – un rendu PNG à 96 DPI de la même page.  
* `output/high_res_output.png` – un PNG à 300 DPI pour une qualité supérieure.

Ouvrez l'un des fichiers avec votre visionneuse préférée pour vérifier que l'ombre apparaît exactement comme définie.

## Questions fréquentes et cas particuliers

**Que se passe-t-il si le répertoire de sortie n'existe pas ?**  
Le script appelle `os.makedirs(output_dir, exist_ok=True)`, ce qui crée le dossier automatiquement. Cela empêche une `FileNotFoundError` lors des opérations d'enregistrement.

**Puis‑je ajouter plusieurs formes avec des ombres différentes ?**  
Oui. Créez des objets `Shape` supplémentaires, configurez chaque propriété `shadow` indépendamment, et insérez‑les avec `builder.insert_node(shape)` avant l'enregistrement.

**L'ombre sera‑t‑elle conservée lors de la conversion vers d'autres formats raster (par ex., JPEG) ?**  
Aspose.Words rend l'ombre pour tous les formats raster pris en charge par `SaveFormat`. Vous pouvez remplacer `aw.SaveFormat.PNG` par `aw.SaveFormat.JPEG` et l'ombre apparaîtra toujours.

**En quoi cela diffère‑t‑il de « convert word to pdf » ?**  
`convert word to pdf` est essentiellement la même opération effectuée à l'étape 4. Le même appel `doc.save` avec `SaveFormat.PDF` gère la conversion en interne, en préservant la mise en page, les polices et les graphiques tels que les ombres.

**Existe‑t‑il une limite de taille pour les formes ?**  
Les formes sont mesurées en points (1 pt ≈ 1/72 pouce). Des dimensions très grandes peuvent augmenter la taille du fichier résultant, mais Aspose.Words n'impose aucune limite stricte. Ajustez les arguments `width` et `height` lors de la construction de `aw.Shape` pour convenir à votre mise en page.

## Conclusion

Vous savez maintenant **how to save PNG** depuis un document Word tout en apprenant à **add shadow to shape**, **save document as PDF**, et **export Word to PNG** en utilisant Aspose.Words for Python. Le script complet montre un modèle propre et réutilisable que vous pouvez adapter à des documents plus volumineux, plusieurs pages ou des effets graphiques plus complexes.

Les prochaines étapes pourraient inclure :

* Expérimenter d'autres valeurs `ShapeType` (ellipse, nuage, etc.).  
* Using `

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et à explorer des approches d'implémentation alternatives dans vos propres projets.

- [Tutoriel Aspose.Words sur l'ombre des formes – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Comment convertir DOCX en PNG en Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Enregistrer des documents Word en PostScript en Python avec Aspose.Words : Guide complet](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}