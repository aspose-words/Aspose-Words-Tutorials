---
"description": "Apprenez à appliquer une bordure de contour à un tableau dans Word avec Aspose.Words pour .NET. Suivez notre guide étape par étape pour une mise en forme parfaite de votre tableau."
"linktitle": "Appliquer une bordure de contour"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Appliquer une bordure de contour"
"url": "/fr/net/programming-with-table-styles-and-formatting/apply-outline-border/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Appliquer une bordure de contour

## Introduction

Dans le tutoriel d'aujourd'hui, nous nous plongeons dans l'univers de la manipulation de documents avec Aspose.Words pour .NET. Plus précisément, nous allons apprendre à appliquer une bordure de contour à un tableau dans un document Word. C'est une compétence essentielle si vous travaillez fréquemment avec la génération et la mise en forme automatisées de documents. Alors, commençons à créer des tableaux non seulement fonctionnels, mais aussi esthétiques.

## Prérequis

Avant de passer au code, vous aurez besoin de quelques éléments :

1. Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Vous pouvez le télécharger. [ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un environnement de développement approprié comme Visual Studio.
3. Connaissances de base de C# : une compréhension fondamentale de C# vous aidera à suivre le didacticiel.

## Importer des espaces de noms

Pour commencer, assurez-vous d'avoir importé les espaces de noms nécessaires. Ceci est essentiel pour accéder aux fonctionnalités d'Aspose.Words.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Décomposons le processus en étapes simples et gérables.

## Étape 1 : Charger le document

Tout d’abord, nous devons charger le document Word qui contient le tableau que nous voulons formater.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

Dans cette étape, nous utilisons le `Document` Classe d'Aspose.Words pour charger un document existant. Remplacer `"YOUR DOCUMENT DIRECTORY"` avec le chemin réel où votre document est stocké.

## Étape 2 : Accéder au tableau

Ensuite, nous devons accéder au tableau spécifique que nous souhaitons formater. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

Ici, `GetChild` La méthode récupère la première table du document. Les paramètres `NodeType.Table, 0, true` assurez-vous que nous obtenons le bon type de nœud.

## Étape 3 : Aligner la table

Maintenant, centrons le tableau sur la page.

```csharp
table.Alignment = TableAlignment.Center;
```

Cette étape garantit que la table est parfaitement centrée, lui donnant un aspect professionnel.

## Étape 4 : Effacer les bordures existantes

Avant d’appliquer de nouvelles frontières, nous devons effacer celles qui existent déjà.

```csharp
table.ClearBorders();
```

Le nettoyage des bordures garantit que nos nouvelles bordures sont appliquées proprement sans qu'aucun ancien style n'interfère.

## Étape 5 : Définir les bordures du contour

Appliquons maintenant les bordures vertes au tableau.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

Chaque type de bordure (gauche, droite, haut, bas) est défini individuellement. Nous utilisons `LineStyle.Single` pour une ligne continue, `1.5` pour la largeur de la ligne, et `Color.Green` pour la couleur de la bordure.

## Étape 6 : Appliquer l'ombrage des cellules

Pour rendre le tableau plus attrayant visuellement, remplissons les cellules avec une couleur vert clair.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

Ici, `SetShading` est utilisé pour appliquer une couleur vert clair unie aux cellules, faisant ressortir le tableau.

## Étape 7 : Enregistrer le document

Enfin, enregistrez le document modifié.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Cette étape enregistre votre document avec la mise en forme appliquée. Vous pouvez l'ouvrir pour voir le tableau parfaitement mis en forme.

## Conclusion

Et voilà ! En suivant ces étapes, vous avez appliqué avec succès une bordure de contour à un tableau dans un document Word avec Aspose.Words pour .NET. Ce tutoriel a couvert le chargement du document, l'accès au tableau, son alignement, la suppression des bordures existantes, l'application de nouvelles bordures, l'ajout d'un ombrage de cellule et enfin l'enregistrement du document. 

Grâce à ces compétences, vous pouvez améliorer la présentation visuelle de vos tableaux et rendre vos documents plus professionnels et attrayants. Bon codage !

## FAQ

### Puis-je appliquer des styles différents à chaque bordure du tableau ?  
Oui, vous pouvez appliquer différents styles et couleurs à chaque bordure en ajustant les paramètres dans le `SetBorder` méthode.

### Comment puis-je modifier la largeur de la bordure ?  
Vous pouvez modifier la largeur en modifiant le troisième paramètre dans le `SetBorder` méthode. Par exemple, `1.5` définit une largeur de 1,5 point.

### Est-il possible d'appliquer un ombrage à des cellules individuelles ?  
Oui, vous pouvez appliquer un ombrage à des cellules individuelles en accédant à chaque cellule et en utilisant le `SetShading` méthode.

### Puis-je utiliser d’autres couleurs pour les bordures et l’ombrage ?  
Absolument ! Vous pouvez utiliser n'importe quelle couleur disponible dans le `System.Drawing.Color` classe.

### Comment centrer la table horizontalement ?  
Le `table.Alignment = TableAlignment.Center;` la ligne dans le code centre le tableau horizontalement sur la page.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}