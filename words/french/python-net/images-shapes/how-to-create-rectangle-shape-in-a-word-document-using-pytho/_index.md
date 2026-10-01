---
category: general
date: 2026-09-30
description: Apprenez à créer une forme rectangulaire, à appliquer une ombre à la
  forme et à enregistrer le document Word avec la forme en utilisant Aspose.Words
  pour Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: fr
lastmod: 2026-09-30
og_description: Créez rapidement une forme rectangulaire dans un document Word. Ce
  tutoriel montre comment ajouter une forme, appliquer une ombre à la forme, régler
  le flou de l'ombre et enregistrer le document Word avec la forme.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Créer une forme rectangulaire dans Word avec Python – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Comment créer une forme rectangulaire dans un document Word à l'aide de Python
url: /fr/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer une forme rectangulaire dans un document Word avec Python

Si vous devez **créer une forme rectangulaire** dans un fichier Word, ce guide vous montre une solution complète et exécutable. Vous verrez comment ajouter la forme, appliquer un effet d’ombre, ajuster le flou, et enfin **enregistrer le Word avec la forme** afin que le résultat puisse être ouvert dans Microsoft Word ou tout visualiseur compatible.

L’exemple utilise **Aspose.Words for Python via .NET**, une bibliothèque qui vous permet de manipuler des documents Word sans Microsoft Office installé. Aucune expérience préalable avec l’API n’est requise — seulement des connaissances de base en Python.

## Ce que vous allez réaliser

- Insérer un rectangle dans la première section d’un nouveau document.  
- Configurer une ombre douce en définissant son flou, son décalage et sa couleur.  
- Enregistrer le document sur le disque et vérifier le résultat visuel.

## Prérequis

- Python 3.8 ou plus récent.  
- `aspose-words` package installé (`pip install aspose-words`).  
- Permission d’écriture sur le répertoire de sortie.

## Créer une forme rectangulaire et configurer son apparence

La première étape consiste à instancier un document vierge et à y ajouter une forme rectangulaire. La forme servira de canevas pour l’effet d’ombre.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Pourquoi c’est important :**  
Créer le rectangle vous fournit un objet concret (`shape`) que vous pourrez styliser plus tard. Définir des dimensions explicites garantit que la forme apparaît de la même façon sur toutes les plateformes.

## Comment ajouter une forme à un document Word

Bien que le code ci‑above ajoute déjà le rectangle, vous pourriez avoir besoin d’ajouter d’autres formes (par ex., des cercles, des flèches) ultérieurement. Le même schéma s’applique : appelez `append_child` sur le corps du document et transmettez le `ShapeType` souhaité.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Astuce :** Utilisez l’énumération `ShapeType` pour explorer toutes les formes prises en charge. Cela rend votre code lisible et évite les nombres magiques.

## Appliquer une ombre à la forme et définir le flou de l’ombre

Une ombre ajoute de la profondeur et de l’intérêt visuel. La classe `ShadowEffect` vous permet de contrôler le flou, le décalage et la couleur. Ci‑dessous, nous appliquons une ombre noire douce au rectangle.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Pourquoi définir le flou ?**  
`blur` détermine à quel point l’ombre est diffusée. Une valeur basse (par ex., 1.0) donne un bord net, tandis qu’une valeur plus élevée (par ex., 5.0) crée un fondu doux, souvent plus esthétique.

**Cas limite :** Si vous définissez `blur` à 0, l’ombre devient une silhouette solide. Certains visualiseurs peuvent la rendre avec des artefacts d’aliasing, il est donc préférable de choisir une valeur supérieure à 0 pour un rendu plus lisse.

## Enregistrer le Word avec la forme

La persistance du document finalise toutes les modifications. La méthode `save` écrit un fichier `.docx` que tout processeur Word moderne peut ouvrir.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Lorsque vous ouvrez `output.docx`, vous verrez un rectangle positionné à un pouce du coin supérieur gauche, avec une ombre noire douce déplacée de deux points vers la droite et vers le bas. Le flou de l’ombre donne l’impression que la forme est soulevée de la page.

**Conseil pro :** Si vous devez générer de nombreux documents dans une boucle, réutilisez la même instance `Document` et videz son corps entre les itérations pour réduire la consommation de mémoire.

## Variations courantes et dépannage

| Situation | Ce qu’il faut changer | Raison |
|-----------|-----------------------|--------|
| Couleur d’ombre différente | `shadow.color = aw.Color.red` | Utiliser les couleurs de la marque ou mettre en évidence les formes importantes. |
| Décalage d’ombre plus grand | Augmenter `shadow.offset_x`/`offset_y` | Mettre en avant la profondeur pour les maquettes UI. |
| Pas d’ombre du tout | Omettre la ligne `shape.shadow = shadow` | Utile pour les rapports minimalistes. |
| Exporter en PDF au lieu de DOCX | `doc.save("output.pdf")` | Le PDF est idéal pour une distribution en lecture seule. |

Si la forme n’apparaît pas, vérifiez que vous l’ajoutez à la bonne section (`get_first_section()`) et que le document est enregistré après les modifications.

## Exemple complet et exécutable

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

L’exécution du script produit `output.docx` contenant le rectangle avec une ombre douce. Ouvrez le fichier dans Microsoft Word pour confirmer que l’effet visuel correspond à la description.

## Conclusion

Vous savez maintenant comment **créer une forme rectangulaire**, **ajouter une forme** à un document Word, **appliquer une ombre à la forme**, **définir le flou de l’ombre**, et enfin **enregistrer le Word avec la forme** en utilisant Aspose.Words for Python. Le même schéma peut être étendu à d’autres types de formes, couleurs et effets, vous offrant un contrôle complet sur les graphiques du document sans dépendre de l’automatisation Office.

**Étapes suivantes**

- Expérimentez avec `Shape.fill` pour ajouter des arrière-plans en dégradé ou image.  
- Utilisez des objets `Paragraph` pour placer du texte à l’intérieur du rectangle.  
- Combinez plusieurs formes pour créer des diagrammes complexes, puis exportez en PDF pour la distribution.  

N'hésitez pas à adapter le code à vos besoins de reporting ou de templating, et partagez vos résultats dans les commentaires !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangulaire avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Créer une forme rectangulaire, ajouter une ombre & enregistrer en PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Tutoriel Ombre de forme Aspose.Words – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}