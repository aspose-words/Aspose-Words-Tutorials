---
category: general
date: 2026-06-21
description: Créez une forme rectangulaire en Python avec Aspose.Words. Apprenez comment
  ajouter une ombre à la forme, définir la couleur de remplissage de la forme et enregistrer
  le document au format PDF en quelques minutes.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: fr
og_description: Créer une forme rectangulaire en Python avec Aspose.Words. Ce guide
  montre comment ajouter une ombre à la forme, définir la couleur de remplissage de
  la forme et enregistrer le document au format PDF.
og_title: Créer une forme rectangulaire en Python – Tutoriel Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Créer une forme rectangulaire en Python – Tutoriel Aspose.Words
url: /fr/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire en Python – Tutoriel Aspose.Words

Vous vous êtes déjà demandé **comment créer une forme rectangulaire** dans un document Word tout en codant en Python ? Vous n'êtes pas le seul. De nombreux développeurs se heurtent à un mur lorsqu'ils ont besoin d'un élément visuel rapide—comme une boîte colorée avec une ombre subtile—et souhaitent ensuite exporter le tout en PDF.  

Dans ce guide, nous parcourrons un exemple complet et exécutable qui **crée une forme rectangulaire**, **définit la couleur de remplissage de la forme**, **ajoute une ombre à la forme**, et enfin **enregistre le document en PDF**. Pas de références vagues, seulement du code concret que vous pouvez copier‑coller et exécuter dès aujourd'hui.

## Ce dont vous avez besoin

Avant de commencer, assurez-vous d'avoir les éléments suivants sur votre machine :

- Python 3.8 ou plus récent (la syntaxe que nous utilisons fonctionne sur toute version récente).
- Une licence active d'Aspose.Words for Python ou un essai gratuit (la bibliothèque est pure‑Python, aucune interopérabilité COM requise).
- Un éditeur de texte ou un IDE avec lequel vous êtes à l'aise—VS Code fonctionne très bien, mais tout autre convient.

C'est tout. Aucun framework lourd, aucune dépendance supplémentaire au niveau du système d'exploitation. Commençons.

## Étape 1 : Installer Aspose.Words pour Python

Première chose, première étape. Si ce n’est pas déjà fait, récupérez le paquet depuis PyPI :

```bash
pip install aspose-words
```

Pourquoi cette étape est importante : Aspose.Words fournit les classes `Document` et `DocumentBuilder` sur lesquelles nous comptons. Sans la bibliothèque, aucun des appels ultérieurs—comme `insert_shape`—n’existe, donc le script planterait avant même de tracer une ligne.

> **Conseil pro :** Gardez votre environnement virtuel propre. Exécutez `python -m venv .venv && source .venv/bin/activate` avant d’installer, afin que la bibliothèque reste isolée des paquets système.

## Étape 2 : Créer un nouveau Document et un DocumentBuilder

Nous allons maintenant réellement **créer une forme rectangulaire** – mais d'abord nous avons besoin d'une toile vierge.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

L'objet `Document` représente le fichier complet, tandis que `DocumentBuilder` est un assistant pratique qui sait où se trouve le curseur et peut insérer des éléments à cet endroit. Pensez au builder comme à un stylo qui écrit sur la page.

## Étape 3 : Insérer la forme rectangulaire

C’est ici que l’action principale se produit. Nous allons **créer une forme rectangulaire** avec une largeur et une hauteur fixes, puis la positionner sur la page.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Pourquoi un rectangle ? C’est la forme la plus simple qui nous permet tout de même de mettre en avant les couleurs de remplissage et les ombres. Si vous avez besoin d’un cercle ou d’une étoile plus tard, remplacez simplement `ShapeType.RECTANGLE` par une autre valeur d’enumération.

## Étape 4 : Définir la couleur de remplissage de la forme

Une simple boîte blanche n’est pas très excitante, alors définissons la **couleur de remplissage de la forme** à quelque chose de doux—le bleu clair fonctionne bien pour les rapports.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Vous pouvez utiliser n’importe lequel des membres prédéfinis de `aw.Color` (`red`, `green`, `dark_gray`, etc.) ou passer un tuple RGB (`aw.Color.from_argb(255, 30, 144, 255)`). La couleur de remplissage est ce que l'utilisateur voit avant l'application d'une ombre ou d'une bordure.

## Étape 5 : Ajouter une ombre à la forme

Passons maintenant à la finition visuelle : **ajouter une ombre à la forme**. Les ombres donnent de la profondeur et font ressortir le rectangle sur la page.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Comment ajouter une ombre** ? Le code ci‑dessus fait exactement cela, mais détaillons pourquoi chaque propriété est importante :

- `visible` – active ou désactive l’effet.
- `color` – définit la teinte ; un gris foncé imite l’éclairage naturel.
- `blur` – des valeurs plus élevées produisent un bord plus doux.
- `offset_x` / `offset_y` – déplacent l’ombre par rapport à la forme ; ajustez‑les pour simuler différents angles de lumière.
- `transparency` – 0 est opaque, 1 est invisible ; 0,2 donne une impression subtile.
- `type` – `OUTER` projette l’ombre à l’extérieur de la forme, tandis que `INNER` l’incrusterait.

