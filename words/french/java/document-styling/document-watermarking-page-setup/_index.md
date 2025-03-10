---
title: Filigranage de documents et mise en page
linktitle: Filigranage de documents et mise en page
second_title: API de traitement de documents Java Aspose.Words
description: Découvrez comment appliquer des filigranes et configurer des pages avec Aspose.Words pour Java. Un guide complet avec code source.
weight: 13
url: /fr/java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Filigranage de documents et mise en page

## Introduction

Dans le domaine de la manipulation de documents, Aspose.Words pour Java est un outil puissant, permettant aux développeurs de contrôler tous les aspects du traitement des documents. Dans ce guide complet, nous allons nous plonger dans les subtilités du filigranage de documents et de la mise en page à l'aide d'Aspose.Words pour Java. Que vous soyez un développeur chevronné ou que vous débutiez dans le monde du traitement de documents Java, ce guide étape par étape vous fournira les connaissances et le code source dont vous avez besoin.

## Filigranage de documents

### Ajout de filigranes

L'ajout de filigranes aux documents peut être crucial pour la valorisation de votre marque ou la sécurisation de votre contenu. Aspose.Words pour Java simplifie cette tâche. Voici comment :

```java
// Charger le document
Document doc = new Document("document.docx");

// Créer un filigrane
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// Positionner le filigrane
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// Insérer le filigrane
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Enregistrer le document
doc.save("document_with_watermark.docx");
```

### Personnalisation des filigranes

Vous pouvez personnaliser davantage les filigranes en ajustant la police, la taille, la couleur et la rotation. Cette flexibilité garantit que votre filigrane correspond parfaitement au style de votre document.

## Mise en page

### Taille et orientation de la page

La mise en page est essentielle dans la mise en forme des documents. Aspose.Words pour Java offre un contrôle complet sur la taille et l'orientation des pages :

```java
// Charger le document
Document doc = new Document("document.docx");

// Définir la taille de la page sur A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// Changer l'orientation de la page en paysage
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// Enregistrer le document modifié
doc.save("formatted_document.docx");
```

### Marges et numérotation des pages

Un contrôle précis des marges et de la numérotation des pages est essentiel pour les documents professionnels. Réalisez-le avec Aspose.Words pour Java :

```java
// Charger le document
Document doc = new Document("document.docx");

// Définir les marges
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// Activer la numérotation des pages
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// Enregistrer le document formaté
doc.save("formatted_document.docx");
```

## FAQ

### Comment puis-je supprimer un filigrane d'un document ?

Pour supprimer un filigrane d'un document, vous pouvez parcourir les formes du document et supprimer celles qui représentent des filigranes. Voici un extrait :

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### Puis-je ajouter plusieurs filigranes à un seul document ?

Oui, vous pouvez ajouter plusieurs filigranes à un document en créant des objets Shape supplémentaires et en les positionnant selon vos besoins.

### Comment puis-je modifier la taille de la page en format légal en orientation paysage ?

Pour définir la taille de la page sur légal en orientation paysage, modifiez la largeur et la hauteur de la page comme suit :

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### Quelle est la police par défaut pour les filigranes ?

La police par défaut pour les filigranes est Calibri avec une taille de police de 36.

### Comment puis-je ajouter des numéros de page à partir d’une page spécifique ?

Vous pouvez y parvenir en définissant le numéro de page de départ de votre document comme suit :

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### Comment aligner au centre du texte dans l’en-tête ou le pied de page ?

Vous pouvez aligner le texte au centre dans l'en-tête ou le pied de page en utilisant la méthode setAlignment sur l'objet Paragraph dans l'en-tête ou le pied de page.

## Conclusion

Dans ce guide complet, nous avons exploré l'art du filigranage de documents et de la mise en page à l'aide d'Aspose.Words pour Java. Armé des extraits de code source et des informations fournies, vous possédez désormais les outils nécessaires pour manipuler et formater vos documents avec finesse. Aspose.Words pour Java vous permet de créer des documents professionnels et de marque adaptés à vos spécifications exactes.

La maîtrise de la manipulation de documents est une compétence précieuse pour les développeurs, et Aspose.Words for Java est votre compagnon de confiance dans ce parcours. Commencez à créer des documents époustouflants dès aujourd'hui !
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
