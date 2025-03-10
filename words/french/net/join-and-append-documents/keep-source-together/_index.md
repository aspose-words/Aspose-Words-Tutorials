---
title: Gardez la table ensemble
linktitle: Gardez la table ensemble
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment empêcher les tableaux de se diviser en plusieurs pages à l'aide d'Aspose.Words pour .NET grâce à ce guide étape par étape. Assurez-vous de documents Word soignés et professionnels
weight: 10
url: /fr/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gardez la table ensemble

## Introduction

Les tableaux sont un élément essentiel de nombreux documents Word, mais il peut arriver que votre tableau soit réparti sur deux pages. Cela peut perturber le flux de votre document et affecter sa lisibilité. Ne serait-il pas agréable de pouvoir conserver l'intégralité du tableau sur une seule page ? Eh bien, avec Aspose.Words pour .NET, il existe une solution simple à ce problème ! Dans ce didacticiel, nous verrons comment empêcher les tableaux de se diviser sur plusieurs pages, garantissant ainsi que votre document soit soigné et professionnel.

## Prérequis

Avant de passer au didacticiel, assurons-nous que vous disposez de tout ce dont vous avez besoin pour le suivre en douceur.

### Bibliothèque Aspose.Words pour .NET

Tout d'abord, vous devez avoir installé Aspose.Words pour .NET. Il s'agit de la puissante bibliothèque qui vous permet de travailler avec des documents Word par programmation.

- [Télécharger Aspose.Words pour .NET](https://releases.aspose.com/words/net/)

### Environnement de développement

Vous devez disposer d'un environnement de développement configuré pour exécuter du code C#, tel que :

- Visual Studio (toute version récente)
- .NET Framework 2.0 ou version ultérieure

### Un document Word avec un tableau

 Vous aurez besoin d'un document Word contenant un tableau. Dans ce tutoriel, nous travaillerons avec un exemple de document appelé`"Table spanning two pages.docx"`Ce fichier contient un tableau qui s'étend actuellement sur deux pages.

### Licence temporaire (facultatif)

 Bien qu'Aspose.Words soit fourni avec un essai gratuit, vous souhaiterez peut-être utiliser un[permis temporaire](https://purchase.aspose.com/temporary-license/) pour exploiter pleinement le potentiel de la bibliothèque.

## Paquets d'importation

Avant d'écrire du code, nous devons importer les espaces de noms nécessaires pour travailler avec Aspose.Words pour .NET. Ajoutez les importations suivantes en haut de votre fichier de code :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

 Ces espaces de noms vous donnent accès à des classes telles que`Document`, `Table`, `Cell`, et d'autres que nous utiliserons dans ce tutoriel.

## Étape 1 : Charger le document

 La première chose que nous devons faire est de charger le document Word qui contient le tableau. Pour cela, nous utiliserons le`Document` classe de Aspose.Words. Cette classe vous permet d'ouvrir et de manipuler des fichiers Word par programmation.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

 Dans cet extrait de code, nous spécifions l'emplacement de notre document. Remplacer`"YOUR DOCUMENTS DIRECTORY"` avec le répertoire réel où votre document est stocké.

## Étape 2 : Accéder au tableau

Une fois le document chargé, l'étape suivante consiste à accéder au tableau que nous souhaitons conserver. Dans cet exemple, nous supposons que le tableau est le premier tableau du document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

 Cette ligne de code recherche le premier tableau du document.`GetChild` la méthode récupère un type spécifique de nœud, qui dans ce cas est`NodeType.Table` . Le`0` indique que nous voulons la première table, et la`true`flag garantit que nous recherchons de manière récursive dans tous les nœuds enfants.

## Étape 3 : Parcourir les cellules du tableau

Nous devons maintenant parcourir chaque cellule du tableau. Étant donné qu'un tableau contient plusieurs lignes et que chaque ligne contient plusieurs cellules, nous allons parcourir chaque cellule et nous assurer qu'elle ne se divise pas en plusieurs pages.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

 Ici,`GetChildNodes` récupère toutes les cellules du tableau et nous parcourons chacune d'elles.`EnsureMinimum()` La méthode garantit que chaque cellule contient au moins un paragraphe, car une cellule vide pourrait causer des problèmes plus tard.

## Étape 4 : définir la propriété KeepWithNext

 Pour éviter que le tableau ne soit réparti sur plusieurs pages, nous devons définir le`KeepWithNext` propriété pour chaque paragraphe du tableau. Cette propriété garantit que le paragraphe reste avec le paragraphe suivant, empêchant ainsi efficacement les sauts de page entre eux.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

 Cette boucle vérifie chaque paragraphe à l'intérieur de chaque cellule. La condition garantit que nous n'appliquons pas la`KeepWithNext`propriété au dernier paragraphe de la dernière ligne. Sinon, la propriété n'aurait aucun effet puisqu'il n'y a pas de paragraphe suivant.

## Étape 5 : Enregistrer le document

 Enfin, après avoir appliqué le`KeepWithNext` propriété, nous devons enregistrer le document modifié.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Cette ligne enregistre le document mis à jour sous un nouveau nom, en préservant le fichier d'origine. Vous pouvez maintenant ouvrir le fichier résultant et constater que le tableau n'est plus divisé sur deux pages !

## Conclusion

Et voilà ! En suivant ces étapes simples, vous pouvez facilement empêcher les tableaux de se diviser en plusieurs pages dans les documents Word à l'aide d'Aspose.Words pour .NET. Que vous travailliez sur des rapports, des contrats ou d'autres documents, le fait de conserver les tableaux intacts garantit un aspect plus soigné et professionnel.

La beauté d'Aspose.Words réside dans sa flexibilité et sa facilité d'utilisation, qui vous permettent de manipuler des documents Word par programmation sans avoir besoin d'installer Microsoft Word sur votre machine. Maintenant que vous savez comment organiser des tableaux, explorez d'autres fonctionnalités de la bibliothèque pour faire passer vos compétences en matière de traitement de documents au niveau supérieur !

## FAQ

### Pourquoi mon tableau continue-t-il à se décomposer sur plusieurs pages après avoir utilisé ce code ?

 Si votre table continue à se casser, assurez-vous d'avoir appliqué le`KeepWithNext` propriété correctement. Vérifiez que tous les paragraphes, sauf le dernier de chaque cellule, ont cette propriété définie.

### Puis-je conserver uniquement des lignes spécifiques ensemble ?

 Oui, vous pouvez appliquer de manière sélective le`KeepWithNext` propriété sur des lignes ou des paragraphes spécifiques dans le tableau pour contrôler les parties qui doivent rester ensemble.

### Cette méthode fonctionne-t-elle avec de grandes tables ?

Pour les tableaux très volumineux, Word peut toujours les diviser sur plusieurs pages s'il n'y a pas assez d'espace pour contenir l'intégralité du tableau sur une seule page. Pensez à ajuster la mise en forme ou les marges de votre tableau pour qu'il puisse accueillir des tableaux plus grands.

### Puis-je utiliser cette méthode avec d’autres formats de documents ?

Oui ! Aspose.Words pour .NET prend en charge de nombreux formats tels que DOC, DOCX, PDF et autres. La même méthode fonctionne sur tous les formats prenant en charge les tableaux.

### Aspose.Words pour .NET est-elle une bibliothèque gratuite ?

 Aspose.Words pour .NET propose un essai gratuit, mais pour un accès complet à toutes les fonctionnalités, vous devrez acheter une licence. Vous pouvez explorer les options de licence sur le site[Page d'achat Aspose](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
