---
title: Définir la position horizontale ou verticale relative
linktitle: Définir la position horizontale ou verticale relative
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir des positions horizontales et verticales relatives pour les tableaux dans les documents Word à l'aide d'Aspose.Words pour .NET avec ce guide étape par étape.
weight: 10
url: /fr/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir la position horizontale ou verticale relative

## Introduction

Vous êtes-vous déjà demandé comment positionner les tableaux exactement comme vous le souhaitez dans vos documents Word ? Eh bien, vous n'êtes pas seul. Que vous créiez un rapport professionnel ou une brochure élégante, l'alignement des tableaux peut faire toute la différence. C'est là qu'Aspose.Words pour .NET s'avère utile. Ce didacticiel vous guidera étape par étape sur la façon de définir des positions horizontales ou verticales relatives pour les tableaux dans vos documents Word. Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET : si vous ne l'avez pas déjà fait, vous pouvez le télécharger[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE compatible .NET.
3. Connaissances de base de C# : ce didacticiel suppose que vous connaissez les bases de la programmation C#.

## Importer des espaces de noms

Tout d’abord, vous devez importer les espaces de noms nécessaires. Ceci est essentiel pour accéder aux fonctionnalités d’Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Étape 1 : Chargez votre document

Pour commencer, vous devez charger votre document Word dans le programme. Voici comment procéder :

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Cet extrait de code définit le chemin d'accès à votre répertoire de documents et charge le document spécifique sur lequel vous souhaitez travailler. Assurez-vous que le chemin d'accès à votre document est correct pour éviter tout problème de chargement.

## Étape 2 : Accéder au tableau

Ensuite, nous devons accéder au tableau dans le document. En règle générale, vous souhaiterez travailler avec le premier tableau de la section corps.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Cette ligne de code récupère le premier tableau du corps du document. Si votre document comporte plusieurs tableaux, vous pouvez ajuster l'index en conséquence.

## Étape 3 : définir la position horizontale

Maintenant, définissons la position horizontale du tableau par rapport à un élément spécifique. Dans cet exemple, nous le positionnerons par rapport à la colonne.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 En définissant le`HorizontalAnchor` à`RelativeHorizontalPosition.Column`, vous dites au tableau de s'aligner horizontalement par rapport à la colonne dans laquelle il se trouve.

## Étape 4 : définir la position verticale

De la même manière que pour le positionnement horizontal, vous pouvez également définir la position verticale. Ici, nous la positionnons par rapport à la page.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 Réglage de la`VerticalAnchor` à`RelativeVerticalPosition.Page` garantit que le tableau est aligné verticalement par rapport à la page.

## Étape 5 : Enregistrez votre document

Enfin, enregistrez vos modifications dans un nouveau document. Il s’agit d’une étape cruciale pour garantir que vos modifications sont conservées.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Cette commande enregistre le document modifié sous un nouveau nom, garantissant ainsi de ne pas écraser votre fichier d'origine.

## Conclusion

Et voilà ! Vous avez réussi à définir les positions horizontales et verticales relatives d'un tableau dans un document Word à l'aide d'Aspose.Words pour .NET. Grâce à cette nouvelle compétence, vous pouvez améliorer la mise en page et la lisibilité de vos documents, leur donnant ainsi un aspect plus professionnel et soigné. Continuez à expérimenter différentes positions et voyez ce qui fonctionne le mieux pour vos besoins.

## FAQ

### Puis-je positionner des tableaux par rapport à d’autres éléments ?  
Oui, Aspose.Words vous permet de positionner des tableaux par rapport à divers éléments tels que des marges, des pages, des colonnes, etc.

### Ai-je besoin d'une licence pour utiliser Aspose.Words pour .NET ?  
 Oui, vous pouvez acheter une licence[ici](https://purchase.aspose.com/buy) ou obtenir un permis temporaire[ici](https://purchase.aspose.com/temporary-license/).

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?  
 Absolument ! Vous pouvez télécharger une version d'essai gratuite[ici](https://releases.aspose.com/).

### Puis-je utiliser Aspose.Words avec d’autres langages de programmation ?  
Aspose.Words est principalement conçu pour .NET, mais il existe des versions disponibles pour Java, Python et d'autres plates-formes.

### Où puis-je trouver une documentation plus détaillée ?  
Pour des informations plus détaillées, consultez la documentation Aspose.Words[ici](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
