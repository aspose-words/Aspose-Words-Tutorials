---
title: Utilisation de filigranes sur des documents dans Aspose.Words pour Java
linktitle: Utilisation de filigranes sur les documents
second_title: API de traitement de documents Java Aspose.Words
description: Découvrez comment ajouter des filigranes aux documents dans Aspose.Words pour Java. Personnalisez les filigranes de texte et d'image pour des documents d'aspect professionnel.
weight: 15
url: /fr/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation de filigranes sur des documents dans Aspose.Words pour Java


## Introduction à l'ajout de filigranes aux documents dans Aspose.Words pour Java

Dans ce didacticiel, nous allons découvrir comment ajouter des filigranes aux documents à l'aide de l'API Aspose.Words pour Java. Les filigranes sont un moyen utile d'étiqueter des documents avec du texte ou des graphiques pour indiquer leur statut, leur confidentialité ou d'autres informations pertinentes. Nous aborderons à la fois les filigranes de texte et d'image dans ce guide.

## Configuration d'Aspose.Words pour Java

Avant de commencer à ajouter des filigranes aux documents, nous devons configurer Aspose.Words pour Java. Suivez ces étapes pour commencer :

1.  Téléchargez Aspose.Words pour Java depuis[ici](https://releases.aspose.com/words/java/).
2. Ajoutez la bibliothèque Aspose.Words pour Java à votre projet Java.
3. Importez les classes nécessaires dans votre code Java.

Maintenant que la bibliothèque est configurée, passons à l'ajout de filigranes.

## Ajout de filigranes de texte

Les filigranes textuels sont un choix courant lorsque vous souhaitez ajouter des informations textuelles à vos documents. Voici comment ajouter un filigrane textuel à l'aide d'Aspose.Words pour Java :

```java
// Créer une instance de document
Document doc = new Document("Document.docx");

// Définir les options de filigrane de texte
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Définir le texte et les options du filigrane
doc.getWatermark().setText("Test", options);

// Enregistrer le document avec le filigrane
doc.save("DocumentWithWatermark.docx");
```

## Ajout de filigranes d'image

En plus des filigranes textuels, vous pouvez également ajouter des filigranes d'image à vos documents. Voici comment ajouter un filigrane d'image :

```java
// Créer une instance de document
Document doc = new Document("Document.docx");

// Charger l'image pour le filigrane
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Définir la taille et la position du filigrane
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Ajouter le filigrane au document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Enregistrer le document avec le filigrane
doc.save("DocumentWithImageWatermark.docx");
```

## Personnalisation des filigranes

Vous pouvez personnaliser les filigranes en modifiant leur apparence et leur position. Pour les filigranes de texte, vous pouvez modifier la police, la taille, la couleur et la mise en page. Pour les filigranes d'image, vous pouvez modifier leur taille et leur position comme indiqué dans les exemples précédents.

## Suppression des filigranes

Pour supprimer les filigranes d'un document, vous pouvez utiliser le code suivant :

```java
// Créer une instance de document
Document doc = new Document("DocumentWithWatermark.docx");

// Supprimer le filigrane
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Enregistrer le document sans le filigrane
doc.save("DocumentWithoutWatermark.docx");
```


## Conclusion

Dans ce didacticiel, nous avons appris à ajouter des filigranes à des documents à l'aide d'Aspose.Words pour Java. Que vous ayez besoin d'ajouter des filigranes de texte ou d'image, Aspose.Words fournit les outils pour les personnaliser et les gérer efficacement. Vous pouvez également supprimer les filigranes lorsqu'ils ne sont plus nécessaires, garantissant ainsi que vos documents sont propres et professionnels.

## FAQ

### Comment puis-je changer la police d’un filigrane de texte ?

 Pour changer la police d'un filigrane de texte, modifiez le`setFontFamily` propriété dans le`TextWatermarkOptions`. Par exemple:

```java
options.setFontFamily("Times New Roman");
```

### Puis-je ajouter plusieurs filigranes à un seul document ?

 Oui, vous pouvez ajouter plusieurs filigranes à un document en créant plusieurs`Shape` objets avec des paramètres différents et les ajouter au document.

### Est-il possible de faire pivoter un filigrane ?

 Oui, vous pouvez faire pivoter un filigrane en définissant le`setRotation` propriété dans le`Shape` objet. Les valeurs positives font pivoter le filigrane dans le sens des aiguilles d'une montre, et les valeurs négatives le font pivoter dans le sens inverse des aiguilles d'une montre.

### Comment puis-je rendre un filigrane semi-transparent ?

 Pour rendre un filigrane semi-transparent, définissez le`setSemitransparent`propriété à`true` dans le`TextWatermarkOptions`.

### Puis-je ajouter des filigranes à des sections spécifiques d’un document ?

Oui, vous pouvez ajouter des filigranes à des sections spécifiques d'un document en parcourant les sections et en ajoutant le filigrane aux sections souhaitées.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
