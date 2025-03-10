---
title: Réduire la taille du PDF en mettant à l'échelle les polices WMF en fonction de la taille du métafichier
linktitle: Réduire la taille du PDF en mettant à l'échelle les polices WMF en fonction de la taille du métafichier
second_title: API de traitement de documents Aspose.Words
description: Guide étape par étape pour réduire la taille du PDF en mettant à l'échelle les polices WMF à la taille du métafichier lors de la conversion au format PDF avec Aspose.Words pour .NET.
weight: 10
url: /fr/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Réduire la taille du PDF en mettant à l'échelle les polices WMF en fonction de la taille du métafichier

## Introduction

Lorsque vous travaillez avec des fichiers PDF, en particulier ceux générés à partir de documents Word contenant des graphiques WMF (Windows Metafile), la gestion de la taille peut devenir un aspect crucial de la gestion des documents. Une façon de contrôler la taille du PDF consiste à ajuster la façon dont les polices WMF sont rendues dans le document. Dans ce didacticiel, nous verrons comment réduire la taille du PDF en mettant à l'échelle les polices WMF à la taille du métafichier à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de passer aux étapes suivantes, assurez-vous de disposer des éléments suivants :

1. Aspose.Words pour .NET : assurez-vous que la bibliothèque Aspose.Words est installée. Sinon, vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : ce didacticiel suppose que vous disposez d’un environnement de développement .NET configuré (comme Visual Studio) dans lequel vous pouvez écrire et exécuter du code C#.
3. Compréhension de base de la programmation .NET : une connaissance des concepts de base de la programmation .NET et de la syntaxe C# sera utile.
4. Document Word avec graphiques WMF : vous aurez besoin d'un document Word contenant des graphiques WMF. Vous pouvez utiliser votre propre document ou en créer un pour le tester.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Cela vous donnera accès aux classes et méthodes requises pour travailler avec Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Charger le document Word

 Pour commencer, chargez le document Word contenant les graphiques WMF. Cela se fait à l'aide de l'`Document` classe de Aspose.Words.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Charger le document
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Ici,`dataDir` est un espace réservé pour le chemin du répertoire de votre document. Nous créons une instance de`Document` classe en passant le chemin vers le fichier Word. Cela charge le document en mémoire, prêt pour un traitement ultérieur.

## Étape 2 : Configurer les options de rendu du métafichier

 Ensuite, vous devez configurer les options de rendu du métafichier. Plus précisément, définissez les`ScaleWmfFontsToMetafileSize`propriété à`false`. Cela contrôle si les polices WMF sont mises à l'échelle pour correspondre à la taille du métafichier.

```csharp
// Créer une nouvelle instance de MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 Le`MetafileRenderingOptions` La classe fournit des options sur la manière dont les métafichiers (comme WMF) sont rendus. En définissant`ScaleWmfFontsToMetafileSize` à`false`, vous demandez à Aspose.Words de ne pas mettre à l'échelle les polices en fonction de la taille du métafichier, ce qui peut aider à réduire la taille globale du PDF.

## Étape 3 : définir les options d’enregistrement du PDF

Configurez maintenant les options d'enregistrement PDF pour utiliser les options de rendu des métafichiers que vous venez de définir. Cela indique à Aspose.Words comment gérer les métafichiers lors de l'enregistrement du document au format PDF.

```csharp
// Créer une nouvelle instance de PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 Le`PdfSaveOptions` La classe vous permet de spécifier différents paramètres pour enregistrer le document au format PDF. En attribuant la classe précédemment configurée`MetafileRenderingOptions` au`MetafileRenderingOptions` propriété de`PdfSaveOptions`, vous vous assurez que le document est enregistré selon les paramètres de rendu de métafichier souhaités.

## Étape 4 : Enregistrer le document au format PDF

Enfin, enregistrez le document Word au format PDF à l'aide des options d'enregistrement configurées. Cela appliquera tous les paramètres, y compris les options de rendu du métafichier, au PDF de sortie.


```csharp
// Enregistrer le document au format PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 Dans cette étape, le`Save` méthode de la`Document` La classe est utilisée pour exporter le document vers un fichier PDF. Le chemin où le PDF sera enregistré est spécifié, ainsi que le`PdfSaveOptions` qui incluent les paramètres de rendu du métafichier.

## Conclusion

En mettant à l'échelle les polices WMF à la taille du métafichier, vous pouvez réduire considérablement la taille de vos fichiers PDF générés à partir de documents Word. Cette technique permet d'optimiser le stockage et la distribution des documents sans compromettre la qualité du contenu visuel. En suivant les étapes décrites ci-dessus, vous garantissez que vos fichiers PDF sont plus faciles à gérer et plus efficaces en termes de taille.

## FAQ

### Qu'est-ce que WMF et pourquoi est-il important pour la taille du PDF ?

WMF (Windows Metafile) est un format graphique utilisé dans Microsoft Windows. Il peut contenir des données vectorielles et bitmap. Étant donné que les données vectorielles peuvent être mises à l'échelle et manipulées, il est important de les gérer correctement pour éviter les fichiers PDF inutilement volumineux.

### Comment la mise à l'échelle des polices WMF à la taille du métafichier affecte-t-elle le PDF ?

La mise à l'échelle des polices WMF à la taille du métafichier peut aider à réduire la taille globale du PDF en évitant le rendu des polices haute résolution qui pourrait augmenter la taille du fichier.

### Puis-je utiliser d’autres formats de métafichier avec Aspose.Words ?

Oui, Aspose.Words prend en charge divers formats de métafichiers, notamment EMF (Enhanced Metafile) en plus de WMF.

### Cette technique est-elle applicable à tous les types de documents Word ?

Oui, cette technique peut être appliquée à n’importe quel document Word contenant des graphiques WMF, aidant à optimiser la taille du PDF généré.

### Où puis-je trouver plus d'informations sur Aspose.Words ?

 Vous pouvez en savoir plus sur Aspose.Words dans le[Documentation Aspose.Words](https://reference.aspose.com/words/net/) Pour les téléchargements, les essais et l'assistance, visitez le[Page de téléchargement d'Aspose.Words](https://releases.aspose.com/words/net/), [Acheter Aspose.Words](https://purchase.aspose.com/buy), [Essai gratuit](https://releases.aspose.com/), [Licence temporaire](https://purchase.aspose.com/temporary-license/) , et[Soutien](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
