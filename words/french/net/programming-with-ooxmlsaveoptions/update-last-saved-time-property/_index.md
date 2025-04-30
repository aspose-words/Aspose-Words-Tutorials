---
"description": "Découvrez comment mettre à jour la propriété « Dernier enregistrement » dans vos documents Word avec Aspose.Words pour .NET. Suivez notre guide détaillé, étape par étape."
"linktitle": "Mettre à jour la propriété de l'heure de la dernière sauvegarde"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Mettre à jour la propriété de l'heure de la dernière sauvegarde"
"url": "/fr/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mettre à jour la propriété de l'heure de la dernière sauvegarde

## Introduction

Vous êtes-vous déjà demandé comment suivre la propriété « Dernière heure enregistrée » dans vos documents Word par programmation ? Si vous gérez plusieurs documents et devez gérer leurs métadonnées, mettre à jour cette propriété peut s'avérer très pratique. Aujourd'hui, je vais vous expliquer ce processus avec Aspose.Words pour .NET. Alors, attachez vos ceintures et c'est parti !

## Prérequis

Avant de passer au guide étape par étape, vous aurez besoin de quelques éléments :

1. Aspose.Words pour .NET : Assurez-vous d'avoir installé Aspose.Words pour .NET. Si ce n'est pas le cas, vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un environnement de développement comme Visual Studio.
3. Connaissances de base de C# : comprendre les bases de la programmation C# sera utile.

## Importer des espaces de noms

Pour commencer, assurez-vous d'importer les espaces de noms nécessaires dans votre projet. Cela vous permettra d'accéder aux classes et méthodes nécessaires à la manipulation des documents Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Décomposons maintenant le processus en étapes simples. Chaque étape vous guidera dans la mise à jour de la propriété « Dernière heure enregistrée » dans votre document Word.

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez spécifier le chemin d'accès à votre répertoire de documents. C'est là que votre document existant est stocké et que le document mis à jour sera enregistré.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Remplacer `"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre répertoire.

## Étape 2 : Chargez votre document Word

Ensuite, chargez le document Word à mettre à jour. Pour ce faire, créez une instance de `Document` classe et en passant le chemin de votre document.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Assurez-vous que le document nommé `Document.docx` est présent dans le répertoire spécifié.

## Étape 3 : Configurer les options d’enregistrement

Maintenant, créez une instance du `OoxmlSaveOptions` Classe. Cette classe vous permet de spécifier les options d'enregistrement de votre document au format Office Open XML (OOXML). Vous y définirez les `UpdateLastSavedTimeProperty` à `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Cela indique à Aspose.Words de mettre à jour la propriété de dernière heure enregistrée du document.

## Étape 4 : Enregistrer le document mis à jour

Enfin, enregistrez le document en utilisant le `Save` méthode de la `Document` classe, en passant le chemin où vous souhaitez enregistrer le document mis à jour et les options d'enregistrement.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Cela enregistrera le document avec la propriété de dernière heure d'enregistrement mise à jour.

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement mettre à jour la propriété « Dernier enregistrement » de vos documents Word avec Aspose.Words pour .NET. Ceci est particulièrement utile pour conserver des métadonnées précises dans vos documents, ce qui peut être crucial pour les systèmes de gestion de documents et diverses autres applications.

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante pour créer, éditer et convertir des documents Word dans des applications .NET.

### Pourquoi devrais-je mettre à jour la propriété de la dernière heure enregistrée ?
La mise à jour de la propriété de dernière heure enregistrée permet de conserver des métadonnées précises, ce qui est essentiel pour le suivi et la gestion des documents.

### Puis-je mettre à jour d’autres propriétés à l’aide d’Aspose.Words pour .NET ?
Oui, Aspose.Words pour .NET vous permet de mettre à jour diverses propriétés de document, telles que le titre, l'auteur et le sujet.

### Aspose.Words pour .NET est-il gratuit ?
Aspose.Words pour .NET est disponible en essai gratuit, mais une licence est requise pour bénéficier de toutes les fonctionnalités. Vous pouvez obtenir une licence. [ici](https://purchase.aspose.com/buy).

### Où puis-je trouver plus de tutoriels sur Aspose.Words pour .NET ?
Vous pouvez trouver plus de tutoriels et de documentation [ici](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}