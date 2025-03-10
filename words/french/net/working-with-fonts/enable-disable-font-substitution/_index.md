---
title: Activer Désactiver la substitution de police
linktitle: Activer Désactiver la substitution de police
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment activer ou désactiver la substitution de polices dans les documents Word à l'aide d'Aspose.Words pour .NET. Assurez-vous que vos documents sont cohérents sur toutes les plateformes.
weight: 10
url: /fr/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Activer Désactiver la substitution de police

## Introduction

Vous êtes-vous déjà retrouvé dans une situation où les polices que vous avez soigneusement choisies dans un document Word sont remplacées lorsqu'elles sont affichées sur un autre ordinateur ? C'est ennuyeux, n'est-ce pas ? Cela se produit en raison de la substitution de polices, un processus par lequel le système remplace une police manquante par une police disponible. Mais ne vous inquiétez pas ! Avec Aspose.Words pour .NET, vous pouvez facilement gérer et contrôler la substitution de polices. Dans ce didacticiel, nous vous guiderons à travers les étapes à suivre pour activer ou désactiver la substitution de polices dans vos documents Word, en veillant à ce que vos documents aient toujours l'apparence souhaitée.

## Prérequis

Avant de passer aux étapes suivantes, assurons-nous que vous disposez de tout ce dont vous avez besoin :

-  Aspose.Words pour .NET : téléchargez la dernière version[ici](https://releases.aspose.com/words/net/).
- Visual Studio : toute version prenant en charge .NET.
- Connaissances de base de C# : cela vous aidera à suivre les exemples de codage.

## Importer des espaces de noms

Pour commencer, assurez-vous que les espaces de noms nécessaires sont importés dans votre projet. Ajoutez-les en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Maintenant, décomposons le processus en étapes simples et gérables.

## Étape 1 : Configurez votre projet

Tout d'abord, configurez un nouveau projet dans Visual Studio et ajoutez une référence à la bibliothèque Aspose.Words pour .NET. Si vous ne l'avez pas déjà fait, téléchargez-la à partir du[Site Web d'Aspose](https://releases.aspose.com/words/net/).

## Étape 2 : Chargez votre document

Ensuite, chargez le document avec lequel vous souhaitez travailler. Voici comment procéder :

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre répertoire de documents. Ce code charge le document en mémoire afin que vous puissiez le manipuler.

## Étape 3 : Configurer les paramètres de police

 Maintenant, créons un`FontSettings` objet pour gérer les paramètres de substitution de police :

```csharp
FontSettings fontSettings = new FontSettings();
```

## Étape 4 : définir la substitution de police par défaut

Définissez la substitution de police par défaut sur une police de votre choix. Cette police sera utilisée si la police d'origine n'est pas disponible :

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Dans cet exemple, nous utilisons Arial comme police par défaut.

## Étape 5 : Désactiver la substitution des informations de police

Pour désactiver la substitution des informations de police, qui empêche le système de remplacer les polices manquantes par celles disponibles, utilisez le code suivant :

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Étape 6 : Appliquer les paramètres de police au document

Appliquez maintenant ces paramètres à votre document :

```csharp
doc.FontSettings = fontSettings;
```

## Étape 7 : Enregistrez votre document

Enfin, enregistrez votre document modifié. Vous pouvez l'enregistrer dans le format de votre choix. Pour ce tutoriel, nous l'enregistrerons au format PDF :

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement contrôler la substitution de polices dans vos documents Word à l'aide d'Aspose.Words pour .NET. Cela garantit que vos documents conservent leur apparence prévue, quel que soit l'endroit où ils sont consultés.

## FAQ

### Puis-je utiliser d'autres polices qu'Arial pour la substitution ?

 Absolument ! Vous pouvez spécifier n'importe quelle police disponible sur votre système en modifiant le nom de la police dans le`DefaultFontName` propriété.

### Que se passe-t-il si la police par défaut spécifiée n'est pas disponible ?

Si la police par défaut n'est pas disponible, Aspose.Words utilisera un mécanisme de secours système pour trouver un remplacement approprié.

### Puis-je réactiver la substitution de police après l'avoir désactivée ?

 Oui, vous pouvez basculer le`Enabled` propriété de`FontInfoSubstitution` retour à`true` si vous souhaitez réactiver la substitution de police.

### Existe-t-il un moyen de vérifier quelles polices sont substituées ?

Oui, Aspose.Words fournit des méthodes pour enregistrer et suivre la substitution de polices, vous permettant de voir quelles polices sont remplacées.

### Puis-je utiliser cette méthode pour d’autres formats de documents en plus de DOCX ?

Absolument ! Aspose.Words prend en charge différents formats et vous pouvez appliquer ces paramètres de police à n'importe quel format pris en charge.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
