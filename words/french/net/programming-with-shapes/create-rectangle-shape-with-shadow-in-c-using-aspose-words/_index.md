---
category: general
date: 2026-03-22
description: Créer une forme rectangulaire en C# et ajouter une ombre à la forme avec
  Aspose.Words. Apprenez comment ajouter une ombre, comment créer un rectangle et
  comment définir les propriétés de l'ombre.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: fr
og_description: Créer une forme rectangulaire en C# et ajouter une ombre à la forme
  à l'aide d'Aspose.Words. Guide étape par étape couvrant comment ajouter une ombre,
  comment créer un rectangle et comment définir l'ombre.
og_title: Créer une forme rectangulaire avec ombre en C# – Guide complet
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer une forme rectangulaire avec ombre en C# à l'aide d'Aspose.Words
url: /fr/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire avec ombre en C# avec Aspose.Words

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un document Word mais vous ne saviez pas comment lui appliquer une ombre subtile ? Vous n'êtes pas seul — de nombreux développeurs rencontrent ce problème lorsqu'ils commencent à automatiser des documents. Dans ce guide, nous allons voir exactement comment **ajouter une ombre à une forme** avec Aspose.Words, et nous répondrons également aux questions « **comment ajouter une ombre** », « **comment créer un rectangle** » et « **comment définir une ombre** » au fil du texte.

Nous partirons d’un `Document` vierge, dessinerons un rectangle, activerons son ombre, ajusterons le flou, la distance, l’angle et la couleur, puis enregistrerons le fichier. À la fin, vous disposerez d’un `.docx` prêt à l’emploi affichant un rectangle gris flottant juste au-dessus de la page. Pas de mystère, juste du code simple à copier‑coller dans n’importe quel projet .NET.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* **Aspose.Words for .NET** (la dernière version en date de mars 2026). Vous pouvez l’obtenir via NuGet avec `Install-Package Aspose.Words`.
* Un environnement de développement .NET — Visual Studio, Rider ou même VS Code avec l’extension C# fonctionnent parfaitement.
* Des connaissances de base en C# — rien de compliqué, juste la capacité de créer une application console ou WinForms.

C’est tout. Pas de bibliothèques supplémentaires, pas d’étapes cachées. Prêt ? C’est parti.

## Étape 1 : Initialiser un nouveau document vide

Pour **créer une forme rectangulaire**, nous avons d’abord besoin d’un conteneur — un objet `Document` qui représente le fichier Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

La classe `Document` est le point d’entrée de tout ce qu’Aspose.Words fait. Pensez‑y comme à une toile vierge ; sans elle vous ne pouvez ajouter aucune forme, tableau ou texte.

## Étape 2 : Créer le rectangle qui portera l’ombre

Nous allons maintenant **créer un rectangle** en instanciant un `Shape` de type `Rectangle`. Nous définissons également sa taille en points (1 point ≈ 1/72 pouce).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Pourquoi choisir 200 × 100 points ? C’est une taille raisonnable pour une démonstration — assez grande pour voir clairement l’ombre, mais pas trop imposante au point d’écraser la page. N’hésitez pas à ajuster ces valeurs selon votre mise en page.

## Étape 3 : Activer l’effet d’ombre et configurer son apparence

Voici le cœur du tutoriel : **comment ajouter une ombre** et **comment définir une ombre**. Aspose.Words expose un objet `Shadow` sur chaque forme, vous permettant d’activer l’effet et d’ajuster les paramètres visuels.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** adoucit les bords — une valeur plus élevée rend l’ombre plus diffusée.
* **Distance** éloigne l’ombre du rectangle.
* **Angle** détermine la direction de la lumière ; 45° donne une ombre diagonale, naturelle.
* **Color** vous laisse choisir n’importe quelle `System.Drawing.Color`. Le gris est une valeur sûre, mais vous pouvez être audacieux avec `Color.Black` ou subtil avec `Color.LightGray`.

Astuce : si vous définissez `Enabled = false`, tous les autres paramètres d’ombre sont ignorés, alors vérifiez toujours ce drapeau.

## Étape 4 : Insérer la forme dans le corps du document

