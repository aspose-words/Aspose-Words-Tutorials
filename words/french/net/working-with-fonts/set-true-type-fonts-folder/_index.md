---
title: Définir le dossier des polices True Type
linktitle: Définir le dossier des polices True Type
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir un dossier de polices True Type dans des documents Word à l'aide d'Aspose.Words pour .NET. Suivez notre guide détaillé étape par étape pour garantir une gestion cohérente des polices.
weight: 10
url: /fr/net/working-with-fonts/set-true-type-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir le dossier des polices True Type

## Introduction

Nous plongeons dans le monde fascinant de la gestion des polices dans les documents Word à l'aide d'Aspose.Words pour .NET. Si vous avez déjà eu du mal à intégrer les bonnes polices ou à vous assurer que votre document s'affiche parfaitement sur tous les appareils, vous êtes au bon endroit. Nous vous expliquerons le processus de configuration d'un dossier de polices True Type pour rationaliser la gestion des polices de votre document, garantissant ainsi la cohérence et la clarté de vos documents.

## Prérequis

Avant de passer au vif du sujet, examinons quelques conditions préalables pour vous assurer que vous êtes prêt à réussir :

1.  Aspose.Words pour .NET : assurez-vous que la dernière version est installée. Vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un environnement de développement .NET fonctionnel, tel que Visual Studio.
3. Connaissances de base de C# : une familiarité avec la programmation C# sera utile.
4. Un exemple de document : Préparez un document Word avec lequel vous souhaitez travailler.

## Importer des espaces de noms

Tout d'abord, nous devons importer les espaces de noms nécessaires. Ils sont en quelque sorte l'équipe des coulisses qui veille au bon déroulement de l'opération.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Étape 1 : Chargez votre document

 Commençons par charger votre document. Nous utiliserons le`Document` classe de Aspose.Words pour charger un document Word existant.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 2 : Initialiser FontSettings

 Ensuite, nous allons créer une instance de`FontSettings`classe. Cette classe nous permet de personnaliser la façon dont les polices sont gérées dans notre document.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Étape 3 : définir le dossier des polices

Vient maintenant la partie intéressante. Nous allons spécifier le dossier dans lequel se trouvent nos polices True Type. Cette étape garantit qu'Aspose.Words utilise les polices de ce dossier lors du rendu ou de l'intégration des polices.

```csharp
// Notez que ce paramètre remplacera toutes les sources de polices par défaut recherchées par défaut.
// Désormais, seuls ces dossiers seront recherchés pour les polices lors du rendu ou de l'incorporation des polices.
fontSettings.SetFontsFolder(@"C:\MyFonts\", false);
```

## Étape 4 : appliquer les paramètres de police au document

Une fois nos paramètres de police configurés, nous allons maintenant appliquer ces paramètres à notre document. Cette étape est cruciale pour garantir que notre document utilise les polices spécifiées.

```csharp
// Définir les paramètres de police
doc.FontSettings = fontSettings;
```

## Étape 5 : Enregistrer le document

Enfin, nous allons enregistrer le document. Vous pouvez l'enregistrer dans différents formats, mais pour ce tutoriel, nous l'enregistrerons au format PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetTrueTypeFontsFolder.pdf");
```

## Conclusion

Et voilà ! Vous avez réussi à configurer un dossier de polices True Type pour vos documents Word à l'aide d'Aspose.Words pour .NET. Cela garantit que vos documents ont un aspect cohérent et professionnel sur toutes les plateformes. La gestion des polices est un aspect essentiel de la création de documents, et avec Aspose.Words, c'est incroyablement simple.

## FAQ

### Puis-je utiliser plusieurs dossiers de polices ?
 Oui, vous pouvez utiliser plusieurs dossiers de polices en combinant`FontSettings.GetFontSources` et`FontSettings.SetFontSources`.

### Que faire si le dossier de polices spécifié n'existe pas ?
Si le dossier de polices spécifié n'existe pas, Aspose.Words ne pourra pas localiser les polices et les polices système par défaut seront utilisées à la place.

### Puis-je revenir aux paramètres de police par défaut ?
 Oui, vous pouvez revenir aux paramètres de police par défaut en réinitialisant le`FontSettings` exemple.

### Est-il possible d'intégrer des polices dans le document ?
Oui, Aspose.Words vous permet d'intégrer des polices dans le document pour garantir la cohérence sur différents appareils.

### Dans quels formats puis-je enregistrer mon document ?
Aspose.Words prend en charge une variété de formats, notamment PDF, DOCX, HTML, etc.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
