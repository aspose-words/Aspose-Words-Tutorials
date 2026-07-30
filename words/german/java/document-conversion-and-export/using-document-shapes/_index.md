---
date: 2025-12-14
description: Erfahren Sie, wie Sie **Bildform einfügen** mit Aspose.Words für Java.
  Dieser Leitfaden zeigt Ihnen, wie Sie Formen hinzufügen, Textfeldformen erstellen,
  Formen in Tabellen platzieren, das Seitenverhältnis von Formen festlegen und Hinweisformen
  hinzufügen.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Verwendung von Dokumentformen in Aspose.Words für Java
url: /de/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man **Bildform einfügt** mit Aspose.Words für Java

In diesem umfassenden Tutorial erfahren Sie, wie Sie **Bildform**‑Objekte in Word‑Dokumente mit Aspose.Words für Java einfügen. Egal, ob Sie Berichte, Marketing‑Materialien oder interaktive Formulare erstellen – Formen ermöglichen Ihnen, Callouts, Schaltflächen, Textfelder, Wasserzeichen und sogar SmartArt hinzuzufügen. Wir gehen Schritt für Schritt durch, erklären, warum Sie eine bestimmte Form verwenden würden, und stellen sofort ausführbare Code‑Snippets bereit.

## Schnellantworten
- **Was ist der primäre Weg, eine Form hinzuzufügen?** Verwenden Sie `DocumentBuilder.insertShape` oder erstellen Sie eine `Shape`‑Instanz und fügen Sie sie dem Dokumentbaum hinzu.  
- **Kann ich ein Bild als Form einfügen?** Ja – rufen Sie `builder.insertImage` auf und behandeln Sie das zurückgegebene `Shape` wie jedes andere.  
- **Wie behalte ich das Seitenverhältnis einer Form?** Setzen Sie `shape.setAspectRatioLocked(true)` oder `false`, je nach Bedarf.  
- **Ist es möglich, Formen zu gruppieren?** Absolut – packen Sie sie in ein `GroupShape` und fügen Sie die Gruppe als einzelnen Knoten ein.  
- **Funktionieren SmartArt‑Diagramme mit Aspose.Words?** Ja, Sie können SmartArt‑Formen programmgesteuert erkennen und aktualisieren.

## Was ist **insert image shape**?
Eine *Bildform* ist ein visuelles Element, das Raster‑ oder Vektorgrafiken innerhalb eines Word‑Dokuments enthält. In Aspose.Words wird ein Bild durch ein `Shape`‑Objekt repräsentiert, das Ihnen volle Kontrolle über Größe, Position, Drehung und Textumbruch gibt.

## Warum Formen in Ihren Dokumenten verwenden?
- **Visuelle Wirkung:** Formen lenken die Aufmerksamkeit auf wichtige Informationen.  
- **Interaktivität:** Schaltflächen und Callouts können mit URLs oder Lesezeichen verknüpft werden.  
- **Layout‑Flexibilität:** Positionieren Sie Grafiken präzise mit absoluten oder relativen Koordinaten.  
- **Automatisierung:** Erzeugen Sie komplexe Layouts ohne manuelle Nachbearbeitung.

## Voraussetzungen
- Java Development Kit (JDK 8 oder höher)  
- Aspose.Words für Java Bibliothek (Download von der offiziellen Seite)  
- Grundkenntnisse in Java und objektorientierter Programmierung  

Sie können die Bibliothek hier herunterladen: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Wie man **Form hinzufügt** – Einfügen eines GroupShape
Ein `GroupShape` ermöglicht es, mehrere Formen als eine Einheit zu behandeln. Das ist nützlich, um mehrere Elemente gemeinsam zu verschieben oder zu formatieren.

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

## Erstellen einer **Textfeld‑Form**
Ein Textfeld ist ein Container, der formatierbaren Text aufnehmen kann. Sie können es zudem drehen, um einen dynamischen Look zu erzielen.

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

## **Seitenverhältnis der Form** festlegen
Manchmal soll sich eine Form frei strecken, ein anderes Mal möchten Sie die ursprünglichen Proportionen beibehalten. Das Seitenverhältnis zu steuern ist unkompliziert.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## **Form in Tabelle** platzieren
Das Einbetten einer Form in eine Tabellenzelle kann für Berichtslayouts praktisch sein. Das nachfolgende Beispiel erstellt eine Tabelle und fügt anschließend eine wasserzeichenähnliche Form ein, die die gesamte Seite einnimmt.

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

## **Callout‑Form** hinzufügen
Eine Callout‑Form eignet sich perfekt, um Notizen oder Warnungen hervorzuheben. Während der obige Code bereits ein `ACCENT_BORDER_CALLOUT_1` demonstriert, können Sie den `ShapeType` zu jeder anderen Callout‑Variante ändern, um Ihr Design anzupassen.

## Arbeiten mit SmartArt‑Formen

### SmartArt‑Formen erkennen
SmartArt‑Diagramme können programmgesteuert identifiziert werden, sodass Sie sie bei Bedarf verarbeiten oder ersetzen können.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt‑Grafiken aktualisieren
Sobald sie erkannt wurden, können Sie die SmartArt‑Grafiken aktualisieren, um Änderungen in den zugrunde liegenden Daten widerzuspiegeln.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Häufige Probleme & Tipps
- **Form wird nicht angezeigt:** Stellen Sie sicher, dass die Form nach dem Zielknoten mit `builder.insertNode` eingefügt wird.  
- **Unerwartete Drehung:** Denken Sie daran, dass die Drehung um das Zentrum der Form erfolgt; passen Sie ggf. `setLeft`/`setTop` an.  
- **Seitenverhältnis gesperrt:** Viele Formen sperren standardmäßig ihr Seitenverhältnis; rufen Sie `setAspectRatioLocked(false)` auf, um frei zu strecken.  
- **SmartArt‑Erkennung schlägt fehl:** Vergewissern Sie sich, dass Sie eine Aspose.Words‑Version verwenden, die SmartArt unterstützt (v24+).

## Häufig gestellte Fragen

**F: Was ist Aspose.Words für Java?**  
A: Aspose.Words für Java ist eine Java‑Bibliothek, die Entwicklern ermöglicht, Word‑Dokumente programmgesteuert zu erstellen, zu ändern und zu konvertieren. Sie bietet eine breite Palette an Funktionen und Werkzeugen für die Arbeit mit Dokumenten in verschiedenen Formaten.

**F: Wie kann ich Aspose.Words für Java herunterladen?**  
A: Sie können Aspose.Words für Java von der Aspose‑Website über diesen Link herunterladen: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**F: Welche Vorteile bieten Dokumentformen?**  
A: Dokumentformen fügen Ihren Dokumenten visuelle Elemente und Interaktivität hinzu, wodurch sie ansprechender und informativer werden. Mit Formen können Sie Callouts, Schaltflächen, Bilder, Wasserzeichen und mehr erstellen und so das Gesamterlebnis verbessern.

**F: Kann ich das Aussehen von Formen anpassen?**  
A: Ja, Sie können das Aussehen von Formen anpassen, indem Sie Eigenschaften wie Größe, Position, Drehung und Füllfarbe ändern. Aspose.Words für Java bietet umfangreiche Optionen zur Form‑Anpassung.

**F: Ist Aspose.Words für Java mit SmartArt kompatibel?**  
A: Ja, Aspose.Words für Java unterstützt SmartArt‑Formen, sodass Sie komplexe Diagramme und Grafiken in Ihren Dokumenten verwenden können.

---

**Zuletzt aktualisiert:** 2025-12-14  
**Getestet mit:** Aspose.Words für Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}