---
title: Insérer un champ TOA sans générateur de documents
linktitle: Insérer un champ TOA sans générateur de documents
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer un champ TOA sans utiliser de générateur de documents dans Aspose.Words pour .NET. Suivez notre guide étape par étape pour gérer efficacement les citations juridiques.
weight: 10
url: /fr/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un champ TOA sans générateur de documents

## Introduction

Créer un champ Table des références (TOA) dans un document Word peut ressembler à un puzzle complexe. Cependant, avec l'aide d'Aspose.Words pour .NET, le processus devient simple et fluide. Dans cet article, nous vous guiderons à travers les étapes à suivre pour insérer un champ TOA sans utiliser de générateur de documents, ce qui vous permettra de gérer facilement vos citations et références juridiques dans vos documents Word.

## Prérequis

Avant de plonger dans le didacticiel, couvrons les éléments essentiels dont vous aurez besoin :

-  Aspose.Words pour .NET : assurez-vous que la dernière version est installée. Vous pouvez la télécharger à partir du[Site Web d'Aspose](https://releases.aspose.com/words/net/).
- Environnement de développement : un IDE compatible .NET comme Visual Studio.
- Connaissances de base de C# : la compréhension de la syntaxe et des concepts de base de C# sera utile.
- Exemple de document Word : créez ou préparez un exemple de document dans lequel vous souhaitez insérer le champ TOA.

## Importer des espaces de noms

Pour commencer, vous devez importer les espaces de noms nécessaires à partir de la bibliothèque Aspose.Words. Cette configuration garantit que vous avez accès à toutes les classes et méthodes requises pour la manipulation des documents.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Décomposons le processus en étapes simples et faciles à suivre. Nous vous guiderons à travers chaque étape, en expliquant ce que fait chaque élément de code et comment il contribue à la création du champ TOA.

## Étape 1 : Initialiser le document

 Tout d’abord, vous devez créer une instance de`Document` classe. Cet objet représente le document Word sur lequel vous travaillez.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Ce code initialise un nouveau document Word. Vous pouvez le considérer comme la création d'une toile vierge sur laquelle vous ajouterez votre contenu.

## Étape 2 : Créer et configurer le champ TA

Ensuite, nous allons ajouter un champ TA (Table des autorités). Ce champ indique les entrées qui apparaîtront dans le TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Nous voulons insérer les champs TA et TOA comme ceci :
// { TA \c 1 \l "Valeur 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Voici un aperçu :
- Paragraphe para = nouveau Paragraphe(doc);: Crée un nouveau paragraphe dans le document.
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false); : ajoute un champ TA au paragraphe. Le`FieldType.FieldTOAEntry` spécifie qu'il s'agit d'un champ de saisie TOA.
- fieldTA.EntryCategory = "1";: Définit la catégorie d'entrée. Ceci est utile pour classer différents types d'entrées.
- fieldTA.LongCitation = "Value 0";: Spécifie le texte de citation long. Il s'agit du texte qui apparaîtra dans le TOA.
- doc.FirstSection.Body.AppendChild(para);: Ajoute le paragraphe avec le champ TA au corps du document.

## Étape 3 : ajouter le champ TOA

Maintenant, nous allons insérer le champ TOA réel qui compile toutes les entrées TA dans une table.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Dans cette étape :
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false); : ajoute un champ TOA au paragraphe.
- fieldToa.EntryCategory = "1";: Filtre les entrées pour inclure uniquement celles marquées avec la catégorie « 1 ».

## Étape 4 : mettre à jour le champ TOA

Après avoir inséré le champ TOA, vous devez le mettre à jour pour vous assurer qu'il reflète les dernières entrées.

```csharp
fieldToa.Update();
```

Cette commande actualise le champ TOA, garantissant que toutes les entrées marquées sont correctement affichées dans la table.

## Étape 5 : Enregistrer le document

Enfin, enregistrez votre document avec le champ TOA nouvellement ajouté.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 Cette ligne de code enregistre le document dans le répertoire spécifié. Assurez-vous de remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel où vous souhaitez enregistrer votre fichier.

## Conclusion

Et voilà ! Vous avez ajouté avec succès un champ TOA à un document Word sans utiliser de générateur de documents. En suivant ces étapes, vous pouvez gérer efficacement les citations et créer des tables de référence complètes dans vos documents juridiques. Aspose.Words pour .NET rend ce processus fluide et efficace, en vous offrant les outils nécessaires pour gérer facilement des tâches documentaires complexes.

## FAQ

### Puis-je ajouter plusieurs champs TA avec différentes catégories ?
 Oui, vous pouvez ajouter plusieurs champs TA avec différentes catégories en définissant le`EntryCategory`propriété en conséquence.

### Comment puis-je personnaliser l'apparence du TOA ?
Vous pouvez personnaliser l'apparence du TOA en modifiant les propriétés du champ TOA, telles que la mise en forme des entrées et les étiquettes de catégorie.

### Est-il possible de mettre à jour le champ TOA automatiquement ?
 Bien que vous puissiez mettre à jour manuellement le champ TOA à l'aide de l'`Update` méthode, Aspose.Words ne prend actuellement pas en charge les mises à jour automatiques lors des modifications du document.

### Puis-je ajouter des champs TA par programmation dans des parties spécifiques du document ?
Oui, vous pouvez ajouter des champs TA à des emplacements spécifiques en les insérant dans les paragraphes ou sections souhaités.

### Comment gérer plusieurs champs TOA dans un seul document ?
 Vous pouvez gérer plusieurs champs TOA en attribuant différents`EntryCategory` valeurs et en veillant à ce que chaque champ TOA filtre les entrées en fonction de sa catégorie.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
