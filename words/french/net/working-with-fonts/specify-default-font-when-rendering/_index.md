---
"description": "Apprenez à spécifier une police par défaut lors du rendu de documents Word avec Aspose.Words pour .NET. Assurez une apparence cohérente des documents sur toutes les plateformes."
"linktitle": "Spécifier la police par défaut lors du rendu"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Spécifier la police par défaut lors du rendu"
"url": "/fr/net/working-with-fonts/specify-default-font-when-rendering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spécifier la police par défaut lors du rendu

## Introduction

S'assurer que vos documents Word s'affichent correctement sur différentes plateformes peut s'avérer complexe, notamment en ce qui concerne la compatibilité des polices. Pour garantir une apparence cohérente, vous pouvez spécifier une police par défaut lors du rendu de vos documents au format PDF ou autre. Dans ce tutoriel, nous allons découvrir comment définir une police par défaut avec Aspose.Words pour .NET, afin que vos documents s'affichent parfaitement, quel que soit l'emplacement de consultation.

## Prérequis

Avant de plonger dans le code, voyons ce que vous devrez suivre avec ce tutoriel :

- Aspose.Words pour .NET : Assurez-vous d'avoir installé la dernière version. Vous pouvez la télécharger. [ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre environnement de développement .NET.
- Connaissances de base de C# : ce didacticiel suppose que vous êtes à l'aise avec la programmation C#.

## Importer des espaces de noms

Pour commencer, vous devez importer les espaces de noms nécessaires. Ceux-ci vous permettront d'accéder aux classes et méthodes nécessaires à l'utilisation d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Décomposons maintenant le processus de spécification d’une police par défaut en étapes faciles à suivre.

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, définissez le chemin d'accès à votre répertoire de documents. C'est là que seront stockés vos fichiers d'entrée et de sortie.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Chargez votre document

Ensuite, chargez le document à afficher. Dans cet exemple, nous utiliserons un fichier nommé « Rendu.docx ».

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 3 : Configurer les paramètres de police

Créer une instance de `FontSettings` et spécifiez la police par défaut. Si la police définie est introuvable lors du rendu, Aspose.Words utilisera la police la plus proche disponible sur la machine.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Étape 4 : Appliquer les paramètres de police au document

Affectez les paramètres de police configurés à votre document.

```csharp
doc.FontSettings = fontSettings;
```

## Étape 5 : Enregistrer le document

Enfin, enregistrez le document au format souhaité. Dans ce cas, nous l'enregistrerons au format PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Conclusion

En suivant ces étapes, vous pouvez garantir que vos documents Word s'affichent avec une police par défaut spécifique, garantissant ainsi la cohérence sur différentes plateformes. Cela peut être particulièrement utile pour les documents largement partagés ou consultés sur des systèmes dont la disponibilité des polices varie.


## FAQ

### Pourquoi spécifier une police par défaut dans Aspose.Words ?
La spécification d'une police par défaut garantit que votre document apparaît de manière cohérente sur différentes plates-formes, même si les polices d'origine ne sont pas disponibles.

### Que se passe-t-il si la police par défaut n'est pas trouvée lors du rendu ?
Aspose.Words utilisera la police la plus proche disponible sur la machine pour conserver l'apparence du document aussi fidèlement que possible.

### Puis-je spécifier plusieurs polices par défaut ?
Non, vous ne pouvez spécifier qu'une seule police par défaut. Cependant, vous pouvez gérer la substitution de polices dans des cas spécifiques grâce à l'option `FontSettings` classe.

### Aspose.Words pour .NET est-il compatible avec toutes les versions de documents Word ?
Oui, Aspose.Words pour .NET prend en charge une large gamme de formats de documents Word, notamment DOC, DOCX, RTF, etc.

### Où puis-je obtenir de l’aide si je rencontre des problèmes ?
Vous pouvez obtenir du soutien de la communauté Aspose et des développeurs sur le [Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}