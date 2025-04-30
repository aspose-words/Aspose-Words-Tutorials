---
"description": "Découvrez comment ajouter un filigrane textuel avec des options spécifiques à vos documents Word grâce à Aspose.Words pour .NET. Personnalisez facilement la police, la taille, la couleur et la mise en page."
"linktitle": "Ajouter un filigrane de texte avec des options spécifiques"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Ajouter un filigrane de texte avec des options spécifiques"
"url": "/fr/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un filigrane de texte avec des options spécifiques

## Introduction

Les filigranes peuvent apporter une touche élégante et fonctionnelle à vos documents Word, permettant de les marquer comme confidentiels ou d'y apporter une touche personnelle. Dans ce tutoriel, nous allons découvrir comment ajouter un filigrane textuel à un document Word avec Aspose.Words pour .NET. Nous détaillerons les options spécifiques que vous pouvez configurer, telles que la famille de polices, la taille, la couleur et la mise en page. À la fin, vous pourrez personnaliser le filigrane de votre document selon vos besoins. Alors, à vos éditeurs de code !

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants en place :

1. Bibliothèque Aspose.Words pour .NET : vous devez installer la bibliothèque Aspose.Words. Si ce n'est pas déjà fait, vous pouvez la télécharger depuis le [Lien de téléchargement d'Aspose.Words](https://releases.aspose.com/words/net/).
2. Compréhension de base de C# : Ce tutoriel utilisera C# comme langage de programmation. Une compréhension fondamentale de la syntaxe C# sera utile.
3. Environnement de développement .NET : assurez-vous de disposer d’un environnement de développement configuré (comme Visual Studio) dans lequel vous pouvez créer et exécuter vos applications .NET.

## Importer des espaces de noms

Pour utiliser Aspose.Words, vous devez inclure les espaces de noms nécessaires dans votre projet. Voici ce que vous devez importer :

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Étape 1 : Configurez votre document

Tout d'abord, vous devez charger le document que vous souhaitez utiliser. Pour ce tutoriel, nous utiliserons un exemple de document nommé `Document.docx`Assurez-vous que ce document existe dans votre répertoire spécifié.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Dans cette étape, vous définissez le répertoire où se trouve votre document et le chargez dans une instance du `Document` classe.

## Étape 2 : Configurer les options de filigrane

Configurez ensuite les options de votre filigrane textuel. Vous pouvez personnaliser divers aspects, tels que la police, la taille, la couleur et la mise en page. Configurons ces options.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Voici ce que fait chaque option :
- `FontFamily`: Spécifie la police du texte du filigrane.
- `FontSize`Définit la taille du texte du filigrane.
- `Color`: Définit la couleur du texte du filigrane.
- `Layout`: Détermine l'orientation du filigrane (horizontal ou diagonal).
- `IsSemitrasparent`: Définit si le filigrane est semi-transparent.

## Étape 3 : ajouter le texte du filigrane

Appliquez maintenant le filigrane à votre document en utilisant les options précédemment configurées. À cette étape, vous définirez le texte du filigrane sur « Test » et appliquerez les options définies.

```csharp
doc.Watermark.SetText("Test", options);
```

Cette ligne de code ajoute le filigrane avec le texte « Test » au document, en appliquant les options spécifiées.

## Étape 4 : Enregistrer le document

Enfin, enregistrez le document avec le nouveau filigrane appliqué. Vous pouvez l'enregistrer sous un nouveau nom pour éviter d'écraser le document d'origine.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Cet extrait de code enregistre le document modifié dans le même répertoire avec un nouveau nom de fichier.

## Conclusion

Ajouter un filigrane textuel à vos documents Word avec Aspose.Words pour .NET est un processus simple à réaliser en plusieurs étapes faciles à gérer. En suivant ce tutoriel, vous avez appris à configurer différentes options de filigrane, notamment la police, la taille, la couleur, la mise en page et la transparence. Grâce à ces compétences, vous pouvez désormais personnaliser vos documents pour mieux répondre à vos besoins ou y inclure des informations essentielles comme la confidentialité ou l'image de marque.

Si vous avez des questions ou avez besoin d'aide supplémentaire, n'hésitez pas à consulter le [Documentation Aspose.Words](https://reference.aspose.com/words/net/) ou visitez le [Forum d'assistance Aspose](https://forum.aspose.com/c/words/8) pour plus d'aide.

## FAQ

### Puis-je utiliser différentes polices pour le filigrane ?

Oui, vous pouvez choisir n'importe quelle police installée sur votre système en spécifiant le `FontFamily` propriété dans le `TextWatermarkOptions`.

### Comment changer la couleur du filigrane ?

Vous pouvez modifier la couleur du filigrane en définissant le `Color` propriété dans le `TextWatermarkOptions` à n'importe quel `System.Drawing.Color` valeur.

### Est-il possible d'ajouter plusieurs filigranes à un document ?

Aspose.Words permet d'ajouter un filigrane à la fois. Pour en ajouter plusieurs, vous devez les créer et les appliquer séquentiellement.

### Puis-je ajuster la position du filigrane ?

Le `WatermarkLayout` La propriété détermine l'orientation, mais les ajustements de positionnement précis ne sont pas pris en charge directement. Vous devrez peut-être utiliser d'autres techniques pour un positionnement précis.

### Que faire si j’ai besoin d’un filigrane semi-transparent ?

Réglez le `IsSemitrasparent` propriété à `true` pour rendre votre filigrane semi-transparent.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}