---
category: general
date: 2026-06-24
description: Créer une forme rectangulaire en Python avec Aspose.Words, apprendre
  à ajouter une ombre à la forme, définir l’angle de l’ombre et enregistrer le document
  au format PDF en quelques minutes.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: fr
og_description: Créer une forme rectangulaire en Python, ajouter une ombre à la forme,
  définir l’angle de l’ombre et enregistrer le document au format PDF avec Aspose.Words.
  Suivez ce guide étape par étape.
og_title: Créer une forme rectangulaire en Python – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Créer une forme rectangulaire en Python – Guide complet d'Aspose.Words
url: /fr/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire en Python – Guide complet Aspose.Words

Vous êtes-vous déjà demandé comment **créer une forme rectangulaire** dans un document Word en utilisant Python ? Peut‑être avez‑vous besoin d’une boîte d’appel en gras, d’un repère visuel pour un diagramme, ou simplement d’un joli rectangle pour un rapport. Quoi qu’il en soit, vous êtes au bon endroit. Dans ce tutoriel, nous parcourrons l’ensemble du processus : insertion du rectangle, ajout d’une ombre subtile, réglage de l’angle de l’ombre, puis **enregistrement du document au format PDF** afin de pouvoir le partager avec n’importe qui.

Nous utiliserons **Aspose.Words for Python via .NET**, une bibliothèque puissante qui vous permet de manipuler des fichiers Word sans jamais ouvrir Word. À la fin de ce guide, vous pourrez répondre à la question *« comment ajouter une ombre à une forme »* avec assurance, et vous disposerez d’un script prêt à l’emploi que vous pourrez intégrer à n’importe quel projet.

---

## Ce dont vous avez besoin

Avant de commencer, assurez‑vous d’avoir les éléments suivants :

- **Python 3.8+** installé sur votre machine.  
- **Aspose.Words for Python via .NET** (package `aspose-words`). Installez‑le avec :

  ```bash
  pip install aspose-words
  ```

- Un dossier accessible en écriture où le PDF généré sera enregistré.  
- (Facultatif) Un IDE ou éditeur de texte — VS Code fonctionne très bien.

C’est tout. Aucun DLL supplémentaire, aucune installation d’Office, juste un seul package pip.

---

## Étape 1 : Configurer le document et le constructeur

La première chose à faire est de **créer des objets compatibles avec la création de forme rectangulaire** : un `Document` et un `DocumentBuilder`. Pensez au constructeur comme à votre stylo ; il dessine tout pour vous.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Pourquoi c’est important :** L’objet `Document` représente le fichier .docx complet, tandis que le `DocumentBuilder` fournit des méthodes comme `insert_shape` qui simplifient le dessin de formes.

---

## Étape 2 : Insérer la forme rectangulaire

Maintenant que nous disposons d’un constructeur, nous pouvons enfin **créer une forme rectangulaire**. La méthode `insert_shape` nécessite trois arguments : le type de forme, la largeur et la hauteur. Nous utiliserons une largeur de 200 pt et une hauteur de 100 pt pour une proportion agréable.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

À ce stade, vous avez **créé une forme rectangulaire** dans votre document. Si vous ouvrez le DOCX généré (nous le ferons plus tard), vous verrez un simple rectangle placé à l’endroit du curseur.

---

## Étape 3 : Accéder à l’objet de format d’ombre

Pour **ajouter une ombre à la forme**, nous devons d’abord récupérer le format d’ombre de la forme. Chaque forme dans Aspose.Words possède une propriété `shadow_format` qui expose tous les paramètres liés à l’ombre.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Disposer de la référence `shadow` nous permet d’activer ou désactiver la visibilité, le flou, la distance, l’angle, la couleur et la transparence — le tout en quelques lignes de code.

---

## Étape 4 : Activer l’ombre et configurer son apparence

C’est ici que la magie opère. Nous allons **ajouter une ombre à la forme**, la rendre légèrement floue, la décaler un peu, définir la direction (la partie **définir l’angle de l’ombre**), et lui donner une teinte noire semi‑transparente.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Astuce :** Si vous avez besoin d’un effet plus dramatique, augmentez `blur_radius` ou diminuez `transparency`. À l’inverse, une ombre nette et totalement opaque peut être obtenue avec `blur_radius = 0` et `transparency = 0`.

