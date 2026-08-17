---
category: general
date: 2026-08-17
description: Enregistrez le document en tant qu'image et exportez toutes les pages
  au format PNG avec Aspose.Words pour Python. Apprenez à convertir un DOCX en PNG
  en une seule commande.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as image
- convert docx to png
- export docx to png
- export all pages png
- export word pages image
language: fr
lastmod: 2026-08-17
og_description: Enregistrez le document en tant qu'image et exportez toutes les pages
  au format PNG avec Aspose.Words pour Python. Ce guide montre comment convertir un
  DOCX en PNG de manière efficace.
og_image_alt: Diagram showing a multi‑page Word document converted into a single PNG
  grid preview
og_title: Enregistrer le document en image et convertir DOCX en PNG avec Python
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  headline: 'Save document as image: convert DOCX to PNG in Python'
  type: TechArticle
- description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  name: 'Save document as image: convert DOCX to PNG in Python'
  steps:
  - name: '**Save format** – PNG is lossless and widely supported.'
    text: '**Save format** – PNG is lossless and widely supported.'
  - name: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
    text: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
  - name: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
    text: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
  type: HowTo
tags:
- Aspose.Words
- Python
- DOCX
title: 'Enregistrer le document en tant qu’image : convertir DOCX en PNG avec Python'
url: /fr/python/document-conversion/save-document-as-image-convert-docx-to-png-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer le document en tant qu'image : convertir DOCX en PNG avec Python

Si vous devez **save document as image** et générer un aperçu unique pour un fichier Word multi‑pages, ce guide vous montre comment le faire avec Aspose.Words for Python. Vous apprendrez également comment **convert DOCX to PNG** en une opération simple.

Exporter chaque page d'un document Word en PNG peut être fastidieux si vous écrivez vous‑même une boucle. Aspose.Words fournit des options intégrées qui vous permettent de **export all pages PNG** en un seul appel, tout en vous offrant un contrôle sur la mise en page, la résolution et la plage de pages. À la fin de ce tutoriel, vous disposerez d'un script prêt à l'exécution qui produit un PNG de type grille contenant toutes les pages du document source.

## Prérequis

* Python 3.8 ou version plus récente installé.
* Le package `aspose-words` (`pip install aspose-words`).
* Un fichier Word (`.docx`) contenant au moins deux pages.
* Permission d'écriture sur le répertoire où vous souhaitez stocker le PNG résultant.

Aucun outil externe supplémentaire n'est requis ; Aspose.Words gère la conversion entièrement en mémoire.

## Étape 1 : Charger le document Word

La première étape consiste à créer un objet `aw.Document` qui représente le fichier DOCX source. Cet objet vous donne accès à toutes les pages, sections et ressources du document.

```python
import aspose.words as aw

# Load the multi‑page Word document
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)
```

*Pourquoi c'est important* : charger le document une fois vous fournit un modèle d'objet complet que Aspose.Words pourra ensuite rendre dans n'importe quel format d'image pris en charge. La classe `aw.Document` valide également le fichier, vous obtenant ainsi un retour précoce si le DOCX est corrompu.

## Étape 2 : Créer les options d'enregistrement PNG et les configurer

Aspose.Words utilise `ImageSaveOptions` pour contrôler la façon dont un document est rasterisé. Dans cette étape, nous définissons trois propriétés importantes :

1. **Save format** – PNG est sans perte et largement supporté.
2. **Page set** – définit la plage de pages à exporter ; en utilisant `0, document.page_count` on capture chaque page.
3. **Layout** – `GRID` organise toutes les pages exportées en une seule image, ce qui est idéal pour les scénarios d'aperçu.

```python
# Configure PNG export options
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export all pages (page index starts at 0)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid layout (rows × columns are auto‑calculated)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: increase resolution for sharper output (default is 96 DPI)
png_options.resolution = 150  # DPI
```

*Pourquoi c'est important* : définir `page_set` sur la plage complète vous permet de **export docx to png** sans itérer manuellement sur les pages. La mise en page `GRID` produit une image unique contenant chaque page côte à côte, répondant à l'exigence **export word pages image** de façon compacte. Ajuster `resolution` aide lorsque le document source contient des détails fins.

