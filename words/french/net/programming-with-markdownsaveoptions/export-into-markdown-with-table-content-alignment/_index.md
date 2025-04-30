---
"description": "Apprenez à exporter des documents Word vers Markdown avec des tableaux alignés grâce à Aspose.Words pour .NET. Suivez notre guide étape par étape pour des tableaux Markdown parfaits."
"linktitle": "Exporter vers Markdown avec alignement du contenu du tableau"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Exporter vers Markdown avec alignement du contenu du tableau"
"url": "/fr/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exporter vers Markdown avec alignement du contenu du tableau

## Introduction

Salut ! Vous êtes-vous déjà demandé comment exporter votre document Word au format Markdown avec des tableaux parfaitement alignés ? Que vous soyez développeur travaillant sur la documentation ou simplement passionné de Markdown, ce guide est fait pour vous. Nous allons explorer les subtilités de l'utilisation d'Aspose.Words pour .NET pour y parvenir. Prêt à transformer vos tableaux Word en tableaux Markdown parfaitement alignés ? C'est parti !

## Prérequis

Avant de plonger dans le code, vous devez mettre en place quelques éléments :

1. Bibliothèque Aspose.Words pour .NET : Assurez-vous de disposer de la bibliothèque Aspose.Words pour .NET. Vous pouvez la télécharger depuis le [Page des versions d'Aspose](https://releases.aspose.com/words/net/).
2. Environnement de développement : Configurez votre environnement de développement. Visual Studio est un choix populaire pour le développement .NET.
3. Connaissances de base de C# : comprendre C# est essentiel car nous allons écrire du code dans ce langage.
4. Exemple de document Word : disposez d’un document Word que vous pouvez utiliser pour les tests.

## Importer des espaces de noms

Avant de commencer le codage, importons les espaces de noms nécessaires. Ils nous donneront accès aux classes et méthodes Aspose.Words que nous utiliserons.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Initialiser le document et DocumentBuilder

Tout d’abord, nous devons créer un nouveau document Word et initialiser un `DocumentBuilder` objet pour commencer à construire notre document.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Créer un nouveau document.
Document doc = new Document();

// Initialiser DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Insérer des cellules et aligner le contenu

Nous allons ensuite insérer des cellules dans notre document et définir leur alignement. Ceci est essentiel pour garantir que l'exportation Markdown conserve le bon alignement.

```csharp
// Insérez une cellule et définissez l'alignement à droite.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Insérez une autre cellule et définissez l’alignement au centre.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Étape 3 : Définir l'alignement du contenu du tableau pour l'exportation Markdown

Maintenant, il est temps de configurer le `MarkdownSaveOptions` Pour contrôler l'alignement du contenu du tableau dans le fichier Markdown exporté. Nous allons enregistrer le document avec différents paramètres d'alignement pour voir comment cela fonctionne.

```csharp
// Créez un objet MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Enregistrer le document avec un alignement à gauche.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Modifiez l'alignement à droite et enregistrez.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Modifiez l'alignement au centre et enregistrez.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Étape 4 : Utiliser l’alignement automatique du contenu du tableau

Le `Auto` L'option d'alignement reprend l'alignement du premier paragraphe de la colonne correspondante du tableau. Cela peut être pratique lorsque vous avez des alignements mixtes dans un même tableau.

```csharp
// Définissez l'alignement sur Auto.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Enregistrer le document avec alignement automatique.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Conclusion

Et voilà ! Exporter des documents Word en Markdown avec des tableaux alignés avec Aspose.Words pour .NET est un jeu d'enfant une fois que vous maîtrisez la technique. Cette puissante bibliothèque simplifie le contrôle de la mise en forme et de l'alignement de vos tableaux, garantissant ainsi l'apparence parfaite de vos documents Markdown. Bon code !

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, modifier, convertir et exporter des documents Word par programmation.

### Puis-je définir des alignements différents pour différentes colonnes dans le même tableau ?
Oui, en utilisant le `Auto` option d'alignement, vous pouvez avoir différents alignements en fonction du premier paragraphe de chaque colonne.

### Ai-je besoin d’une licence pour utiliser Aspose.Words pour .NET ?
Oui, Aspose.Words pour .NET nécessite une licence pour bénéficier de toutes ses fonctionnalités. Vous pouvez obtenir une [permis temporaire](https://purchase.aspose.com/temporary-license/) pour évaluation.

### Est-il possible d'exporter d'autres éléments de document vers Markdown à l'aide d'Aspose.Words ?
Oui, Aspose.Words prend en charge l'exportation de divers éléments tels que des titres, des listes et des images au format Markdown.

### Où puis-je obtenir de l’aide si je rencontre des problèmes ?
Vous pouvez obtenir du soutien auprès du [Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}