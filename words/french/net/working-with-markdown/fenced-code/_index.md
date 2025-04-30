---
"description": "Apprenez à ajouter du code et des chaînes d'informations délimités à vos documents Word avec Aspose.Words pour .NET. Guide étape par étape inclus. Améliorez vos compétences en mise en forme de documents."
"linktitle": "Code clôturé"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Code clôturé"
"url": "/fr/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Code clôturé

## Introduction

Salut à tous les codeurs ! Aujourd'hui, nous plongeons dans l'univers d'Aspose.Words pour .NET pour maîtriser l'art d'ajouter du code délimité et du code délimité avec des chaînes d'informations à vos documents Word. Imaginez votre document Word comme une toile, et vous, l'artiste, vous apprêtez à peindre avec la précision d'un développeur chevronné. Avec Aspose.Words, vous avez la possibilité d'enrichir vos documents par programmation avec des blocs de code structurés et formatés, pour des documents techniques d'une clarté et d'un professionnalisme irréprochables.

## Prérequis

Avant de passer au tutoriel, assurons-nous que vous disposez de tout ce dont vous avez besoin :

- Connaissances de base de C# : Une compréhension générale de C# vous aidera à saisir rapidement les concepts.
- Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Si ce n'est pas encore le cas, téléchargez-le. [ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre IDE C# avec lequel vous êtes à l’aise.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires. C'est comme rassembler tous vos outils avant de démarrer un projet.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Maintenant, décomposons le processus étape par étape.

## Étape 1 : Configuration de votre projet

Avant de pouvoir créer de beaux blocs de code formatés dans notre document Word, nous devons configurer un nouveau projet dans Visual Studio.

1. Créer un nouveau projet : ouvrez Visual Studio et créez une nouvelle application console C#.
2. Ajouter une référence à Aspose.Words : installez Aspose.Words via le gestionnaire de packages NuGet. Pour ce faire, faites un clic droit sur votre projet dans l'Explorateur de solutions, sélectionnez « Gérer les packages NuGet » et recherchez Aspose.Words.

## Étape 2 : Initialiser le DocumentBuilder

Maintenant que votre projet est configuré, initialisons le DocumentBuilder, qui sera notre outil principal pour ajouter du contenu au document Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Étape 3 : Créer un style pour le code clôturé

Pour ajouter du code clôturé, nous devons d'abord créer un style. Considérez cela comme la définition du thème de notre bloc de code.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Étape 4 : ajouter du code clôturé au document

Notre style étant prêt, nous pouvons maintenant ajouter un bloc de code clôturé au document.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Étape 5 : Créer un style pour le code clôturé avec une chaîne d'informations

Parfois, vous souhaiterez peut-être spécifier le langage de programmation ou ajouter des informations supplémentaires à votre bloc de code. Créons un style pour cela.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Étape 6 : Ajouter un code clôturé avec une chaîne d'informations au document

Maintenant, ajoutons un bloc de code clôturé avec une chaîne d’informations pour indiquer qu’il s’agit de code C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Conclusion

Félicitations ! Vous venez d'ajouter des blocs de code délimités et du code délimité avec des chaînes d'informations à vos documents Word grâce à Aspose.Words pour .NET. Ce n'est que la partie émergée de l'iceberg. Avec Aspose.Words, vous pouvez automatiser et améliorer le traitement de vos documents. Continuez à explorer et bon codage !

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, manipuler et convertir des documents Word par programmation.

### Puis-je utiliser Aspose.Words avec d’autres langages de programmation ?
Aspose.Words prend principalement en charge les langages .NET, mais il existe des versions disponibles pour Java, Python et d'autres langages.

### L'utilisation d'Aspose.Words est-elle gratuite ?
Aspose.Words est un produit commercial, mais vous pouvez télécharger une version d'essai gratuite [ici](https://releases.aspose.com/) pour explorer ses fonctionnalités.

### Comment puis-je obtenir de l'aide pour Aspose.Words ?
Vous pouvez obtenir du soutien de la communauté Aspose et des développeurs [ici](https://forum.aspose.com/c/words/8).

### Quelles autres fonctionnalités propose Aspose.Words ?
Aspose.Words propose une large gamme de fonctionnalités, notamment la conversion de documents, la génération de documents basés sur des modèles, la création de rapports et bien plus encore.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}