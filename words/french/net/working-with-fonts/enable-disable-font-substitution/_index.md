---
"description": "Découvrez comment activer ou désactiver la substitution de polices dans vos documents Word avec Aspose.Words pour .NET. Assurez la cohérence de vos documents sur toutes les plateformes."
"linktitle": "Activer Désactiver la substitution de police"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Activer Désactiver la substitution de police"
"url": "/fr/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Activer Désactiver la substitution de police

## Introduction

Vous est-il déjà arrivé que les polices que vous aviez soigneusement choisies dans un document Word soient remplacées lorsqu'elles sont affichées sur un autre ordinateur ? C'est agaçant, non ? Ce phénomène est dû à la substitution de polices, un processus par lequel le système remplace une police manquante par une police disponible. Mais pas d'inquiétude ! Avec Aspose.Words pour .NET, vous pouvez facilement gérer et contrôler la substitution de polices. Dans ce tutoriel, nous vous expliquerons comment activer ou désactiver la substitution de polices dans vos documents Word, afin que vos documents s'affichent toujours comme vous le souhaitez.

## Prérequis

Avant de plonger dans les étapes, assurons-nous que vous avez tout ce dont vous avez besoin :

- Aspose.Words pour .NET : téléchargez la dernière version [ici](https://releases.aspose.com/words/net/).
- Visual Studio : toute version prenant en charge .NET.
- Connaissances de base de C# : cela vous aidera à suivre les exemples de codage.

## Importer des espaces de noms

Pour commencer, assurez-vous d'avoir importé les espaces de noms nécessaires dans votre projet. Ajoutez-les en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Décomposons maintenant le processus en étapes simples et gérables.

## Étape 1 : Configurez votre projet

Commencez par configurer un nouveau projet dans Visual Studio et ajoutez une référence à la bibliothèque Aspose.Words pour .NET. Si ce n'est pas déjà fait, téléchargez-la depuis le [Site Web d'Aspose](https://releases.aspose.com/words/net/).

## Étape 2 : Chargez votre document

Ensuite, chargez le document sur lequel vous souhaitez travailler. Voici comment procéder :

```csharp
// Chemin d'accès à votre répertoire de documents 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Remplacer `"YOUR DOCUMENT DIRECTORY"` avec le chemin d'accès réel à votre répertoire de documents. Ce code charge le document en mémoire afin que vous puissiez le manipuler.

## Étape 3 : Configurer les paramètres de police

Maintenant, créons un `FontSettings` objet pour gérer les paramètres de substitution de police :

```csharp
FontSettings fontSettings = new FontSettings();
```

## Étape 4 : définir la substitution de police par défaut

Définissez la police de substitution par défaut sur la police de votre choix. Cette police sera utilisée si la police d'origine n'est pas disponible :

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

## Étape 7 : Enregistrez votre document

Enfin, enregistrez votre document modifié. Vous pouvez l'enregistrer au format de votre choix. Pour ce tutoriel, nous l'enregistrerons au format PDF :

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement contrôler la substitution de polices dans vos documents Word avec Aspose.Words pour .NET. Vos documents conservent ainsi leur aspect et leur convivialité, quel que soit l'endroit où ils sont consultés.

## FAQ

### Puis-je utiliser d'autres polices qu'Arial pour la substitution ?

Absolument ! Vous pouvez spécifier n'importe quelle police disponible sur votre système en modifiant son nom dans le `DefaultFontName` propriété.

### Que se passe-t-il si la police par défaut spécifiée n'est pas disponible ?

Si la police par défaut n'est pas disponible, Aspose.Words utilisera un mécanisme de secours système pour trouver un remplacement approprié.

### Puis-je réactiver la substitution de police après l'avoir désactivée ?

Oui, vous pouvez basculer le `Enabled` propriété de `FontInfoSubstitution` retour à `true` si vous souhaitez réactiver la substitution de police.

### Existe-t-il un moyen de vérifier quelles polices sont remplacées ?

Oui, Aspose.Words fournit des méthodes pour enregistrer et suivre la substitution de polices, vous permettant de voir quelles polices sont remplacées.

### Puis-je utiliser cette méthode pour d’autres formats de documents en plus de DOCX ?

Absolument ! Aspose.Words prend en charge différents formats et vous pouvez appliquer ces paramètres de police à n'importe quel format pris en charge.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}