---
title: Insérer un objet Ole en tant qu'icône à l'aide de Stream
linktitle: Insérer un objet Ole en tant qu'icône à l'aide de Stream
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer un objet OLE en tant qu'icône à l'aide d'un flux avec Aspose.Words pour .NET dans ce didacticiel détaillé, étape par étape.
weight: 10
url: /fr/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon-using-stream/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un objet Ole en tant qu'icône à l'aide de Stream

## Introduction

Dans ce tutoriel, nous allons nous plonger dans une fonctionnalité très intéressante d'Aspose.Words pour .NET : l'insertion d'un objet OLE (Object Linking and Embedding) sous forme d'icône à l'aide d'un flux. Que vous intégriez une présentation PowerPoint, une feuille de calcul Excel ou tout autre type de fichier, ce guide vous montrera exactement comment procéder. Prêt à commencer ? C'est parti !

## Prérequis

Avant de passer au code, vous aurez besoin de quelques éléments :

-  Aspose.Words pour .NET : si vous ne l'avez pas déjà fait,[télécharger](https://releases.aspose.com/words/net/) et installez Aspose.Words pour .NET.
- Environnement de développement : Visual Studio ou tout autre environnement de développement C#.
- Fichiers d'entrée : le fichier que vous souhaitez intégrer (par exemple, une présentation PowerPoint) et une image d'icône.

## Importer des espaces de noms

Pour commencer, assurez-vous d’avoir importé les espaces de noms nécessaires dans votre projet :

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Décomposons le processus étape par étape pour le rendre facile à suivre.

## Étape 1 : Créer un nouveau document

Tout d’abord, nous allons créer un nouveau document et un générateur de documents pour travailler avec lui.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Pense à`Document` comme votre toile vierge et`DocumentBuilder` comme votre pinceau. Nous préparons nos outils pour commencer à créer notre chef-d'œuvre.

## Étape 2 : Préparez le flux

Ensuite, nous devons préparer un flux mémoire contenant le fichier que nous souhaitons intégrer. Dans cet exemple, nous allons intégrer une présentation PowerPoint.

```csharp
using (MemoryStream stream = new MemoryStream(File.ReadAllBytes("Path_to_your_directory/Presentation.pptx")))
{
```

Cette étape consiste à charger votre peinture sur le pinceau. Nous préparons notre fichier à être intégré.

## Étape 3 : insérer l’objet OLE en tant qu’icône

Nous allons maintenant utiliser le générateur de documents pour insérer l'objet OLE dans le document. Nous allons spécifier le flux de fichiers, le ProgID pour le type de fichier (dans ce cas, « Package »), le chemin d'accès à l'image de l'icône et une étiquette pour le fichier incorporé.

```csharp
builder.InsertOleObjectAsIcon(stream, "Package", "Path_to_your_directory/Logo icon.ico", "My embedded file");
}
```

C'est ici que la magie opère ! Nous intégrons notre fichier et l'affichons sous forme d'icône dans le document.

## Étape 4 : Enregistrer le document

Enfin, nous enregistrons le document dans un chemin spécifié.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIconUsingStream.docx");
```

Cette étape consiste à encadrer votre tableau et à l'accrocher au mur. Votre document est maintenant prêt à être utilisé !

## Conclusion

Et voilà ! Vous avez réussi à intégrer un objet OLE sous forme d'icône dans un document Word à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité puissante peut vous aider à créer facilement des documents dynamiques et interactifs. Que vous intégriez des présentations, des feuilles de calcul ou d'autres fichiers, Aspose.Words vous facilite la tâche. Alors, n'hésitez pas, essayez-le et constatez la différence qu'il peut apporter à vos documents !

## FAQ

### Puis-je intégrer différents types de fichiers en utilisant cette méthode ?
Oui, vous pouvez intégrer n’importe quel type de fichier pris en charge par OLE, y compris Word, Excel, PowerPoint, etc.

### Ai-je besoin d'une licence spéciale pour utiliser Aspose.Words pour .NET ?
 Oui, Aspose.Words pour .NET nécessite une licence. Vous pouvez obtenir une[essai gratuit](https://releases.aspose.com/) ou acheter un[permis temporaire](https://purchase.aspose.com/temporary-license/) pour tester.

### Puis-je personnaliser l'icône utilisée pour l'objet OLE ?
 Absolument ! Vous pouvez utiliser n'importe quel fichier image pour l'icône en spécifiant son chemin dans le`InsertOleObjectAsIcon` méthode.

### Que se passe-t-il si les chemins d’accès aux fichiers ou aux icônes sont incorrects ?
La méthode génère une exception. Assurez-vous que les chemins d'accès à vos fichiers sont corrects pour éviter les erreurs.

### Est-il possible de lier l'objet incorporé au lieu de l'incorporer ?
Oui, Aspose.Words vous permet d'insérer des objets OLE liés, qui référencent le fichier sans incorporer son contenu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
