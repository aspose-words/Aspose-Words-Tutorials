---
"description": "Découvrez comment définir les options par défaut des étiquettes de données dans un graphique avec Aspose.Words pour .NET. Suivez notre guide étape par étape pour créer et personnaliser facilement des graphiques."
"linktitle": "Définir les options par défaut pour les étiquettes de données dans un graphique"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Définir les options par défaut pour les étiquettes de données dans un graphique"
"url": "/fr/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Définir les options par défaut pour les étiquettes de données dans un graphique

## Introduction

Bonjour ! Envie de vous lancer dans l'automatisation documentaire ? Aujourd'hui, nous allons découvrir comment utiliser Aspose.Words pour .NET pour créer de superbes documents par programmation. Aspose.Words est une bibliothèque puissante qui vous permet de manipuler facilement des documents Word. Dans ce tutoriel, nous nous concentrerons sur la définition des options par défaut pour les étiquettes de données d'un graphique. Que vous soyez un développeur expérimenté ou un débutant, ce guide vous guidera étape par étape pour une prise en main rapide.

## Prérequis

Avant de commencer, assurez-vous que vous disposez de tout le nécessaire pour suivre ce tutoriel. Voici une liste de contrôle rapide :

- Visual Studio ou tout autre IDE compatible .NET : c'est ici que vous écrirez et exécuterez votre code.
- Aspose.Words pour .NET : vous pouvez [télécharger la dernière version](https://releases.aspose.com/words/net/) et installez-le dans votre projet.
- Connaissances de base de la programmation C# : Bien que ce guide soit adapté aux débutants, une petite familiarité avec C# sera utile.
- .NET Framework installé : assurez-vous que .NET Framework est configuré sur votre machine.
- Une licence temporaire pour Aspose.Words : obtenez-en une [ici](https://purchase.aspose.com/temporary-license/) pour déverrouiller toutes les fonctionnalités.

Une fois ces prérequis réglés, nous sommes prêts à démarrer !

## Importer des espaces de noms

Commençons par configurer notre projet et importer les espaces de noms nécessaires. Ces espaces sont essentiels pour accéder à la fonctionnalité Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Étape 1 : Créer un nouveau document


Le voyage commence par la création d’un nouveau document et l’initialisation d’un `DocumentBuilder`. Le `DocumentBuilder` la classe fournit un ensemble de méthodes pour manipuler facilement le contenu du document.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Créer un nouveau document
Document doc = new Document();

// Initialiser DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Explication

Dans cette étape, nous avons configuré le document et le générateur que nous utiliserons pour insérer et formater notre contenu. `dataDir` la variable contient le chemin où nous enregistrerons notre document final.

## Étape 2 : Insérer un graphique

Ensuite, nous allons ajouter un graphique à secteurs à notre document. `InsertChart` méthode de la `DocumentBuilder` la classe rend cela super facile.

```csharp
// Insérer un graphique à secteurs
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Accéder à l'objet graphique
Chart chart = shape.Chart;
```

### Explication

Ici, nous insérons un graphique à secteurs dans notre document. `InsertChart` La méthode requiert le type, la largeur et la hauteur du graphique comme paramètres. Après avoir inséré le graphique, nous accédons à l'objet graphique pour le manipuler ultérieurement.

## Étape 3 : Personnaliser la série de graphiques

Nous allons maintenant supprimer toutes les séries existantes du graphique et ajouter notre série personnalisée. Cette série représentera nos points de données.

```csharp
// Effacer les séries de graphiques existantes
chart.Series.Clear();

// Ajouter une nouvelle série au graphique
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Explication

Dans cette étape, nous nous assurons que notre graphique est vide en supprimant toutes les séries existantes. Ensuite, nous ajoutons une nouvelle série avec des catégories et des valeurs personnalisées, qui s'affichera dans notre graphique à secteurs.

## Étape 4 : Définir les options par défaut pour les étiquettes de données

Les étiquettes de données sont essentielles pour rendre votre graphique informatif. Nous définirons des options pour afficher le pourcentage, la valeur et personnaliser le séparateur.

```csharp
// Accéder à la collection d'étiquettes de données
ChartDataLabelCollection labels = series.DataLabels;

// Définir les options d'étiquette de données
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Explication

Ici, nous accédons à la `DataLabels` Propriété de notre série permettant de personnaliser l'apparence et les informations affichées sur chaque étiquette de données. Nous avons choisi d'afficher le pourcentage et la valeur, de masquer les lignes de repère et de définir un séparateur personnalisé.

## Étape 5 : Enregistrer le document

Enfin, nous enregistrerons notre document dans le répertoire spécifié. Cette étape garantit que toutes nos modifications seront enregistrées dans un fichier.

```csharp
// Enregistrer le document
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Explication

Dans cette dernière étape, nous sauvegardons notre document en utilisant le `Save` méthode. Le document sera enregistré dans le répertoire spécifié par `dataDir`, avec le nom « WorkingWithCharts.DefaultOptionsForDataLabels.docx ».

## Conclusion

Et voilà ! Vous avez créé avec succès un document Word avec un diagramme circulaire personnalisé grâce à Aspose.Words pour .NET. Cette puissante bibliothèque simplifie l'automatisation de la création et de la manipulation de documents, vous faisant gagner du temps et des efforts. Que vous génériez des rapports, des factures ou tout autre type de document, Aspose.Words est là pour vous.

N'hésitez pas à explorer le [Documentation d'Aspose.Words](https://reference.aspose.com/words/net/) Pour plus de fonctionnalités et d'exemples, bon codage !

## FAQ

### Puis-je utiliser Aspose.Words gratuitement ?
Vous pouvez utiliser Aspose.Words gratuitement avec un [permis temporaire](https://purchase.aspose.com/temporary-license/) ou explorez ses fonctionnalités en utilisant le [essai gratuit](https://releases.aspose.com/).

### Comment obtenir de l'aide pour Aspose.Words ?
Vous pouvez obtenir de l'aide via le [Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).

### Puis-je ajouter d’autres types de graphiques ?
Oui, Aspose.Words prend en charge différents types de graphiques, tels que les graphiques à barres, les graphiques linéaires et les graphiques à colonnes. Consultez la section [documentation](https://reference.aspose.com/words/net/) pour plus de détails.

### Aspose.Words est-il compatible avec .NET Core ?
Oui, Aspose.Words est compatible avec .NET Core. Vous trouverez plus d'informations dans le [documentation](https://reference.aspose.com/words/net/).

### Comment puis-je acheter une licence pour Aspose.Words ?
Vous pouvez acheter une licence auprès du [Magasin Aspose](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}