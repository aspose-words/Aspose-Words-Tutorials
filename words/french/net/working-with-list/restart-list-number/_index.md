---
"description": "Apprenez à réinitialiser les numéros de liste dans des documents Word avec Aspose.Words pour .NET. Ce guide détaillé de 2 000 mots couvre tout ce que vous devez savoir, de la configuration à la personnalisation avancée."
"linktitle": "Numéro de liste de redémarrage"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Numéro de liste de redémarrage"
"url": "/fr/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Numéro de liste de redémarrage

## Introduction

Vous souhaitez maîtriser l'art de la manipulation de listes dans vos documents Word avec Aspose.Words pour .NET ? Vous êtes au bon endroit ! Dans ce tutoriel, nous allons explorer en profondeur la réinitialisation des numéros de liste, une fonctionnalité pratique qui vous permettra d'améliorer vos compétences en automatisation de documents. Attachez vos ceintures, c'est parti !

## Prérequis

Avant de passer au code, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1. Aspose.Words pour .NET : Aspose.Words pour .NET doit être installé. Si ce n'est pas déjà fait, vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : assurez-vous de disposer d’un environnement de développement approprié comme Visual Studio.
3. Connaissances de base de C# : une compréhension de base de C# vous aidera à suivre le didacticiel.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Ils sont essentiels pour accéder aux fonctionnalités d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Décomposons maintenant le processus en étapes faciles à suivre. Nous aborderons toutes les étapes, de la création d'une liste à la reprise de sa numérotation.

## Étape 1 : Configurez votre document et votre générateur

Avant de pouvoir manipuler des listes, vous avez besoin d'un document et d'un DocumentBuilder. DocumentBuilder est l'outil idéal pour ajouter du contenu à votre document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Créez et personnalisez votre première liste

Nous allons ensuite créer une liste à partir d'un modèle et personnaliser son apparence. Dans cet exemple, nous utilisons le format numérique arabe avec parenthèses.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Ici, nous avons défini la couleur de la police sur rouge et aligné le texte à droite.

## Étape 3 : Ajoutez des éléments à votre première liste

Votre liste étant prête, il est temps d'ajouter quelques éléments. Le DocumentBuilder `ListFormat.List` la propriété aide à appliquer le format de liste au texte.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Étape 4 : Redémarrer la numérotation de la liste

Pour réutiliser la liste et recommencer sa numérotation, vous devez créer une copie de la liste d'origine. Cela vous permet de modifier la nouvelle liste indépendamment.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Dans cet exemple, la nouvelle liste commence au numéro 10.

## Étape 5 : Ajouter des éléments à la nouvelle liste

Comme précédemment, ajoutez des éléments à votre nouvelle liste. Cela montre que la liste redémarre au nombre spécifié.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Étape 6 : Enregistrez votre document

Enfin, enregistrez votre document dans le répertoire spécifié.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusion

Recommencer les numéros de liste dans des documents Word avec Aspose.Words pour .NET est simple et extrêmement utile. Que vous génériez des rapports, créiez des documents structurés ou souhaitiez simplement mieux contrôler vos listes, cette technique est faite pour vous.

## FAQ

### Puis-je utiliser d'autres modèles de liste en plus de NumberArabicParenthesis ?

Absolument ! Aspose.Words propose différents modèles de listes, avec puces, lettres, chiffres romains, etc. Choisissez celui qui correspond le mieux à vos besoins.

### Comment puis-je changer le niveau de la liste ?

Vous pouvez modifier le niveau de la liste en modifiant le `ListLevels` propriété. Par exemple, `list1.ListLevels[1]` ferait référence au deuxième niveau de la liste.

### Puis-je recommencer la numérotation à n'importe quel numéro ?

Oui, vous pouvez définir le numéro de départ sur n'importe quelle valeur entière à l'aide de la `StartAt` propriété du niveau de la liste.

### Est-il possible d'avoir un formatage différent pour différents niveaux de liste ?

En effet ! Chaque niveau de liste peut avoir ses propres paramètres de formatage, tels que la police, l'alignement et le style de numérotation.

### Que faire si je souhaite continuer la numérotation à partir d’une liste précédente au lieu de recommencer ?

Si vous souhaitez poursuivre la numérotation, inutile de créer une copie de la liste. Continuez simplement à ajouter des éléments à la liste d'origine.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}