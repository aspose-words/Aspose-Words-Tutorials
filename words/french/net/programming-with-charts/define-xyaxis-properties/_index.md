---
"description": "Apprenez à définir les propriétés de l'axe XY dans un graphique avec Aspose.Words pour .NET grâce à ce guide étape par étape. Idéal pour les développeurs .NET."
"linktitle": "Définir les propriétés de l'axe XY dans un graphique"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Définir les propriétés de l'axe XY dans un graphique"
"url": "/fr/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Définir les propriétés de l'axe XY dans un graphique

## Introduction

Les graphiques sont un outil puissant pour visualiser les données. Pour créer des documents professionnels avec des graphiques dynamiques, Aspose.Words pour .NET est une bibliothèque précieuse. Cet article vous guidera pas à pas dans la définition des propriétés de l'axe XY d'un graphique avec Aspose.Words pour .NET, en détaillant chaque étape pour plus de clarté et de facilité de compréhension.

## Prérequis

Avant de plonger dans le codage, vous devez mettre en place quelques prérequis :

1. Aspose.Words pour .NET : Assurez-vous de disposer de la bibliothèque Aspose.Words pour .NET. Vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : vous avez besoin d’un environnement de développement intégré (IDE) comme Visual Studio.
3. .NET Framework : assurez-vous que votre environnement de développement est configuré pour le développement .NET.
4. Connaissances de base de C# : ce guide suppose que vous avez une compréhension de base de la programmation C#.

## Importer des espaces de noms

Pour commencer, vous devez importer les espaces de noms nécessaires dans votre projet. Cela vous permettra d'accéder à toutes les classes et méthodes nécessaires à la création et à la manipulation de documents et de graphiques.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Nous allons décomposer le processus en étapes simples, chacune se concentrant sur une partie spécifique de la définition des propriétés de l'axe XY dans un graphique.

## Étape 1 : Initialiser le document et DocumentBuilder

Tout d’abord, vous devez initialiser un nouveau document et un `DocumentBuilder` objet. Le `DocumentBuilder` aide à insérer du contenu dans le document.

```csharp
// Chemin d'accès à votre répertoire de documents 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Insérer un graphique

Vous allez ensuite insérer un graphique dans le document. Dans cet exemple, nous utiliserons un graphique en aires. Vous pouvez personnaliser les dimensions du graphique selon vos besoins.

```csharp
// Insérer un graphique
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Étape 3 : Effacer la série par défaut et ajouter des données personnalisées

Par défaut, le graphique contient des séries prédéfinies. Nous les effacerons et ajouterons nos séries de données personnalisées.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Étape 4 : Définir les propriétés de l’axe X

Il est maintenant temps de définir les propriétés de l'axe X. Cela comprend la définition du type de catégorie, la personnalisation du croisement des axes et l'ajustement des graduations et des étiquettes.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Mesuré en unités d'affichage de l'axe Y (centaines).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Étape 5 : Définir les propriétés de l’axe Y

De même, vous définirez les propriétés de l'axe Y. Cela comprend la définition de la position de l'étiquette de graduation, des unités principales et secondaires, de l'unité d'affichage et de la mise à l'échelle.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Étape 6 : Enregistrer le document

Enfin, enregistrez le document dans le répertoire spécifié. Le document Word contenant le graphique personnalisé sera alors généré.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Conclusion

Créer et personnaliser des graphiques dans des documents Word avec Aspose.Words pour .NET est simple une fois les étapes maîtrisées. Ce guide vous guide pas à pas dans la définition des propriétés de l'axe XY d'un graphique, de l'initialisation du document à l'enregistrement du résultat final. Grâce à ces compétences, vous pourrez créer des graphiques détaillés et professionnels qui sublimeront vos documents.

## FAQ

### Quels types de graphiques puis-je créer avec Aspose.Words pour .NET ?
Vous pouvez créer différents types de graphiques, notamment des graphiques à aires, à barres, à courbes, à secteurs, etc.

### Comment installer Aspose.Words pour .NET ?
Vous pouvez télécharger Aspose.Words pour .NET à partir de [ici](https://releases.aspose.com/words/net/) et suivez les instructions d'installation fournies.

### Puis-je personnaliser l’apparence de mes graphiques ?
Oui, Aspose.Words pour .NET permet une personnalisation étendue des graphiques, y compris les couleurs, les polices et les propriétés des axes.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
Oui, vous pouvez obtenir un essai gratuit [ici](https://releases.aspose.com/).

### Où puis-je trouver plus de tutoriels et de documentation ?
Vous pouvez trouver plus de tutoriels et de documentation détaillée sur le [Page de documentation d'Aspose.Words pour .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}