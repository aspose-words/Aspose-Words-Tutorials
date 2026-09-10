---
date: 2025-12-22
description: Apprenez à exporter du markdown en convertissant des documents Word en
  Markdown avec Aspose.Words pour Java. Ce guide étape par étape couvre l'alignement
  des tableaux, la gestion des images et bien plus encore.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Comment exporter du Markdown avec Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment exporter du Markdown avec Aspose.Words pour Java

## Introduction à l'exportation de Markdown dans Aspose.Words pour Java

Dans ce tutoriel pas à pas, **vous apprendrez comment exporter du markdown** à partir de documents Word en utilisant Aspose.Words pour Java. Markdown est un langage de balisage léger idéal pour la documentation, les générateurs de sites statiques et de nombreuses plateformes de publication. À la fin de ce guide, vous serez capable de **convertir Word en markdown**, de personnaliser l'alignement des tableaux et de **gérer les images en markdown** sans effort.

## Réponses rapides
- **Quelle est la classe principale pour enregistrer en Markdown ?** `MarkdownSaveOptions`
- **Les images peuvent‑elles être intégrées automatiquement ?** Oui – définissez le dossier des images via `setImagesFolder`.
- **Comment contrôler l'alignement des tableaux ?** Utilisez `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Quelles sont les exigences minimales ?** JDK 8+ et la bibliothèque Aspose.Words pour Java.
- **Une version d'essai est‑elle disponible ?** Oui, téléchargez‑la depuis le site Aspose.

## Qu’est‑ce que « exporter du markdown » ?
Exporter du markdown signifie prendre un document Word riche (`.docx`) et produire un fichier texte brut `.md` qui préserve les titres, les tableaux et les images en syntaxe Markdown.

## Pourquoi utiliser Aspose.Words pour Java pour convertir des docx avec images ?
Aspose.Words gère les mises en page complexes, les images incorporées et les structures de tableau sans perdre de fidélité. Il vous offre également un contrôle granulaire sur la sortie Markdown, tel que l'alignement des tableaux et la gestion du dossier d'images.

## Prérequis

- Kit de développement Java (JDK) installé sur votre système.  
- Bibliothèque Aspose.Words pour Java. Vous pouvez la télécharger [ici](https://releases.aspose.com/words/java/).

## Étape 1 : Créer un document Word simple

Tout d'abord, nous allons créer un petit document contenant un tableau. Cela nous permettra de démontrer **la personnalisation de l'alignement du tableau** plus tard.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Dans l’extrait ci‑dessus, nous :

1. Créons un nouveau `Document`.  
2. Utilisons `DocumentBuilder` pour insérer un tableau à deux cellules.  
3. Appliquons un alignement de paragraphe **à droite** et **au centre** à l’intérieur de chaque cellule.  
4. Enregistrons le fichier au format Markdown avec `MarkdownSaveOptions`.

## Étape 2 : Personnaliser l’alignement du contenu du tableau

Aspose.Words vous permet de définir comment les cellules du tableau sont rendues dans le Markdown final. Vous pouvez forcer un alignement à gauche, à droite, centré, ou laisser la bibliothèque décider automatiquement en fonction du premier paragraphe de chaque colonne.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

En modifiant la propriété `TableContentAlignment`, vous contrôlez **la personnalisation de l'alignement du tableau** pour la sortie Markdown.

## Étape 3 : Gérer les images lors de l’exportation vers le markdown

Lorsqu'un document contient des images, vous voudrez que ces images apparaissent correctement dans le fichier `.md` généré. Définissez le dossier où Aspose.Words doit déposer les images extraites.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Remplacez `"document_with_images.docx"` par le chemin de votre fichier source et `"images_folder/"` par l’emplacement où vous souhaitez stocker les images. Le Markdown résultant contiendra des liens d’image pointant vers ce dossier, vous permettant de **gérer les images en markdown** de façon fluide.

## Code source complet pour enregistrer des documents au format Markdown avec Aspose.Words pour Java

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| Les images n’apparaissent pas dans le fichier `.md` | Vérifiez que `setImagesFolder` pointe vers un répertoire accessible en écriture et que le dossier est correctement référencé dans le Markdown généré. |
| L’alignement du tableau semble incorrect | Utilisez `TableContentAlignment.AUTO` pour laisser Aspose.Words déterminer le meilleur alignement en fonction du premier paragraphe de chaque colonne. |
| Le fichier de sortie est vide | Assurez‑vous que l’objet `Document` contient réellement du contenu avant d’appeler `save`. |

## Foire aux questions

**Q : Comment installer Aspose.Words pour Java ?**  
R : Aspose.Words pour Java peut être installé en incluant la bibliothèque dans votre projet Java. Vous pouvez télécharger la bibliothèque [ici](https://releases.aspose.com/words/java/) et suivre les instructions d’installation fournies dans la documentation.

**Q : Puis‑je convertir des documents Word complexes avec tableaux et images en Markdown ?**  
R : Oui, Aspose.Words pour Java prend en charge la conversion de documents Word complexes contenant des tableaux, des images et divers éléments de mise en forme en Markdown. Vous pouvez personnaliser la sortie Markdown en fonction de la complexité de votre document.

**Q : Comment gérer les images dans les fichiers Markdown ?**  
R : Définissez le chemin du dossier d’images à l’aide de la méthode `setImagesFolder` dans `MarkdownSaveOptions`. Assurez‑vous que les fichiers image sont stockés dans le dossier spécifié ; Aspose.Words générera les liens d’image Markdown appropriés.

**Q : Existe‑t‑il une version d’essai d’Aspose.Words pour Java ?**  
R : Oui, vous pouvez obtenir une version d’essai d’Aspose.Words pour Java depuis le site Aspose. La version d’essai vous permet d’évaluer les capacités de la bibliothèque avant d’acheter une licence.

**Q : Où puis‑je trouver plus d’exemples et de documentation ?**  
R : Pour plus d’exemples, de documentation et d’informations détaillées sur Aspose.Words pour Java, veuillez visiter la [documentation](https://reference.aspose.com/words/java/).

---

**Dernière mise à jour :** 2025-12-22  
**Testé avec :** Aspose.Words pour Java 24.12 (dernière version au moment de la rédaction)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}