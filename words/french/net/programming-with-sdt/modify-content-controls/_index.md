---
title: Modifier les contrôles de contenu
linktitle: Modifier les contrôles de contenu
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment modifier les balises de documents structurés dans Word à l'aide d'Aspose.Words pour .NET. Mettez à jour le texte, les listes déroulantes et les images étape par étape.
weight: 10
url: /fr/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifier les contrôles de contenu

## Introduction

Si vous avez déjà travaillé avec des documents Word et que vous avez eu besoin de modifier des contrôles de contenu structuré (comme du texte brut, des listes déroulantes ou des images) à l'aide d'Aspose.Words pour .NET, vous êtes au bon endroit ! Les balises de document structuré (SDT) sont des outils puissants qui facilitent et assouplissent l'automatisation des documents. Dans ce didacticiel, nous verrons comment modifier ces balises de document structuré pour répondre à vos besoins. Que vous mettiez à jour du texte, modifiiez des sélections déroulantes ou échangiez des images, ce guide vous guidera tout au long du processus, étape par étape.

## Prérequis

Avant de passer aux détails de la modification des contrôles de contenu, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET installé : assurez-vous que la bibliothèque Aspose.Words est installée. Si ce n'est pas le cas, vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).

2. Connaissances de base de C# : ce didacticiel suppose que vous êtes familiarisé avec les concepts de base de la programmation C#.

3. Un environnement de développement .NET : vous devez disposer d’un IDE tel que Visual Studio configuré pour exécuter des applications .NET.

4. Un exemple de document : nous utiliserons un exemple de document Word avec différents types de SDT. Vous pouvez utiliser celui de l'exemple ou créer le vôtre.

5.  Accès à la documentation Aspose : Pour des informations plus détaillées, consultez le[Documentation Aspose.Words](https://reference.aspose.com/words/net/).

## Importer des espaces de noms

Pour commencer à travailler avec Aspose.Words, vous devez importer les espaces de noms pertinents dans votre projet C#. Voici comment procéder :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Ces espaces de noms vous donneront accès aux classes et méthodes nécessaires à la manipulation des balises de documents structurés dans vos documents Word.

## Étape 1 : Configurez le chemin de votre document

 Avant d'effectuer des modifications, vous devez spécifier le chemin d'accès à votre document. Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel où votre document est stocké.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Étape 2 : Parcourir les balises de documents structurés

 Pour modifier les SDT, vous devez d'abord parcourir tous les SDT du document. Pour cela, utilisez la commande`GetChildNodes` méthode pour obtenir tous les nœuds de type`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modifier les SDT en fonction de leur type
}
```

## Étape 3 : modifier les SDT en texte brut

Si le SDT est de type texte brut, vous pouvez remplacer son contenu. Tout d'abord, effacez le contenu existant, puis ajoutez un nouveau texte.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Explication : Ici,`RemoveAllChildren()`efface le contenu existant du SDT. Nous créons ensuite un nouveau`Paragraph` et`Run` objet pour insérer le nouveau texte.

## Étape 4 : Modifier les SDT de la liste déroulante

 Pour les SDT à liste déroulante, vous pouvez modifier l'élément sélectionné en accédant à l'`ListItems` collection. Ici, nous sélectionnons le troisième élément de la liste.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Explication : cet extrait de code sélectionne l'élément à l'index 2 (troisième élément) dans la liste déroulante. Ajustez l'index en fonction de vos besoins.

## Étape 5 : Modifier les SDT d'image

Pour mettre à jour une image dans un SDT d'images, vous pouvez remplacer l'image existante par une nouvelle.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Explication : Ce code vérifie si la forme contient une image, puis la remplace par une nouvelle image située à`ImagesDir`.

## Étape 6 : Enregistrez votre document modifié

Après avoir effectué toutes les modifications nécessaires, enregistrez le document modifié sous un nouveau nom pour conserver votre document d'origine intact.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Explication : Cela enregistre le document avec un nouveau nom de fichier afin que vous puissiez facilement le différencier de l'original.

## Conclusion

La modification des contrôles de contenu dans un document Word à l'aide d'Aspose.Words pour .NET est simple une fois que vous avez compris les étapes impliquées. Que vous mettiez à jour du texte, modifiiez des sélections déroulantes ou échangiez des images, Aspose.Words fournit une API robuste pour ces tâches. En suivant ce didacticiel, vous pouvez gérer et personnaliser efficacement les contrôles de contenu structuré de votre document, rendant ainsi vos documents plus dynamiques et adaptés à vos besoins.

## FAQ

1. Qu'est-ce qu'une balise de document structurée (SDT) ?

Les SDT sont des éléments dans les documents Word qui aident à gérer et à formater le contenu du document, comme les zones de texte, les listes déroulantes ou les images.

2. Comment puis-je ajouter un nouvel élément déroulant à un SDT ?

 Pour ajouter un nouvel élément, utilisez le`ListItems` propriété et ajouter une nouvelle`SdtListItem` à la collection.

3. Puis-je utiliser Aspose.Words pour supprimer les SDT d’un document ?

Oui, vous pouvez supprimer les SDT en accédant aux nœuds du document et en supprimant le SDT souhaité.

4. Comment gérer les SDT imbriqués dans d’autres éléments ?

 Utilisez le`GetChildNodes` méthode avec des paramètres appropriés pour accéder aux SDT imbriqués.

5. Que dois-je faire si le SDT que je dois modifier n’est pas visible dans le document ?

Assurez-vous que le SDT n'est pas masqué ou protégé. Vérifiez les paramètres du document et assurez-vous que votre code cible correctement le type de SDT.


### Exemple de code source pour la modification des contrôles de contenu à l'aide d'Aspose.Words pour .NET 

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Et voilà ! Vous avez modifié avec succès différents types de contrôles de contenu dans votre document Word à l'aide d'Aspose.Words pour .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