Si vous avez besoin d’une ombre portée dramatique, augmentez `blur` à 10‑15 et poussez `offset_x`/`offset_y` à 6‑8.

## Étape 6 : Enregistrer le document en PDF

Tout ce travail est inutile si nous ne pouvons pas **enregistrer le document en PDF** et le partager. Aspose.Words rend cela possible en une seule ligne :

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Pourquoi le PDF ? Les PDF conservent la mise en page sur toutes les plateformes, ce qui les rend idéaux pour les rapports, factures ou tout autre document imprimable. La méthode `save` détecte automatiquement l’extension du fichier et choisit le bon format—assurez‑vous simplement que le chemin se termine par `.pdf`.

### Résultat attendu

Ouvrez le fichier `ShapeWithShadow.pdf` généré et vous devriez voir un rectangle bleu clair centré près du haut de la première page, avec une ombre gris foncé douce légèrement décalée vers la droite et le bas. Les bords de la forme sont nets, l’ombre est subtile, et la taille du fichier est généralement inférieure à 100 KB.

## Bonus : Ajuster les ombres – Réponses à « comment ajouter une ombre »

Vous vous demandez peut‑être, *« Puis‑je changer la direction de l’ombre sans déplacer la forme ? »* Absolument. La position de l’ombre est indépendante des coordonnées de la forme ; il suffit d’ajuster `offset_x` et `offset_y`. Les valeurs positives déplacent l’ombre vers la droite/bas, les valeurs négatives la déplacent vers la gauche/haut. Pour une source de lumière en haut à gauche, utilisez `offset_x = -3` et `offset_y = -3`.

Une autre question fréquente : *« Et si j’ai besoin de plusieurs ombres sur la même forme ? »* Aspose.Words ne prend en charge qu’une seule ombre par forme. Si vous avez besoin d’effets superposés, créez une forme dupliquée, décalez‑la légèrement, et appliquez une ombre différente à chacune. C’est un petit bricolage, mais cela fonctionne.

## Script complet – Prêt à exécuter

Voici le script complet et autonome. Copiez‑le dans un fichier nommé `create_rectangle_with_shadow.py` et exécutez‑le avec `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Note :** Remplacez `YOUR_DIRECTORY` par un chemin absolu ou relatif qui existe sur votre machine. Si le dossier n’existe pas, Python lèvera une `FileNotFoundError`.

## Pièges courants et comment les éviter

| Problème | Cause | Solution |
|----------|-------|----------|
| Ombre non affichée | `shadow.visible` laissé à la valeur par défaut `False` | Assurez‑vous que `shadow.visible = True` |
| Forme invisible | Couleur de remplissage définie sur `aw.Color.transparent` ou `None` | Utilisez une couleur solide comme `aw.Color.light_blue` |
| PDF vide | Oubli d’appeler `doc.save` ou sauvegarde avec une mauvaise extension | Appelez `doc.save("output.pdf")` et vérifiez le chemin |
| Erreur d’exécution `ImportError` | Aspose.Words non installé ou mauvais environnement Python | Exécutez `pip install aspose-words` dans l’environnement virtuel actif |

## Prochaines étapes – Explorer d’autres formes et formats

Maintenant que vous avez maîtrisé **la création d’une forme rectangulaire**, vous pouvez :

- Remplacer `ShapeType.RECTANGLE` par `ShapeType.ELLIPSE` ou `ShapeType.PENTAGON` pour expérimenter d’autres géométries.
- Ajouter du texte à l’intérieur de la forme en utilisant `builder.move_to(rectangle.absolute_position)` puis `builder.writeln("Hello World")`.
- Combiner plusieurs formes en un groupe avec `group = aw.drawing.GroupShape(doc)` pour des diagrammes complexes.
- Exporter vers d’autres formats comme DOCX (`doc.save("output.docx")`) ou HTML (`doc.save("output.html")`) pour voir comment l’ombre se traduit.

Chaque de ces extensions repose sur les mêmes concepts de base : **ajouter une ombre à la forme**, **définir la couleur de remplissage de la forme**, et **enregistrer le document en PDF** (ou un autre format).

---

### Aperçu de l’image *(optionnel)*

![Créer une forme rectangulaire avec ombre en Python](https://example.com/rectangle-shadow.png "Créer une forme rectangulaire avec ombre en Python")

*La capture d’écran montre le rendu PDF final avec un rectangle bleu clair et une ombre extérieure subtile.*

---

## Conclusion

Nous avons parcouru chaque étape nécessaire pour **créer une forme rectangulaire** en Python, appliquer un remplissage personnalisé, **ajouter une ombre à la forme**, et enfin **enregistrer le document en PDF**. Le code est entièrement exécutable, les explications couvrent le *pourquoi* de chaque propriété, et nous avons abordé les cas limites courants et les prochaines -

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word en Java – Ajouter une forme rectangulaire avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriel Ombre de forme Aspose.Words – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}