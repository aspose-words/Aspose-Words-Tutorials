---
category: general
date: 2026-06-30
description: Ajoutez une ombre à une forme avec Aspose.Words pour Python. Apprenez
  à définir la distance de l'ombre, à personnaliser le flou et à enregistrer rapidement
  un PDF avec l'ombre de la forme.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: fr
og_description: Ajoutez une ombre à une forme dans un document Word avec Aspose.Words
  pour Python. Ce tutoriel montre comment définir la distance, le flou et la couleur
  de l'ombre, puis enregistrer en PDF.
og_title: Ajouter une ombre à une forme en Python – Guide complet d'Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Ajouter une ombre à une forme en Python avec Aspose.Words – Guide complet
url: /fr/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une ombre à une forme en Python avec Aspose.Words – Guide complet

Ajouter une ombre à une forme dans un document Word en utilisant Aspose.Words pour Python est plus facile que vous ne le pensez. Si vous vous êtes déjà demandé **comment définir la distance de l'ombre** ou **comment ajouter une ombre à une forme** pour un rendu soigné, ce guide vous couvre.

Dans les quelques minutes qui suivent, nous passerons en revue tout ce dont vous avez besoin : de la création d’un nouveau document, à l’insertion d’un rectangle, en passant par le réglage de ses propriétés d’ombre, jusqu’à l’enregistrement final d’un PDF qui montre l’effet. À la fin, vous pourrez appliquer une ombre à n’importe quelle forme — rectangle, ellipse ou dessin personnalisé—sans fouiller dans la documentation de l’API.

> **Prérequis** – Vous devez avoir Python 3.7+ installé, une licence Aspose.Words pour Python (ou une évaluation gratuite), et une connaissance de base du scripting Python. Aucune autre bibliothèque externe n’est requise.

---

## Ajouter une ombre à une forme – Vue d'ensemble étape par étape

Voici une feuille de route rapide de ce que nous allons accomplir :

1. **Créer un nouveau document** et un `DocumentBuilder` pour le modifier.  
2. **Insérer une forme rectangle** de la taille dont vous avez besoin.  
3. **Activer et personnaliser l’ombre** – c’est ici que le mot‑clé principal brille.  
4. **Enregistrer le document** au format PDF qui conserve l’ombre de la forme.

Chaque étape est détaillée dans sa propre section, afin que vous puissiez copier‑coller les extraits de code directement dans votre IDE.

---

## Étape 1 : Initialiser le Document et le Builder

First things first—without a `Document` you have nothing to work on. The `DocumentBuilder` is your paintbrush.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Pourquoi c’est important* : l’objet `Document` représente le fichier complet, tandis que le `DocumentBuilder` simplifie l’insertion de texte, de tableaux et de formes. Pensez au builder comme à un curseur que vous pouvez déplacer sur la page.

---

## Étape 2 : Insérer une forme rectangle

Now we’ll add a rectangle—our canvas for the shadow effect. You can replace `RECTANGLE` with `ELLIPSE`, `STAR`, or any other `ShapeType` if you need a different geometry.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Astuce pro* : les dimensions sont exprimées en points (1 pt ≈ 1/72 pouce). Ajustez‑les pour correspondre à votre mise en page ; l’ombre s’ajustera automatiquement.

---

## Comment définir la distance de l'ombre

The shadow’s **distance** determines how far it appears from the shape. A larger distance mimics a light source farther away, while a smaller value gives a subtle lift.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Remarque** : la distance fonctionne conjointement avec `angle`. Modifier l’angle fait pivoter l’ombre autour de la forme, tandis que `distance` la pousse vers l’extérieur.

---

## Comment ajouter une ombre à une forme – Personnalisation du flou, de la couleur et de l'angle

Adding a shadow isn’t just about turning it on; you often want to tweak blur, color, and direction for a realistic effect.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Pourquoi ces paramètres ?*  
- **Rayon du flou** adoucit les bords, évitant une silhouette trop dure.  
- **Angle** simule la source de lumière ; 45° est une valeur par défaut courante qui donne un rendu équilibré.  
- **Couleur** peut être n’importe quel objet `Color` ; essayez `Color.gray` pour un effet plus doux.

---

## Étape 4 : Enregistrer le document au format PDF

Once the shape and its shadow are ready, persisting the result is a breeze. Aspose.Words handles the conversion to PDF automatically, preserving the visual fidelity.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Résultat attendu* : ouvrez le fichier généré `ShadowShape.pdf`. Vous verrez une page unique contenant un rectangle de 200 × 100 pt, son ombre projetée à 4 pt de distance sous un angle de 45°, floutée de 5 pt. L’ombre doit apparaître comme un halo gris‑noir subtil entourant la forme.

---

## Questions fréquentes et cas particuliers

### Et si j’ai besoin d’une forme différente ?

Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g., `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code needed.

### Puis‑je appliquer une ombre à plusieurs formes en même temps ?

Yes. Loop over the shapes you create and configure each `shadow_format` individually. Here’s a quick snippet:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Comment modifier l’opacité de l’ombre ?

Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Exemple complet fonctionnel

Below is the complete script—copy it, adjust the output folder, and run it. No pieces are missing.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Run the script, then open the resulting PDF. You should see the rectangle with a crisp, offset shadow—exactly what **add shadow to shape** promises.

---

## Conclusion

We’ve just demonstrated how to **add shadow to shape** in a Word document using Aspose.Words for Python, covering the essential steps to **set shadow distance**, customize blur, angle, and color, and finally export a PDF that retains the effect. This technique works for any shape type, and you can extend it with loops, opacity tweaks, or even gradient shadows.

Ready for the next challenge? Try combining multiple shadows, layering shapes, or generating a report where each chart gets its own stylized shadow. Experimenting will cement the concepts and reveal new possibilities for document automation.

If you found this guide helpful, feel free to share it, star the Aspose.Words repository, or drop a comment with your own shadow‑tweaking tips. Happy coding!

## Que devriez‑vous apprendre ensuite ?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}