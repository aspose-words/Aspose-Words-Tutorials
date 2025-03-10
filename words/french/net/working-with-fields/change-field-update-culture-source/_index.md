---
title: Changer le champ Mettre à jour la culture Source
linktitle: Changer le champ Mettre à jour la culture Source
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment modifier la source de la culture de mise à jour des champs dans Aspose.Words pour .NET avec ce guide. Contrôlez facilement le formatage des dates en fonction de différentes cultures.
weight: 10
url: /fr/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Changer le champ Mettre à jour la culture Source

## Introduction

Dans ce didacticiel, nous allons plonger dans le monde d'Aspose.Words pour .NET et découvrir comment modifier la source de la culture de mise à jour des champs. Si vous travaillez avec des documents Word qui incluent des champs de date et que vous devez contrôler la façon dont ces dates sont formatées en fonction de différentes cultures, ce guide est fait pour vous. Examinons le processus étape par étape, en veillant à ce que vous compreniez chaque concept et que vous puissiez l'appliquer efficacement dans vos projets.

## Prérequis

Avant de passer au code, assurez-vous de disposer des éléments suivants :

-  Aspose.Words pour .NET : vous pouvez le télécharger à partir de[ici](https://releases.aspose.com/words/net/).
- Environnement de développement : tout IDE compatible .NET (par exemple, Visual Studio).
- Connaissances de base de C# : ce didacticiel suppose que vous avez une compréhension fondamentale de la programmation C#.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires à notre projet. Cela nous permettra d'avoir accès à toutes les classes et méthodes requises fournies par Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Maintenant, décomposons l’exemple en plusieurs étapes pour vous aider à comprendre comment modifier la source de culture de mise à jour de champ dans Aspose.Words pour .NET.

## Étape 1 : Initialiser le document

 La première étape consiste à créer une nouvelle instance de`Document` classe et un`DocumentBuilder`. Ceci établit les bases de la construction et de la manipulation de notre document Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : insérer des champs avec des paramètres régionaux spécifiques

Ensuite, nous devons insérer des champs dans le document. Pour cet exemple, nous allons insérer deux champs de date. Nous allons définir les paramètres régionaux de la police sur l'allemand (LocaleId = 1031) pour montrer comment la culture affecte le format de date.

```csharp
builder.Font.LocaleId = 1031; // Allemand
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Étape 3 : Définir la source de la culture de mise à jour du champ

 Pour contrôler la culture utilisée lors de la mise à jour des champs, nous définissons le`FieldUpdateCultureSource` propriété de la`FieldOptions`classe. Cette propriété détermine si la culture est extraite du code de champ ou du document.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Étape 4 : Exécuter le publipostage

Nous devons maintenant exécuter une opération de publipostage pour remplir les champs avec des données réelles. Dans cet exemple, nous allons définir le deuxième champ de date (`Date2`) jusqu'au 1er janvier 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Étape 5 : Enregistrer le document

Enfin, nous enregistrons le document dans le répertoire spécifié. Cette étape termine le processus de modification de la source de culture de mise à jour du champ.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Conclusion

Et voilà ! Vous avez modifié avec succès la source de culture de mise à jour de champ dans Aspose.Words pour .NET. En suivant ces étapes, vous pouvez vous assurer que vos documents Word affichent les dates et autres valeurs de champ conformément aux paramètres de culture spécifiés. Cela peut être particulièrement utile lors de la génération de documents destinés à un public international.

## FAQ

###  Quel est le but de définir le`LocaleId`?
 Le`LocaleId` spécifie les paramètres de culture pour le texte, ce qui affecte la manière dont les dates et autres données sensibles aux paramètres régionaux sont formatées.

### Puis-je utiliser une langue autre que l'allemand ?
 Oui, vous pouvez définir le`LocaleId`à n'importe quel identifiant de paramètres régionaux valide. Par exemple, 1033 pour l'anglais (États-Unis).

###  Que se passe-t-il si je ne règle pas le`FieldUpdateCultureSource` property?
Si cette propriété n'est pas définie, les paramètres de culture par défaut du document seront utilisés lors de la mise à jour des champs.

### Est-il possible de mettre à jour les champs en fonction de la culture du document au lieu du code du champ ?
 Oui, vous pouvez définir`FieldUpdateCultureSource` à`FieldUpdateCultureSource.Document` pour utiliser les paramètres de culture du document.

### Comment formater les dates selon un modèle différent ?
 Vous pouvez modifier le modèle de format de date dans le`InsertField` méthode en modifiant le`\\@` valeur de commutation.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
