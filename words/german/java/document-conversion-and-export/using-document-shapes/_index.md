---
title: Verwenden von Dokumentformen in Aspose.Words für Java
linktitle: Verwenden von Dokumentformen
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Nutzen Sie die Leistungsfähigkeit von Dokumentformen in Aspose.Words für Java. Lernen Sie anhand von Schritt-für-Schritt-Beispielen, visuell ansprechende Dokumente zu erstellen.
weight: 14
url: /de/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Dokumentformen in Aspose.Words für Java


## Einführung in die Verwendung von Dokumentformen in Aspose.Words für Java

In diesem umfassenden Leitfaden tauchen wir in die Welt der Dokumentformen in Aspose.Words für Java ein. Formen sind wesentliche Elemente, wenn es darum geht, optisch ansprechende und interaktive Dokumente zu erstellen. Egal, ob Sie Callouts, Schaltflächen, Bilder oder Wasserzeichen hinzufügen müssen, Aspose.Words für Java bietet die Tools, um dies effizient zu tun. Lassen Sie uns anhand von Quellcodebeispielen Schritt für Schritt erkunden, wie Sie diese Formen verwenden.

## Erste Schritte mit Dokumentformen

 Bevor wir uns in den Code stürzen, richten wir unsere Umgebung ein. Stellen Sie sicher, dass Sie Aspose.Words für Java in Ihr Projekt integriert haben. Falls noch nicht geschehen, können Sie es von der Aspose-Website herunterladen.[Laden Sie Aspose.Words für Java herunter](https://releases.aspose.com/words/java/)

## Hinzufügen von Formen zu Dokumenten

### Einfügen einer Gruppenform

 A`GroupShape` ermöglicht Ihnen die Gruppierung mehrerer Formen. So erstellen und fügen Sie eine`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### Einfügen einer Textfeldform

 Um eine Textfeldform einzufügen, können Sie das`insertShape` Methode wie im folgenden Beispiel gezeigt:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Bearbeiten von Formeigenschaften

### Seitenverhältnis verwalten

Sie können steuern, ob das Seitenverhältnis einer Form gesperrt ist oder nicht. So entsperren Sie das Seitenverhältnis einer Form:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Platzieren einer Form in einer Tabellenzelle

Wenn Sie eine Form in eine Tabellenzelle einfügen müssen, können Sie dies mit dem folgenden Code erreichen:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Zeigen Sie die Form außerhalb der Tabellenzelle an, wenn sie in einer Zelle platziert wird.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Arbeiten mit SmartArt-Formen

### Erkennen von SmartArt-Formen

Sie können SmartArt-Formen in einem Dokument mit dem folgenden Code erkennen:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualisieren von SmartArt-Zeichnungen

Um SmartArt-Zeichnungen in einem Dokument zu aktualisieren, verwenden Sie den folgenden Code:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Abschluss

In diesem Handbuch haben wir die Welt der Dokumentformen in Aspose.Words für Java erkundet. Sie haben gelernt, wie Sie Ihren Dokumenten verschiedene Formen hinzufügen, ihre Eigenschaften bearbeiten und mit SmartArt-Formen arbeiten. Mit diesem Wissen können Sie mühelos optisch ansprechende und interaktive Dokumente erstellen.

## Häufig gestellte Fragen

### Was ist Aspose.Words für Java?

Aspose.Words für Java ist eine Java-Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, ändern und konvertieren können. Sie bietet eine breite Palette an Funktionen und Tools für die Arbeit mit Dokumenten in verschiedenen Formaten.

### Wie kann ich Aspose.Words für Java herunterladen?

 Sie können Aspose.Words für Java von der Aspose-Website herunterladen, indem Sie diesem Link folgen:[Laden Sie Aspose.Words für Java herunter](https://releases.aspose.com/words/java/)

### Welche Vorteile bietet die Verwendung von Dokumentformen?

Dokumentformen fügen Ihren Dokumenten visuelle Elemente und Interaktivität hinzu und machen sie dadurch ansprechender und informativer. Mit Formen können Sie Beschriftungen, Schaltflächen, Bilder, Wasserzeichen und mehr erstellen und so das allgemeine Benutzererlebnis verbessern.

### Kann ich das Erscheinungsbild von Formen anpassen?

Ja, Sie können das Erscheinungsbild von Formen anpassen, indem Sie ihre Eigenschaften wie Größe, Position, Drehung und Füllfarbe anpassen. Aspose.Words für Java bietet umfangreiche Optionen zur Formanpassung.

### Ist Aspose.Words für Java mit SmartArt kompatibel?

Ja, Aspose.Words für Java unterstützt SmartArt-Formen, sodass Sie in Ihren Dokumenten mit komplexen Diagrammen und Grafiken arbeiten können.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
