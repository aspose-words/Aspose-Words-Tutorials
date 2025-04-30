---
"description": "Guide étape par étape pour réduire la taille du PDF avec l'échelle des polices WMF à la taille du métafichier lors de la conversion au format PDF avec Aspose.Words pour .NET."
"linktitle": "Réduire la taille du PDF en adaptant les polices WMF à la taille du métafichier"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Réduire la taille du PDF en adaptant les polices WMF à la taille du métafichier"
"url": "/fr/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Réduire la taille du PDF en adaptant les polices WMF à la taille du métafichier

## Introduction

Lors de l'utilisation de fichiers PDF, notamment ceux générés à partir de documents Word contenant des graphiques WMF (Windows Metafile), la gestion de la taille peut devenir un aspect crucial. Une façon de contrôler la taille d'un PDF consiste à ajuster le rendu des polices WMF. Dans ce tutoriel, nous verrons comment réduire la taille d'un PDF en adaptant les polices WMF à la taille du métafichier à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de passer aux étapes suivantes, assurez-vous d'avoir les éléments suivants :

1. Aspose.Words pour .NET : Assurez-vous d'avoir installé la bibliothèque Aspose.Words. Sinon, vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : ce didacticiel suppose que vous disposez d’un environnement de développement .NET configuré (comme Visual Studio) dans lequel vous pouvez écrire et exécuter du code C#.
3. Compréhension de base de la programmation .NET : une connaissance des concepts de base de la programmation .NET et de la syntaxe C# sera utile.
4. Document Word avec graphiques WMF : Vous aurez besoin d'un document Word contenant des graphiques WMF. Vous pouvez utiliser votre propre document ou en créer un pour le tester.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Cela vous donnera accès aux classes et méthodes nécessaires à l'utilisation d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Charger le document Word

Pour commencer, chargez le document Word contenant les images WMF. Pour ce faire, utilisez le `Document` classe d'Aspose.Words.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Charger le document
Document doc = new Document(dataDir + "WMF with text.docx");
```

Ici, `dataDir` est un espace réservé pour le chemin d'accès à votre répertoire de documents. Nous créons une instance de `Document` en transmettant le chemin d'accès au fichier Word. Le document est alors chargé en mémoire, prêt pour un traitement ultérieur.

## Étape 2 : Configurer les options de rendu du métafichier

Ensuite, vous devez configurer les options de rendu du métafichier. Plus précisément, définissez `ScaleWmfFontsToMetafileSize` propriété à `false`. Cela contrôle si les polices WMF sont mises à l'échelle pour correspondre à la taille du métafichier.

```csharp
// Créer une nouvelle instance de MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

Le `MetafileRenderingOptions` La classe fournit des options pour le rendu des métafichiers (comme WMF). En définissant `ScaleWmfFontsToMetafileSize` à `false`, vous demandez à Aspose.Words de ne pas mettre à l'échelle les polices en fonction de la taille du métafichier, ce qui peut aider à réduire la taille globale du PDF.

## Étape 3 : définir les options d’enregistrement du PDF

Configurez maintenant les options d'enregistrement PDF pour utiliser les options de rendu des métafichiers que vous venez de définir. Cela indique à Aspose.Words comment gérer les métafichiers lors de l'enregistrement du document au format PDF.

```csharp
// Créer une nouvelle instance de PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

Le `PdfSaveOptions` Cette classe vous permet de spécifier différents paramètres pour l'enregistrement du document au format PDF. En attribuant la classe précédemment configurée, `MetafileRenderingOptions` au `MetafileRenderingOptions` propriété de `PdfSaveOptions`, vous vous assurez que le document est enregistré selon les paramètres de rendu de métafichier souhaités.

## Étape 4 : Enregistrer le document au format PDF

Enfin, enregistrez le document Word au format PDF en utilisant les options d'enregistrement configurées. Tous les paramètres, y compris les options de rendu des métafichiers, seront alors appliqués au PDF de sortie.


```csharp
// Enregistrer le document au format PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

Dans cette étape, le `Save` méthode de la `Document` La classe permet d'exporter le document au format PDF. Le chemin d'accès au fichier PDF est spécifié, ainsi que le `PdfSaveOptions` qui incluent les paramètres de rendu du métafichier.

## Conclusion

En adaptant les polices WMF à la taille du métafichier, vous pouvez réduire considérablement la taille de vos fichiers PDF générés à partir de documents Word. Cette technique permet d'optimiser le stockage et la distribution des documents sans compromettre la qualité du contenu visuel. En suivant les étapes décrites ci-dessus, vous garantissez une gestion et une gestion optimales de vos fichiers PDF.

## FAQ

### Qu'est-ce que WMF et pourquoi est-il important pour la taille du PDF ?

WMF (Windows Metafile) est un format graphique utilisé par Microsoft Windows. Il peut contenir des données vectorielles et bitmap. Les données vectorielles étant redimensionnables et manipulables, il est important de les gérer correctement afin d'éviter des fichiers PDF inutilement volumineux.

### Comment la mise à l'échelle des polices WMF à la taille du métafichier affecte-t-elle le PDF ?

La mise à l'échelle des polices WMF à la taille du métafichier peut aider à réduire la taille globale du PDF en évitant le rendu des polices haute résolution qui pourrait augmenter la taille du fichier.

### Puis-je utiliser d'autres formats de métafichier avec Aspose.Words ?

Oui, Aspose.Words prend en charge divers formats de métafichiers, notamment EMF (Enhanced Metafile) en plus de WMF.

### Cette technique est-elle applicable à tous les types de documents Word ?

Oui, cette technique peut être appliquée à n’importe quel document Word contenant des graphiques WMF, aidant à optimiser la taille du PDF généré.

### Où puis-je trouver plus d'informations sur Aspose.Words ?

Vous pouvez en savoir plus sur Aspose.Words dans le [Documentation Aspose.Words](https://reference.aspose.com/words/net/)Pour les téléchargements, les essais et l'assistance, visitez le [Page de téléchargement d'Aspose.Words](https://releases.aspose.com/words/net/), [Acheter Aspose.Words](https://purchase.aspose.com/buy), [Essai gratuit](https://releases.aspose.com/), [Licence temporaire](https://purchase.aspose.com/temporary-license/), et [Soutien](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}