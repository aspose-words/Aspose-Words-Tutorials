---
title: Spécifier la police par défaut lors du rendu
linktitle: Spécifier la police par défaut lors du rendu
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment spécifier une police par défaut lors du rendu de documents Word à l'aide d'Aspose.Words pour .NET. Assurez une apparence cohérente des documents sur toutes les plateformes.
weight: 10
url: /fr/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spécifier la police par défaut lors du rendu

## Introduction

Il peut être difficile de garantir que vos documents Word s'affichent correctement sur différentes plates-formes, en particulier en ce qui concerne la compatibilité des polices. Pour conserver une apparence cohérente, vous pouvez spécifier une police par défaut lors du rendu de vos documents au format PDF ou dans d'autres formats. Dans ce didacticiel, nous verrons comment définir une police par défaut à l'aide d'Aspose.Words pour .NET, afin que vos documents aient une belle apparence, quel que soit l'endroit où ils sont affichés.

## Prérequis

Avant de plonger dans le code, voyons ce que vous devrez suivre avec ce tutoriel :

- Aspose.Words pour .NET : assurez-vous que la dernière version est installée. Vous pouvez la télécharger[ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre environnement de développement .NET.
- Connaissances de base de C# : ce didacticiel suppose que vous êtes à l'aise avec la programmation C#.

## Importer des espaces de noms

Pour commencer, vous devez importer les espaces de noms nécessaires. Ceux-ci vous permettront d'accéder aux classes et méthodes requises pour travailler avec Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Maintenant, décomposons le processus de spécification d’une police par défaut en étapes faciles à suivre.

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, définissez le chemin d'accès à votre répertoire de documents. C'est là que vos fichiers d'entrée et de sortie seront stockés.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Chargez votre document

Ensuite, chargez le document que vous souhaitez restituer. Dans cet exemple, nous utiliserons un fichier nommé « Rendering.docx ».

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 3 : Configurer les paramètres de police

 Créer une instance de`FontSettings` et spécifiez la police par défaut. Si la police définie ne peut pas être trouvée pendant le rendu, Aspose.Words utilisera la police la plus proche disponible sur la machine.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Étape 4 : appliquer les paramètres de police au document

Affectez les paramètres de police configurés à votre document.

```csharp
doc.FontSettings = fontSettings;
```

## Étape 5 : Enregistrer le document

Enfin, enregistrez le document au format souhaité. Dans ce cas, nous l'enregistrerons au format PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Conclusion

En suivant ces étapes, vous pouvez garantir que vos documents Word s'affichent avec une police par défaut spécifiée, en maintenant la cohérence sur différentes plates-formes. Cela peut être particulièrement utile pour les documents largement partagés ou affichés sur des systèmes avec une disponibilité de polices variable.


## FAQ

### Pourquoi spécifier une police par défaut dans Aspose.Words ?
La spécification d'une police par défaut garantit que votre document apparaît de manière cohérente sur différentes plates-formes, même si les polices d'origine ne sont pas disponibles.

### Que se passe-t-il si la police par défaut n'est pas trouvée lors du rendu ?
Aspose.Words utilisera la police la plus proche disponible sur la machine pour conserver l'apparence du document aussi fidèlement que possible.

### Puis-je spécifier plusieurs polices par défaut ?
 Non, vous ne pouvez spécifier qu'une seule police par défaut. Cependant, vous pouvez gérer la substitution de police pour des cas spécifiques à l'aide de l'`FontSettings` classe.

### Aspose.Words pour .NET est-il compatible avec toutes les versions de documents Word ?
Oui, Aspose.Words pour .NET prend en charge une large gamme de formats de documents Word, notamment DOC, DOCX, RTF, etc.

### Où puis-je obtenir de l’aide si je rencontre des problèmes ?
 Vous pouvez obtenir de l'aide de la communauté Aspose et des développeurs sur le[Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
