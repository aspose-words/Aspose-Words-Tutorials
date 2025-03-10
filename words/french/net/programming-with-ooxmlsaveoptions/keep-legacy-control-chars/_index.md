---
title: Conserver les caractères de contrôle hérités
linktitle: Conserver les caractères de contrôle hérités
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment conserver les caractères de contrôle hérités dans les documents Word à l’aide d’Aspose.Words pour .NET avec ce guide étape par étape.
weight: 10
url: /fr/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Conserver les caractères de contrôle hérités

## Introduction

Avez-vous déjà été intrigué par ces caractères de contrôle étranges et invisibles dans vos documents Word ? Ils ressemblent à de minuscules gremlins cachés qui peuvent perturber la mise en forme et les fonctionnalités. Heureusement, Aspose.Words pour .NET fournit une fonctionnalité pratique pour conserver ces caractères de contrôle hérités intacts lors de l'enregistrement de documents. Dans ce didacticiel, nous allons découvrir en détail comment gérer ces caractères de contrôle à l'aide d'Aspose.Words pour .NET. Nous allons le décomposer étape par étape, en veillant à ce que vous saisissiez tous les détails en cours de route. Prêt à commencer ? Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET : téléchargez et installez depuis[ici](https://releases.aspose.com/words/net/).
2.  Une licence Aspose valide : Vous pouvez obtenir une licence temporaire[ici](https://purchase.aspose.com/temporary-license/).
3. Environnement de développement : Visual Studio ou tout autre IDE prenant en charge .NET.
4. Connaissances de base de C# : Une familiarité avec le langage de programmation C# sera utile.

## Importer des espaces de noms

Avant d'écrire votre code, vous devez importer les espaces de noms nécessaires. Ajoutez les lignes suivantes en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Configuration de votre projet

Tout d’abord, vous devez configurer votre projet dans Visual Studio (ou votre IDE préféré). 

1. Créez un nouveau projet C# : ouvrez Visual Studio et créez un nouveau projet d’application console C#.
2. Installer Aspose.Words pour .NET : utilisez le gestionnaire de packages NuGet pour installer Aspose.Words pour .NET. Cliquez avec le bouton droit sur votre projet dans l'Explorateur de solutions, sélectionnez « Gérer les packages NuGet », recherchez « Aspose.Words » et installez-le.

## Étape 2 : Chargez votre document

Ensuite, vous chargerez le document Word qui contient les caractères de contrôle hérités.

1. Spécifiez le chemin d’accès au document : définissez le chemin d’accès à votre répertoire de documents.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2.  Charger le document : Utilisez le`Document` classe pour charger votre document.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Étape 3 : Configurer les options d’enregistrement

Maintenant, configurons les options de sauvegarde pour conserver les caractères de contrôle hérités intacts.

1.  Créer des options de sauvegarde : initialiser une instance de`OoxmlSaveOptions` et définissez le`KeepLegacyControlChars`propriété à`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Étape 4 : Enregistrer le document

Enfin, enregistrez le document avec les options d’enregistrement configurées.

1.  Enregistrer le document : Utilisez le`Save` méthode de la`Document` classe pour enregistrer le document avec les options d'enregistrement spécifiées.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez vous assurer que vos caractères de contrôle hérités sont conservés lorsque vous travaillez avec des documents Word dans Aspose.Words pour .NET. Cette fonctionnalité peut s'avérer très utile, en particulier lorsque vous traitez des documents complexes dans lesquels les caractères de contrôle jouent un rôle crucial. 

## FAQ

### Que sont les caractères de contrôle hérités ?

Les caractères de contrôle hérités sont des caractères non imprimables utilisés dans les documents plus anciens pour contrôler le formatage et la mise en page.

### Puis-je supprimer ces caractères de contrôle au lieu de les conserver ?

Oui, vous pouvez utiliser Aspose.Words pour .NET pour supprimer ou remplacer ces caractères si nécessaire.

### Cette fonctionnalité est-elle disponible dans toutes les versions d'Aspose.Words pour .NET ?

Cette fonctionnalité est disponible dans les versions récentes. Assurez-vous d'utiliser la dernière version pour accéder à toutes les fonctionnalités.

### Ai-je besoin d'une licence pour utiliser Aspose.Words pour .NET ?

 Oui, vous avez besoin d'un permis valide. Vous pouvez obtenir un permis temporaire à des fins d'évaluation[ici](https://purchase.aspose.com/temporary-license/).

### Où puis-je trouver plus de documentation sur Aspose.Words pour .NET ?

 Vous trouverez une documentation détaillée[ici](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
