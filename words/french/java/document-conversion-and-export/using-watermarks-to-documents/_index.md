---
date: 2025-12-18
description: Apprenez comment ajouter un filigrane aux documents avec Aspose.Words
  pour Java, y compris un exemple de filigrane d'image, modifier la couleur du filigrane,
  définir la transparence du filigrane et supprimer le filigrane d’un document.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Comment ajouter un filigrane aux documents avec Aspose.Words pour Java
url: /fr/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter un filigrane aux documents avec Aspose.Words pour Java

## Introduction à l'ajout de filigranes aux documents avec Aspose.Words pour Java

Dans ce tutoriel, vous apprendrez **comment ajouter un filigrane** aux documents Word avec Aspose.Words pour Java. Les filigranes sont un moyen rapide d'étiqueter un fichier comme confidentiel, brouillon ou approuvé, et ils peuvent être basés sur du texte ou sur une image. Nous parcourrons la configuration de la bibliothèque, la création de filigranes texte et image, la personnalisation de leur apparence (y compris le changement de couleur du filigrane et la définition de la transparence du filigrane), et même la suppression d'un filigrane d'un document lorsqu'il n'est plus nécessaire.

## Réponses rapides
- **Qu'est‑ce qu'un filigrane ?** Une superposition semi‑transparente (texte ou image) qui apparaît derrière le contenu principal du document.  
- **Puis‑je ajouter plusieurs filigranes ?** Oui – créez plusieurs objets `Shape` et ajoutez‑les aux sections souhaitées.  
- **Comment changer la couleur du filigrane ?** Ajustez la propriété `Color` dans `TextWatermarkOptions`.  
- **Existe‑t‑il un exemple de filigrane image ?** Voir la section « Ajout de filigranes image » ci‑dessous.  
- **Ai‑je besoin d'une licence pour supprimer un filigrane ?** Une licence valide d'Aspose.Words est requise pour une utilisation en production.

## Configuration d'Aspose.Words pour Java

Avant de commencer à ajouter des filigranes aux documents, nous devons configurer Aspose.Words pour Java. Suivez ces étapes pour commencer :

1. Téléchargez Aspose.Words pour Java depuis [ici](https://releases.aspose.com/words/java/).  
2. Ajoutez la bibliothèque Aspose.Words pour Java à votre projet Java.  
3. Importez les classes nécessaires dans votre code Java.

Maintenant que la bibliothèque est configurée, plongeons dans la création réelle de filigranes.

## Ajout de filigranes texte

Les filigranes texte sont un choix courant lorsque vous souhaitez ajouter des informations textuelles à vos documents. Voici comment ajouter un filigrane texte avec Aspose.Words pour Java :

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Pourquoi c'est important :** En ajustant `setFontFamily`, `setFontSize` et `setColor`, vous pouvez **modifier la couleur du filigrane** pour correspondre à votre identité visuelle, et `setSemitransparent(true)` vous permet de **définir la transparence du filigrane** pour un effet subtil.

## Ajout de filigranes image

En plus des filigranes texte, vous pouvez également ajouter des filigranes image à vos documents. Ci‑dessous se trouve un **exemple de filigrane image** qui montre comment intégrer un logo ou un tampon PNG :

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Vous pouvez répéter ce bloc avec différentes images ou positions pour **ajouter plusieurs filigranes** à un même fichier.

## Personnalisation des filigranes

Vous pouvez personnaliser les filigranes en ajustant leur apparence et leur position. Pour les filigranes texte, vous pouvez modifier la police, la taille, la couleur et la mise en page. Pour les filigranes image, vous pouvez modifier la taille, la rotation et l'alignement comme démontré dans les exemples précédents.

## Suppression des filigranes

Si vous devez **supprimer le filigrane d'un document**, le code suivant parcourt toutes les formes et supprime celles identifiées comme filigranes :

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Cas d'utilisation courants et astuces
- **Brouillons confidentiels :** Appliquez un filigrane texte semi‑transparent tel que « CONFIDENTIAL ».  
- **Branding :** Utilisez un filigrane image contenant le logo de votre entreprise.  
- **Filigranes spécifiques à une section :** Parcourez `doc.getSections()` et ajoutez un filigrane uniquement aux sections que vous choisissez.  
- **Astuce de performance :** Réutilisez la même instance `TextWatermarkOptions` lors de l'application du même filigrane à de nombreux documents.

## FAQ

### Comment puis‑je changer la police d'un filigrane texte ?

Pour changer la police d'un filigrane texte, modifiez la propriété `setFontFamily` dans `TextWatermarkOptions`. Par exemple :

```java
options.setFontFamily("Times New Roman");
```

### Puis‑je ajouter plusieurs filigranes à un même document ?

Oui, vous pouvez ajouter plusieurs filigranes à un document en créant plusieurs objets `Shape` avec des paramètres différents et en les ajoutant au document.

### Est‑il possible de faire pivoter un filigrane ?

Oui, vous pouvez faire pivoter un filigrane en définissant la propriété `setRotation` dans l'objet `Shape`. Les valeurs positives font pivoter le filigrane dans le sens des aiguilles d'une montre, et les valeurs négatives le font pivoter dans le sens inverse.

### Comment rendre un filigrane semi‑transparent ?

Pour rendre un filigrane semi‑transparent, définissez la propriété `setSemitransparent` sur `true` dans `TextWatermarkOptions`.

### Puis‑je ajouter des filigranes à des sections spécifiques d'un document ?

Oui, vous pouvez ajouter des filigranes à des sections spécifiques d'un document en parcourant les sections et en ajoutant le filigrane aux sections souhaitées.

---

**Dernière mise à jour :** 2025-12-18  
**Testé avec :** Aspose.Words for Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}