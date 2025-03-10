---
title: Révision de la forme
linktitle: Révision de la forme
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment gérer les révisions de formes dans les documents Word à l'aide d'Aspose.Words pour .NET avec ce guide complet. Maîtrisez le suivi des modifications, l'insertion de formes et bien plus encore.
weight: 10
url: /fr/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Révision de la forme

## Introduction

La modification de documents Word par programmation peut être une tâche ardue, en particulier lorsqu'il s'agit de gérer des formes. Que vous créiez des rapports, conceviez des modèles ou automatisiez simplement la création de documents, la capacité de suivre et de gérer les révisions de formes est essentielle. Aspose.Words pour .NET propose une API puissante pour rendre ce processus transparent et efficace. Dans ce didacticiel, nous allons nous plonger dans les spécificités de la révision des formes dans les documents Word, en veillant à ce que vous disposiez des outils et des connaissances nécessaires pour gérer vos documents en toute simplicité.

## Prérequis

Avant de plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin :

-  Aspose.Words pour .NET : assurez-vous que la bibliothèque Aspose.Words est installée. Vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : vous devez disposer d’un environnement de développement configuré, tel que Visual Studio.
- Compréhension de base de C# : Familiarité avec le langage de programmation C# et les concepts de base de la programmation orientée objet.
- Document Word : un document Word avec lequel travailler, ou vous pouvez en créer un pendant le didacticiel.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Ceux-ci nous donneront accès aux classes et méthodes nécessaires à la gestion des documents et formes Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Étape 1 : Configuration de votre répertoire de documents

Avant de commencer à travailler avec les formes, nous devons définir le chemin d'accès à notre répertoire de documents. C'est là que nous enregistrerons nos documents modifiés.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Créer un nouveau document

Créons un nouveau document Word dans lequel nous insérerons et réviserons les formes.

```csharp
Document doc = new Document();
```

## Étape 3 : insertion d'une forme en ligne

Nous allons commencer par insérer une forme en ligne dans notre document sans suivre les révisions. Une forme en ligne est une forme qui s'intègre au texte.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Étape 4 : Commencer à suivre les révisions

Pour suivre les modifications apportées à notre document, nous devons activer le suivi des révisions. Cela est essentiel pour identifier les modifications apportées aux formes.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Étape 5 : insertion d'une autre forme avec des révisions

Maintenant que le suivi des révisions est activé, insérons une autre forme. Cette fois, toutes les modifications seront suivies.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Étape 6 : Récupérer et modifier les formes

Nous pouvons récupérer toutes les formes du document et les modifier selon nos besoins. Ici, nous allons récupérer les formes et supprimer la première.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Étape 7 : enregistrement du document

Après avoir effectué nos modifications, nous devons enregistrer le document. Cela garantit que toutes les révisions et modifications sont enregistrées.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Étape 8 : Gestion des révisions de déplacement de forme

Lorsqu'une forme est déplacée, Aspose.Words considère cela comme une révision. Cela signifie qu'il y aura deux instances de la forme : une à son emplacement d'origine et une à son nouvel emplacement.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Conclusion

Et voilà ! Vous avez appris avec succès à gérer les révisions de formes dans les documents Word à l'aide d'Aspose.Words pour .NET. Que vous gériez des modèles de documents, automatisiez des rapports ou que vous suiviez simplement les modifications, ces compétences sont inestimables. En suivant ce guide étape par étape, vous avez non seulement maîtrisé les bases, mais vous avez également acquis un aperçu des techniques de gestion de documents plus avancées.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, modifier et convertir des documents Word par programmation à l'aide de C#.

### Puis-je suivre les modifications apportées à d’autres éléments dans un document Word ?
Oui, Aspose.Words pour .NET prend en charge le suivi des modifications apportées à divers éléments, notamment le texte, les tableaux, etc.

### Comment puis-je obtenir un essai gratuit d'Aspose.Words pour .NET ?
 Vous pouvez obtenir un essai gratuit d'Aspose.Words pour .NET[ici](https://releases.aspose.com/).

### Est-il possible d’accepter ou de rejeter des révisions par programmation ?
Oui, Aspose.Words pour .NET fournit des méthodes pour accepter ou rejeter les révisions par programmation.

### Puis-je utiliser Aspose.Words pour .NET avec d’autres langages .NET en plus de C# ?
Absolument ! Aspose.Words pour .NET peut être utilisé avec n'importe quel langage .NET, y compris VB.NET et F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