Une fois le rectangle prêt et son ombre configurée, il faut le placer dans le document. La façon la plus simple est de l’ajouter au premier paragraphe de la première section.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Si votre document contient déjà du texte, vous pouvez localiser un `Paragraph` spécifique ou même une cellule de `Table` et y insérer la forme. La méthode `AppendChild` est polyvalente — elle fonctionne avec tout type de `Node`.

## Étape 5 : Enregistrer le document et vérifier le résultat

Enfin, nous écrivons le fichier sur le disque. Modifiez le chemin selon vos besoins ; le dossier doit exister, sinon une exception sera levée.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Ouvrez le `ShadowedRectangle.docx` généré dans Microsoft Word (ou LibreOffice) et vous devriez voir un rectangle gris avec une ombre nette, diagonale, qui glisse vers le bas‑droite. Si l’ombre paraît trop pâle, augmentez `BlurRadius` ou `Distance` et relancez le code — l’expérimentation fait partie du plaisir.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Créer une forme rectangulaire avec ombre exemple"}

### Résultat attendu

* Un document Word d’une seule page.
* Un rectangle gris de 200 × 100 points positionné en haut‑à‑gauche de la page.
* Une ombre grise subtile décalée de 8 pixels à un angle de 45°, floutée de 5 pixels.

## Ajouter une ombre à une forme – approfondissement

Vous vous demandez peut‑être, *« Puis‑je animer l’ombre ou la faire varier en fonction d’une entrée utilisateur ? »* Bien qu’Aspose.Words ne supporte pas l’animation, vous pouvez ajuster les propriétés d’ombre de façon programmatique avant l’enregistrement, créant ainsi plusieurs versions du même document avec des apparences différentes. Par exemple, en parcourant une collection de couleurs :

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Ce petit extrait montre **comment définir une ombre** dynamiquement — idéal pour générer des rapports thématiques.

## Créer un rectangle – formes alternatives

Si vous avez besoin d’un rectangle aux coins arrondis, changez simplement le `ShapeType` :

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Ou, pour un carré parfait, définissez `Width` égal à `Height`. Les mêmes propriétés d’ombre s’appliquent, vous êtes donc déjà couvert sur **comment ajouter une ombre** pour toute forme que vous choisissez.

## Problèmes courants et dépannage

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| L’ombre n’apparaît pas | `Shadow.Enabled` laissé à `false` | Définir `rectangleShape.Shadow.Enabled = true;` |
| L’ombre est trop nette | `BlurRadius` à 0 | Augmenter `BlurRadius` à au moins 3 |
| Le document lève `FileNotFoundException` lors de l’enregistrement | Le dossier de destination n’existe pas | Créer le dossier d’abord ou utiliser un chemin valide |
| La forme est invisible | `Width`/`Height` à 0 | S’assurer que les deux dimensions sont > 0 |

Surveiller ces points vous évite le classique « pourquoi ma forme n’apparaît‑elle pas ? ».

## Récapitulatif – ce que nous avons accompli

* **Créer une forme rectangulaire** dans un nouveau document Word avec Aspose.Words.  
* **Ajouter une ombre à une forme** en activant le drapeau `Shadow.Enabled` et en ajustant le flou, la distance, l’angle et la couleur.  
* Démonstration de **comment ajouter une ombre**, **comment créer un rectangle** et **comment définir une ombre** dans un extrait de code propre et réutilisable.  
* Fourniture d’un exemple complet, prêt à être exécuté, que vous pouvez coller dans n’importe quel projet C#.

## Et après ?

Maintenant que vous maîtrisez les bases, vous pouvez explorer :

* **Comment ajouter une ombre aux images** — la même API `Shadow` fonctionne pour `ShapeType.Image`.
* **Combiner plusieurs formes** — créez des organigrammes ou des infographies directement dans Word.
* **Exporter en PDF** — appelez `document.Save("output.pdf")` après avoir ajouté les ombres pour obtenir une version imprimable.

N’hésitez pas à jouer avec différentes couleurs, angles ou même des remplissages en dégradé. L’API est suffisamment flexible pour vous permettre de créer des documents d’aspect professionnel sans jamais ouvrir Word manuellement.

---

Bon codage ! Si vous rencontrez le moindre problème, laissez un commentaire ci‑dessous ou consultez les forums Aspose.Words — la communauté est réactive et prête à aider.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}