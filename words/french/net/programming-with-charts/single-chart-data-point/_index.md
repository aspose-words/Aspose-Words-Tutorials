---
"description": "Découvrez comment personnaliser des points de données de graphiques individuels avec Aspose.Words pour .NET grâce à un guide détaillé étape par étape. Améliorez vos graphiques avec des marqueurs et des tailles uniques."
"linktitle": "Personnaliser un seul point de données dans un graphique"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Personnaliser un seul point de données dans un graphique"
"url": "/fr/net/programming-with-charts/single-chart-data-point/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Personnaliser un seul point de données dans un graphique

## Introduction

Vous êtes-vous déjà demandé comment mettre en valeur vos graphiques grâce à des données uniques ? C'est votre jour de chance ! Nous allons vous montrer comment personnaliser un seul point de données avec Aspose.Words pour .NET. Suivez ce tutoriel pas à pas, non seulement informatif, mais aussi ludique et facile à suivre.

## Prérequis

Avant de commencer, assurons-nous que vous disposez de tous les éléments essentiels :

- Bibliothèque Aspose.Words pour .NET : assurez-vous d’avoir la dernière version. [Téléchargez-le ici](https://releases.aspose.com/words/net/).
- .NET Framework : assurez-vous que .NET Framework est installé sur votre machine.
- Compréhension de base de C# : une compréhension de base de la programmation C# sera utile.
- Environnement de développement intégré (IDE) : Visual Studio est recommandé.

## Importer des espaces de noms

Tout d’abord, importons les espaces de noms nécessaires pour lancer le processus :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Étape 1 : Initialiser le document et DocumentBuilder

Très bien, commençons par initialiser un nouveau document et un DocumentBuilder. Ce sera le canevas de notre graphique.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ici, `dataDir` est le chemin du répertoire où vous enregistrerez votre document. Le `DocumentBuilder` la classe aide à construire le document.

## Étape 2 : Insérer un graphique

Ensuite, insérons un graphique en courbes dans le document. Ce sera notre terrain de jeu pour personnaliser les points de données.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

Le `InsertChart` La méthode prend en compte le type, la largeur et la hauteur du graphique. Dans ce cas, nous insérons un graphique en courbes de 432 de large et 252 de haut.

## Étape 3 : Accéder à la série de graphiques

Il est maintenant temps d'accéder aux séries de notre graphique. Un graphique peut comporter plusieurs séries, chacune contenant des points de données.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Ici, nous accédons aux deux premières séries de notre graphique. 

## Étape 4 : Personnaliser les points de données

C'est ici que la magie opère ! Personnalisons des points de données spécifiques dans notre série.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Nous récupérons les points de données de la première série. Personnalisons maintenant ces points.

### Personnaliser le point de données 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

Pour `dataPoint00`, nous définissons une explosion (utile pour les graphiques à secteurs), changeons le symbole du marqueur en un cercle et définissons la taille du marqueur à 15.

### Personnaliser le point de données 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

Pour `dataPoint01`, nous changeons le symbole du marqueur en un losange et définissons la taille du marqueur à 20.

### Personnaliser le point de données dans la série 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

Pour le troisième point de données dans `series1`, nous le configurons pour l'inverser si la valeur est négative, en changeant le symbole du marqueur en étoile et en définissant la taille du marqueur sur 20.

## Étape 5 : Enregistrer le document

Enfin, sauvegardons notre document avec toutes les personnalisations.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

Cette ligne enregistre le document dans votre répertoire spécifié avec le nom `WorkingWithCharts.SingleChartDataPoint.docx`.

## Conclusion

Et voilà ! Vous avez réussi à personnaliser les points de données individuels d'un graphique avec Aspose.Words pour .NET. En modifiant quelques propriétés, vous pouvez rendre vos graphiques beaucoup plus informatifs et visuellement plus attrayants. Alors, n'hésitez pas à tester différents marqueurs et tailles pour trouver celui qui convient le mieux à vos données.

## FAQ

### Puis-je personnaliser les points de données dans d’autres types de graphiques ?

Absolument ! Vous pouvez personnaliser les points de données dans différents types de graphiques, notamment les graphiques à barres, les graphiques à secteurs, etc. Le processus est similaire pour tous les types de graphiques.

### Est-il possible d’ajouter des étiquettes personnalisées aux points de données ?

Oui, vous pouvez ajouter des étiquettes personnalisées aux points de données à l'aide de l' `ChartDataPoint.Label` propriété. Cela vous permet de fournir plus de contexte pour chaque point de données.

### Comment puis-je supprimer un point de données d’une série ?

Vous pouvez supprimer un point de données en définissant sa visibilité sur false à l'aide de `dataPoint.IsVisible = false`.

### Puis-je utiliser des images comme marqueurs pour les points de données ?

Bien qu'Aspose.Words ne prenne pas en charge l'utilisation directe d'images comme marqueurs, vous pouvez créer des formes personnalisées et les utiliser comme marqueurs.

### Est-il possible d'animer des points de données dans le graphique ?

Aspose.Words pour .NET ne prend pas en charge l'animation des points de données des graphiques. Cependant, vous pouvez créer des graphiques animés avec d'autres outils et les intégrer à vos documents Word.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}