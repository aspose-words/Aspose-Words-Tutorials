---
title: Limites des axes dans un graphique
linktitle: Limites des axes dans un graphique
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir les limites d’un axe dans un graphique à l’aide d’Aspose.Words pour .NET en contrôlant la plage de valeurs affichées sur l’axe.
weight: 10
url: /fr/net/programming-with-charts/bounds-of-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Limites des axes dans un graphique

## Introduction

Vous cherchez à créer des documents professionnels avec des graphiques dans .NET ? Vous êtes au bon endroit ! Ce guide vous guidera tout au long du processus d'utilisation d'Aspose.Words pour .NET pour définir les limites de l'axe dans un graphique. Nous allons décomposer chaque étape pour vous assurer de pouvoir suivre facilement, même si vous êtes nouveau dans la bibliothèque. Alors, allons-y et commençons !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Aspose.Words pour .NET : vous pouvez[télécharger](https://releases.aspose.com/words/net/) la dernière version ou utilisez un[essai gratuit](https://releases.aspose.com/).
- .NET Framework : assurez-vous que .NET est installé sur votre système.
- IDE : un environnement de développement comme Visual Studio.

Une fois que tout est prêt, nous pouvons passer aux étapes suivantes.

## Importer des espaces de noms

Pour commencer, vous devrez importer les espaces de noms nécessaires. Ceux-ci vous permettront d'accéder à la bibliothèque Aspose.Words et à ses fonctionnalités de création de graphiques.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez configurer le répertoire dans lequel votre document sera enregistré. Il s'agit d'une étape simple mais essentielle pour organiser vos fichiers.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Créer un nouveau document

Créez ensuite un nouvel objet document. Ce document servira de conteneur pour votre graphique.

```csharp
Document doc = new Document();
```

## Étape 3 : Initialiser le générateur de documents

La classe DocumentBuilder fournit un moyen rapide et simple de créer des documents. Initialisez-la avec votre document.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 4 : Insérer un graphique

Il est maintenant temps d'insérer un graphique dans votre document. Dans cet exemple, nous utiliserons un graphique à colonnes.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Étape 5 : Effacer les séries existantes

Pour vous assurer de repartir sur une base vierge, effacez toutes les séries existantes du graphique.

```csharp
chart.Series.Clear();
```

## Étape 6 : Ajouter des données au graphique

Ici, nous ajoutons des données au graphique. Cela inclut la spécification du nom de la série et des points de données.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## Étape 7 : Définir les limites des axes

La définition des limites de l’axe Y garantit que votre graphique est correctement mis à l’échelle.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## Étape 8 : Enregistrer le document

Enfin, enregistrez votre document dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

Et voilà ! Vous avez réussi à créer un document avec un graphique à l'aide d'Aspose.Words pour .NET. 

## Conclusion

Grâce à Aspose.Words pour .NET, vous pouvez facilement créer et manipuler des graphiques dans vos documents. Ce guide étape par étape vous a montré comment définir les limites de l'axe dans un graphique, rendant ainsi votre présentation de données plus précise et professionnelle. Que vous génériez des rapports, des présentations ou tout autre document, Aspose.Words fournit les outils dont vous avez besoin.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque qui vous permet de créer, modifier et convertir des documents Word par programmation à l'aide du framework .NET.

### Comment configurer Aspose.Words pour .NET ?
 Vous pouvez le télécharger à partir de[ici](https://releases.aspose.com/words/net/)et suivez les instructions d'installation fournies.

### Puis-je utiliser Aspose.Words gratuitement ?
 Oui, vous pouvez utiliser un[essai gratuit](https://releases.aspose.com/) ou obtenir un[permis temporaire](https://purchase.aspose.com/temporary-license/).

### Où puis-je trouver la documentation pour Aspose.Words pour .NET ?
 Une documentation détaillée est disponible[ici](https://reference.aspose.com/words/net/).

### Comment puis-je obtenir de l'aide pour Aspose.Words ?
 Vous pouvez visiter le[Forum de soutien](https://forum.aspose.com/c/words/8) pour obtenir de l'aide.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
