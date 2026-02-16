---
date: 2026-02-16
description: Erfahren Sie, wie Sie ein Textfeld erstellen, ein Wasserzeichen‑Wort
  hinzufügen, mehrere Formen gruppieren, das Seitenverhältnis einer Form festlegen
  und eine Form in einer Tabellenzelle platzieren, indem Sie Aspose.Words für Java
  verwenden.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Wie man ein Textfeld erstellt und Dokumentformen in Aspose.Words für Java verwendet
url: /de/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

 any markdown formatting.

Make sure code block placeholders remain unchanged.

Proceed to final.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwendung von Dokumentformen in Aspose.Words für Java

## Einführung in die Verwendung von Dokumentformen in Aspose.Words für Java

In diesem umfassenden Leitfaden **you’ll learn how to create text box** Objekte und andere leistungsstarke Formen mit Aspose.Words für Java. Formen ermöglichen es Ihnen, Word‑Dokumente mit Callouts, Schaltflächen, Wasserzeichen, SmartArt und mehr zu bereichern – sie visuell ansprechend und interaktiv zu machen. Wir gehen reale Beispiele durch, vom Einfügen eines einfachen Textfelds über das Gruppieren mehrerer Formen, das Festlegen von Seitenverhältnissen bis hin zum Platzieren von Formen in Tabellenzellen.

