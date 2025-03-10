---
title: Rappel de césure
linktitle: Rappel de césure
second_title: API de traitement de documents Aspose.Words
description: Apprenez à implémenter le rappel de césure dans Aspose.Words pour .NET pour améliorer la mise en forme du document avec ce guide complet étape par étape.
weight: 10
url: /fr/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rappel de césure


## Introduction

Bonjour ! Vous êtes-vous déjà retrouvé embrouillé dans les complexités du formatage de texte, en particulier lorsqu'il s'agit de langues qui nécessitent une césure ? Vous n'êtes pas seul. La césure, bien que cruciale pour une mise en page de texte correcte, peut être un casse-tête. Mais devinez quoi ? Aspose.Words pour .NET est là pour vous. Cette puissante bibliothèque vous permet de gérer le formatage de texte de manière transparente, y compris la gestion de la césure via un mécanisme de rappel. Intrigué ? Plongeons dans les détails de la façon dont vous pouvez implémenter un rappel de césure à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de nous salir les mains avec le code, assurons-nous que vous avez tout ce dont vous avez besoin :

1. Aspose.Words pour .NET : Assurez-vous d'avoir la bibliothèque. Vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
2. IDE : un environnement de développement comme Visual Studio.
3. Connaissances de base de C# : Compréhension de C# et du framework .NET.
4. Dictionnaires de césure : dictionnaires de césure pour les langues que vous prévoyez d'utiliser.
5.  Licence Aspose : Une licence Aspose valide. Vous pouvez obtenir une[permis temporaire](https://purchase.aspose.com/temporary-license/) si vous n'en avez pas.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Cela garantit que notre code a accès à toutes les classes et méthodes dont nous avons besoin à partir d'Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Étape 1 : Enregistrer le rappel de césure

Pour commencer, nous devons enregistrer notre rappel de césure. C'est ici que nous indiquons à Aspose.Words d'utiliser notre logique de césure personnalisée.

```csharp
try
{
    // Enregistrer le rappel de césure.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 Ici, nous créons une instance de notre rappel personnalisé et l'attribuons à`Hyphenation.Callback`.

## Étape 2 : Définir le chemin du document

Ensuite, nous devons définir le répertoire dans lequel nos documents sont stockés. Ceci est crucial car nous allons charger et enregistrer des documents à partir de ce chemin.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers vos documents.

## Étape 3 : Charger le document

Maintenant, chargeons le document qui nécessite une césure.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Ici, nous chargeons un document texte allemand. Vous pouvez remplacer`"German text.docx"` avec le nom de fichier de votre document.

## Étape 4 : Enregistrer le document

Après avoir chargé le document, nous l'enregistrons dans un nouveau fichier, en appliquant le rappel de césure dans le processus.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Cette ligne enregistre le document au format PDF avec césure appliquée.

## Étape 5 : gérer l'exception de césure manquante du dictionnaire

Il peut arriver que vous rencontriez un problème lié à l'absence du dictionnaire de césure. Résolvons ce problème.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

Dans ce bloc, nous capturons l'exception spécifique liée aux dictionnaires manquants et imprimons le message.

## Étape 6 : implémenter la classe de rappel de césure personnalisée

 Maintenant, mettons en œuvre le`CustomHyphenationCallback` classe qui gère la demande de dictionnaires de césure.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Enregistrer le dictionnaire pour la langue demandée.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 Dans cette classe, le`RequestDictionary` La méthode est appelée chaque fois qu'un dictionnaire de césure est nécessaire. Elle vérifie la langue et enregistre le dictionnaire approprié.

## Conclusion

Et voilà ! Vous venez d'apprendre à implémenter un rappel de césure dans Aspose.Words pour .NET. En suivant ces étapes, vous pouvez vous assurer que vos documents sont magnifiquement formatés, quelle que soit la langue. Que vous travailliez en anglais, en allemand ou dans toute autre langue, cette méthode vous permet de gérer la césure sans effort.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une puissante bibliothèque de manipulation de documents qui permet aux développeurs de créer, modifier et convertir des documents par programmation.

### Pourquoi la césure est-elle importante dans la mise en forme des documents ?
La césure améliore la mise en page du texte en coupant les mots aux endroits appropriés, garantissant ainsi un document plus lisible et visuellement attrayant.

### Puis-je utiliser Aspose.Words gratuitement ?
 Aspose.Words propose un essai gratuit. Vous pouvez l'obtenir[ici](https://releases.aspose.com/).

### Comment puis-je obtenir un dictionnaire de césure ?
Vous pouvez télécharger des dictionnaires de césure à partir de diverses ressources en ligne ou créer les vôtres si nécessaire.

### Que se passe-t-il si un dictionnaire de césure est manquant ?
 Si un dictionnaire est manquant, le`RequestDictionary`La méthode génère une exception, que vous pouvez gérer pour informer l'utilisateur ou fournir une solution de secours.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