## Étape 3 : Enregistrer le document en tant qu'aperçu PNG unique

Avec les options préparées, l'enregistrement se fait en une seule ligne. Aspose.Words écrit le fichier PNG sur le disque en utilisant les paramètres définis ci‑dessus.

```python
# Destination path for the combined PNG image
output_path = "YOUR_DIRECTORY/preview.png"

# Perform the export – this creates one PNG that contains all pages
document.save(output_path, png_options)
print(f"Document successfully saved as image: {output_path}")
```

**Sortie attendue**

L'exécution du script crée `preview.png`. Si le DOCX source contenait trois pages, le PNG affichera ces trois pages disposées en grille (par ex., 2 × 2 avec la dernière case vide). Ouvrir le fichier dans n'importe quel visualiseur d'images confirme que chaque page a été rasterisée correctement.

### Astuce pro

Si vous avez besoin uniquement d'un sous‑ensemble de pages, modifiez les arguments de `PageSet`, par exemple :

```python
# Export pages 2‑4 only (zero‑based index)
png_options.page_set = aw.saving.PageSet(1, 4)
```

Cela respecte toujours la logique **export all pages png** pour la plage sélectionnée, réduisant l'utilisation de mémoire pour les documents très volumineux.

## Gestion des documents volumineux et des contraintes de mémoire

Lorsque vous travaillez avec des documents contenant des dizaines ou des centaines de pages, le PNG généré peut devenir volumineux. Considérez ces stratégies :

* **Increase `resolution` only as needed** – un DPI plus élevé produit des fichiers plus gros.
* **Use `PageLayout.SINGLE_COLUMN`** – crée une bande verticale au lieu d'une grille, ce qui peut être plus facile à faire défiler.
* **Stream the output** – Aspose.Words prend également en charge l'enregistrement vers un flux `BytesIO` si vous devez envoyer l'image sur le réseau sans écrire sur le disque.

```python
import io

stream = io.BytesIO()
document.save(stream, png_options)
# Now `stream.getvalue()` holds the PNG bytes
```

## Script complet pour copier‑coller rapidement

Ci‑dessous se trouve l'exemple complet et exécutable qui intègre toutes les étapes abordées. Remplacez `YOUR_DIRECTORY` par le chemin réel du dossier sur votre machine.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# 1. Load the source DOCX file
# ----------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)

# ----------------------------------------------------------------------
# 2. Configure PNG export options (save document as image)
# ----------------------------------------------------------------------
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export every page (export docx to png)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid (export word pages image)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: higher DPI for sharper output
png_options.resolution = 150

# ----------------------------------------------------------------------
# 3. Save the combined PNG file
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/preview.png"
document.save(output_path, png_options)

print(f"Document successfully saved as image: {output_path}")
```

L'exécution de ce script produit un PNG unique contenant toutes les pages de `multi_page.docx`. Cette approche fonctionne avec n'importe quel fichier DOCX, quelle que soit la complexité du contenu (tableaux, images, mises en page complexes).

## Conclusion

Vous savez maintenant comment **save document as image**, **convert DOCX to PNG**, et **export all pages PNG** en utilisant Aspose.Words for Python. En exploitant `ImageSaveOptions`, vous évitez les boucles manuelles, obtenez un aperçu de type grille, et conservez le contrôle sur la résolution et la mise en page.  

Ensuite, vous pourriez explorer :

* Exporter vers d'autres formats raster (JPEG, BMP) – il suffit de changer `SaveFormat`.
* Ajouter des filigranes ou des annotations avant l'export – manipuler l'objet `Document`.
* Intégrer ce script dans un service web pour générer des aperçus à la volée.

Expérimentez avec différentes valeurs de `layout` et `resolution` pour trouver le compromis qui convient le mieux aux exigences de performance et de qualité de votre application. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Optimiser la gestion des images RTF en Python avec l'API Aspose.Words : enregistrer au format WMF et garantir la compatibilité](/words/english/python-net/images-shapes/optimize-rtf-image-handling-aspose-words-python/)
- [Convertir DOCX en XAML à forme fixe en Python avec Aspose.Words : guide complet](/words/english/python-net/document-operations/python-docx-to-xaml-aspose-tutorial/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}