---
"description": "Apprenez à utiliser les balises de document structurées (SDT) dans Aspose.Words pour Java grâce à ce guide complet. Créez, modifiez et liez des SDT à des données XML personnalisées."
"linktitle": "Utilisation des balises de documents structurés (SDT)"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Utilisation des balises de document structurées (SDT) dans Aspose.Words pour Java"
"url": "/fr/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des balises de document structurées (SDT) dans Aspose.Words pour Java


## Introduction à l'utilisation des balises de document structurées (SDT) dans Aspose.Words pour Java

Les balises de document structurées (SDT) sont une fonctionnalité puissante d'Aspose.Words pour Java qui vous permet de créer et de manipuler du contenu structuré dans vos documents. Ce guide complet vous présente les différents aspects de l'utilisation des balises de document structurées dans Aspose.Words pour Java. Que vous soyez débutant ou développeur expérimenté, vous trouverez dans cet article des informations précieuses et des exemples pratiques.

## Commencer

Avant d'entrer dans les détails, configurons notre environnement et créons un SDT de base. Dans cette section, nous aborderons les sujets suivants :

- Créer un nouveau document
- Ajout d'une balise de document structuré
- Sauvegarde du document

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Créer une balise de document structuré de type CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Enregistrer le document
doc.save("WorkingWithSDT.docx");
```

## Vérification de l'état actuel d'une case à cocher SDT

Après avoir ajouté une case à cocher SDT à votre document, vous pouvez vérifier son état actuel par programmation. Cela peut être utile pour valider une saisie utilisateur ou effectuer des actions spécifiques en fonction de l'état de la case à cocher.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // La case à cocher est cochée
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Modification des contrôles de contenu

Dans cette section, nous verrons comment modifier les contrôles de contenu dans votre document. Nous aborderons trois types de contrôles : texte brut, liste déroulante et image.

### Modification du contrôle du contenu en texte brut

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Effacer le contenu existant
    sdtPlainText.removeAllChildren();

    // Ajouter un nouveau texte
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Modification du contrôle du contenu de la liste déroulante

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Sélectionnez le deuxième élément de la liste
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Modification du contrôle du contenu de l'image

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Remplacer l'image par une nouvelle
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Création d'un contrôle de contenu ComboBox

Un contrôle de contenu ComboBox permet aux utilisateurs de sélectionner des options parmi une liste prédéfinie. Créons-en un dans notre document.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Travailler avec le contrôle de contenu de texte enrichi

Les contrôles de contenu de texte enrichi sont parfaits pour ajouter du texte formaté à vos documents. Créons-en un et définissons son contenu.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## Définition des styles de contrôle de contenu

Vous pouvez appliquer des styles aux contrôles de contenu pour améliorer l'apparence visuelle de votre document. Voyons comment définir le style d'un contrôle de contenu.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Appliquer un style personnalisé
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Liaison d'un SDT à des données XML personnalisées

Dans certains cas, vous devrez peut-être lier un SDT à des données XML personnalisées pour générer du contenu dynamique. Voyons comment procéder.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Création d'un tableau avec des sections répétitives mappées à des données XML personnalisées

Les tableaux avec des sections répétitives peuvent être extrêmement utiles pour présenter des données structurées. Créons un tel tableau et mappons-le à des données XML personnalisées.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## Travailler avec des balises de documents structurés à sections multiples

Les balises de document structurées peuvent s'étendre sur plusieurs sections d'un document. Dans cette section, nous allons découvrir comment utiliser des balises de document structurées multi-sections.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Conclusion

Les balises de documents structurés dans Aspose.Words pour Java offrent une solution polyvalente pour gérer et mettre en forme le contenu de vos documents. Que vous ayez besoin de créer des modèles, des formulaires ou des documents dynamiques, les balises de documents structurés offrent la flexibilité et le contrôle nécessaires. En suivant les exemples et les conseils fournis dans cet article, vous pourrez exploiter la puissance des balises de documents structurés pour optimiser vos tâches de traitement de documents.

## FAQ

### Quel est le but des balises de documents structurés (SDT) ?

Les balises de documents structurés (SDT) servent à organiser et à formater le contenu des documents, ce qui facilite la création de modèles, de formulaires et de documents structurés.

### Comment puis-je vérifier l'état actuel d'un SDT Checkbox ?

Vous pouvez vérifier l'état actuel d'un SDT Checkbox à l'aide de l' `setChecked` méthode, comme démontré dans l'article.

### Puis-je appliquer des styles aux contrôles de contenu ?

Oui, vous pouvez appliquer des styles aux contrôles de contenu pour personnaliser leur apparence dans le document.

### Est-il possible de lier un SDT à des données XML personnalisées ?

Oui, vous pouvez lier un SDT à des données XML personnalisées, permettant ainsi la génération de contenu dynamique et le mappage de données.

### Que sont les sections répétitives dans les SDT ?

Les sections répétitives dans les SDT vous permettent de créer des tables avec des données dynamiques, où les lignes peuvent être répétées en fonction des données XML mappées.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}