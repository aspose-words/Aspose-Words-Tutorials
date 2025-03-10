---
title: Convertir des métafichiers en SVG
linktitle: Convertir des métafichiers en SVG
second_title: API de traitement de documents Aspose.Words
description: Convertissez des métafichiers en SVG dans des documents Word à l'aide d'Aspose.Words pour .NET avec ce guide détaillé, étape par étape. Parfait pour les développeurs de tous niveaux.
weight: 10
url: /fr/net/programming-with-htmlsaveoptions/convert-metafiles-to-svg/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convertir des métafichiers en SVG

## Introduction

Bonjour à tous les passionnés de codage ! Vous êtes-vous déjà demandé comment convertir des métafichiers en SVG dans vos documents Word à l'aide d'Aspose.Words pour .NET ? Eh bien, vous allez vous régaler ! Aujourd'hui, nous allons plonger dans le monde d'Aspose.Words, une bibliothèque puissante qui simplifie la manipulation des documents. À la fin de ce didacticiel, vous serez un pro de la conversion de métafichiers en SVG, ce qui rendra vos documents Word plus polyvalents et visuellement attrayants. Alors, commençons, d'accord ?

## Prérequis

Avant de passer aux détails, assurons-nous que nous avons tout ce dont nous avons besoin pour commencer :

1.  Aspose.Words pour .NET : vous pouvez le télécharger à partir du[Page de sortie d'Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur.
3. Environnement de développement : n’importe quel IDE comme Visual Studio fera l’affaire.
4. Connaissances de base de C# : une petite familiarité avec C# sera utile, mais ne vous inquiétez pas si vous êtes débutant, nous vous expliquerons tout en détail.

## Importer des espaces de noms

Tout d'abord, commençons par les importations. Dans votre projet C#, vous devrez importer les espaces de noms nécessaires. Ceci est crucial pour accéder aux fonctionnalités d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Maintenant que nous avons trié nos prérequis et nos espaces de noms, plongeons dans le guide étape par étape pour convertir les métafichiers en SVG.

## Étape 1 : Initialiser le document et DocumentBuilder

 Très bien, commençons par créer un nouveau document Word et initialiser le`DocumentBuilder` objet. Ce générateur nous aidera à ajouter du contenu à notre document.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ici, nous initialisons un nouveau document et un générateur de documents.`dataDir` la variable contient le chemin d'accès à votre répertoire de documents où vous enregistrerez vos fichiers.

## Étape 2 : Ajouter du texte au document

 Ensuite, ajoutons du texte à notre document. Nous utiliserons le`Write` méthode de la`DocumentBuilder` pour insérer du texte.

```csharp
builder.Write("Here is an SVG image: ");
```

Cette ligne ajoute le texte « Voici une image SVG : » à votre document. Il est toujours judicieux de fournir un contexte ou une description de l'image SVG que vous êtes sur le point d'insérer.

## Étape 3 : Insérer une image SVG

 Maintenant, passons à la partie amusante ! Nous allons insérer une image SVG dans notre document en utilisant le`InsertHtml` méthode.

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg> ");
```

Cet extrait insère une image SVG dans le document. Le code SVG définit un polygone simple avec des points, des couleurs et des styles spécifiés. N'hésitez pas à personnaliser le code SVG selon vos besoins.

## Étape 4 : définir les options HtmlSaveOptions

 Pour garantir que nos métafichiers sont enregistrés au format SVG, nous allons définir le`HtmlSaveOptions` et définissez le`MetafileFormat`propriété à`HtmlMetafileFormat.Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

Cela indique à Aspose.Words d'enregistrer tous les métafichiers du document au format SVG lors de l'exportation au format HTML.

## Étape 5 : Enregistrer le document

 Enfin, sauvegardons notre document. Nous utiliserons le`Save` méthode de la`Document` classe et transmettez le chemin du répertoire et les options d'enregistrement.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
```

 Cette ligne enregistre le document dans le répertoire spécifié avec le nom de fichier`WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html` . Le`saveOptions` assurez-vous que les métafichiers sont convertis en SVG.

## Conclusion

Et voilà ! Vous avez réussi à convertir des métafichiers en SVG dans votre document Word à l'aide d'Aspose.Words pour .NET. Plutôt sympa, non ? Avec seulement quelques lignes de code, vous pouvez améliorer vos documents Word en ajoutant des graphiques vectoriels évolutifs, les rendant ainsi plus dynamiques et visuellement attrayants. Alors, allez-y et essayez-le dans vos projets. Bon codage !

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui vous permet de créer, modifier et convertir des documents Word par programmation à l'aide de C#.

### Puis-je utiliser Aspose.Words pour .NET avec .NET Core ?
Oui, Aspose.Words pour .NET prend en charge .NET Core, ce qui le rend polyvalent pour différentes applications .NET.

### Comment puis-je obtenir un essai gratuit d'Aspose.Words pour .NET ?
 Vous pouvez télécharger une version d'essai gratuite à partir du[Page de sortie d'Aspose](https://releases.aspose.com/).

### Est-il possible de convertir d'autres formats d'image en SVG à l'aide d'Aspose.Words ?
Oui, Aspose.Words prend en charge la conversion de divers formats d'image, y compris les métafichiers, en SVG.

### Où puis-je trouver la documentation d'Aspose.Words pour .NET ?
 Vous trouverez une documentation détaillée sur le[Page de documentation d'Aspose](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
