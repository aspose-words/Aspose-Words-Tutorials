---
title: Formater le nombre d'étiquettes de données dans un graphique
linktitle: Formater le nombre d'étiquettes de données dans un graphique
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment formater les étiquettes de données dans les graphiques à l'aide d'Aspose.Words pour .NET grâce à ce guide étape par étape. Améliorez vos documents Word sans effort.
weight: 10
url: /fr/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formater le nombre d'étiquettes de données dans un graphique

## Introduction

La création de documents attrayants et informatifs implique souvent l'inclusion de graphiques avec des étiquettes de données bien formatées. Si vous êtes un développeur .NET cherchant à améliorer vos documents Word avec des graphiques sophistiqués, Aspose.Words pour .NET est une bibliothèque fantastique pour vous aider à y parvenir. Ce didacticiel vous guidera pas à pas dans le processus de mise en forme des étiquettes de nombres dans un graphique à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de plonger dans le code, vous devez mettre en place quelques prérequis :

-  Aspose.Words pour .NET : Assurez-vous que la bibliothèque Aspose.Words pour .NET est installée. Si vous ne l'avez pas encore installée, vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : vous devez disposer d'un environnement de développement .NET. Visual Studio est fortement recommandé.
- Connaissances de base de C# : la familiarité avec la programmation C# est essentielle car ce didacticiel implique l'écriture et la compréhension du code C#.
-  Licence temporaire : Pour utiliser Aspose.Words sans aucune limitation, vous pouvez obtenir une[permis temporaire](https://purchase.aspose.com/temporary-license/).

Maintenant, plongeons dans le processus étape par étape de mise en forme des étiquettes numériques dans un graphique.

## Importer des espaces de noms

Tout d’abord, nous devons importer les espaces de noms nécessaires pour travailler avec Aspose.Words pour .NET. Ajoutez les lignes suivantes en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Étape 1 : Configurez votre répertoire de documents

Avant de pouvoir commencer à manipuler votre document Word, vous devez spécifier le répertoire dans lequel votre document sera enregistré. Ceci est essentiel pour l'opération de sauvegarde ultérieure.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre répertoire de documents.

## Étape 2 : Initialiser le document et DocumentBuilder

 L'étape suivante consiste à initialiser un nouveau`Document` et un`DocumentBuilder` . Le`DocumentBuilder` est une classe d'aide qui nous permet de construire le contenu du document.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 3 : Insérer un graphique dans le document

 Maintenant, insérons un graphique dans le document en utilisant le`DocumentBuilder`Dans ce didacticiel, nous utiliserons un graphique linéaire comme exemple.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Ici, nous insérons un graphique linéaire avec une largeur et une hauteur spécifiques et définissons le titre du graphique.

## Étape 4 : Effacer la série par défaut et ajouter une nouvelle série

Par défaut, le graphique contient des séries pré-générées. Nous devons les effacer et ajouter nos propres séries avec des points de données spécifiques.

```csharp
// Supprimer la série générée par défaut.
chart.Series.Clear();

// Ajoutez une nouvelle série avec des points de données personnalisés.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Étape 5 : Activer les étiquettes de données

Pour afficher les étiquettes de données sur le graphique, nous devons les activer pour notre série.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Étape 6 : formater les étiquettes de données

Le cœur de ce tutoriel est le formatage des étiquettes de données. Nous pouvons appliquer différents formats de nombres à chaque étiquette de données individuellement.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Format de devise
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Format de date
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Format de pourcentage
```

 De plus, vous pouvez lier le format d'une étiquette de données à une cellule source. Une fois liée, la`NumberFormat` sera réinitialisé au général et hérité de la cellule source.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Étape 7 : Enregistrer le document

Enfin, enregistrez le document dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Cela enregistre votre document avec le nom spécifié et garantit que votre graphique avec des étiquettes de données formatées est conservé.

## Conclusion

La mise en forme des étiquettes de données dans un graphique à l'aide d'Aspose.Words pour .NET peut grandement améliorer la lisibilité et le professionnalisme de vos documents Word. En suivant ce guide étape par étape, vous devriez maintenant être en mesure de créer un graphique, d'ajouter des séries de données et de formater les étiquettes de données pour répondre à vos besoins. Aspose.Words pour .NET est un outil puissant qui permet une personnalisation et une automatisation étendues des documents Word, ce qui en fait un atout précieux pour les développeurs .NET.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante permettant de créer, de manipuler et de convertir des documents Word par programmation à l'aide de C#.

### Puis-je formater d’autres types de graphiques avec Aspose.Words pour .NET ?
Oui, Aspose.Words pour .NET prend en charge une variété de types de graphiques, notamment à barres, à colonnes, à secteurs, etc.

### Comment obtenir une licence temporaire pour Aspose.Words pour .NET ?
Vous pouvez obtenir un permis temporaire[ici](https://purchase.aspose.com/temporary-license/).

### Est-il possible de lier des étiquettes de données à des cellules sources dans Excel ?
Oui, vous pouvez lier des étiquettes de données à des cellules sources, ce qui permet au format numérique d'être hérité de la cellule source.

### Où puis-je trouver une documentation plus détaillée sur Aspose.Words pour .NET ?
 Vous trouverez une documentation complète[ici](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
