---
title: Définir les dossiers de polices
linktitle: Définir les dossiers de polices
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir des dossiers de polices personnalisés dans Aspose.Words pour .NET avec ce guide complet, étape par étape. Idéal pour les développeurs qui cherchent à améliorer les polices de leurs documents.
weight: 10
url: /fr/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir les dossiers de polices

## Introduction

Bonjour ! Vous êtes prêt à plonger dans le monde des polices personnalisées dans Aspose.Words pour .NET ? Commençons. Ce didacticiel vous guidera tout au long du processus de configuration des dossiers de polices personnalisées, garantissant que vos documents s'affichent exactement comme vous le souhaitez. Que vous soyez un développeur chevronné ou que vous débutiez, ce guide vous guidera à chaque étape. Alors, faisons en sorte que ces polices soient fabuleuses !

## Prérequis

Avant de nous lancer, assurons-nous que vous avez tout ce dont vous avez besoin :

-  Aspose.Words pour .NET : vous pouvez[télécharger](https://releases.aspose.com/words/net/) si vous ne l'avez pas déjà fait.
- Visual Studio : n’importe quelle version fonctionnera, mais la plus récente est toujours la meilleure.
- Un document : nous utiliserons un document Word pour ce tutoriel. Vous pouvez créer le vôtre ou utiliser un document existant.
- Polices personnalisées : préparez des polices personnalisées. Nous les utiliserons pour vous montrer comment définir des dossiers de polices.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Cela est essentiel pour accéder aux classes et méthodes dont nous avons besoin à partir d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Avec ces espaces de noms importés, nous sommes prêts à commencer à configurer nos dossiers de polices personnalisés.

## Étape 1 : Définissez votre répertoire de documents

 Commençons par définir le chemin d'accès à votre répertoire de documents. C'est là que votre document Word est stocké. Nous utiliserons une variable appelée`dataDir` pour stocker ce chemin.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin d'accès réel à votre répertoire. Ceci est crucial car Aspose.Words devra savoir où trouver votre document.

## Étape 2 : définir les sources de police

 Ensuite, nous devons configurer les sources de polices. C'est ici que nous indiquons à Aspose.Words où trouver nos polices personnalisées. Nous allons utiliser le`FontSettings.DefaultInstance.SetFontsSources` méthode pour y parvenir.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Voici ce que nous faisons :

- SystemFontSource : cela indique à Aspose.Words d'utiliser les polices par défaut du système.
-  FolderFontSource : c'est ici que nous spécifions le dossier contenant nos polices personnalisées. Remplacer`"C:\\MyFonts\\"` avec le chemin d'accès à votre répertoire de polices personnalisées.`true` le paramètre indique que les sous-répertoires doivent également être inclus.

## Étape 3 : Chargez votre document

Maintenant que nous avons configuré nos sources de polices, il est temps de charger le document avec lequel nous voulons travailler. Nous utiliserons le`Document` classe d'Aspose.Mots pour cela.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Assurez-vous que`"Rendering.docx"` est le nom de votre document Word. Si votre document porte un nom différent, veillez à le mettre à jour en conséquence.

## Étape 4 : Enregistrez votre document au format PDF

 Enfin, enregistrons notre document au format PDF pour voir les polices personnalisées en action. Nous utiliserons le`Save` méthode de la`Document` classe.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Cela enregistrera votre document au format PDF dans le répertoire spécifié, en utilisant les polices personnalisées que nous avons configurées précédemment.

## Conclusion

Et voilà ! Vous avez réussi à configurer des dossiers de polices personnalisées dans Aspose.Words pour .NET et à enregistrer votre document au format PDF avec ces polices personnalisées. Plutôt sympa, non ? La personnalisation des polices peut faire une énorme différence dans l'apparence de vos documents, et vous savez maintenant exactement comment procéder. Bon codage !

## FAQ

### Comment installer Aspose.Words pour .NET ?

 Tu peux[télécharger](https://releases.aspose.com/words/net/) la dernière version d'Aspose.Words pour .NET à partir du site Web.

### Puis-je utiliser plusieurs dossiers de polices personnalisés ?

 Oui, vous pouvez ajouter plusieurs`FolderFontSource` des cas à la`SetFontsSources`méthode pour utiliser des polices provenant de différents répertoires.

### Est-il nécessaire d'inclure les polices système ?

L'inclusion des polices système est facultative mais recommandée pour garantir que toutes les polices standard sont disponibles.

### Quels types de fichiers sont pris en charge par Aspose.Words ?

Aspose.Words prend en charge une large gamme de formats de fichiers, notamment DOCX, DOC, PDF, TXT, HTML et bien d'autres.

### Comment puis-je obtenir une licence temporaire pour Aspose.Words ?

 Vous pouvez obtenir un[permis temporaire](https://purchase.aspose.com/temporary-license/) depuis le site Web Aspose pour tester toutes les fonctionnalités d'Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