---

## Étape 5 : Enregistrer le document au format PDF

Nous avons **créé une forme rectangulaire**, nous avons **ajouté une ombre à la forme**, et maintenant nous allons **enregistrer le document au format PDF** afin que le résultat soit identique sur n’importe quel appareil. Aspose.Words rend cela possible en une seule ligne.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

L’exécution du script générera `shadowed_rectangle.pdf` dans le dossier `output`. Ouvrez‑le avec n’importe quel lecteur PDF et vous verrez un rectangle net avec une ombre douce à 45 degrés — exactement ce que nous avons configuré.

---

## Exemple complet fonctionnel

Voici le script complet, prêt à être exécuté, qui combine toutes les étapes ci‑dessus. Copiez‑collez‑le dans un fichier nommé `create_rectangle_with_shadow.py` et lancez `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Résultat attendu :** Un fichier PDF affichant un seul rectangle avec une ombre douce et diagonale. Aucun page supplémentaire, aucun artefact caché — juste la forme que nous avons créée.

---

## Questions fréquentes et cas particuliers

### Et si j’ai besoin d’une forme différente ?

Aspose.Words prend en charge de nombreuses valeurs `ShapeType` (ellipse, étoile, appel, etc.). Remplacez simplement `aw.drawing.ShapeType.RECTANGLE` par l’énumération souhaitée, par exemple `aw.drawing.ShapeType.ELLIPSE`.

### Puis‑je ajouter plusieurs ombres ?

L’API expose un seul `ShadowFormat` par forme, mais vous pouvez simuler plusieurs ombres en dupliquant la forme, en décalant chaque copie et en ajustant la transparence.

### Comment changer la couleur de l’ombre pour qu’elle corresponde à ma charte ?

Il suffit de définir `shadow.color` sur n’importe quel `aw.drawing.Color`. Pour un bleu de marque, utilisez `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Et si je veux enregistrer en DOCX plutôt qu’en PDF ?

Remplacez `document.save(pdf_path)` par `document.save("output/shadowed_rectangle.docx")`. Le rendu de l’ombre est conservé dans les deux formats.

### L’ombre fonctionne‑t‑elle sur les anciens lecteurs PDF ?

Aspose.Words rend l’ombre comme un effet vectoriel, largement supporté. Cependant, les lecteurs très anciens pourraient aplatir l’effet ; il est toujours judicieux de tester sur les appareils de votre audience cible.

---

## Conseils pour peaufiner votre PDF

- **Ajouter une bordure :** `rectangle.line_format.width = 1.5` et définissez une couleur pour un contour net.  
- **Centrer le rectangle :** Utilisez `builder.move_to_document_start()` avant l’insertion, puis `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combiner avec du texte :** Insérez un `TextFragment` après le rectangle pour le légender, par exemple : `"Section importante"`.

Ces petits ajustements peuvent transformer un simple rectangle en une boîte d’appel soignée qui paraît professionnelle dans les rapports, les propositions ou les e‑books.

---

## Conclusion

Vous disposez désormais d’une recette solide, de bout en bout, pour **créer une forme rectangulaire** en Python, **ajouter une ombre à la forme**, **définir l’angle de l’ombre**, et **enregistrer le document au format PDF** à l’aide d’Aspose.Words. Les étapes sont simples, le code est totalement autonome, et vous avez compris pourquoi chaque ligne est importante — de l’initialisation du document à la finition du PDF final.

Ensuite, vous pourriez explorer **comment ajouter une ombre à des dessins plus complexes**, expérimenter les remplissages en dégradé, ou générer des tableaux à l’intérieur de vos formes. La bibliothèque prend également en charge le lien de formes à des signets, ce qui peut être pratique pour des PDF interactifs.

Vous avez essayé une variante ? Partagez‑la dans les commentaires, ou posez vos questions restantes. Bon codage, et profitez de cette profondeur supplémentaire dans vos documents ! 

![Forme rectangulaire avec ombre – exemple de création d’une forme rectangulaire en Python](/images/rectangle-shadow.png)


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word en Java – Ajouter une forme rectangulaire avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutoriel Aspose.Words Shape Shadow – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}