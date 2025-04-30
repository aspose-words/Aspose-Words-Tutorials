---
"description": "Apprenez à convertir des documents Word en Markdown avec Aspose.Words pour Java. Ce guide étape par étape couvre l'alignement des tableaux, la gestion des images et bien plus encore."
"linktitle": "Enregistrer des documents au format Markdown"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Enregistrer des documents au format Markdown dans Aspose.Words pour Java"
"url": "/fr/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer des documents au format Markdown dans Aspose.Words pour Java


## Introduction à l'enregistrement de documents au format Markdown dans Aspose.Words pour Java

Dans ce guide étape par étape, nous vous montrerons comment enregistrer des documents au format Markdown avec Aspose.Words pour Java. Markdown est un langage de balisage léger, couramment utilisé pour la mise en forme de documents texte. Avec Aspose.Words pour Java, vous pouvez facilement convertir vos documents Word au format Markdown. Nous aborderons différents aspects de l'enregistrement de fichiers Markdown, notamment l'alignement du contenu des tableaux et la gestion des images.

## Prérequis

Avant de commencer, assurez-vous de disposer des prérequis suivants :

- Java Development Kit (JDK) installé sur votre système.
- Bibliothèque Aspose.Words pour Java. Vous pouvez la télécharger depuis [ici](https://releases.aspose.com/words/java/).

## Étape 1 : Création d'un document Word

Commençons par créer un document Word que nous convertirons ensuite au format Markdown. Vous pouvez personnaliser ce document selon vos besoins.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer un tableau avec deux cellules
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Enregistrer le document au format Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Dans cet exemple, nous créons un tableau simple à deux cellules et définissons l'alignement des paragraphes à l'intérieur de ces cellules. Nous enregistrons ensuite le document au format Markdown à l'aide de l'outil `MarkdownSaveOptions`.

## Étape 2 : Personnaliser l’alignement du contenu du tableau

Aspose.Words pour Java vous permet de personnaliser l'alignement du contenu des tableaux lors de l'enregistrement au format Markdown. Vous pouvez aligner le contenu du tableau à gauche, à droite, au centre ou le laisser s'aligner automatiquement en fonction du premier paragraphe de chaque colonne.

Voici comment personnaliser l’alignement du contenu du tableau :

```java
// Définir l'alignement du contenu du tableau à gauche
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Définir l'alignement du contenu du tableau à droite
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Définir l'alignement du contenu du tableau au centre
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Définir l'alignement du contenu du tableau sur automatique (déterminé par le premier paragraphe)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

En changeant le `TableContentAlignment` propriété, vous pouvez contrôler la manière dont le contenu à l'intérieur des tableaux est aligné lors de la conversion en Markdown.

## Étape 3 : Gestion des images

Pour inclure des images dans votre document Markdown, vous devez spécifier le dossier où elles se trouvent. Aspose.Words pour Java vous permet de définir le dossier des images dans le `MarkdownSaveOptions`.

Voici comment définir le dossier d'images et enregistrer le document avec les images :

```java
// Charger un document contenant des images
Document doc = new Document("document_with_images.docx");

// Définir le chemin du dossier des images
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Enregistrer le document avec les images
doc.save("document_with_images.md", saveOptions);
```

Assurez-vous de remplacer `"document_with_images.docx"` avec le chemin vers votre document Word contenant des images et `"images_folder/"` avec le chemin réel vers le dossier où vos images sont stockées.

## Code source complet pour l'enregistrement de documents au format Markdown dans Aspose.Words pour Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Permet d'aligner tous les paragraphes à l'intérieur du tableau.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// L'alignement dans ce cas sera repris du premier paragraphe de la colonne de tableau correspondante.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Conclusion

Dans ce guide, nous avons découvert comment enregistrer des documents au format Markdown avec Aspose.Words pour Java. Nous avons abordé la création d'un document Word, la personnalisation de l'alignement du contenu des tableaux et la gestion des images dans les fichiers Markdown. Vous pouvez désormais convertir efficacement vos documents Word au format Markdown, les rendant ainsi compatibles avec diverses plateformes de publication et besoins de documentation.

## FAQ

### Comment installer Aspose.Words pour Java ?

Vous pouvez installer Aspose.Words pour Java en incluant la bibliothèque dans votre projet Java. Vous pouvez la télécharger depuis [ici](https://releases.aspose.com/words/java/) et suivez les instructions d'installation fournies dans la documentation.

### Puis-je convertir des documents Word complexes contenant des tableaux et des images en Markdown ?

Oui, Aspose.Words pour Java prend en charge la conversion en Markdown de documents Word complexes contenant des tableaux, des images et divers éléments de mise en forme. Vous pouvez personnaliser le rendu Markdown en fonction de la complexité de votre document.

### Comment puis-je gérer les images dans les fichiers Markdown ?

Pour inclure des images dans des fichiers Markdown, définissez le chemin du dossier des images à l'aide du `setImagesFolder` méthode dans `MarkdownSaveOptions`Assurez-vous que les fichiers image sont stockés dans le dossier spécifié et Aspose.Words pour Java gérera les références d'image en conséquence.

### Existe-t-il une version d'essai d'Aspose.Words pour Java disponible ?

Oui, vous pouvez obtenir une version d'essai d'Aspose.Words pour Java sur le site web d'Aspose. Cette version vous permet d'évaluer les fonctionnalités de la bibliothèque avant d'acheter une licence.

### Où puis-je trouver plus d'exemples et de documentation ?

Pour plus d'exemples, de documentation et d'informations détaillées sur Aspose.Words pour Java, veuillez visiter le [documentation](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}