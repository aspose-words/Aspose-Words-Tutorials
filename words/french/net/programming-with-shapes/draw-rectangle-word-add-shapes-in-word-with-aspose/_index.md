---
category: general
date: 2026-07-29
description: Dessinez un rectangle dans Word à l’aide d’Aspose.Words. Apprenez à ajouter
  une forme rectangle, à ajouter une forme ligne et à gérer plusieurs formes Word
  dans un même document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: fr
lastmod: 2026-07-29
og_description: Dessinez un rectangle dans Word avec Aspose.Words. Suivez ce guide
  étape par étape pour ajouter une forme rectangle, ajouter une forme ligne et travailler
  sans effort avec plusieurs formes Word.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Dessiner un rectangle dans Word – Maîtriser l’ajout de formes dans Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Dessiner un rectangle dans Word – Ajouter des formes dans Word avec Aspose
url: /fr/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Guide complet pour ajouter des formes dans Word

Vous vous êtes déjà demandé comment **draw rectangle word** des documents sans ouvrir l'interface chaque fois ? Vous n'êtes pas seul. De nombreux développeurs doivent générer des fichiers Word à la volée, et la façon la plus simple est de laisser une bibliothèque faire le travail lourd. Dans ce tutoriel, nous vous montrerons exactement **how to add shapes** — spécifiquement un rectangle et une ligne — en utilisant Aspose.Words for .NET, et nous garderons l'accent sur l'expression *draw rectangle word* afin que vous ne vous perdiez jamais.

Imaginez cela comme un mini‑studio d'art qui vit à l'intérieur de votre code. À la fin, vous serez capable d'**add rectangle shape**, d'**add line shape**, et même de les combiner en groupes **multiple shapes word**. Pas d'interface, pas de manipulation manuelle, juste du C# propre et réutilisable.

## Ce que vous apprendrez

- Configurer un nouveau document Word avec Aspose.Words.  
- Créer un **GroupShape** qui peut contenir plusieurs objets.  
- **Add rectangle shape** et **add line shape** à l'intérieur de ce groupe.  
- Insérer les formes groupées dans le corps du document.  
- Enregistrer le fichier et voir le résultat instantanément.  

Si vous êtes à l'aise avec le C# de base et que vous possédez une copie d'Aspose.Words, vous êtes prêt. Aucun paquet NuGet supplémentaire au-delà de la bibliothèque principale n'est requis.

> **Astuce :** Aspose.Words fonctionne avec .NET 6, .NET 7 et .NET Framework 4.6+. Choisissez le runtime qui correspond à votre projet.

