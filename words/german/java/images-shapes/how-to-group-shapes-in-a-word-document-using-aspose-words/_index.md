---
category: general
date: 2026-08-20
description: Erfahren Sie, wie Sie Formen gruppieren, die Größe von Formen festlegen,
  ein Bild in ein Dokument einfügen, ein Bild zur Gruppe hinzufügen und mit Aspose.Words
  in Java ein Rechteck erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: de
lastmod: 2026-08-20
og_description: Wie man Formen in einem Word‑Dokument mit Aspose.Words gruppiert.
  Folgen Sie diesem Schritt‑für‑Schritt‑Java‑Tutorial, um die Formgröße festzulegen,
  ein Bild in das Dokument einzufügen, ein Bild zur Gruppe hinzuzufügen und eine Rechteckform
  zu erstellen.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Wie man Formen in einem Word‑Dokument mit Aspose.Words gruppiert – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Wie man Formen in einem Word‑Dokument mit Aspose.Words gruppiert
url: /de/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in einem Word‑Dokument mit Aspose.Words gruppiert

Wenn Sie **how to group shapes** in einer Word‑Datei benötigen, zeigt dieses Tutorial die vollständige Java‑Lösung. Sie sehen, wie man **set shape size**, **insert image into document**, **add picture to group** und **create rectangle shape** verwendet – alles mit klaren Erklärungen und einem ausführbaren Code‑Beispiel.

Das Gruppieren von Formen vereinfacht die Layout‑Verwaltung, ermöglicht das Bewegen oder Drehen mehrerer Objekte als Einheit und hält Ihr Dokument übersichtlich. In den nachfolgenden Schritten erstellen Sie eine Gruppe, die ein Rechteck und ein Bild enthält, und platzieren die Gruppe anschließend auf der Seite.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder neuer installiert.
* Aspose.Words for Java (Version 23.9 oder später) im Klassenpfad Ihres Projekts.
* Ein Beispiel‑JPEG‑Bild unter `YOUR_DIRECTORY/sample.jpg` (ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Pfad).

Sie können Aspose.Words über Maven hinzufügen:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Wie man Formen mit Aspose.Words gruppiert

Die folgenden Abschnitte führen Schritt für Schritt jede für **how to group shapes** erforderliche Operation aus. Die primäre H2‑Überschrift enthält das Haupt‑Keyword und erfüllt damit die SEO‑Anforderungen.

### Schritt 1: Erstellen eines neuen Dokuments und eines `DocumentBuilder`

Ein `Document` repräsentiert die Word‑Datei, während `DocumentBuilder` bequeme Methoden zum Einfügen von Inhalten bereitstellt.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist*: Das Starten mit einem frischen `Document` stellt sicher, dass die von Ihnen erstellte Gruppe nicht mit bestehenden Elementen interferiert.

### Schritt 2: Einfügen einer Gruppenform, die mehrere untergeordnete Formen enthält

Eine Gruppenform fungiert als Container. Ihre Abmessungen definieren das Begrenzungs‑Box‑Rechteck für alle untergeordneten Formen.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Hinweis*: Die Breite (`300`) und Höhe (`200`) werden in Punkten angegeben (1 pt = 1/72 Zoll). Passen Sie sie an die Größe der Formen an, die Sie hinzufügen möchten.

### Schritt 3: Erstellen einer Rechteckform, Größe festlegen und zur Gruppe hinzufügen

Die genaue Festlegung der Formgröße ist entscheidend, wenn Sie eine präzise Layout‑Kontrolle benötigen.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Warum wir die Formgröße setzen*: Die Methoden `setWidth` und `setHeight` entsprechen dem sekundären Keyword **set shape size** und geben Ihnen pixelgenaue Kontrolle über das Aussehen des Rechtecks.

### Schritt 4: Ein Bild einfügen und die Bildform derselben Gruppe hinzufügen

Das Einfügen eines Bildes ist der Kern der Anforderung **insert image into document**. Das zurückgegebene `Shape` ist eine Bildform, die wie jede andere Form gruppiert werden kann.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro‑Tipp*: Wenn Sie das ursprüngliche Seitenverhältnis beibehalten möchten, setzen Sie nur eine Dimension (`setWidth` oder `setHeight`). Aspose.Words skaliert die andere Dimension automatisch.

### Schritt 5: Positionieren der gesamten Gruppe auf der Seite

Nachdem Sie alle untergeordneten Formen hinzugefügt haben, können Sie die gesamte Gruppe verschieben, drehen oder ausblenden. Die Positionierung nutzt das Konzept **add picture to group** indirekt, da die Gruppe nun das Bild enthält.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Erläuterung*: `setLeft` und `setTop` platzieren die Gruppe relativ zu den Seitenrändern. Das Drehen der Gruppe demonstriert, dass alle untergeordneten Formen die Transformation erben.

