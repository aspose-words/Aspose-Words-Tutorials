---
"description": "Découvrez comment définir les limites d’un axe dans un graphique à l’aide d’Aspose.Words pour .NET en contrôlant la plage de valeurs affichées sur l’axe."
"linktitle": "Limites des axes dans un graphique"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Limites des axes dans un graphique"
"url": "/fr/net/programming-with-charts/bounds-of-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Limites des axes dans un graphique

## Introduction

Vous souhaitez créer des documents professionnels avec des graphiques en .NET ? Vous êtes au bon endroit ! Ce guide vous guidera pas à pas dans l'utilisation d'Aspose.Words pour .NET pour définir les limites des axes d'un graphique. Nous détaillerons chaque étape pour que vous puissiez suivre facilement, même si vous débutez avec la bibliothèque. Alors, c'est parti !

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants :

- Aspose.Words pour .NET : vous pouvez [télécharger](https://releases.aspose.com/words/net/) la dernière version ou utilisez un [essai gratuit](https://releases.aspose.com/).
- .NET Framework : assurez-vous que .NET est installé sur votre système.
- IDE : un environnement de développement comme Visual Studio.

Une fois que tout est prêt, nous pouvons passer aux étapes suivantes.

## Importer des espaces de noms

Pour commencer, vous devrez importer les espaces de noms nécessaires. Ceux-ci vous permettront d'accéder à la bibliothèque Aspose.Words et à ses fonctionnalités graphiques.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez configurer le répertoire où sera enregistré votre document. C'est une étape simple, mais essentielle pour organiser vos fichiers.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Créer un nouveau document

Créez ensuite un nouvel objet document. Ce document servira de conteneur pour votre graphique.

```csharp
Document doc = new Document();
```

## Étape 3 : Initialiser le générateur de documents

La classe DocumentBuilder offre un moyen simple et rapide de créer des documents. Initialisez-la avec votre document.

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

## Étape 8 : Enregistrer le document

Enfin, enregistrez votre document dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

Et voilà ! Vous avez créé avec succès un document avec un graphique avec Aspose.Words pour .NET. 

## Conclusion

Avec Aspose.Words pour .NET, créez et manipulez facilement des graphiques dans vos documents. Ce guide étape par étape vous explique comment définir les limites des axes d'un graphique, améliorant ainsi la précision et la qualité de votre présentation. Que vous créiez des rapports, des présentations ou tout autre document, Aspose.Words vous offre les outils dont vous avez besoin.

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque qui vous permet de créer, modifier et convertir des documents Word par programmation à l'aide du framework .NET.

### Comment configurer Aspose.Words pour .NET ?
Vous pouvez le télécharger à partir de [ici](https://releases.aspose.com/words/net/) et suivez les instructions d'installation fournies.

### Puis-je utiliser Aspose.Words gratuitement ?
Oui, vous pouvez utiliser un [essai gratuit](https://releases.aspose.com/) ou obtenir un [permis temporaire](https://purchase.aspose.com/temporary-license/).

### Où puis-je trouver la documentation pour Aspose.Words pour .NET ?
Une documentation détaillée est disponible [ici](https://reference.aspose.com/words/net/).

### Comment puis-je obtenir de l'aide pour Aspose.Words ?
Vous pouvez visiter le [forum d'assistance](https://forum.aspose.com/c/words/8) pour obtenir de l'aide.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}