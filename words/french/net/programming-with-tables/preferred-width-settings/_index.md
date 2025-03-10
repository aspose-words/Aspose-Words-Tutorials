---
title: Paramètres de largeur préférés
linktitle: Paramètres de largeur préférés
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment créer des tableaux avec des paramètres de largeur absolus, relatifs et automatiques dans Aspose.Words pour .NET avec ce guide étape par étape.
weight: 10
url: /fr/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Paramètres de largeur préférés

## Introduction

Les tableaux constituent un moyen efficace d'organiser et de présenter des informations dans vos documents Word. Lorsque vous travaillez avec des tableaux dans Aspose.Words pour .NET, vous disposez de plusieurs options pour définir la largeur des cellules du tableau afin de garantir qu'elles s'adaptent parfaitement à la mise en page de votre document. Ce guide vous guidera tout au long du processus de création de tableaux avec des paramètres de largeur préférés à l'aide d'Aspose.Words pour .NET, en mettant l'accent sur les options de dimensionnement absolu, relatif et automatique. 

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET : Assurez-vous que Aspose.Words pour .NET est installé dans votre environnement de développement. Vous pouvez le télécharger[ici](https://releases.aspose.com/words/net/).

2. Environnement de développement .NET : configurez un environnement de développement .NET, tel que Visual Studio.

3. Connaissances de base de C# : la familiarité avec la programmation C# vous aidera à mieux comprendre les extraits de code et les exemples.

4.  Documentation Aspose.Words : reportez-vous à la[Documentation Aspose.Words](https://reference.aspose.com/words/net/) pour des informations détaillées sur l'API et des lectures complémentaires.

## Importer des espaces de noms

Avant de commencer à coder, vous devez importer les espaces de noms nécessaires dans votre projet C# :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ces espaces de noms donnent accès aux fonctionnalités principales d'Aspose.Words et de l'objet Table, vous permettant de manipuler les tables de documents.

Décomposons le processus de création d’un tableau avec différents paramètres de largeur préférés en étapes claires et gérables.

## Étape 1 : Initialiser le document et DocumentBuilder

Rubrique : Création d'un nouveau document et DocumentBuilder

 Explication : Commencez par créer un nouveau document Word et un`DocumentBuilder` exemple. Le`DocumentBuilder` La classe fournit un moyen simple d'ajouter du contenu à votre document.

```csharp
// Définissez le chemin pour enregistrer le document.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Créer un nouveau document.
Document doc = new Document();

// Créez un DocumentBuilder pour ce document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ici, vous spécifiez le répertoire où le document sera enregistré et initialisez le`Document` et`DocumentBuilder` objets.

## Étape 2 : insérer la première cellule du tableau avec une largeur absolue

Insérez la première cellule du tableau avec une largeur fixe de 40 points. Cela garantira que cette cellule conserve toujours une largeur de 40 points quelle que soit la taille du tableau.

```csharp
// Insérer une cellule de taille absolue.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

Dans cette étape, vous commencez à créer le tableau et insérez une cellule avec une largeur absolue.`PreferredWidth.FromPoints(40)` la méthode définit la largeur de la cellule à 40 points et`Shading.BackgroundPatternColor` applique une couleur de fond jaune clair.

## Étape 3 : insérer une cellule de taille relative

Insérer une autre cellule dont la largeur est égale à 20 % de la largeur totale du tableau. Ce dimensionnement relatif garantit que la cellule s'ajuste proportionnellement à la largeur du tableau.

```csharp
// Insérer une cellule de taille relative (pourcentage).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

La largeur de cette cellule sera de 20 % de la largeur totale du tableau, ce qui la rendra adaptable à différentes tailles d'écran ou mises en page de documents.

### Étape 4 : insérer une cellule à taille automatique

Enfin, insérez une cellule qui s’agrandit automatiquement en fonction de l’espace disponible restant dans le tableau.

```csharp
// Insérer une cellule de taille automatique.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 Le`PreferredWidth.Auto` Le paramètre permet à cette cellule de s'agrandir ou de se contracter en fonction de l'espace restant après la prise en compte des autres cellules. Cela garantit que la mise en page du tableau est équilibrée et professionnelle.

## Étape 5 : Finaliser et enregistrer le document

Une fois que vous avez inséré toutes vos cellules, complétez le tableau et enregistrez le document dans le chemin spécifié.

```csharp
// Sauvegarder le document.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Cette étape finalise le tableau et enregistre le document avec le nom de fichier « WorkingWithTables.PreferredWidthSettings.docx » dans votre répertoire désigné.

## Conclusion

Créer des tableaux avec des paramètres de largeur préférés dans Aspose.Words pour .NET est simple une fois que vous avez compris les différentes options de dimensionnement disponibles. Que vous ayez besoin de largeurs de cellule fixes, relatives ou automatiques, Aspose.Words offre la flexibilité nécessaire pour gérer efficacement divers scénarios de mise en page de tableau. En suivant les étapes décrites dans ce guide, vous pouvez vous assurer que vos tableaux sont bien structurés et visuellement attrayants dans vos documents Word.

## FAQ

### Quelle est la différence entre les largeurs de cellule absolues et relatives ?
Les largeurs absolues des cellules sont fixes et ne changent pas, tandis que les largeurs relatives s'ajustent en fonction de la largeur totale du tableau.

### Puis-je utiliser des pourcentages négatifs pour les largeurs relatives ?
Non, les pourcentages négatifs ne sont pas valables pour les largeurs de cellules. Seuls les pourcentages positifs sont autorisés.

### Comment fonctionne la fonction de dimensionnement automatique ?
Le dimensionnement automatique ajuste la largeur de la cellule pour remplir tout espace restant dans le tableau une fois que d'autres cellules ont été dimensionnées.

### Puis-je appliquer différents styles à des cellules avec différents paramètres de largeur ?
Oui, vous pouvez appliquer différents styles et formats aux cellules, quels que soient leurs paramètres de largeur.

### Que se passe-t-il si la largeur totale du tableau est inférieure à la somme de toutes les largeurs de cellules ?
Le tableau ajustera automatiquement la largeur des cellules pour s'adapter à l'espace disponible, ce qui peut entraîner le rétrécissement de certaines cellules.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