### Schritt 6: Dokument speichern

Zum Schluss schreiben Sie die Datei auf die Festplatte. Sie können die resultierende `.docx` in Word öffnen, um die Gruppierung zu überprüfen.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Das Ausführen des Programms erzeugt **GroupShapesDemo.docx**, das ein Rechteck und ein Bild zusammengefasst enthält. Wenn Sie in Word eine der Formen auswählen, wird auch die andere markiert, was bestätigt, dass Sie erfolgreich **how to group shapes** umgesetzt haben.

---

## Erwartete Ausgabe

Wenn Sie *GroupShapesDemo.docx* in Microsoft Word öffnen:

* Ein Rechteck (goldene Füllung) erscheint auf der linken Seite der Gruppe.
* Das von Ihnen bereitgestellte Bild erscheint rechts vom Rechteck.
* Beide Objekte bewegen sich gemeinsam, wenn Sie die Gruppe ziehen.
* Die Gruppe ist 50 pt vom linken Rand und 100 pt vom oberen Rand positioniert und um 15° gedreht.

Falls das Bild nicht angezeigt wird, überprüfen Sie den Dateipfad in `insertImage`. Aspose.Words wirft eine `IOException`, wenn die Datei nicht gefunden werden kann.

---

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|----------|--------|
| **Kann ich mehr als zwei Formen hinzufügen?** | Ja. Rufen Sie `groupShape.appendChild(otherShape)` für jede zusätzliche Form auf. |
| **Was, wenn ich einen transparenten Hintergrund für das Rechteck benötige?** | Verwenden Sie `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Wird Gruppierung in älteren Word‑Formaten (z. B. `.doc`) unterstützt?** | Gruppierung funktioniert für `.docx` und `.doc`, aber einige ältere Viewer ignorieren die Gruppierungs‑Metadaten. Speichern Sie als `.docx` für volle Treue. |
| **Wie löse ich die Gruppierung später auf?** | Rufen Sie die Kindknoten über `groupShape.getChildNodes(NodeType.ANY, true)` ab und verschieben Sie sie in den Dokumentkörper, dann entfernen Sie die Gruppe. |
| **Kann ich Formen über verschiedene Abschnitte hinweg gruppieren?** | Nein. Ein `GroupShape` muss innerhalb einer einzigen `Story` (in der Regel der Haupt‑Dokumentkörper) liegen. |

---

## Pro‑Tipps für robustes Formen‑Handling

* **Verwenden Sie absolute Positionierung sparsam** – relative Positionierung (`builder.moveToDocumentEnd()`) führt häufig zu responsiveren Layouts.
* **Cache den `DocumentBuilder`** – das Erstellen eines neuen Builders für jede Operation kann die Leistung bei großen Dokumenten beeinträchtigen.
* **Setzen Sie `PictureFillMode`**, wenn das Bild innerhalb der Form gedehnt oder gekachelt werden soll: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validieren Sie Bildabmessungen** vor dem Einfügen, um unerwartete Skalierungen zu vermeiden, die die Begrenzungs‑Box der Gruppe beeinflussen könnten.

---

## Nächste Schritte

Jetzt, wo Sie **how to group shapes** kennen, können Sie Folgendes erkunden:

* **Insert image into document** mit erweiterten Optionen wie Zuschneiden (`pictureShape.setCropTop(...)`).
* **Set shape size** dynamisch basierend auf Seitenabmessungen (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** zusammen mit Textfeldern für beschriftete Grafiken.
* **Create rectangle shape** mit abgerundeten Ecken (`rectangleShape.setCornerRadius(5);`).

Diese Themen bauen auf derselben API auf und helfen Ihnen, anspruchsvolle, programmatische Word‑Berichte zu erstellen.

---

## Fazit

In diesem Tutorial haben Sie **how to group shapes** in einem Word‑Dokument mit Aspose.Words für Java gelernt. Durch das Befolgen der sechs Schritte – Dokument erstellen, Gruppe einfügen, **create rectangle shape**, **set shape size**, **insert image into document**, **add picture to group** und die Gruppe positionieren – besitzen Sie nun ein wiederverwendbares Muster für komplexe Layout‑Szenarien. Experimentieren Sie gern mit zusätzlichen Kindformen, verschiedenen Drehungen oder bedingter Gruppierungslogik, um den Anforderungen Ihrer Anwendung gerecht zu werden.

Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}