## Schnelle Antworten
- **Was ist die primäre Methode, um ein Textfeld hinzuzufügen?** Verwenden Sie `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Kann ich Formen zusammen gruppieren?** Ja – erstellen Sie ein `GroupShape` und hängen Sie Kindformen an.
- **Wie sperre oder entsperre ich das Seitenverhältnis einer Form?** Rufen Sie `shape.setAspectRatioLocked(true/false)` auf.
- **Ist es möglich, ein Wasserzeichen mit einer Form hinzuzufügen?** Absolut – fügen Sie ein `Shape` mit `TEXT_PLAIN_TEXT` ein und setzen Sie dessen Füllung/Umrandung.
- **Funktionieren SmartArt‑Diagramme mit Aspose.Words?** Ja – erkennen Sie sie mit `shape.hasSmartArt()` und aktualisieren Sie sie über `shape.updateSmartArtDrawing()`.

## Was ist ein Textfeld und warum **create text box**‑Formen erstellen?

Ein Textfeld ist ein Container, der formatierte Texte, Bilder oder andere Formen enthalten kann. Die Verwendung von **create text box** in Ihrer Automatisierung ermöglicht es Ihnen, schwebende Inhalte an beliebiger Stelle einer Seite zu platzieren, ideal für Anmerkungen, Callouts oder dekorative Elemente, ohne den Hauptdokumentenfluss zu ändern.

## Wie man eine Form hinzufügt

Bevor wir in den Code eintauchen, stellen Sie sicher, dass Aspose.Words für Java in Ihrem Projekt referenziert ist. Wenn Sie es noch nicht hinzugefügt haben, laden Sie die Bibliothek von der offiziellen Seite herunter:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Formen zu Dokumenten hinzufügen

## Wie man mehrere Formen gruppiert

Ein `GroupShape` ermöglicht es, mehrere einzelne Formen als eine Einheit zu behandeln – nützlich, um sie gemeinsam zu verschieben oder zu drehen.

### Einfügen eines GroupShape

Im Folgenden finden Sie ein vollständiges Beispiel, das eine Gruppe erstellt, zwei verschiedene Formen hinzufügt und die Gruppe in das Dokument einfügt.

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

## Wie man ein Textfeld erstellt (create text box)

### Einfügen einer Textfeld‑Form

Die Methode `insertShape` macht das Hinzufügen eines Textfelds unkompliziert. Das nachstehende Beispiel zeigt zwei Möglichkeiten, ein Textfeld zu positionieren und zu drehen.

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

## Wie man das Seitenverhältnis einer Form festlegt

### Verwalten des Seitenverhältnisses

Manchmal muss eine Form gedehnt werden, ohne ihr ursprüngliches Verhältnis beizubehalten. Der folgende Codeausschnitt demonstriert das Entsperren des Seitenverhältnisses einer Bildform.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Wie man eine Form in einer Tabellenzelle platziert

### Platzieren einer Form in einer Tabellenzelle

Im Folgenden finden Sie ein Schritt‑für‑Schritt‑Beispiel, das eine Tabelle erstellt und anschließend eine Wasserzeichen‑Form einfügt, die relativ zur Seite positioniert ist, aber auch in einer Zelle platziert werden kann.

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

## Arbeiten mit SmartArt‑Formen

### Erkennen von SmartArt‑Formen

Sie können programmgesteuert SmartArt‑Objekte in einem Dokument mit der Methode `hasSmartArt()` finden.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualisieren von SmartArt‑Zeichnungen

Nachdem Sie SmartArt‑Formen gefunden haben, können Sie deren interne Zeichnungsdaten mit `updateSmartArtDrawing()` aktualisieren.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Fazit

In diesem Leitfaden haben wir behandelt, wie man **create text box**‑Objekte erstellt, mehrere Formen gruppiert, Seitenverhältnisse anpasst, Formen in Tabellenzellen einbettet, Wasserzeichen hinzufügt und mit SmartArt‑Diagrammen unter Verwendung von Aspose.Words für Java arbeitet. Diese Techniken befähigen Sie, programmgesteuert reich formatierte, interaktive Word‑Dokumente zu erstellen.

## FAQ

### Was ist Aspose.Words für Java?

Aspose.Words für Java ist eine Java‑Bibliothek, die Entwicklern ermöglicht, Word‑Dokumente programmgesteuert zu erstellen, zu ändern und zu konvertieren. Sie bietet eine breite Palette von Funktionen und Werkzeugen für die Arbeit mit Dokumenten in verschiedenen Formaten.

### Wie kann ich Aspose.Words für Java herunterladen?

Sie können Aspose.Words für Java von der Aspose‑Website herunterladen, indem Sie diesem Link folgen: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Was sind die Vorteile der Verwendung von Dokumentformen?

Dokumentformen fügen Ihren Dokumenten visuelle Elemente und Interaktivität hinzu, wodurch sie ansprechender und informativer werden. Mit Formen können Sie Callouts, Schaltflächen, Bilder, Wasserzeichen und mehr erstellen und so das Gesamterlebnis des Benutzers verbessern.

### Kann ich das Aussehen von Formen anpassen?

Ja, Sie können das Aussehen von Formen anpassen, indem Sie deren Eigenschaften wie Größe, Position, Drehung und Füllfarbe ändern. Aspose.Words für Java bietet umfangreiche Optionen zur Form‑Anpassung.

### Ist Aspose.Words für Java mit SmartArt kompatibel?

Ja, Aspose.Words für Java unterstützt SmartArt‑Formen, sodass Sie mit komplexen Diagrammen und Grafiken in Ihren Dokumenten arbeiten können.

## Häufig gestellte Fragen

**Q: Kann ich ein Textfeld mit einem Bild innerhalb derselben Form kombinieren?**  
A: Ja. Fügen Sie nach dem Erstellen der Form ein Bild in das Textfeld‑Shape ein, indem Sie `builder.insertImage()` verwenden, und passen Sie anschließend das Layout nach Bedarf an.

**Q: Wie stelle ich sicher, dass ein Wasserzeichen hinter allen Dokumentinhalten erscheint?**  
A: Setzen Sie den `WrapType` der Form auf `NONE` und passen Sie `RelativeHorizontalPosition` sowie `RelativeVerticalPosition` auf `PAGE` an. Dadurch wird das Wasserzeichen hinter dem Hauptfluss positioniert.

**Q: Ist es möglich, eine gruppierte Form in Word zu animieren?**  
A: Während Aspose.Words Formen erstellen und gruppieren kann, werden Animationsfunktionen nicht unterstützt, da sie von den UI‑Möglichkeiten von Word abhängen.

**Q: Welche Version von Aspose.Words ist für SmartArt‑Unterstützung erforderlich?**  
A: Die Erkennung und Aktualisierung von SmartArt ist ab Aspose.Words 20.9 für Java und später verfügbar.

**Q: Handhabt die Bibliothek große Dokumente mit vielen Formen effizient?**  
A: Ja. Verwenden Sie `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` oder höher, um die Leistung bei Dokumenten mit vielen Formen zu verbessern.

---

**Zuletzt aktualisiert:** 2026-02-16  
**Getestet mit:** Aspose.Words für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}