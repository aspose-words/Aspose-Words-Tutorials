---
category: general
date: 2026-11-18
description: L'exemple d'ombre de forme Aspose.Words montre comment ajouter une ombre
  à une forme Word en utilisant Python. Suivez ce guide étape par étape pour modifier
  et enregistrer le document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: fr
lastmod: 2026-11-18
og_description: L'exemple d'ombre de forme Aspose.Words montre comment ajouter une
  ombre à une forme Word avec Python. Découvrez le code complet, pourquoi chaque étape
  est importante et comment l'adapter.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Exemple d'ombre de forme Aspose.Words – Guide Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Exemple d'ombre de forme Aspose.Words en Python
url: /fr/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exemple d'ombre de forme Aspose.Words en Python

L'exemple d'ombre de forme Aspose.Words montre comment ajouter un effet d'ombre à une forme dans un document Word en utilisant Python. Dans ce tutoriel, vous obtiendrez un script complet et exécutable qui charge un document, configure l'ombre et enregistre le résultat.

Appliquer une ombre à une forme est un moyen courant d'améliorer la hiérarchie visuelle dans les rapports, brochures ou factures. Le code ci‑dessous fonctionne avec Aspose.Words for Python via .NET et ne nécessite aucune bibliothèque tierce supplémentaire.

## Ce que vous allez apprendre

* Comment charger un fichier `.docx` avec **Aspose.Words for Python**.  
* Comment localiser la première forme (y compris les formes à l'intérieur des tableaux ou des groupes).  
* Comment configurer le flou, le décalage horizontal et le décalage vertical de l'ombre.  
* Comment enregistrer le document modifié tout en préservant tout le reste du contenu.  

**Prérequis**

* Python 3.8 ou version ultérieure.  
* Aspose.Words for Python via .NET installé (`pip install aspose-words`).  
* Un document Word (`input.docx`) contenant au moins une forme (par ex., une image, AutoShape ou une zone de texte).  

Si vous devez installer la bibliothèque, exécutez :

```bash
pip install aspose-words
```

## Exemple d'ombre de forme Aspose.Words – aperçu

Le script suivant est la solution complète. Il suit les quatre étapes logiques d'un flux de travail typique de **manipulation de documents Aspose** : charger, localiser, modifier et enregistrer.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Résultat attendu

Ouvrez `output.docx` dans Microsoft Word. La première forme que vous avez ajoutée devrait maintenant afficher une ombre douce décalée de 2 pt horizontalement et verticalement, avec un rayon de flou de 5 pt. Tout le reste du contenu reste inchangé.

## Étape 1 : Charger le document Word

Charger un document est la première opération dans tout flux de travail **Aspose.Words for Python**. La classe `Document` analyse le fichier et construit un modèle d'objet en mémoire. Comme la bibliothèque fonctionne sur la plateforme .NET, elle peut gérer efficacement les gros fichiers.

*Pourquoi c'est important :* Charger le document une fois et conserver une référence (`doc`) évite des entrées/sorties répétées, ce qui améliore les performances lorsque vous devez appliquer plusieurs modifications.

## Étape 2 : Accéder à la forme

Les formes peuvent être des enfants directs du corps du document, ou être imbriquées à l'intérieur de tableaux, de groupes ou de canevas de dessin. L'utilisation de `get_child(NodeType.SHAPE, 0, True)` effectue une recherche récursive et renvoie la première forme correspondante.

*Pourquoi c'est important :* Le drapeau `True` garantit que vous ne manquez pas les formes cachées à l'intérieur d'autres nœuds. Si vous l'omettez, seules les formes de niveau supérieur seraient prises en compte, et de nombreux documents réels renverraient `None`.

### Alternative : Trouver une forme par son nom

Si votre document contient plusieurs formes, vous pourriez préférer localiser une forme spécifique :

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Cet extrait montre une variante **python shape shadow** qui filtre par la propriété `name` de la forme.

## Étape 3 : Configurer l'ombre de la forme

La propriété `shadow` d'un objet `Shape` vous donne un contrôle fin sur l'effet visuel. Les trois attributs les plus couramment ajustés sont :

| Propriété | Plage typique | Impact visuel |
|-----------|---------------|---------------|
| `blur`    | 0 – 15        | Des valeurs plus élevées créent un bord plus doux. |
| `offset_x`| –10 – 10      | Des valeurs positives déplacent l'ombre vers la droite. |
| `offset_y`| –10 – 10      | Des valeurs positives déplacent l'ombre vers le bas. |

Vous pouvez également modifier `color`, `transparency`, `visible` et `style`. L'exemple définit un flou modeste et un léger décalage pour garder l'ombre subtile.

**Astuce :** Lorsqu'une forme possède déjà une ombre, les propriétés ci‑dessus écrasent les paramètres existants. Si vous devez préserver le style original, lisez les valeurs actuelles avant de les modifier.

## Étape 4 : Enregistrer le document modifié

Appeler `doc.save()` écrit la représentation en mémoire dans un fichier `.docx`. Aspose.Words met automatiquement à jour toutes les relations internes, de sorte que le fichier de sortie reste entièrement compatible avec Microsoft Word.

*Pourquoi c'est important :* Enregistrer une seule fois à la fin du processus réduit le risque de corruption du fichier et améliore la vitesse globale, surtout lors du traitement de nombreux documents dans un travail par lots.

## Variations courantes et cas limites

### Travailler avec plusieurs formes

Si vous devez appliquer la même ombre à chaque forme, itérez sur la collection de nœuds :

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Appliquer une ombre à un type de forme spécifique

Vous pouvez filtrer par `ShapeType` (par ex., `aw.ShapeType.IMAGE`). Cela est utile lorsque vous ne voulez affecter que les images, pas les AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Gérer les documents sans formes

Le script lève déjà une `ValueError` claire si aucune forme n'est trouvée. Dans le code de production, vous pourriez consigner le problème et continuer à traiter d'autres fichiers.

### Notes de compatibilité

* Le code fonctionne avec **Aspose.Words for Python via .NET** version 23.10 et ultérieure.  
* L'effet d'ombre est pris en charge dans Word 2007+ (`.docx`). Les formats plus anciens (`.doc`) perdront l'effet après conversion.

## Conclusion

Cet **exemple d'ombre de forme aspose.words** vous guide à travers le chargement d'un fichier Word, la localisation d'une forme, la configuration de son ombre et l'enregistrement du résultat avec **Aspose.Words for Python**. Vous disposez désormais d'un modèle réutilisable pour tout scénario de **manipulation de documents Aspose** impliquant des améliorations visuelles.

Ensuite, vous pourriez explorer :

* Ajouter des remplissages en dégradé ou des styles de ligne aux formes (`modify shape shadow` et autres propriétés visuelles).  
* Combiner la configuration de l'ombre avec le formatage du texte pour créer des modèles entièrement stylisés.  
* Automatiser le processus pour un lot de documents en utilisant `os.listdir` et le modèle présenté ci‑dessus.

N'hésitez pas à expérimenter différents niveaux de flou, décalages et couleurs pour correspondre à vos directives de marque. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Ajouter une ombre à une forme en Python – Tutoriel complet Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Comment définir une ombre sur une forme dans Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [Comment enregistrer un PNG et ajouter une ombre à une forme avec Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}