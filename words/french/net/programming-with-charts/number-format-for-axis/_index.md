---
"description": "Apprenez à formater les nombres des axes d'un graphique avec Aspose.Words pour .NET grâce à ce guide étape par étape. Améliorez la lisibilité et le professionnalisme de votre document sans effort."
"linktitle": "Format numérique pour l'axe d'un graphique"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Format numérique pour l'axe d'un graphique"
"url": "/fr/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format numérique pour l'axe d'un graphique

## Introduction

Bonjour ! Avez-vous déjà travaillé avec des graphiques dans vos documents et souhaité pouvoir formater les nombres sur vos axes pour un rendu plus professionnel ? Eh bien, vous avez de la chance ! Dans ce tutoriel, nous allons vous expliquer comment y parvenir avec Aspose.Words pour .NET. Cette puissante bibliothèque vous permet de gérer vos documents Word en toute simplicité. Aujourd'hui, nous nous concentrons sur la refonte de vos axes de graphiques grâce à des formats de nombres personnalisés.

## Prérequis

Avant de commencer, assurons-nous que vous avez tout ce dont vous avez besoin. Voici une liste de contrôle rapide :

- Aspose.Words pour .NET : assurez-vous de l'avoir installé. Sinon, vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
- .NET Framework : assurez-vous d’avoir installé un framework .NET compatible.
- Environnement de développement : un IDE comme Visual Studio fonctionnera parfaitement.
- Connaissances de base de C# : cela vous aidera à suivre les exemples de codage.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet. C'est comme poser les fondations avant de construire une maison. Ajoutez les directives using suivantes en haut de votre fichier de code :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Décomposons maintenant le processus en étapes simples et faciles à suivre.

## Étape 1 : Configuration du document

Titre : Initialiser votre document

Tout d'abord, vous devez créer un nouveau document et un générateur de documents. Considérez cette étape comme la préparation de votre toile et de votre pinceau avant de commencer votre chef-d'œuvre.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ici, `dataDir` est le chemin vers votre répertoire de documents où vous enregistrerez le fichier final. `Document` et `DocumentBuilder` sont des classes d'Aspose.Words qui vous aident à créer et à manipuler des documents Word.

## Étape 2 : Insertion d'un graphique

Titre : ajouter un graphique à votre document

Ensuite, ajoutons un graphique à votre document. C'est là que la magie opère. Nous allons insérer un histogramme qui servira de toile vierge.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

Le `InsertChart` La méthode insère un graphique de type spécifié (colonne dans ce cas) et de dimensions dans le document.

## Étape 3 : Personnalisation de la série de graphiques

Titre : Remplissez votre graphique avec des données

Il nous faut maintenant ajouter des données à notre graphique. Cette étape revient à remplir votre graphique avec des informations pertinentes.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Ici, nous ajoutons une nouvelle série appelée « Aspose Series 1 » avec cinq points de données. `Series.Clear` Cette méthode garantit que toutes les données préexistantes sont supprimées avant d'ajouter notre nouvelle série.

## Étape 4 : Formatage des numéros d'axe

Titre : Embellissez vos numéros d'axe

Enfin, formatons les nombres sur l'axe des Y pour les rendre plus lisibles. C'est comme mettre la touche finale à votre œuvre.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

Le `FormatCode` Cette propriété vous permet de définir un format personnalisé pour les nombres sur l'axe. Dans cet exemple, `#,##0` garantit que les grands nombres sont affichés avec des virgules pour les milliers.

## Étape 5 : Enregistrement du document

Titre : Sauvegardez votre chef-d'œuvre

Maintenant que tout est configuré, il est temps d'enregistrer votre document. Cette étape est la révélation de votre travail.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Ici, le `Save` la méthode enregistre le document dans le chemin spécifié avec le nom de fichier `WorkingWithCharts.NumberFormatForAxis.docx`.

## Conclusion

Et voilà ! Vous avez réussi à formater les nombres sur l'axe des Y de votre graphique avec Aspose.Words pour .NET. Vos graphiques sont ainsi non seulement plus professionnels, mais aussi plus lisibles. Aspose.Words offre une multitude de fonctionnalités pour créer de superbes documents Word par programmation. Alors, pourquoi ne pas explorer davantage et découvrir d'autres possibilités ?

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, manipuler et convertir des documents Word par programmation.

### Puis-je formater d’autres aspects du graphique en plus des numéros d’axe ?
Absolument ! Aspose.Words pour .NET vous permet de formater les titres, les étiquettes et même de personnaliser l'apparence du graphique.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
Oui, vous pouvez obtenir un [essai gratuit ici](https://releases.aspose.com/).

### Puis-je utiliser Aspose.Words pour .NET avec d’autres langages .NET en plus de C# ?
Oui, Aspose.Words pour .NET est compatible avec n'importe quel langage .NET, y compris VB.NET et F#.

### Où puis-je trouver une documentation plus détaillée ?
Une documentation détaillée est disponible sur le [Page de documentation d'Aspose.Words pour .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}