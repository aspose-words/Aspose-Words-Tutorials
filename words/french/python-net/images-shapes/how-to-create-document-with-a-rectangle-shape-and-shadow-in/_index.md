---
category: general
date: 2026-10-04
description: Comment créer un document en Python et ajouter une ombre à une forme
  avec Aspose.Words. Apprenez à définir la couleur de l’ombre, insérer une forme rectangulaire
  et personnaliser l’ombre extérieure.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: fr
lastmod: 2026-10-04
og_description: Comment créer un document en Python et ajouter une ombre à une forme.
  Ce guide vous montre comment définir la couleur de l’ombre, insérer une forme rectangulaire
  et appliquer une ombre externe avec Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Comment créer un document avec une forme rectangulaire et une ombre en Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Comment créer un document avec une forme rectangulaire et une ombre en Python
url: /fr/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document avec une forme rectangulaire et une ombre en Python

Si vous avez besoin de **how to create document** contenant un rectangle stylisé, ce guide fournit une solution complète. Vous verrez comment **add shadow to shape**, définir la couleur de l’ombre et contrôler son décalage ainsi que son flou — le tout avec Aspose.Words for Python. À la fin du tutoriel, vous pourrez générer un fichier `.docx` au rendu soigné et prêt à être distribué.

Les étapes ci‑dessous couvrent tout, de l’installation de la bibliothèque à la personnalisation de l’apparence de l’ombre. Aucun document externe n’est requis ; le code est prêt à être copié, exécuté et adapté à vos propres projets. Vous apprendrez également à **insert rectangle shape**, choisir un **outer shadow style**, et gérer les problèmes courants tels que les ombres invisibles ou les paramètres d’habillage incorrects.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Python 3.8 ou une version plus récente installé.
* Une licence active d’Aspose.Words for Python (ou une clé d’évaluation gratuite).
* Une connaissance de base du scripting Python.
* Un accès à un emplacement du système de fichiers où le document généré sera enregistré.

Vous pouvez installer le SDK avec pip :

```bash
pip install aspose-words
```

## Étape 1 : Importer la bibliothèque et créer un nouveau document vierge

Créer un nouveau document est la première action dans tout scénario d’automatisation Word. Le constructeur `aw.Document()` vous fournit un fichier vide que vous pouvez remplir avec du texte, des images ou des formes.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

L’objet `DocumentBuilder` simplifie l’insertion de contenu. Il suit la position actuelle du curseur, vous permettant d’ajouter des éléments séquentiellement sans gérer manuellement les sections.

## Étape 2 : Insérer une forme rectangulaire de la taille souhaitée

