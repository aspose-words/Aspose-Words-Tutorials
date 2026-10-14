---
category: general
date: 2026-10-13
description: Erfahren Sie, wie Sie gruppierte Formen in Word mit Java erstellen. Dieser
  Leitfaden zeigt Ihnen, wie Sie eine Gruppenform einfügen, eine Linie zur Gruppe
  hinzufügen und mehrere Formen im gesamten Dokument gruppieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: de
lastmod: 2026-10-13
og_description: Erstelle gruppierte Formen in Word mit Java. Folge diesem vollständigen
  Tutorial, um eine Gruppierung von Formen einzufügen, eine Linie zur Gruppe hinzuzufügen
  und mehrere Formen in Word‑Dokumenten zu gruppieren.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Gruppierte Formen in Word mit Java erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Wie man gruppierte Formen in einem Word‑Dokument mit Java erstellt
url: /de/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man gruppierte Formen in einem Word‑Dokument mit Java erstellt

Wenn Sie **gruppierte Formen** in einer Microsoft‑Word‑Datei aus Java erstellen müssen, führt Sie dieses Tutorial durch den gesamten Prozess. Sie sehen, wie Sie **group shape einfügen**, ein Rechteck und eine Linie im selben Container platzieren und schließlich das Dokument mit den gruppierten Grafiken speichern.

Das Gruppieren von Formen erleichtert das Verschieben, Skalieren oder Stylen mehrerer Zeichenobjekte als eine Einheit – perfekt für Diagramme, Flussdiagramme oder benutzerdefinierte Seiten­dekorationen. Am Ende dieses Leitfadens können Sie **add line to group**, **group multiple shapes word** Dokumente hinzufügen und dieselbe Technik für beliebig viele Formen wiederverwenden.

## Voraussetzungen

- Java 17 oder neuer, installiert auf Ihrem Entwicklungsrechner.  
- Eine Aspose.Words for Java‑Lizenz (oder eine kostenlose Evaluation).  
- Ein Maven‑ oder Gradle‑Projekt, in dem Sie die Aspose.Words‑Abhängigkeit hinzufügen können:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Keine zusätzlichen Bibliotheken sind erforderlich.

## Schritt 1: Das group‑Shape‑Container einfügen

Der erste Schritt besteht darin, **group shape** in das Dokument **einzufügen**. Dieser Container hält jede nachfolgende Form.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` erzeugt ein leeres `Shape`‑Objekt vom Typ `GROUPSHAPE`. Denken Sie daran wie an eine transparente Leinwand, die andere Zeichenobjekte enthalten kann.

## Schritt 2: Ein Rechteck zur Gruppe hinzufügen

Ein Rechteck dient häufig als visueller Hintergrund für eine Gruppe von Formen.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Durch das Setzen von `Left` und `Top` auf `0` wird das Rechteck in der oberen linken Ecke der Gruppe positioniert. Sie können diese Werte ändern, um die Form innerhalb der Gruppe zu versetzen.

## Schritt 3: **Add line to group** – eine Linienform erstellen

Jetzt **add line to group**. Die Linie erscheint unter dem Rechteck.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Die Eigenschaft `Top` verschiebt die Linie 60 Punkte unter das Rechteck und erzeugt ein einfaches gestapeltes Layout. Sie könnten auch `Left` setzen, falls ein horizontaler Versatz nötig ist.

## Schritt 4: Das Dokument mit den gruppierten Formen speichern

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Wenn Sie `GroupShapeDemo.docx` in Microsoft Word öffnen, sehen Sie eine einzige Gruppe, die sowohl das Rechteck als auch die Linie enthält. Das Auswählen der Gruppe ermöglicht das gleichzeitige Verschieben beider Formen, was zeigt, dass Sie **group multiple shapes word** erfolgreich umgesetzt haben.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm mit allen Imports und Fehlerbehandlung. Kopieren Sie es in Ihre IDE, ersetzen Sie `YOUR_DIRECTORY` durch einen existierenden Ordnerpfad und führen Sie es aus.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Erwartete Ausgabe

- Eine Datei namens `GroupShapeDemo.docx` erscheint im Zielordner.  
- Beim Öffnen der Datei in Word wird ein einzelnes gruppiertes Objekt angezeigt, das ein Rechteck oben und eine Linie darunter enthält.  
- Das Ziehen der Gruppe bewegt beide Formen zusammen, was bestätigt, dass Sie **created grouped shapes** erfolgreich erstellt haben.

## Tipps und häufige Stolperfallen

- **Pro‑Tipp:** Wenn Sie einzelne Formen innerhalb der Gruppe drehen oder stylen müssen, rufen Sie die jeweiligen Setter (`setRotation`, `getFill().setForeColor` usw.) **vor** dem Anhängen an die Gruppe auf. Die Gruppe bewahrt diese visuellen Eigenschaften.
- **Achten Sie darauf:** Das Vergessen, die `Top`‑Eigenschaft für die Linie zu setzen, kann dazu führen, dass sie das Rechteck überlappt und die Gruppe unordentlich wirkt.
- **Randfall:** Wenn Sie mehr als zwei Formen hinzufügen, denken Sie daran, dass die Koordinaten jedes Kindes relativ zum Ursprung der Gruppe (0,0) sind. Planen Sie das Layout entsprechend.
- **Performance‑Hinweis:** Das Gruppieren einer großen Anzahl von Formen (Hunderte) kann die Dateigröße leicht erhöhen, vereinfacht jedoch die nachträgliche Bearbeitung in Word.

## Wie man **group multiple shapes word** Dokumente programmgesteuert gruppiert

Das oben gezeigte Muster – einen Gruppen‑Container erstellen, jedes Kind‑Shape konfigurieren und anhängen – funktioniert für jede Anzahl von Formen: Kreise, Bilder, Textfelder usw. Wiederholen Sie einfach die Schritte „Shape erstellen → Eigenschaften setzen → anhängen“, bevor Sie `doc.save()` aufrufen.

Falls Sie **add line to group** hinzufügen möchten, nachdem die Gruppe bereits andere Formen enthält, können Sie die bestehende Gruppe folgendermaßen abrufen:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Damit wird gezeigt, dass Sie eine Gruppe jederzeit im Dokumentlebenszyklus modifizieren können.

## Fazit

Sie wissen jetzt, wie man **create grouped shapes** in einem Word‑Dokument mit Java und Aspose.Words erstellt. Durch **inserting group shape**, **adding line to group** und **group multiple shapes word** können Sie komplexe Zeichnungen bauen, die sich wie ein einzelnes Objekt verhalten – ideal für Diagramme, Vorlagen und automatisierte Berichtserstellung.

Als Nächstes können Sie diese verwandten Themen erkunden:

- **Applying styles to grouped shapes** – lernen Sie, wie Sie Füllfarben, Rahmen und Effekte für alle Kinder gleichzeitig festlegen.  
- **Exporting grouped shapes to PDF** – sehen Sie, wie die gleiche Gruppe beim Konvertieren des Dokuments erhalten bleibt.  
- **Animating shapes with VBA** – kombinieren Sie Java‑generierte Gruppen mit Word‑Makros für interaktive Dokumente.

Experimentieren Sie gern mit verschiedenen Formtypen, Größen und Positionen. Das Gruppieren gibt Ihnen die Flexibilität, viele Objekte wie eines zu behandeln, was sowohl den Code als auch die Benutzerinteraktion vereinfacht. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}