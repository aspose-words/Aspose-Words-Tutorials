---
"description": "Apprenez à extraire facilement le contenu de vos documents avec Aspose.Words pour Java. Notre guide étape par étape et nos exemples de code simplifient le processus."
"linktitle": "Extraction de contenu à partir de documents"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Extraction de contenu de documents dans Aspose.Words pour Java"
"url": "/fr/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Extraction de contenu de documents dans Aspose.Words pour Java


## Introduction à l'extraction de contenu de documents dans Aspose.Words pour Java

Dans le monde du traitement de documents, l'extraction de contenu est une exigence courante. Que vous ayez besoin d'extraire du texte, des tableaux, des images ou des éléments spécifiques, Aspose.Words pour Java offre des outils puissants pour simplifier cette tâche. Dans ce guide complet, nous vous expliquerons comment extraire du contenu de documents avec Aspose.Words pour Java. 

## Prérequis

Avant de nous plonger dans le processus d’extraction, assurez-vous que les conditions préalables suivantes sont en place :

1. Aspose.Words pour Java : Aspose.Words pour Java doit être installé et configuré dans votre environnement de développement Java. Vous pouvez le télécharger ici. [ici](https://releases.aspose.com/words/java/).

2. Document pour extraire du contenu : Pour ce guide, nous utiliserons un exemple de document intitulé « Extraire le contenu.docx ». Assurez-vous d'avoir un document similaire prêt à être extrait.

## Extraction de contenu entre les nœuds de niveau bloc

```java
// Exemple de code Java pour l'extraction de contenu entre les nœuds de niveau bloc
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## Extraction de contenu entre les signets

```java
// Exemple de code Java pour extraire le contenu entre les signets
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## Extraction de contenu entre les plages de commentaires

```java
// Exemple de code Java pour extraire le contenu entre les plages de commentaires
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## Extraction de contenu entre les paragraphes

```java
// Exemple de code Java pour extraire le contenu entre les paragraphes
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Extraction de contenu entre les styles de paragraphe

```java
// Exemple de code Java pour extraire le contenu entre les styles de paragraphe
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Extraction de contenu entre les exécutions

```java
// Exemple de code Java pour l'extraction de contenu entre les exécutions
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Extraction de contenu à l'aide de DocumentVisitor

```java
// Exemple de code Java pour l'extraction de contenu à l'aide de DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Extraction de contenu à l'aide d'un champ

```java
// Exemple de code Java pour l'extraction de contenu à l'aide de Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Extraction de la table des matières

```java
// Exemple de code Java pour l'extraction de la table des matières
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## Extraction de texte uniquement

```java
// Exemple de code Java pour l'extraction de texte uniquement
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Extraction de contenu en fonction des styles

```java
// Exemple de code Java pour l'extraction de contenu en fonction des styles
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## Extraction et impression de texte

```java
// Exemple de code Java pour l'extraction et l'impression de texte
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Extraction d'images vers des fichiers

```java
// Exemple de code Java pour extraire des images vers des fichiers
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## Conclusion

Félicitations ! Vous avez appris à extraire le contenu de documents avec Aspose.Words pour Java. Ce guide aborde différentes techniques d'extraction, notamment le contenu entre les nœuds de niveau bloc, les signets, les plages de commentaires, les paragraphes, etc. Vous êtes désormais équipé pour extraire efficacement le contenu de vos documents dans vos applications Java.

## FAQ

### Comment extraire le contenu de sections spécifiques d'un document ?

Pour extraire le contenu de sections de document spécifiques, vous pouvez identifier les points de départ et de fin des sections et utiliser les méthodes Aspose.Words pour Java appropriées pour extraire le contenu entre elles.

### Puis-je extraire le contenu de documents protégés par mot de passe ?

Oui, Aspose.Words pour Java permet d'extraire le contenu de documents protégés par mot de passe. Vous pouvez saisir le mot de passe à l'ouverture du document grâce à l'option `Document` constructeur de classe.

### Comment puis-je extraire du contenu et l'enregistrer dans différents formats, tels que du texte brut ou du HTML ?

Vous pouvez extraire le contenu d'un document et l'enregistrer sous différents formats grâce à Aspose.Words pour Java. Après extraction, vous pouvez utiliser l'outil `Document` méthodes de classe pour l'enregistrer dans des formats tels que du texte brut, du HTML ou d'autres.

### Existe-t-il un moyen d’extraire le contenu d’éléments de document spécifiques, tels que des tableaux ou des images ?

Oui, vous pouvez extraire le contenu d'éléments spécifiques d'un document, tels que des tableaux ou des images, avec Aspose.Words pour Java. Identifiez les éléments à extraire, puis utilisez les méthodes appropriées pour extraire leur contenu.

### Comment puis-je automatiser le processus d’extraction de contenu dans mon application Java ?

Pour automatiser le processus d'extraction de contenu dans votre application Java, vous pouvez créer du code personnalisé basé sur les techniques décrites dans ce guide. Vous pouvez également implémenter une logique pour parcourir plusieurs documents et extraire le contenu selon vos besoins.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}