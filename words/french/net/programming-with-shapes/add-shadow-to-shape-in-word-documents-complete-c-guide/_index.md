---
category: general
date: 2026-06-20
description: Ajoutez rapidement une ombre à une forme et apprenez comment modifier
  la transparence de l’ombre, ajouter une ombre à la forme et appliquer une ombre
  floue avec Aspose.Words pour .NET.
draft: false
keywords:
- add shadow to shape
- how to change shadow transparency
- how to add shape shadow
- how to apply blur shadow
language: fr
og_description: Ajoutez une ombre à une forme dans un fichier Word, découvrez comment
  modifier la transparence de l'ombre, ajoutez une ombre à la forme et appliquez une
  ombre floue avec des exemples de code clairs.
og_title: Ajouter une ombre à une forme – Tutoriel C# étape par étape
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  headline: Add Shadow to Shape in Word Documents – Complete C# Guide
  type: TechArticle
- description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  name: Add Shadow to Shape in Word Documents – Complete C# Guide
  steps:
  - name: What if the shape has no existing shadow object?
    text: Aspose.Words automatically creates a `Shadow` object when you first access
      `targetShape.Shadow`. No extra initialization is required.
  - name: Does this work with other shape types, like circles or pictures?
    text: Absolutely. The shadow API is shape‑agnostic. Just retrieve the appropriate
      `Shape` node, and the same properties apply.
  - name: How to make the shadow invisible again?
    text: Set `targetShape.Shadow.Visible = false;` or simply omit the shadow configuration.
  - name: Compatibility with older .NET versions?
    text: The code uses only features available in Aspose.Words 23.x and .NET Standard
      2.0+, so it runs on .NET Framework 4.6.1 and newer.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
- Shapes
title: Ajouter une ombre à une forme dans les documents Word – Guide complet C#
url: /fr/net/programming-with-shapes/add-shadow-to-shape-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une ombre à une forme dans les documents Word – Guide complet C#

Vous êtes-vous déjà demandé comment **ajouter une ombre à une forme** dans un fichier Word sans passer par l’interface graphique ? Vous n’êtes pas seul. De nombreux développeurs doivent améliorer l’esthétique des documents de façon programmatique, et la bonne nouvelle, c’est qu’Aspose.Words rend cela très simple.

Dans ce tutoriel, nous passerons en revue les étapes exactes pour **ajouter une ombre à une forme**, vous montrerons **comment modifier la transparence de l’ombre**, couvrirons **comment ajouter une ombre à une forme** dans différents scénarios, et expliquerons même **comment appliquer une ombre floue** pour obtenir cet effet de profondeur professionnel. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez intégrer à n’importe quel projet .NET.

## Ce que vous allez apprendre

- Charger un DOCX, localiser une forme et configurer ses propriétés d’ombre.
- Ajuster l’opacité de l’ombre avec `Transparency`.
- Appliquer un flou et un décalage pour créer une ombre portée réaliste.
- Enregistrer le document modifié et vérifier le résultat.
- Astuces pour gérer plusieurs formes, différents types de formes et cas particuliers.

> **Prérequis :** .NET 6 ou supérieur, Aspose.Words for .NET (package NuGet `Aspose.Words`), et une compréhension de base du C#. Aucun outil UI requis.

![add shadow to shape example](image.png){ alt="exemple d'ajout d'ombre à la forme" }

## Étape 1 : Configurer votre projet et charger le document

Avant de pouvoir **ajouter une ombre à une forme**, vous avez besoin d’un objet document avec lequel travailler. Cette étape est simple mais indispensable — sans charger le fichier, il n’y a rien à modifier.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load an existing DOCX that already contains a shape (e.g., a rectangle)
Document document = new Document(@"C:\Docs\input.docx");
```

*Pourquoi c’est important :*  
`Document` est le point d’entrée de toutes les opérations Aspose.Words. En chargeant le fichier dès le départ, vous vous assurez que toute manipulation de forme ultérieure s’effectue sur l’arbre de nœuds correct.

## Étape 2 : Récupérer la forme cible

Maintenant que le document est en mémoire, nous devons localiser la forme que nous voulons améliorer. Si vous avez plusieurs formes, vous pouvez ajuster l’indice ou utiliser un sélecteur plus sophistiqué.

```csharp
// Grab the first shape in the document – change the index if needed
Shape targetShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
```

> **Astuce :** Utilisez `document.GetChild(NodeType.Shape, index, true)` pour rechercher de façon récursive. Si vous avez besoin d’une forme spécifique par son nom, consultez `targetShape.Name`.

## Étape 3 : Activer l’ombre et définir sa couleur de base

Une ombre n’apparaîtra pas tant qu’elle n’est pas visible et qu’elle n’a pas de couleur. Donnons‑lui un gris foncé subtil qui fonctionne bien sur des fonds clairs.

```csharp
// Make sure the shadow is turned on
targetShape.Shadow.Visible = true;