Une forme rectangulaire agit comme un conteneur pour les éléments visuels. Vous pouvez définir sa largeur et sa hauteur en points (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

À ce stade, la forme n’a aucun style visuel, elle apparaît donc comme un simple contour. Les étapes suivantes lui donneront profondeur et couleur.

## Étape 3 : Configurer la forme pour qu’elle s’écoule en ligne avec le texte environnant

Lorsqu’une forme est **inline**, elle se comporte comme un caractère dans un paragraphe. Cela garantit que le rectangle reste à l’endroit attendu dans la mise en page du document.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Si vous préférez que la forme flotte au-dessus du texte, vous pouvez utiliser `WrapType.SQUARE` ou `WrapType.TOP_BOTTOM`, mais pour la plupart des rapports, une forme en ligne rend la mise en page prévisible.

## Étape 4 : Rendre l’ombre visible et choisir sa couleur

Une ombre qui n’est pas visible n’apporte aucun bénéfice visuel. Le drapeau `visible` active l’effet, et la propriété `color` détermine sa teinte. Utiliser le noir donne une profondeur classique et subtile.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Vous pouvez remplacer `aw.drawing.Color.black` par n’importe quelle autre couleur, comme `aw.drawing.Color.gray` ou une valeur RGB personnalisée (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Étape 5 : Définir le décalage et le flou de l’ombre pour lui donner de la profondeur

Le décalage contrôle la distance à laquelle l’ombre est déplacée par rapport à la forme, tandis que le rayon de flou adoucit les bords. De petites valeurs créent une ombre nette ; des valeurs plus grandes produisent un rendu plus doux.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Expérimentez avec ces nombres pour correspondre à vos directives de conception. Pour une ombre portée importante, vous pouvez augmenter à la fois le décalage et le flou.

## Étape 6 : Choisir un style d’ombre extérieure

Aspose.Words propose plusieurs styles d’ombre, tels que `INNER`, `OUTER` et `PERSPECTIVE`. Le style **outer** place l’ombre à l’extérieur de la bordure de la forme, idéal pour un rendu propre et professionnel.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Si vous avez besoin d’un effet plus dramatique, essayez `ShadowStyle.PERSPECTIVE` — il ajoute une inclinaison tridimensionnelle.

## Étape 7 : Enregistrer le document avec la forme ombrée

L’enregistrement finalise le fichier et écrit tous les formats sur le disque. Choisissez un répertoire où vous avez les droits d’écriture et donnez au fichier un nom descriptif.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

L’exécution du script produit un fichier Word contenant un rectangle avec une ombre visible et colorée. Ouvrez le fichier dans Microsoft Word ou LibreOffice pour vérifier le résultat.

## Exemple complet exécutable

Voici le script complet qui intègre chaque étape décrite. Copiez le code dans un fichier nommé `create_shadowed_shape.py` et exécutez‑le avec `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Résultat attendu**

Lorsque vous ouvrez `ShapeWithShadow.docx`, vous verrez un seul rectangle centré sur la page. Le rectangle est accompagné d’une subtile ombre noire décalée vers le bas‑à‑droite, légèrement floutée pour créer de la profondeur. L’ombre respecte le style extérieur, de sorte qu’elle n’intersecte pas l’intérieur du rectangle.

## Questions fréquentes et cas limites

### Pourquoi l’ombre apparaît‑elle parfois invisible ?

L’ombre n’est rendue que si `shadow.visible` est défini sur `True` **et** que le `wrap_type` de la forme le permet. Une forme en ligne fonctionne de façon fiable ; les formes flottantes peuvent nécessiter des ajustements supplémentaires de la mise en page.

### Comment changer la couleur de l’ombre pour correspondre à une palette de marque ?

Remplacez `aw.drawing.Color.black` par une valeur RGB personnalisée :

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Que faire si je veux que la forme apparaisse derrière le texte ?

Définissez le type d’habillage sur `WrapType.BEHIND` et ajustez `z_order_position` si nécessaire. Gardez à l’esprit que certains visionneurs peuvent rendre les formes « derrière le texte » différemment.

### Puis‑je appliquer les mêmes paramètres d’ombre à plusieurs formes ?

Oui. Créez une fonction d’assistance qui configure l’ombre et appelez‑la pour chaque forme que vous insérez. Cela favorise la réutilisation du code et garantit une cohérence de style.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusion

Vous savez maintenant **how to create document** contenant une forme rectangulaire avec une ombre personnalisée grâce à Aspose.Words for Python. Le tutoriel a couvert l’insertion d’un rectangle, la mise en ligne de la forme, l’activation de l’ombre, la définition de sa couleur, de son décalage, de son flou et de son style, puis l’enregistrement du fichier.

À partir d’ici, vous pouvez explorer des sujets connexes tels que **add shadow to shape** pour d’autres types de formes, **set shadow color** dynamiquement en fonction des données, ou **how to add shadow** aux images et zones de texte. Expérimentez avec différentes dimensions, couleurs et styles d’ombre pour respecter vos directives de marque ou votre système de design.

Prêt à automatiser davantage de documents Word ? Essayez d’ajouter des tableaux, des en‑têtes ou du contenu dynamique — chaque étape s’appuie sur les mêmes principes démontrés ici. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos projets.

- [Créer une forme rectangulaire, ajouter une ombre & enregistrer en PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Créer un document Word vierge avec une forme rectangulaire ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Comment gérer les variables de document avec Aspose.Words en Python : guide complet](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}