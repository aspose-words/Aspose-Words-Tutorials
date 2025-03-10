---
title: Ajouter un préfixe de nom de classe CSS
linktitle: Ajouter un préfixe de nom de classe CSS
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment ajouter un préfixe de nom de classe CSS lors de l'enregistrement de documents Word au format HTML à l'aide d'Aspose.Words pour .NET. Guide étape par étape, extraits de code et FAQ inclus.
weight: 10
url: /fr/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un préfixe de nom de classe CSS

## Introduction

Bienvenue ! Si vous plongez dans le monde d'Aspose.Words pour .NET, vous allez vous régaler. Aujourd'hui, nous allons découvrir comment ajouter un préfixe de nom de classe CSS lors de l'enregistrement d'un document Word au format HTML à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité est très pratique lorsque vous souhaitez éviter les conflits de noms de classe dans vos fichiers HTML.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Aspose.Words pour .NET : si vous ne l'avez pas encore installé,[téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre IDE C#.
-  Un document Word : nous utiliserons un document nommé`Rendering.docx`Placez-le dans le répertoire de votre projet.

## Importer des espaces de noms

Tout d'abord, assurez-vous que les espaces de noms nécessaires sont importés dans votre projet C#. Ajoutez-les en haut de votre fichier de code :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Maintenant, plongeons dans le guide étape par étape !

## Étape 1 : Configurez votre projet

Avant de pouvoir commencer à ajouter un préfixe de nom de classe CSS, configurons notre projet.

### Étape 1.1 : Créer un nouveau projet

 Lancez votre Visual Studio et créez un nouveau projet d'application console. Nommez-le de manière accrocheuse, comme`AsposeCssPrefixExample`.

### Étape 1.2 : ajouter Aspose.Words pour .NET

Si vous ne l'avez pas déjà fait, ajoutez Aspose.Words for .NET à votre projet via NuGet. Ouvrez simplement la console du gestionnaire de packages NuGet et exécutez :

```bash
Install-Package Aspose.Words
```

Super ! Nous sommes maintenant prêts à commencer à coder.

## Étape 2 : Chargez votre document

La première chose que nous devons faire est de charger le document Word que nous voulons convertir en HTML.

### Étape 2.1 : Définir le chemin du document

 Définissez le chemin d'accès à votre répertoire de documents. Pour les besoins de ce tutoriel, supposons que votre document se trouve dans un dossier nommé`Documents` dans votre répertoire de projet.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Étape 2.2 : Charger le document

Maintenant, chargeons le document en utilisant Aspose.Words :

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 3 : Configurer les options d’enregistrement HTML

Ensuite, nous devons configurer les options d’enregistrement HTML pour inclure un préfixe de nom de classe CSS.

### Étape 3.1 : Créer des options d'enregistrement HTML

 Instancier le`HtmlSaveOptions` objet et définir le type de feuille de style CSS sur`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Étape 3.2 : définir le préfixe du nom de la classe CSS

 Maintenant, définissons le`CssClassNamePrefix` propriété au préfixe souhaité. Pour cet exemple, nous utiliserons`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Étape 4 : Enregistrer le document au format HTML

Enfin, enregistrons le document sous forme de fichier HTML avec nos options configurées.


Spécifiez le chemin du fichier HTML de sortie et enregistrez le document.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Étape 5 : Vérifier la sortie

 Après avoir exécuté votre projet, accédez à votre`Documents` dossier. Vous devriez trouver un fichier HTML nommé`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` . Ouvrez ce fichier dans un éditeur de texte ou un navigateur pour vérifier que les classes CSS ont le préfixe`pfx_`.

## Conclusion

Et voilà ! En suivant ces étapes, vous avez ajouté avec succès un préfixe de nom de classe CSS à votre sortie HTML à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité simple mais puissante peut vous aider à conserver des styles propres et sans conflit dans vos documents HTML.

## FAQ

### Puis-je utiliser un préfixe différent pour chaque opération de sauvegarde ?
 Oui, vous pouvez personnaliser le préfixe à chaque fois que vous enregistrez un document en modifiant le`CssClassNamePrefix` propriété.

### Cette méthode prend-elle en charge le CSS en ligne ?
 Le`CssClassNamePrefix`La propriété fonctionne avec le CSS externe. Pour le CSS en ligne, vous aurez besoin d'une approche différente.

### Comment puis-je inclure d’autres options de sauvegarde HTML ?
 Vous pouvez configurer diverses propriétés de`HtmlSaveOptions` pour personnaliser votre sortie HTML. Vérifiez le[documentation](https://reference.aspose.com/words/net/) pour plus de détails.

### Est-il possible d'enregistrer le HTML dans un flux ?
 Absolument ! Vous pouvez enregistrer le document dans un flux en transmettant l'objet de flux à l'`Save` méthode.

### Comment puis-je obtenir de l’aide si je rencontre des problèmes ?
 Vous pouvez obtenir de l'aide auprès de[Forum Aspose](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
