---
title: Format de règle horizontale dans un document Word
linktitle: Format de règle horizontale dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer des règles horizontales personnalisables dans des documents Word à l'aide d'Aspose.Words pour .NET. Améliorez l'automatisation de vos documents.
weight: 10
url: /fr/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format de règle horizontale dans un document Word

## Introduction

Dans le domaine du développement .NET, la manipulation et la mise en forme de documents Word par programmation peuvent être une tâche ardue. Heureusement, Aspose.Words pour .NET fournit une solution robuste, permettant aux développeurs d'automatiser la création, la modification et la gestion de documents en toute simplicité. Cet article se penche sur l'une des fonctionnalités essentielles : l'insertion de règles horizontales dans les documents Word. Que vous soyez un développeur expérimenté ou que vous débutiez avec Aspose.Words, la maîtrise de cette capacité améliorera votre processus de génération de documents.

## Prérequis

Avant de vous lancer dans la mise en œuvre de règles horizontales à l’aide d’Aspose.Words pour .NET, assurez-vous de disposer des prérequis suivants :

- Visual Studio : installez Visual Studio IDE pour le développement .NET.
- Aspose.Words pour .NET : Téléchargez et installez Aspose.Words pour .NET depuis[ici](https://releases.aspose.com/words/net/).
- Connaissances de base en C# : Familiarité avec les bases du langage de programmation C#.
-  Classe DocumentBuilder : Compréhension de la`DocumentBuilder` classe dans Aspose.Words pour la manipulation de documents.

## Importer des espaces de noms

Pour commencer, importez les espaces de noms nécessaires dans votre projet C# :

```csharp
using Aspose.Words;
using System.Drawing;
```

Ces espaces de noms donnent accès aux classes Aspose.Words pour la manipulation de documents et aux classes .NET standard pour la gestion des couleurs.

Décomposons le processus d'ajout d'une règle horizontale dans un document Word à l'aide d'Aspose.Words pour .NET en étapes complètes :

## Étape 1 : Initialiser DocumentBuilder et définir le répertoire

 Tout d’abord, initialisez un`DocumentBuilder` objet et définissez le chemin du répertoire où le document sera enregistré.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## Étape 2 : Insérer une règle horizontale

 Utilisez le`InsertHorizontalRule()` méthode de la`DocumentBuilder` classe pour ajouter une règle horizontale.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## Étape 3 : Personnaliser le format de la règle horizontale

 Accéder au`HorizontalRuleFormat` propriété de la forme insérée pour personnaliser l'apparence de la règle horizontale.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- Alignement : Spécifie l'alignement de la règle horizontale (`HorizontalRuleAlignment.Center` (dans cet exemple).
- WidthPercent : définit la largeur de la règle horizontale en pourcentage de la largeur de la page (70 % dans cet exemple).
- Hauteur : Définit la hauteur de la règle horizontale en points (3 points dans cet exemple).
- Couleur : définit la couleur de la règle horizontale (`Color.Blue` (dans cet exemple).
- NoShade : spécifie si la règle horizontale doit avoir une ombre (`true` (dans cet exemple).

## Étape 4 : Enregistrer le document

 Enfin, enregistrez le document modifié à l'aide du`Save` méthode de la`Document` objet.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## Conclusion

La maîtrise de l'insertion de règles horizontales dans les documents Word à l'aide d'Aspose.Words pour .NET améliore vos capacités d'automatisation des documents. En exploitant la flexibilité et la puissance d'Aspose.Words, les développeurs peuvent rationaliser efficacement les processus de génération et de mise en forme des documents.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante permettant de travailler avec des documents Word par programmation dans des applications .NET.

### Comment puis-je télécharger Aspose.Words pour .NET ?
 Vous pouvez télécharger Aspose.Words pour .NET à partir de[ici](https://releases.aspose.com/words/net/).

### Puis-je personnaliser l'apparence des règles horizontales dans Aspose.Words ?
Oui, vous pouvez personnaliser divers aspects tels que l'alignement, la largeur, la hauteur, la couleur et l'ombrage des règles horizontales à l'aide d'Aspose.Words.

### Aspose.Words est-il adapté au traitement de documents au niveau de l’entreprise ?
Oui, Aspose.Words est largement utilisé dans les environnements d’entreprise pour ses robustes capacités de manipulation de documents.

### Où puis-je obtenir de l'aide pour Aspose.Words pour .NET ?
 Pour obtenir du soutien et de l'engagement communautaire, visitez le[Forum Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
