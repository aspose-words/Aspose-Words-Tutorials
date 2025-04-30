---
"description": "Apprenez à insérer et à manipuler des formes dans des documents Word à l’aide d’Aspose.Words pour .NET avec notre guide étape par étape."
"linktitle": "Insérer une forme"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Insérer une forme"
"url": "/fr/net/programming-with-shapes/insert-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme

## Introduction

Pour créer des documents Word visuellement attrayants et bien structurés, les formes jouent un rôle essentiel. Que vous ajoutiez des flèches, des cadres ou même des formes personnalisées complexes, la possibilité de manipuler ces éléments par programmation offre une flexibilité inégalée. Dans ce tutoriel, nous découvrirons comment insérer et manipuler des formes dans des documents Word avec Aspose.Words pour .NET.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :

1. Aspose.Words pour .NET : téléchargez et installez la dernière version à partir du [Page de publication d'Aspose](https://releases.aspose.com/words/net/).
2. Environnement de développement : un environnement de développement .NET approprié tel que Visual Studio.
3. Connaissances de base de C# : Familiarité avec le langage de programmation C# et les concepts de base.

## Importer des espaces de noms

Pour commencer, vous devrez importer les espaces de noms nécessaires dans votre projet C# :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Étape 1 : Configurez votre projet

Avant de pouvoir commencer à insérer des formes, vous devez configurer votre projet et ajouter la bibliothèque Aspose.Words pour .NET.

1. Créer un nouveau projet : ouvrez Visual Studio et créez un nouveau projet d’application console C#.
2. Ajoutez Aspose.Words pour .NET : installez la bibliothèque Aspose.Words pour .NET via le gestionnaire de packages NuGet.

```bash
Install-Package Aspose.Words
```

## Étape 2 : Initialiser le document

Tout d’abord, vous devrez initialiser un nouveau document et un générateur de documents, qui vous aideront à construire le document.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Initialiser un nouveau document
Document doc = new Document();

// Initialiser un DocumentBuilder pour aider à construire le document
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 3 : Insérer une forme

Insérons maintenant une forme dans le document. Nous commencerons par ajouter une zone de texte simple.

```csharp
// Insérer une forme de zone de texte dans le document
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Faire pivoter la forme
shape.Rotation = 30.0;
```

Dans cet exemple, nous insérons une zone de texte à la position (100, 100) avec une largeur et une hauteur de 50 unités chacune. Nous faisons également pivoter la forme de 30 degrés.

## Étape 4 : ajouter une autre forme

Ajoutons une autre forme au document, cette fois sans spécifier la position.

```csharp
// Ajouter une autre forme de zone de texte
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Faire pivoter la forme
secondShape.Rotation = 30.0;
```

Cet extrait de code insère une autre zone de texte avec les mêmes dimensions et la même rotation que la première mais sans spécifier sa position.

## Étape 5 : Enregistrer le document

Après avoir ajouté les formes, l'étape finale consiste à enregistrer le document. Nous utiliserons `OoxmlSaveOptions` pour spécifier le format de sauvegarde.

```csharp
// Définir les options de sauvegarde avec conformité
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Enregistrer le document
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Conclusion

Et voilà ! Vous avez réussi à insérer et à manipuler des formes dans un document Word avec Aspose.Words pour .NET. Ce tutoriel a abordé les bases, mais Aspose.Words offre de nombreuses fonctionnalités avancées pour travailler avec les formes, comme les styles personnalisés, les connecteurs et les formes de groupe.

Pour des informations plus détaillées, visitez le [Aspose.Words pour la documentation .NET](https://reference.aspose.com/words/net/).

## FAQ

### Comment insérer différents types de formes ?
Vous pouvez modifier le `ShapeType` dans le `InsertShape` méthode pour insérer différents types de formes telles que des cercles, des rectangles et des flèches.

### Puis-je ajouter du texte à l'intérieur des formes ?
Oui, vous pouvez utiliser le `builder.Write` méthode pour ajouter du texte à l'intérieur des formes après les avoir insérées.

### Est-il possible de styliser les formes ?
Oui, vous pouvez styliser les formes en définissant des propriétés telles que `FillColor`, `StrokeColor`, et `StrokeWeight`.

### Comment positionner des formes par rapport à d’autres éléments ?
Utilisez le `RelativeHorizontalPosition` et `RelativeVerticalPosition` propriétés permettant de positionner les formes par rapport aux autres éléments du document.

### Puis-je regrouper plusieurs formes ensemble ?
Oui, Aspose.Words pour .NET vous permet de regrouper des formes à l'aide du `GroupShape` classe.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}