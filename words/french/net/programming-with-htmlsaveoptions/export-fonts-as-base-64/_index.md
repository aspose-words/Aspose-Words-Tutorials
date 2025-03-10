---
title: Exporter les polices en base 64
linktitle: Exporter les polices en base 64
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment exporter des polices au format Base64 à l'aide d'Aspose.Words pour .NET dans ce didacticiel détaillé. Assurez-vous que les polices sont intégrées et affichées correctement dans les fichiers HTML.
weight: 10
url: /fr/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exporter les polices en base 64

## Introduction

Aspose.Words pour .NET est un outil puissant pour manipuler des documents Word par programmation. L'une de ses fonctionnalités intéressantes est l'exportation de polices au format Base64 dans des fichiers HTML, garantissant ainsi que les polices sont intégrées et affichées correctement dans différents navigateurs et systèmes. Dans ce didacticiel, nous verrons comment y parvenir. Vous êtes prêt à rendre les polices de vos documents Word compatibles avec le Web ? Commençons !

## Prérequis

Avant de passer au codage, assurons-nous que vous disposez de tout ce dont vous avez besoin :

-  Bibliothèque Aspose.Words pour .NET : vous pouvez la télécharger à partir du[Sorties d'Aspose](https://releases.aspose.com/words/net/) page.
- Environnement de développement .NET : tout IDE comme Visual Studio fonctionnera parfaitement.
- Connaissances de base de C# : vous n’avez pas besoin d’être un pro, mais une compréhension de base sera utile.

## Importer des espaces de noms

Pour utiliser Aspose.Words pour .NET, vous devez importer les espaces de noms nécessaires dans votre code C#. Cela rend toutes les classes et méthodes disponibles pour l'utilisation.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Configurez votre projet

Tout d’abord, configurons votre projet et installons la bibliothèque Aspose.Words.

### 1.1 Créer un nouveau projet

Ouvrez Visual Studio et créez un nouveau projet d'application console. Nommez-le de manière significative, par exemple « ExportFontsBase64 ».

### 1.2 Installer Aspose.Words

Vous pouvez installer Aspose.Words pour .NET via le gestionnaire de packages NuGet :

1. Faites un clic droit sur votre projet dans l’Explorateur de solutions.
2. Sélectionnez « Gérer les packages NuGet ».
3. Recherchez « Aspose.Words » et installez-le.

Vous pouvez également exécuter la commande suivante dans la console du gestionnaire de packages :

```sh
Install-Package Aspose.Words
```

## Étape 2 : Chargez votre document Word

Maintenant que votre projet est configuré, chargeons le document Word à partir duquel vous souhaitez exporter les polices.

### 2.1 Définir le répertoire des documents

Tout d’abord, définissez le répertoire où se trouve votre document Word :

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre répertoire de documents.

### 2.2 Charger le document

 Ensuite, chargez votre document à l’aide de la`Document` classe:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Assurez-vous que « Rendering.docx » se trouve dans votre répertoire spécifié.

## Étape 3 : Configurer les options d’enregistrement HTML

 Pour exporter des polices en Base64, nous devons configurer le`HtmlSaveOptions`.


 Créer une instance de`HtmlSaveOptions` et définissez le`ExportFontsAsBase64`propriété à`true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Étape 4 : Enregistrer le document au format HTML

Enfin, enregistrons le document avec les options configurées.


 Utilisez le`Save` méthode de la`Document` classe pour sauvegarder votre document :

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Cette ligne enregistrera votre document sous forme de fichier HTML avec les polices exportées en Base64, garantissant qu'elles sont intégrées dans le HTML.

## Conclusion

Félicitations ! Vous avez exporté avec succès des polices au format Base64 à partir d'un document Word à l'aide d'Aspose.Words pour .NET. Cela garantit que vos polices sont conservées et affichées correctement sur différentes plates-formes. Que vous prépariez des documents pour un affichage sur le Web ou que vous garantissiez simplement la compatibilité, cette fonctionnalité est incroyablement utile.

## FAQ

### Qu'est-ce que l'encodage Base64 ?
Base64 est une méthode d'encodage de données binaires (comme les polices) dans un format texte. Cela garantit la compatibilité avec les formats textuels comme HTML.

### Pourquoi devrais-je utiliser Base64 pour les polices en HTML ?
L'utilisation de Base64 garantit que les polices sont intégrées directement dans le HTML, évitant ainsi les problèmes liés aux fichiers de polices manquants et garantissant un affichage cohérent.

### Puis-je utiliser cette méthode pour d’autres ressources comme des images ?
Absolument ! Aspose.Words pour .NET vous permet d'intégrer diverses ressources, y compris des images, au format Base64 dans vos fichiers HTML.

### Que faire si mon document comporte plusieurs polices ?
Aucun problème ! Aspose.Words pour .NET intégrera toutes les polices utilisées dans votre document au format Base64 dans le fichier HTML résultant.

### L'utilisation d'Aspose.Words pour .NET est-elle gratuite ?
 Aspose.Words for .NET est une bibliothèque commerciale. Cependant, vous pouvez télécharger une version d'essai gratuite à partir du[Sorties d'Aspose](https://releases.aspose.com/) page.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
