---
category: general
date: 2026-05-26
description: Créer un document Word en C# avec Aspose.Words, insérer une forme rectangle,
  définir la couleur de remplissage et ajouter un effet d’ombre – guide étape par
  étape.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: fr
og_description: Créer un document Word en C# avec Aspose.Words. Apprenez à insérer
  une forme rectangulaire, à définir sa couleur de remplissage et à ajouter un effet
  d’ombre.
og_title: Créer un document Word – Insérer une forme rectangle et une ombre en C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word – Insérer une forme rectangulaire et son ombre en C#
url: /fr/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word – Insérer une forme rectangulaire et une ombre en C#

Vous êtes‑vous déjà demandé comment **créer un document Word** de manière programmatique sans ouvrir Microsoft Word au préalable ? Vous n'êtes pas le seul. Dans de nombreux scénarios d'automatisation—pensez aux factures, aux contrats ou à la génération massive de rapports—vous avez besoin d'une méthode fiable pour créer un fichier .docx, y insérer une forme, lui appliquer une couleur, et peut‑être même une ombre pour un rendu soigné.

Dans ce tutoriel, nous allons passer en revue exactement cela : utiliser Aspose.Words pour .NET afin de **créer un document Word**, **insérer une forme rectangulaire**, appliquer un remplissage, et **ajouter une ombre**. À la fin, vous disposerez d'un fichier prêt à être enregistré que vous pourrez intégrer à n'importe quel flux de travail en aval.  

Nous aborderons également **comment insérer une forme** de manière flexible, et pourquoi **comment définir le remplissage** est important pour la cohérence visuelle. Pas de blabla, juste le code à copier‑coller et à exécuter.

## Prérequis

- .NET 6+ (ou .NET Framework 4.7+) installé.
- Une licence valide d'Aspose.Words pour .NET (ou une clé d'évaluation temporaire).
- Visual Studio, Rider ou tout autre IDE C# de votre choix.
- Une connaissance de base de la syntaxe C#—rien de compliqué requis.

Vous les avez ? Super, commençons.

## Étape 1 – Créer un document Word

La première chose dont vous avez besoin est un objet document vierge. C’est la toile sur laquelle tout le reste vit.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` représente le fichier .docx en mémoire, tandis que `DocumentBuilder` nous offre une API pratique pour insérer du texte, des tableaux et des formes. **Créer le document Word** de cette façon est instantané—pas d'interface utilisateur, pas d'interop COM, juste du .NET pur.

## Étape 2 – Insérer une forme rectangulaire

Maintenant que nous avons un document, insérons **une forme rectangulaire**. La méthode `InsertShape` prend une énumération `ShapeType`, une largeur et une hauteur (en points). Nous utiliserons un rectangle de 150 × 80 points, ce qui correspond approximativement à 2 × 1 pouce.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

En coulisses, Aspose crée un objet `Shape`, l’ajoute au paragraphe courant et renvoie une référence que vous pouvez styliser. C’est le cœur de **comment insérer une forme**—une seule ligne de code, mais incroyablement puissante.

## Étape 3 – Comment définir le remplissage

Une forme sans remplissage est invisible sur une page blanche. Donnons‑lui un agréable fond bleu clair.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Vous pourriez également utiliser des dégradés, des textures ou même un remplissage d’image, mais une couleur unie simplifie l’exemple. Cela montre **comment définir le remplissage** sur n’importe quelle forme que vous créez, assurant le repère visuel attendu par vos lecteurs.

## Étape 4 – Comment ajouter une ombre

Les ombres ajoutent de la profondeur et font ressortir la forme. Aspose.Words expose un objet `ShadowFormat` où vous pouvez activer la visibilité, choisir une couleur et ajuster le flou, la distance et l’angle.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Pourquoi ces valeurs particulières ? Un angle de 45° fournit une source de lumière naturelle en haut à droite, un flou modéré garde l’ombre subtile, et une courte distance empêche la forme de paraître détachée. N’hésitez pas à expérimenter—modifier l’angle à 135° fera tomber l’ombre en bas à gauche, par exemple.

## Étape 5 – Enregistrer le document

Tout le travail est fait ; maintenant nous écrivons le fichier sur le disque. Choisissez n’importe quel chemin qui vous convient ; assurez‑vous simplement que le dossier existe.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Lorsque vous ouvrez `ShadowShape.docx` dans Microsoft Word, vous verrez un rectangle bleu clair avec une ombre grisâtre douce—exactement ce que nous avons scripté.

## Exemple complet fonctionnel

En assemblant le tout, voici le programme complet, prêt à être copié‑collé :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Résultat attendu

- Un fichier nommé **ShadowShape.docx** apparaît dans le dossier cible.
- En l’ouvrant dans Word, vous voyez un rectangle bleu clair centré sur la première page.
- Le rectangle projette une ombre grise à un angle de 45°, offrant un effet 3‑D subtil.

## Questions fréquentes et cas limites

**Et si j’ai besoin d’une forme différente ?**  
Remplacez `ShapeType.Rectangle` par n’importe quelle autre valeur d’énumération (`Ellipse`, `Star`, `Arrow`, etc.). Le reste du code reste identique.

**Puis‑je ajouter du texte à l’intérieur de la forme ?**  
Oui—après avoir créé la forme, appelez `shape.AppendChild(new Paragraph(doc))` puis insérez un `Run` contenant votre texte. N’oubliez pas de définir les propriétés `shape.TextBox` si vous souhaitez un habillage.

**Qu’en est‑il du DPI ou des unités de mesure ?**  
Aspose travaille en points (1 pt = 1/72 pouce). Si vous préférez les centimètres, multipliez par 28,35 (car 1 cm ≈ 28,35 pt).

**Ai‑je besoin d’une licence pour que cela fonctionne ?**  
La version d’évaluation ajoute un filigrane sur la première page. Une licence valide le supprime et débloque l’API complète.

## Astuces et pièges

- **Astuce pro :** Appelez `builder.MoveToDocumentEnd()` avant d’insérer une forme si vous voulez qu’elle se trouve à la toute fin du document.
- **Attention à :** Enregistrer dans un dossier en lecture seule déclenchera une `UnauthorizedAccessException`. Assurez‑vous que votre application possède les droits d’écriture.
- **Note de performance :** Pour une génération massive (des centaines de documents), réutilisez une seule instance `Document` comme modèle et clonez‑la avec `doc.Clone(true)` afin d’éviter le surcoût d’initialisation répété.

## Conclusion

Vous savez maintenant comment **créer un document Word**, **insérer une forme rectangulaire**, **définir le remplissage** et **ajouter une ombre** en utilisant Aspose.Words pour .NET. L’extrait ci‑dessus est une solution autonome que vous pouvez intégrer à n’importe quel projet C#, qu’il s’agisse d’une application console, d’une API web ou d’un service en arrière‑plan.

À partir d’ici, vous pourriez explorer :

- Ajouter plusieurs formes avec des couleurs variées.
- Utiliser des dégradés ou des remplissages d’image (`shape.FillColor = ...` → `shape.FillPattern`).
- Combiner des formes avec des tableaux pour des mises en page de rapports complexes.

Essayez, ajustez les paramètres, et voyez vos fichiers Word automatisés gagner en professionnalisme avec seulement quelques lignes de code. Bon codage !

## Tutoriels associés

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriel Aspose.Words Ombre de forme – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}