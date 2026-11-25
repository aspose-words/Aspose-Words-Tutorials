---
category: general
date: 2026-11-25
description: Ajoutez une ombre à une forme dans un document Word avec Python. Apprenez
  comment insérer une forme rectangulaire dans Word et appliquer une ombre transparente
  à l’aide d’Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: fr
lastmod: 2026-11-25
og_description: Ajouter une ombre à une forme dans un document Word à l’aide de Python.
  Ce tutoriel montre comment insérer une forme rectangulaire dans Word et définir
  une ombre transparente à 30 % avec Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Ajouter une ombre à une forme dans un document Word avec Python – guide
  étape par étape
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Comment ajouter une ombre à une forme dans un document Word avec Python
url: /fr/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter une ombre à une forme dans un document Word avec Python

Si vous devez **ajouter une ombre à une forme** dans un document Word, ce guide vous montre une solution complète et exécutable. Vous verrez comment créer un fichier Word, insérer une forme rectangulaire et appliquer une ombre à 30 % de transparence — le tout avec la bibliothèque Aspose.Words for Python.

Travailler avec des documents Word de façon programmatique vous évite le formatage manuel et vous permet de générer des rapports, contrats ou flyers marketing à grande échelle. À la fin de ce tutoriel, vous pourrez répondre à « **comment créer un document Word python** » avec un exemple de code prêt à l’emploi.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Python 3.8 ou une version plus récente installé.
* Une licence active d’Aspose.Words for Python (l’essai gratuit suffit pour l’évaluation).
* Le package `aspose-words` installé via `pip install aspose-words`.
* Un dossier où le fichier de sortie pourra être écrit (remplacez `YOUR_DIRECTORY` dans le code).

Aucune dépendance supplémentaire n’est requise.

## Étape 1 : Créer un nouveau document Word

La première étape consiste à instancier un objet `Document`. Cet objet représente l’ensemble du fichier .docx en mémoire.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` fonctionne comme un curseur virtuel. Lorsque vous appelez ses méthodes, la bibliothèque insère les éléments correspondants à la position actuelle du curseur.

## Étape 2 : Insérer une forme rectangulaire

Ensuite, vous **insérez une forme rectangulaire** à l’aide de la méthode `insert_shape` du builder. La méthode nécessite le type de forme et ses dimensions en points (1 point = 1/72 pouce).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Vous pouvez modifier les dimensions pour qu’elles correspondent à votre conception. Le rectangle devient partie de la couche de dessin du document, ce qui signifie que vous pourrez plus tard modifier son remplissage, son contour ou son ombre.

## Étape 3 : Accéder au format d’ombre de la forme

Chaque objet de dessin expose une propriété `shadow_format` qui contrôle l’apparence de l’ombre. Récupérez‑la afin de pouvoir ajuster la transparence, le décalage, le flou et la couleur.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

À ce stade, la forme possède l’ombre par défaut (aucune ombre). L’objet `ShadowFormat` contient tous les paramètres nécessaires pour créer un effet réaliste.

## Étape 4 : Rendre l’ombre à 30 % transparente

La transparence s’exprime par une valeur comprise entre `0` (opaque) et `1` (transparent). La définir à `0.3` donne une ombre à 30 % de transparence, ce qui suffit généralement à ajouter de la profondeur sans submerger le texte.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Ces propriétés supplémentaires ne sont pas obligatoires, mais elles illustrent comment affiner l’effet. Le drapeau `visible` est essentiel ; si vous l’oubliez, l’ombre n’apparaîtra pas même si les autres réglages sont configurés.

## Étape 5 : Enregistrer le document pour voir le résultat

Enfin, écrivez le document sur le disque. L’ouverture du fichier `.docx` résultant dans Microsoft Word ou tout visualiseur compatible montre le rectangle avec l’ombre transparente appliquée.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Lorsque vous ouvrirez `output.docx`, vous verrez un simple rectangle avec une ombre grise subtile décalée vers le bas‑à‑droite. La transparence de 30 % de l’ombre fait paraître la forme comme soulevée de la page.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Exemple d’ajout d’ombre à une forme dans un document Word créé avec Python"}

## Script complet et exécutable

Assembler toutes les pièces donne un script autonome que vous pouvez copier, coller et exécuter immédiatement.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Résultat attendu :** L’ouverture du `output.docx` généré affiche une page unique contenant un rectangle qui projette une ombre légère et semi‑transparente. Aucun formatage supplémentaire n’est requis.

## Variantes courantes et cas limites

| Situation | Comment adapter le code |
|-----------|--------------------------|
| **Type de forme différent** (par ex., ellipse) | Remplacez `aw.drawing.ShapeType.RECTANGLE` par `aw.drawing.ShapeType.ELLIPSE`. |
| **Couleur d’ombre personnalisée** | Définissez `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` pour une ombre rougeâtre. |
| **Plusieurs formes** | Appelez `builder.insert_shape` plusieurs fois ; chaque appel renvoie un objet `Shape` distinct que vous pouvez styliser indépendamment. |
| **Enregistrement en PDF** | Remplacez `doc.save(output_path)` par `doc.save(output_path.replace('.docx', '.pdf'))` et utilisez l’extension `.pdf`. |
| **Exécution sans licence** | L’essai gratuit ajoute un filigrane à la première page. Procurez‑vous une licence pour le supprimer en production. |

Ces variantes montrent que le même schéma — créer un document, insérer une forme, ajuster `shadow_format`, enregistrer — couvre la plupart des scénarios d’automatisation.

## Astuces et bonnes pratiques

* **Réutiliser le builder** : Conservez une seule instance de `DocumentBuilder` pour tout le document afin d’éviter la création d’objets superflus.
* **Libérer les ressources** : Dans des services de longue durée, appelez `doc.dispose()` après l’enregistrement pour libérer la mémoire native.
* **Valider la sortie** : Utilisez `doc.validate(aw.ValidationType.FULL_VALIDATION)` avant d’enregistrer si vous devez garantir la conformité au standard Open XML.
* **Compatibilité des versions** : Le code fonctionne avec Aspose.Words for Python ≥ 22.9. Assurez‑vous que votre package est à jour avec `pip install --upgrade aspose-words`.

## Conclusion

Vous savez maintenant comment **ajouter une ombre à une forme** dans un document Word en utilisant Python. En suivant les cinq étapes — créer un document, **insérer une forme rectangulaire**, configurer l’ombre et enregistrer — vous pouvez automatiser la génération de documents soignés pour des rapports, factures ou supports marketing.

À partir d’ici, vous pourrez explorer d’autres options de formatage comme les remplissages en dégradé, le texte enroulé, ou la conversion du document en PDF. Chacun de ces sujets s’appuie sur les mêmes concepts de `DocumentBuilder` et de mise en forme de forme présentés dans ce tutoriel.

Bon codage, et profitez de la profondeur visuelle qu’une simple ombre peut apporter à vos documents Word automatisés !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}