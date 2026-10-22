---
category: general
date: 2026-09-27
description: Apprenez à définir l’ombre sur une forme avec Aspose.Words pour Python.
  Ce guide couvre l’ajout d’ombre à une forme, l’application d’un effet d’ombre et
  la définition de la couleur de l’ombre.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: fr
lastmod: 2026-09-27
og_description: Comment définir une ombre sur une forme avec Aspose.Words pour Python.
  Suivez le guide étape par étape pour ajouter une ombre à la forme, appliquer l'effet
  d'ombre et définir la couleur de l'ombre.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Comment appliquer une ombre à une forme dans Aspose.Words pour Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Comment définir l'ombre d'une forme dans Aspose.Words pour Python
url: /fr/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment appliquer une ombre à une forme dans Aspose.Words pour Python

Si vous devez **appliquer une ombre** à un objet de dessin, ce guide montre le processus complet. Vous verrez comment ajouter une ombre à une forme, configurer le flou, le décalage et la couleur de l’ombre, puis enregistrer le document mis à jour sans quitter le code.

Le tutoriel suppose que vous avez déjà un environnement de base Aspose.Words pour Python. À la fin de l’article, vous pourrez appliquer un effet d’ombre professionnel à n’importe quelle forme dans un fichier DOCX.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Python 3.8+ installé.
* Aspose.Words pour Python via .NET (`pip install aspose-words`) installé.
* Un document Word (`input.docx`) contenant au moins une forme (par ex., un rectangle ou une image).  
  Si le document est vide, le code créera une nouvelle forme à des fins de démonstration.

Ces éléments garantissent que les étapes suivantes s’exécutent sans erreurs d’importation.

## Étape 1 : Charger ou créer le document Word

La première opération consiste à obtenir un objet `Document`. Vous pouvez soit charger un fichier existant, soit en créer un nouveau.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Pourquoi cette étape est importante* : L’objet `Document` est le point d’entrée pour toutes les opérations de traitement Word. Sans lui, vous ne pouvez pas accéder aux formes ni appliquer d’effets visuels.

## Étape 2 : Récupérer la forme cible

Pour manipuler l’apparence d’une forme, vous avez besoin d’une référence au nœud de forme. L’exemple ci‑dessous récupère la première forme trouvée dans la hiérarchie du document.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Pourquoi cette étape est importante* : `add shadow to shape` nécessite un objet forme concret. Le code gère en toute sécurité le cas où le document ne contient aucune forme, garantissant que le tutoriel fonctionne pour chaque lecteur.

## Étape 3 : Configurer l’apparence de l’ombre

Vous pouvez maintenant **appliquer l’effet d’ombre** en ajustant la propriété `shadow` de la forme. Les paramètres suivants donnent une ombre subtile et sombre.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Pourquoi chaque propriété est importante* :

| Propriété | Effet |
|-----------|-------|
| `blur`   | Contrôle le degré de flou de l’ombre. |
| `offset_x` / `offset_y` | Détermine la direction et la distance par rapport à la forme. |
| `color`  | Définit la teinte de l’ombre ; vous pouvez utiliser n’importe quel `aw.Color`. |
| `visible`| Garantit que l’ombre est rendue dans le fichier de sortie. |

Vous pouvez remplacer `aw.Color.black` par `aw.Color.from_argb(255, 0, 0, 0)` pour une valeur RGBA personnalisée, ou toute autre couleur prédéfinie.

## Étape 4 : Enregistrer le document modifié

Après avoir configuré l’ombre, persistez les modifications dans un nouveau fichier.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Lorsque vous ouvrirez `output.docx` dans Microsoft Word, la forme sélectionnée affichera une douce ombre noire déplacée de 2 pt vers la droite et de 2 pt vers le bas.

## Exemple complet fonctionnel

Assembler toutes les étapes donne un script autonome que vous pouvez copier‑coller dans votre IDE.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

L’exécution du script produit `output.docx` où la première forme possède l’ombre configurée.

## Problèmes courants et comment les éviter

| Problème | Raison | Solution |
|----------|--------|----------|
| `shape` est `None` même après le chargement du document | Le document ne contient aucun objet de dessin. | Utilisez le bloc de création de forme de secours présenté à l’Étape 2. |
| L’ombre n’apparaît pas dans Word | `shape.shadow.visible` laissé à `False` ou le document a été enregistré dans un format ancien (ex., `.doc`). | Assurez‑vous que `visible = True` et enregistrez en `.docx`. |
| La couleur diffère de ce qui était attendu | Le thème du document surcharge les couleurs explicites. | Définissez `shape.shadow.color` après avoir désactivé les surcharges de thème, ou utilisez `aw.Color.from_argb`. |

Traiter ces cas limites rend la solution robuste pour du code en production.

## Extension de l’effet (prochaines étapes)

Maintenant que vous savez **comment ajouter une ombre**, vous pouvez explorer des améliorations connexes :

* **apply shadow effect** avec un dégradé ou plusieurs ombres en ajustant les sous‑propriétés de `shape.shadow`.
* Utiliser **set shadow color** dynamiquement selon l’entrée utilisateur ou les couleurs du thème.
* Combiner **add shadow to shape** avec d’autres actions de formatage telles que la rotation, le style de ligne ou les effets 3‑D.
* Automatiser l’ajout d’ombre pour chaque forme d’un document en itérant sur `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

Ces extensions vous permettent de créer des pipelines de génération de documents sophistiqués produisant des sorties polies et visuellement cohérentes.

## Conclusion

Vous disposez maintenant d’une solution complète et exécutable pour **comment appliquer une ombre** à une forme avec Aspose.Words pour Python. Le guide a couvert le chargement d’un document, la récupération ou la création d’une forme, la configuration du flou, du décalage et du **set shadow color**, puis l’enregistrement du fichier. Appliquez ce modèle à n’importe quelle forme dans vos projets d’automatisation et expérimentez d’autres ajustements visuels pour répondre à vos exigences de conception.

--- 

*N’hésitez pas à adapter le code pour d’autres types de formes, couleurs ou valeurs de décalage. Si vous rencontrez des problèmes, la table « Problèmes courants » constitue un bon point de départ.*

## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Add shadow to shape in C# – Complete Guide to Apply Shadow Effect](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}