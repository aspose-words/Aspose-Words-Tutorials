---
category: general
date: 2026-09-11
description: Mail merge d’Aspose vous permet de charger un modèle Word et de le remplir
  avec des données, automatisant la génération de documents pour créer des lettres
  personnalisées.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: fr
lastmod: 2026-09-11
og_description: Mail merge d'Aspose vous permet de charger un modèle Word et de le
  remplir, rationalisant la génération de documents afin que vous puissiez créer rapidement
  des lettres personnalisées.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Fusion de courrier Aspose : remplissez un modèle Word en quelques minutes'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Comment effectuer une fusion de courrier Aspose pour remplir un modèle Word
url: /fr/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment effectuer une fusion de courrier Aspose pour remplir un modèle Word

Si vous avez besoin de **mail merge aspose** pour générer un lot de lettres personnalisées, ce guide vous montre exactement comment charger un modèle Word, le remplir avec des données, et automatiser la génération de documents en quelques lignes de C#. Que vous construisiez un système de mailing ou un outil de reporting, l'exemple complet ci‑dessous vous permet de créer des lettres personnalisées sans écrire de logique de fusion manuelle.

Vous apprendrez comment **charger le modèle Word**, utiliser la classe low‑code `MailMerger`, et **remplir le modèle Word** avec une source de données anonyme. À la fin du tutoriel, vous disposerez d’une application console prête à l’emploi qui produit un document Word fusionné que vous pouvez envoyer par e‑mail, imprimer ou archiver.

## Prérequis

* SDK .NET 6.0 ou version ultérieure installé  
* Une licence valide Aspose.Words for .NET (ou une clé d’évaluation gratuite)  
* Le package NuGet `Aspose.Words` (version 23.10 ou plus récente) installé dans votre projet  
* Un fichier Word (`MailMergeTemplate.docx`) contenant des espaces réservés MERGEFIELD tels que **«Name»** et **«Age»**  

Vous pouvez créer le modèle dans Microsoft Word en insérant *Insert → Quick Parts → Field → MergeField* et en nommant les champs exactement comme les noms de propriétés de votre source de données.

## Étape 1 – Préparer la source de données pour la fusion de courrier

La fusion low‑code fonctionne avec n’importe quelle collection énumérable. Dans cet exemple, nous utilisons un tableau d’objets anonymes, mais vous pourriez également passer un `DataTable`, une liste de POCO, ou des données lues depuis une base de données.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Pourquoi c’est important :**  
Le nom de chaque propriété d’objet (`Name`, `Age`) doit correspondre à un MERGEFIELD dans le modèle. La classe `MailMerger` mappe automatiquement les propriétés aux champs, éliminant ainsi le besoin d’événements `FieldMerging` manuels.

## Étape 2 – Charger le modèle Word contenant des MERGEFIELDs

Charger le modèle est simple avec la classe `Document`. Le chemin peut être absolu ou relatif au répertoire de travail de l’exécutable.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Astuce pro :**  
Si vous exécutez le code depuis Visual Studio, définissez *Copy to Output Directory* du fichier modèle sur **Copy always**. Cela garantit que le fichier est disponible lorsque le binaire compilé s’exécute.

## Étape 3 – Créer une instance de MailMerger liée au modèle

La classe `MailMerger` se trouve dans l’espace de noms `Aspose.Words.LowCode` et fournit une seule méthode `Execute` qui accepte la source de données.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Pourquoi utiliser MailMerger ?**  
`MailMerger` abstrait les appels répétitifs `MailMerge.Execute`, gérant la détection des champs, la liaison des données et le clonage du document en interne. Cela rend le code idéal pour les scénarios **automate document generation** où vous souhaitez une solution propre et low‑code.

## Étape 4 – Exécuter la fusion low‑code avec les données préparées

L’appel à `Execute` renvoie un nouveau `Document` qui contient

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Renommer les champs de fusion Word avec Aspose.Words pour Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Créer un document Word avec en‑tête et pied de page en utilisant Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Créer et styliser un document Word dans Aspose.Words pour .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}