---
title: Obtenir des types de révision de mots
linktitle: Obtenir des types de révision de mots
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment obtenir les types de révision des mots dans un document Word à l'aide d'Aspose.Words pour .NET. Ce guide étape par étape vous aide à gérer efficacement les révisions de documents.
weight: 10
url: /fr/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obtenir des types de révision de mots

## Introduction

Vous êtes-vous déjà retrouvé plongé dans une mer de révisions de documents, vous demandant qui a déplacé quoi et quand ? Vous n'êtes pas seul. La gestion des révisions de documents peut être une tâche fastidieuse, en particulier lorsqu'il s'agit de documents volumineux. Mais ne vous inquiétez pas ! Avec Aspose.Words pour .NET, vous pouvez facilement identifier et gérer ces révisions. Dans ce guide, nous vous expliquerons étape par étape comment obtenir les types de révision des mots dans un document Word à l'aide d'Aspose.Words pour .NET. Alors, attachez vos ceintures et plongeons-nous dans le vif du sujet !

## Prérequis

Avant de nous salir les mains avec du code, vous aurez besoin de quelques éléments :

1.  Bibliothèque Aspose.Words pour .NET : si vous ne l'avez pas déjà fait, téléchargez-la à partir de[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE compatible .NET.
3. Connaissances de base de C# : La compréhension du langage de programmation C# sera bénéfique.
4.  Un document Word avec des révisions : assurez-vous d'avoir un`.docx`fichier avec des modifications suivies pour tester le code.

## Importer des espaces de noms

Pour commencer, vous devrez importer les espaces de noms nécessaires dans votre projet C#. Cela vous permettra d'accéder aux fonctionnalités fournies par Aspose.Words pour .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Décomposons l’exemple en plusieurs étapes pour une meilleure compréhension et mise en œuvre.

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez définir le chemin d'accès à votre répertoire de documents. C'est là que se trouvera votre document Word avec les révisions.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre dossier de documents.

## Étape 2 : Chargez votre document Word

Ensuite, vous devez charger le document Word dans votre projet. Ce document doit contenir les révisions que vous souhaitez analyser.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 Assurez-vous que le fichier`Revisions.docx` existe dans le répertoire spécifié.

## Étape 3 : Accéder à la collection de paragraphes

Maintenant que votre document est chargé, vous devez accéder aux paragraphes de la première section du corps du document. Cela vous aidera à parcourir chaque paragraphe pour vérifier les révisions.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Étape 4 : Parcourez les paragraphes et vérifiez les révisions

C'est ici que la magie opère. Vous parcourrez chaque paragraphe et vérifierez s'il a été déplacé (supprimé ou inséré).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 Cette boucle parcourt chaque paragraphe et utilise le`IsMoveFromRevision` et`IsMoveToRevision` propriétés permettant de déterminer si le paragraphe a été déplacé (supprimé) ou déplacé (inséré).

## Conclusion

Et voilà ! Avec seulement quelques lignes de code, vous pouvez facilement identifier les types de révisions dans votre document Word à l'aide d'Aspose.Words pour .NET. Cette puissante bibliothèque simplifie la gestion des révisions de documents, vous permettant ainsi de vous concentrer sur des tâches plus importantes. 

## FAQ

### Puis-je utiliser Aspose.Words pour .NET pour suivre les modifications apportées par des utilisateurs spécifiques ?

Oui, Aspose.Words pour .NET fournit des fonctionnalités permettant d’accéder aux détails de révision, y compris l’auteur des modifications.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?

 Absolument ! Vous pouvez obtenir un essai gratuit[ici](https://releases.aspose.com/).

### Comment puis-je appliquer une licence temporaire pour Aspose.Words pour .NET ?

 Vous pouvez demander et appliquer une licence temporaire auprès de[ici](https://purchase.aspose.com/temporary-license/).

### Où puis-je trouver une documentation plus détaillée sur Aspose.Words pour .NET ?

 Une documentation détaillée est disponible sur le[Site Web d'Aspose](https://reference.aspose.com/words/net/).

### Puis-je utiliser Aspose.Words pour .NET dans un projet non commercial ?

Oui, Aspose.Words pour .NET peut être utilisé dans des projets commerciaux et non commerciaux, mais assurez-vous de vérifier les conditions de licence.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