![exemple draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – formes groupées dans un fichier Word")

## draw rectangle word – Configuration du document

Avant de pouvoir **draw rectangle word**, nous avons besoin d'une toile propre. La classe `Document` est cette toile ; le `DocumentBuilder` est notre pinceau.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Les deux lignes ci‑dessus nous donnent un nouveau `.docx` en mémoire. Rien n'est encore écrit sur le disque, ce qui signifie que nous pouvons expérimenter sans encombrer le système de fichiers.

## Comment ajouter des formes – Création d'un conteneur GroupShape

Lorsque vous souhaitez que **multiple shapes word** se comporte comme une unité unique—se déplacer ensemble, pivoter ensemble—vous les encapsulez dans un `GroupShape`. Pensez à un groupe comme à un dossier qui contient d'autres formes.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Pourquoi un groupe ? Parce que plus tard vous pourriez vouloir **add rectangle shape** et **add line shape**, puis les déplacer ensemble. Sans groupe, vous devriez repositionner chaque forme individuellement.

## add rectangle shape – Insertion d'un rectangle dans le groupe

Maintenant que le conteneur existe, ajoutons **add rectangle shape**. Un rectangle est un `Shape` dont le `ShapeType` est `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Notez que les valeurs `Left` et `Top` sont relatives à l'origine du groupe, pas à la page. Cela facilite l'alignement précis des formes. Le rectangle apparaîtra près du coin supérieur gauche du groupe.

## add line shape – Ajout d'une ligne au même groupe

Une ligne est simplement un autre `Shape`, mais son `ShapeType` est `Line`. Nous la positionnerons sous le rectangle.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Comme la hauteur de la ligne est zéro, la propriété `Top` détermine où la ligne se situe verticalement. La `Width` contrôle la longueur horizontale de la ligne.

## multiple shapes word – Insertion du groupe dans le corps du document

Nous avons un groupe qui contient maintenant **add rectangle shape** et **add line shape**. L'étape finale consiste à insérer le tout dans le document.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` place le groupe exactement à l'endroit où le `DocumentBuilder` est actuellement positionné. Si vous avez besoin de l'insérer dans un paragraphe spécifique, déplacez d'abord le builder avec `builder.MoveToParagraph(index)`.

## Enregistrement du résultat – Voir la sortie draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Ouvrez le fichier généré dans Microsoft Word et vous verrez un groupe unique contenant un rectangle et une ligne. Vous pouvez cliquer sur le groupe, le faire glisser, ou même le redimensionner—toutes les formes se déplacent ensemble. C’est la puissance de **multiple shapes word**.

### Résultat attendu

- Un fichier `.docx` nommé `GroupShape.docx`.  
- Une page avec un rectangle groupé (120 × 80 pt) près du coin supérieur gauche.  
- Une ligne horizontale (150 pt de long) positionnée juste sous le rectangle.  
- Les deux formes sont sélectionnables comme un seul objet.

Si vous double‑cliquez sur le groupe, Word vous permettra de modifier chaque forme individuellement—parfait pour les réglages fins.

## Questions fréquentes & cas particuliers

**Que faire si j'ai besoin de plus de deux formes ?**  
Continuez simplement d'appeler `group.AppendChild(yourShape)` pour chaque objet supplémentaire. Le groupe peut contenir n'importe quel nombre de formes, ce qui le rend idéal pour les diagrammes complexes.

**Puis-je changer la couleur de remplissage du rectangle ?**  
Absolument. Après avoir créé le rectangle, définissez `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Cela fonctionne pour toute forme qui supporte le remplissage.

**Dois‑je définir `Height = 0` pour une ligne ?**  
Oui, pour une ligne horizontale droite la hauteur doit être zéro. Pour une ligne verticale, définissez `Width = 0` et donnez une valeur positive à `Height`.

**Cette méthode fonctionnera‑t‑elle avec les fichiers .doc (Word 97‑2003) ?**  
Aspose.Words peut enregistrer au format `.doc` plus ancien, mais certaines fonctionnalités modernes de formes peuvent être limitées. Privilégiez le `.docx` pour une fidélité complète.

**Comment faire pivoter tout le groupe ?**  
Vous pouvez définir `group.Rotation = 45;` (degrés) avant de l'insérer. La rotation s'applique à chaque forme enfant.

## Récapitulatif – Comment ajouter des formes dans Word programmatiquement

- **draw rectangle word** commence par créer un `Document` et un `DocumentBuilder`.  
- Créez un **GroupShape** pour contenir **multiple shapes word**.  
- **add rectangle shape** et **add line shape** sont ajoutés au groupe.  
- Insérez le groupe dans le corps avec `builder.InsertNode`.  
- Enregistrez le fichier et ouvrez‑le pour vérifier le résultat visuel.

C’est l’ensemble du flux de travail, présenté dans une seule liste de code facile à lire.

## Prochaines étapes & sujets associés

Maintenant que vous savez **how to add shapes**, envisagez d'explorer :

- **add rectangle shape** avec coins arrondis (`ShapeType.Rectangle` + `CornerRadius`).  
- Styliser les lignes avec différents motifs de tirets (`line.LineFormat.DashStyle`).  
- Intégrer des images aux côtés des formes pour des rapports plus riches.  
- Utiliser **multiple shapes word** pour créer des organigrammes ou des diagrammes UML simples.  

Chacun de ces sujets s'appuie naturellement sur les bases présentées ici, et ils suivent tous le même schéma de création de formes, de configuration et de groupement si nécessaire.

---

Bonne programmation ! Si vous rencontrez des problèmes ou avez un cas d'utilisation intéressant à partager, laissez un commentaire ci‑dessous. Vos retours nous aident tous à maîtriser l'art du **draw rectangle word** et bien plus.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer une forme rectangle dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insérer des formes dans des documents Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}