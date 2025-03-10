---
title: Comparaison de la granularité dans un document Word
linktitle: Comparaison de la granularité dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez la fonctionnalité Comparer la granularité dans les documents Word d'Aspose.Words pour .NET qui permet de comparer les documents caractère par caractère, en signalant les modifications apportées.
weight: 10
url: /fr/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comparaison de la granularité dans un document Word

Voici un guide étape par étape pour expliquer le code source C# ci-dessous, qui utilise la fonctionnalité Comparer la granularité dans le document Word d'Aspose.Words pour .NET.

## Étape 1 : Introduction

La fonctionnalité Comparer la granularité d'Aspose.Words pour .NET vous permet de comparer des documents au niveau des caractères. Cela signifie que chaque caractère sera comparé et que les modifications seront signalées en conséquence.

## Étape 2 : Configuration de l'environnement

Avant de commencer, vous devez configurer votre environnement de développement pour qu'il fonctionne avec Aspose.Words pour .NET. Assurez-vous que la bibliothèque Aspose.Words est installée et que vous disposez d'un projet C# approprié pour intégrer le code.

## Étape 3 : ajouter les assemblages requis

Pour utiliser la fonctionnalité Comparer la granularité d'Aspose.Words pour .NET, vous devez ajouter les assemblys nécessaires à votre projet. Assurez-vous d'avoir les références appropriées à Aspose.Words dans votre projet.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Étape 4 : Création de documents

Dans cette étape, nous allons créer deux documents à l'aide de la classe DocumentBuilder. Ces documents seront utilisés pour la comparaison.

```csharp
// Créer le document A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Créer le document B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Étape 5 : Configuration des options de comparaison

Dans cette étape, nous allons configurer les options de comparaison pour spécifier la granularité de la comparaison. Ici, nous utiliserons la granularité au niveau des caractères.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Étape 6 : Comparaison des documents

Comparons maintenant les documents à l'aide de la méthode Compare de la classe Document. Les modifications seront enregistrées dans le document A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 Le`Compare`La méthode compare le document A avec le document B et enregistre les modifications apportées au document A. Vous pouvez spécifier le nom de l'auteur et la date de comparaison pour référence.

## Conclusion

Dans cet article, nous avons exploré la fonctionnalité Comparer la granularité d'Aspose.Words pour .NET. Cette fonctionnalité vous permet de comparer des documents au niveau des caractères et de signaler les modifications. Vous pouvez utiliser ces connaissances pour effectuer des comparaisons de documents détaillées dans vos projets.

### Exemple de code source pour la granularité de comparaison à l'aide d'Aspose.Words pour .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusion

Dans ce didacticiel, nous avons exploré la fonctionnalité de granularité de comparaison d'Aspose.Words pour .NET. Cette fonctionnalité vous permet de spécifier le niveau de détail lors de la comparaison de documents. En choisissant différents niveaux de granularité, vous pouvez effectuer des comparaisons détaillées au niveau du caractère, du mot ou du bloc, en fonction de vos besoins spécifiques. Aspose.Words pour .NET offre une fonction de comparaison de documents flexible et puissante, facilitant l'identification des différences dans les documents avec différents niveaux de granularité.

### FAQ

#### Q : Quel est le but de l’utilisation de la granularité de comparaison dans Aspose.Words pour .NET ?

A : La granularité de comparaison dans Aspose.Words pour .NET vous permet de spécifier le niveau de détail lors de la comparaison de documents. Grâce à cette fonctionnalité, vous pouvez comparer des documents à différents niveaux, tels que le niveau des caractères, des mots ou même des blocs. Chaque niveau de granularité fournit un niveau de détail différent dans les résultats de comparaison.

#### Q : Comment utiliser la granularité de comparaison dans Aspose.Words pour .NET ?

R : Pour utiliser la granularité de comparaison dans Aspose.Words pour .NET, suivez ces étapes :
1. Configurez votre environnement de développement avec la bibliothèque Aspose.Words.
2. Ajoutez les assemblages nécessaires à votre projet en référençant Aspose.Words.
3.  Créez les documents que vous souhaitez comparer à l'aide de la`DocumentBuilder` classe.
4.  Configurez les options de comparaison en créant un`CompareOptions` objet et réglage de la`Granularity` propriété au niveau souhaité (par exemple,`Granularity.CharLevel` (pour une comparaison au niveau des caractères).
5.  Utilisez le`Compare`méthode sur un document, en passant l'autre document et le`CompareOptions` objet comme paramètres. Cette méthode comparera les documents en fonction de la granularité spécifiée et enregistrera les modifications dans le premier document.

#### Q : Quels sont les niveaux de granularité de comparaison disponibles dans Aspose.Words pour .NET ?

R : Aspose.Words pour .NET fournit trois niveaux de granularité de comparaison :
- `Granularity.CharLevel`: Compare les documents au niveau des caractères.
- `Granularity.WordLevel`: Compare les documents au niveau du mot.
- `Granularity.BlockLevel`: Compare les documents au niveau du bloc.

#### Q : Comment puis-je interpréter les résultats de comparaison avec une granularité au niveau des caractères ?

R : Avec la granularité au niveau des caractères, chaque caractère des documents comparés est analysé pour détecter les différences. Les résultats de la comparaison montreront les changements au niveau de chaque caractère, y compris les ajouts, les suppressions et les modifications.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
