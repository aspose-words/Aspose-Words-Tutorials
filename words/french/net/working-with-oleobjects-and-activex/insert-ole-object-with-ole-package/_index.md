---
title: Insérer un objet Ole dans Word avec le package Ole
linktitle: Insérer un objet Ole dans Word avec le package Ole
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer des objets OLE dans des documents Word à l'aide d'Aspose.Words pour .NET. Suivez notre guide détaillé étape par étape pour intégrer des fichiers de manière transparente.
weight: 10
url: /fr/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un objet Ole dans Word avec le package Ole

## Introduction

Si vous avez toujours voulu intégrer un fichier dans un document Word, vous êtes au bon endroit. Qu'il s'agisse d'un fichier ZIP, d'une feuille Excel ou de tout autre type de fichier, l'intégrer directement dans votre document Word peut s'avérer extrêmement utile. Considérez cela comme un compartiment secret dans votre document où vous pouvez cacher toutes sortes de trésors. Et aujourd'hui, nous allons vous expliquer comment procéder à l'aide d'Aspose.Words pour .NET. Prêt à devenir un expert de Word ? Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1. Aspose.Words pour .NET : Si vous ne l'avez pas déjà fait, téléchargez-le à partir de[ici](https://releases.aspose.com/words/net/).
2. Un environnement de développement : Visual Studio ou tout autre environnement de développement .NET.
3. Compréhension de base de C# : vous n’avez pas besoin d’être un expert, mais connaître C# vous aidera.
4. Un répertoire de documents : un dossier dans lequel vous pouvez stocker et récupérer des documents.

## Importer des espaces de noms

Tout d'abord, mettons en ordre nos espaces de noms. Vous devez inclure les espaces de noms suivants dans votre projet :

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Décomposons cela en étapes de la taille d'une bouchée, afin qu'il soit facile de suivre.

## Étape 1 : Configurez votre document

Imaginez que vous êtes un artiste avec une toile vierge. Tout d'abord, nous avons besoin de notre toile vierge, qui est notre document Word. Voici comment le configurer :

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ce code initialise un nouveau document Word et configure un DocumentBuilder, que nous utiliserons pour insérer du contenu dans notre document.

## Étape 2 : Lisez votre objet Ole

Ensuite, lisons le fichier que vous souhaitez intégrer. Considérez cela comme la récupération du trésor que vous souhaitez cacher dans votre compartiment secret :

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Cette ligne lit tous les octets de votre fichier ZIP et les stocke dans un tableau d'octets.

## Étape 3 : Insérer l'objet Ole

Vient maintenant la partie magique. Nous allons intégrer le fichier dans notre document Word :

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Ici, nous créons un flux de mémoire à partir du tableau d'octets et utilisons le`InsertOleObject` méthode pour l'intégrer dans le document. Nous définissons également le nom de fichier et le nom d'affichage de l'objet incorporé.

## Étape 4 : Enregistrez votre document

Enfin, sauvons notre chef-d'œuvre :

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Cela enregistre le document avec votre fichier intégré dans le répertoire spécifié.

## Conclusion

Et voilà ! Vous avez réussi à intégrer un objet OLE dans un document Word à l'aide d'Aspose.Words pour .NET. C'est comme si vous ajoutiez un joyau caché à l'intérieur de votre document qui peut être dévoilé à tout moment. Cette technique peut être incroyablement utile pour une variété d'applications, de la documentation technique aux rapports dynamiques. 

## FAQ

### Puis-je intégrer d’autres types de fichiers en utilisant cette méthode ?
Oui, vous pouvez intégrer différents types de fichiers tels que des feuilles Excel, des PDF et des images.

### Ai-je besoin d'une licence pour Aspose.Words ?
 Oui, vous avez besoin d'un permis valide. Vous pouvez obtenir un[permis temporaire](https://purchase.aspose.com/temporary-license/) pour évaluation.

### Comment puis-je personnaliser le nom d'affichage de l'objet OLE ?
 Vous pouvez définir le`DisplayName` propriété de la`OlePackage` pour le personnaliser.

### Aspose.Words est-il compatible avec .NET Core ?
Oui, Aspose.Words prend en charge .NET Framework et .NET Core.

### Puis-je modifier l’objet OLE intégré dans le document Word ?
Non, vous ne pouvez pas modifier l'objet OLE directement dans Word. Vous devez l'ouvrir dans son application native.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
