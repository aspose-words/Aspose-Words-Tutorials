---
title: Insérer un graphique à dispersion dans un document Word
linktitle: Insérer un graphique à dispersion dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer un graphique en nuage de points dans Word avec Aspose.Words pour .NET. Étapes simples pour intégrer des représentations de données visuelles dans vos documents.
weight: 10
url: /fr/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un graphique à dispersion dans un document Word

## Introduction

Dans ce didacticiel, vous apprendrez à utiliser Aspose.Words pour .NET pour insérer un graphique en nuage de points dans votre document Word. Les graphiques en nuage de points sont des outils visuels puissants qui peuvent afficher efficacement des points de données en fonction de deux variables, ce qui rend vos documents plus attrayants et informatifs.

## Prérequis

Avant de nous lancer dans la création de graphiques en nuage de points avec Aspose.Words pour .NET, assurez-vous de disposer des prérequis suivants :

1.  Installation d'Aspose.Words pour .NET : Téléchargez et installez Aspose.Words pour .NET depuis[ici](https://releases.aspose.com/words/net/).
   
2. Connaissances de base de C# : Une familiarité avec le langage de programmation C# et le framework .NET sera bénéfique.

## Importer des espaces de noms

Pour commencer, vous devez importer les espaces de noms nécessaires dans votre projet C# :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Maintenant, décomposons le processus d'insertion d'un graphique en nuage de points dans votre document Word à l'aide d'Aspose.Words pour .NET :

## Étape 1 : Initialiser le document et DocumentBuilder

 Tout d’abord, initialisez une nouvelle instance du`Document` classe et`DocumentBuilder` classe pour commencer à construire votre document.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : insérer le graphique en nuage de points

 Utilisez le`InsertChart` méthode de la`DocumentBuilder` classe pour insérer un graphique en nuage de points dans le document.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Étape 3 : ajouter une série de données au graphique

Ajoutez maintenant des séries de données à votre graphique en nuage de points. Cet exemple montre comment ajouter une série avec des points de données spécifiques.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Étape 4 : Enregistrer le document

 Enfin, enregistrez le document modifié à l'emplacement souhaité à l'aide du`Save` méthode de la`Document` classe.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Conclusion

Félicitations ! Vous avez appris avec succès à insérer un graphique en nuage de points dans votre document Word à l'aide d'Aspose.Words pour .NET. Les graphiques en nuage de points sont d'excellents outils pour visualiser les relations entre les données et, avec Aspose.Words, vous pouvez les intégrer sans effort dans vos documents pour améliorer la clarté et la compréhension.

## FAQ

### Puis-je personnaliser l'apparence du graphique en nuage de points à l'aide d'Aspose.Words ?
Oui, Aspose.Words permet une personnalisation étendue des propriétés des graphiques telles que les couleurs, les axes et les étiquettes.

### Aspose.Words est-il compatible avec différentes versions de Microsoft Word ?
Aspose.Words prend en charge différentes versions de Microsoft Word, garantissant ainsi la compatibilité entre les plates-formes.

### Aspose.Words prend-il en charge d’autres types de graphiques ?
Oui, Aspose.Words prend en charge une large gamme de types de graphiques, notamment les graphiques à barres, les graphiques linéaires et les graphiques à secteurs.

### Puis-je mettre à jour dynamiquement les données du graphique en nuage de points par programmation ?
Absolument, vous pouvez mettre à jour les données du graphique de manière dynamique à l'aide des appels d'API Aspose.Words.

### Où puis-je obtenir une assistance ou un support supplémentaire pour Aspose.Words ?
 Pour obtenir de l'aide, visitez le[Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
