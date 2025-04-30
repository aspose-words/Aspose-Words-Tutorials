---
"description": "Apprenez à appliquer des styles de code en ligne dans vos documents Word avec Aspose.Words pour .NET. Ce tutoriel aborde les guillemets simples et multiples pour la mise en forme du code."
"linktitle": "Code en ligne"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Code en ligne"
"url": "/fr/net/working-with-markdown/inline-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Code en ligne

## Introduction

Si vous générez ou manipulez des documents Word par programmation, vous devrez peut-être formater du texte pour qu'il ressemble à du code. Que ce soit pour de la documentation ou des extraits de code dans un rapport, Aspose.Words pour .NET offre une solution robuste pour gérer le style du texte. Dans ce tutoriel, nous allons nous concentrer sur l'application de styles de code en ligne à du texte avec Aspose.Words. Nous explorerons comment définir et utiliser des styles personnalisés pour des guillemets simples ou multiples, afin de mettre en valeur vos segments de code dans vos documents.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1. Bibliothèque Aspose.Words pour .NET : Assurez-vous qu'Aspose.Words est installé dans votre environnement .NET. Vous pouvez le télécharger depuis le [Page des versions d'Aspose.Words pour .NET](https://releases.aspose.com/words/net/).

2. Connaissances de base de la programmation .NET : ce guide suppose que vous avez une compréhension fondamentale de la programmation C# et .NET.

3. Environnement de développement : vous devez disposer d’un environnement de développement .NET configuré, tel que Visual Studio, dans lequel vous pouvez écrire et exécuter du code C#.

## Importer des espaces de noms

Pour commencer à utiliser Aspose.Words dans votre projet, vous devez importer les espaces de noms nécessaires. Voici comment procéder :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Décomposons le processus en étapes claires :

## Étape 1 : Initialiser le document et DocumentBuilder

Tout d’abord, vous devez créer un nouveau document et un `DocumentBuilder` exemple. Le `DocumentBuilder` La classe vous aide à ajouter du contenu et à le formater dans un document Word.

```csharp
// Initialisez DocumentBuilder avec le nouveau document.
DocumentBuilder builder = new DocumentBuilder();
```

## Étape 2 : ajouter un style de code en ligne avec un backtick

Dans cette étape, nous allons définir un style pour le code en ligne avec un seul accent grave. Ce style formatera le texte pour qu'il ressemble à du code en ligne.

### Définir le style

```csharp
// Définissez un nouveau style de caractère pour le code en ligne avec un backtick.
Style inlineCode1BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode");
inlineCode1BackTicks.Font.Name = "Courier New"; // Une police typique pour le code.
inlineCode1BackTicks.Font.Size = 10.5; // Taille de police pour le code en ligne.
inlineCode1BackTicks.Font.Color = System.Drawing.Color.Blue; // Couleur du texte du code.
inlineCode1BackTicks.Font.Bold = true; // Mettez le texte du code en gras.
```

### Appliquer le style

Vous pouvez désormais appliquer ce style au texte de votre document.

```csharp
// Utilisez DocumentBuilder pour insérer du texte avec le style de code en ligne.
builder.Font.Style = inlineCode1BackTicks;
builder.Writeln("Text with InlineCode style with 1 backtick");
```

## Étape 3 : ajouter un style de code en ligne avec trois guillemets graves

Ensuite, nous allons définir un style pour le code en ligne avec trois guillemets inversés, qui est généralement utilisé pour les blocs de code multilignes.

### Définir le style

```csharp
// Définissez un nouveau style de caractère pour le code en ligne avec trois guillemets inversés.
Style inlineCode3BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode.3");
inlineCode3BackTicks.Font.Name = "Courier New"; // Police cohérente pour le code.
inlineCode3BackTicks.Font.Size = 10.5; // Taille de police pour le bloc de code.
inlineCode3BackTicks.Font.Color = System.Drawing.Color.Green; // Couleur différente pour la visibilité.
inlineCode3BackTicks.Font.Bold = true; // Gardez-le en gras pour le mettre en valeur.
```

### Appliquer le style

Appliquez ce style au texte pour le formater sous forme de bloc de code multiligne.

```csharp
// Appliquer le style au bloc de code.
builder.Font.Style = inlineCode3BackTicks;
builder.Writeln("Text with InlineCode style with 3 backticks");
```

## Conclusion

Mettre en forme du texte sous forme de code en ligne dans des documents Word avec Aspose.Words pour .NET est simple une fois la procédure maîtrisée. En définissant et en appliquant des styles personnalisés avec un ou plusieurs guillemets graves, vous pouvez mettre en valeur vos extraits de code. Cette méthode est particulièrement utile pour la documentation technique ou tout document où la lisibilité du code est essentielle.

N'hésitez pas à tester différents styles et options de mise en forme pour répondre au mieux à vos besoins. Aspose.Words offre une grande flexibilité, vous permettant de personnaliser considérablement l'apparence de votre document.

## FAQ

### Puis-je utiliser différentes polices pour les styles de code en ligne ?
Oui, vous pouvez utiliser la police qui vous convient. Des polices comme « Courier New » sont généralement utilisées pour le code en raison de leur espacement fixe.

### Comment changer la couleur du texte du code en ligne ?
Vous pouvez changer la couleur en définissant le `Font.Color` propriété du style à tout `System.Drawing.Color`.

### Puis-je appliquer plusieurs styles au même texte ?
Dans Aspose.Words, vous ne pouvez appliquer qu'un seul style à la fois. Si vous devez combiner des styles, pensez à en créer un nouveau qui intègre toute la mise en forme souhaitée.

### Comment appliquer des styles à un texte existant dans un document ?
Pour appliquer des styles à un texte existant, vous devez d'abord sélectionner le texte, puis appliquer le style souhaité à l'aide du `Font.Style` propriété.

### Puis-je utiliser Aspose.Words pour d’autres formats de documents ?
Aspose.Words est spécialement conçu pour les documents Word. Pour les autres formats, vous devrez peut-être utiliser d'autres bibliothèques ou convertir les documents dans un format compatible.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}