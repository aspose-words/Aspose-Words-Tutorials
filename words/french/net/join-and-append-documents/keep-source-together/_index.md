---
"description": "Découvrez comment éviter le fractionnement des tableaux sur plusieurs pages avec Aspose.Words pour .NET grâce à ce guide étape par étape. Obtenez des documents Word nets et professionnels."
"linktitle": "Gardez la table ensemble"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Gardez la table ensemble"
"url": "/fr/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gardez la table ensemble

## Introduction

Les tableaux sont essentiels à de nombreux documents Word, mais il arrive parfois qu'ils soient répartis sur deux pages. Cela peut perturber la fluidité de votre document et nuire à sa lisibilité. Ne serait-il pas judicieux de pouvoir conserver l'intégralité du tableau sur une seule page ? Aspose.Words pour .NET offre une solution simple à ce problème ! Dans ce tutoriel, nous vous expliquerons comment éviter que les tableaux ne soient répartis sur plusieurs pages, garantissant ainsi un rendu soigné et professionnel.

## Prérequis

Avant de passer au didacticiel, assurons-nous que vous disposez de tout ce dont vous avez besoin pour suivre le tutoriel en douceur.

### Bibliothèque Aspose.Words pour .NET

Tout d'abord, vous devez installer Aspose.Words pour .NET. Cette puissante bibliothèque vous permet de travailler avec des documents Word par programmation.

- [Télécharger Aspose.Words pour .NET](https://releases.aspose.com/words/net/)

### Environnement de développement

Vous devez disposer d'un environnement de développement configuré pour exécuter du code C#, tel que :

- Visual Studio (toute version récente)
- .NET Framework 2.0 ou version ultérieure

### Un document Word avec un tableau

Vous aurez besoin d'un document Word contenant un tableau. Dans ce tutoriel, nous utiliserons un exemple de document intitulé `"Table spanning two pages.docx"`Ce fichier contient un tableau qui s'étend actuellement sur deux pages.

### Licence temporaire (facultatif)

Bien qu'Aspose.Words soit fourni avec un essai gratuit, vous souhaiterez peut-être utiliser un [permis temporaire](https://purchase.aspose.com/temporary-license/) pour libérer tout le potentiel de la bibliothèque.

## Importer des packages

Avant d'écrire du code, nous devons importer les espaces de noms nécessaires à l'utilisation d'Aspose.Words pour .NET. Ajoutez les importations suivantes en haut de votre fichier de code :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ces espaces de noms vous donnent accès à des classes telles que `Document`, `Table`, `Cell`, et d'autres que nous utiliserons dans ce tutoriel.

## Étape 1 : Charger le document

La première chose à faire est de charger le document Word contenant le tableau. Pour cela, nous utiliserons l'outil `Document` Classe d'Aspose.Words. Cette classe permet d'ouvrir et de manipuler des fichiers Word par programmation.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

Dans cet extrait de code, nous spécifions l'emplacement de notre document. Remplacer `"YOUR DOCUMENTS DIRECTORY"` avec le répertoire réel dans lequel votre document est stocké.

## Étape 2 : Accéder au tableau

Une fois le document chargé, l'étape suivante consiste à accéder au tableau que nous souhaitons conserver. Dans cet exemple, nous supposons que ce tableau est le premier du document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Cette ligne de code recherche le premier tableau du document. `GetChild` La méthode récupère un type spécifique de nœud, qui dans ce cas est `NodeType.Table`. Le `0` indique que nous voulons la première table, et la `true` flag garantit que nous recherchons de manière récursive dans tous les nœuds enfants.

## Étape 3 : Parcourir les cellules du tableau

Nous devons maintenant parcourir chaque cellule du tableau. Comme un tableau contient plusieurs lignes et que chaque ligne contient plusieurs cellules, nous allons parcourir chaque cellule et veiller à ce que l'itération ne soit pas interrompue sur plusieurs pages.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Ici, `GetChildNodes` récupère toutes les cellules du tableau et nous parcourons chacune d'elles. `EnsureMinimum()` La méthode garantit que chaque cellule contient au moins un paragraphe, car une cellule vide pourrait causer des problèmes plus tard.

## Étape 4 : définir la propriété KeepWithNext

Pour éviter que le tableau ne soit divisé en plusieurs pages, nous devons définir le `KeepWithNext` Propriété pour chaque paragraphe du tableau. Cette propriété garantit que le paragraphe reste en harmonie avec le paragraphe suivant, empêchant ainsi les sauts de page entre eux.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Cette boucle vérifie chaque paragraphe de chaque cellule. La condition garantit que nous n'appliquons pas la `KeepWithNext` propriété au dernier paragraphe de la dernière ligne. Sinon, la propriété n'aurait aucun effet puisqu'il n'y a pas de paragraphe suivant.

## Étape 5 : Enregistrer le document

Enfin, après avoir appliqué le `KeepWithNext` propriété, nous devons enregistrer le document modifié.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Cette ligne enregistre le document mis à jour sous un nouveau nom, préservant ainsi le fichier d'origine. Vous pouvez maintenant ouvrir le fichier résultant et constater que le tableau n'est plus divisé en deux pages !

## Conclusion

Et voilà ! En suivant ces étapes simples, vous pouvez facilement éviter que les tableaux ne se fragmentent sur plusieurs pages de vos documents Word grâce à Aspose.Words pour .NET. Que vous travailliez sur des rapports, des contrats ou d'autres documents, conserver les tableaux intacts garantit un rendu plus soigné et professionnel.

L'atout majeur d'Aspose.Words réside dans sa flexibilité et sa simplicité d'utilisation, vous permettant de manipuler des documents Word par programmation sans avoir besoin d'installer Microsoft Word sur votre ordinateur. Maintenant que vous maîtrisez la gestion des tableaux, explorez les autres fonctionnalités de la bibliothèque pour améliorer vos compétences en traitement de documents !

## FAQ

### Pourquoi mon tableau continue-t-il de se briser sur plusieurs pages après avoir utilisé ce code ?

Si votre table continue de se casser, assurez-vous d'avoir appliqué le `KeepWithNext` Propriété correctement. Vérifiez que tous les paragraphes, sauf le dernier de chaque cellule, ont cette propriété définie.

### Puis-je conserver uniquement des lignes spécifiques ensemble ?

Oui, vous pouvez appliquer de manière sélective le `KeepWithNext` propriété sur des lignes ou des paragraphes spécifiques dans le tableau pour contrôler quelles parties doivent rester ensemble.

### Cette méthode fonctionne-t-elle avec de grandes tables ?

Pour les tableaux très volumineux, Word peut les diviser sur plusieurs pages s'il n'y a pas assez d'espace pour les contenir tous sur une seule page. Pensez à ajuster la mise en forme ou les marges de votre tableau pour l'adapter aux tableaux plus grands.

### Puis-je utiliser cette méthode avec d’autres formats de documents ?

Oui ! Aspose.Words pour .NET prend en charge de nombreux formats tels que DOC, DOCX, PDF, etc. La même méthode fonctionne avec tous les formats prenant en charge les tableaux.

### Aspose.Words pour .NET est-elle une bibliothèque gratuite ?

Aspose.Words pour .NET propose un essai gratuit, mais pour accéder à toutes les fonctionnalités, vous devrez acheter une licence. Vous pouvez explorer les options de licence sur le site [Page d'achat Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}