// Choose a neutral color for the shadow
targetShape.Shadow.Color = Color.DarkGray;
```

*Explication :*  
Définir `Visible` à `true` active l’effet, tandis que `Color.DarkGray` fournit une teinte neutre qui ne choque pas la plupart des thèmes de document.

## Étape 4 : Comment modifier la transparence de l’ombre

La transparence est la clé pour rendre une ombre naturelle. Une valeur de `0` est totalement opaque ; `1` est complètement invisible. Voici comment **modifier la transparence de l’ombre** à 30 % :

```csharp
// 30 % transparent (0.3 means 30 % see‑through)
targetShape.Shadow.Transparency = 0.3;
```

*Pourquoi 0,3 ?*  
Une ombre à 30 % de transparence imite l’éclairage réel sans submerger les bords de la forme. Vous pouvez expérimenter — `0.5` donne un rendu plus doux, tandis que `0.1` rend l’ombre plus prononcée.

## Étape 5 : Comment appliquer une ombre floue pour la profondeur

Une ombre nette et à bord dur paraît plate. Ajouter du flou lui donne de la profondeur. C’est ici que nous répondons à **comment appliquer une ombre floue** en code.

```csharp
// Define the blur radius (in points). Larger values = softer shadow.
targetShape.Shadow.BlurRadius = 5;   // 5 pt blur

// Offset determines where the shadow falls relative to the shape.
targetShape.Shadow.OffsetX = 3;      // 3 pt to the right
targetShape.Shadow.OffsetY = 3;      // 3 pt downwards
```

*Ce qui se passe :*  
`BlurRadius` adoucit les bords, tandis que `OffsetX/Y` positionnent l’ombre comme si une source de lumière était située en haut à gauche. Ajustez ces valeurs pour correspondre à votre langage de design.

## Étape 6 : Comment ajouter une ombre à plusieurs formes (facultatif)

Si votre document contient plusieurs formes, vous voudrez probablement **ajouter une ombre à chaque forme**. Une boucle rapide fait l’affaire :

```csharp
// Iterate over every shape in the document
foreach (Shape shape in document.GetChildNodes(NodeType.Shape, true))
{
    shape.Shadow.Visible = true;
    shape.Shadow.Color = Color.DarkGray;
    shape.Shadow.Transparency = 0.3;
    shape.Shadow.BlurRadius = 5;
    shape.Shadow.OffsetX = 3;
    shape.Shadow.OffsetY = 3;
}
```

*Pro tip :*  
Si vous ne souhaitez affecter que les rectangles, vérifiez `shape.ShapeType == ShapeType.Rectangle` à l’intérieur de la boucle.

## Étape 7 : Enregistrer le document modifié

Tout le travail lourd est terminé — il ne reste plus qu’à persister les modifications. Vous pouvez écraser le fichier original ou écrire vers un nouvel emplacement.

```csharp
// Save to a new file to keep the original untouched
document.Save(@"C:\Docs\output.docx");
```

Lorsque vous ouvrirez `output.docx` dans Word, vous verrez le rectangle (ou toute forme ciblée) affichant une ombre subtile, semi‑transparente et floue.

## Questions fréquentes & cas particuliers

### Que faire si la forme n’a pas d’objet ombre existant ?
Aspose.Words crée automatiquement un objet `Shadow` lorsque vous accédez pour la première fois à `targetShape.Shadow`. Aucune initialisation supplémentaire n’est requise.

### Cela fonctionne‑t‑il avec d’autres types de formes, comme des cercles ou des images ?
Absolument. L’API d’ombre est indépendante du type de forme. Il suffit de récupérer le nœud `Shape` approprié, et les mêmes propriétés s’appliquent.

### Comment rendre l’ombre invisible à nouveau ?
Définissez `targetShape.Shadow.Visible = false;` ou omettez simplement la configuration de l’ombre.

### Compatibilité avec les versions .NET plus anciennes ?
Le code utilise uniquement des fonctionnalités disponibles dans Aspose.Words 23.x et .NET Standard 2.0+, il fonctionne donc sur .NET Framework 4.6.1 et versions supérieures.

## Exemple complet fonctionnel

Voici le programme complet, prêt à être exécuté, qui assemble tous les éléments :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load the document that contains the shape
        Document doc = new Document(@"C:\Docs\input.docx");

        // Retrieve the first shape (e.g., a rectangle) from the document
        Shape rect = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // Enable shadow and set its basic properties
        rect.Shadow.Visible = true;
        rect.Shadow.Color = Color.DarkGray;

        // How to change shadow transparency – 30 % transparent
        rect.Shadow.Transparency = 0.3;

        // How to apply blur shadow – add depth with blur and offset
        rect.Shadow.BlurRadius = 5;   // 5 pt blur radius
        rect.Shadow.OffsetX = 3;      // horizontal offset
        rect.Shadow.OffsetY = 3;      // vertical offset

        // Save the modified document
        doc.Save(@"C:\Docs\output.docx");
    }
}
```

**Résultat attendu :** Ouvrez `output.docx` et vous verrez le rectangle original rendu avec une ombre gris foncé, 30 % transparente, floue et légèrement décalée vers le bas‑droite.

## Conclusion

Nous avons couvert tout ce qu’il faut savoir pour **ajouter une ombre à une forme** de façon programmatique, du chargement du fichier à l’ajustement de la transparence et du flou. Vous savez maintenant **comment modifier la transparence de l’ombre**, **comment ajouter une ombre à une forme** sur plusieurs éléments, et **comment appliquer une ombre floue** pour obtenir un rendu soigné.

Prêt pour l’étape suivante ? Essayez d’expérimenter avec :

- Différentes couleurs d’ombre (`Color.Black`, `Color.FromArgb(128, 0, 0, 0)`) pour des effets plus sombres.
- Des décalages dynamiques basés sur la taille de la forme afin de conserver les proportions.
- La combinaison d’ombres avec des dégradés ou des reflets pour un style avancé.

N’hésitez pas à laisser un commentaire si vous rencontrez des difficultés, et bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Add Group Shape](/words/english/net/programming-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}