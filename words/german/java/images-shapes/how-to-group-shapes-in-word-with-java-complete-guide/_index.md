---
category: general
date: 2026-10-16
description: Erfahren Sie, wie Sie Formen in Word mit Java gruppieren. Dieses Tutorial
  zeigt, wie man ein Rechteck hinzufügt, die Größe und Abmessungen der Form festlegt
  und das Dokument speichert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: de
lastmod: 2026-10-16
og_description: Formen in Word mit Java gruppieren. Rechteck hinzufügen, Größe und
  Abmessungen festlegen und professionelle Dokumente programmgesteuert erstellen.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Formen in Word mit Java gruppieren – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Wie man Formen in Word mit Java gruppiert – vollständige Anleitung
url: /de/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So gruppieren Sie Formen in Word mit Java – vollständige Anleitung

Wenn Sie **Formen in Word** programmgesteuert **gruppieren** müssen, bietet Ihnen dieses Tutorial eine sofort einsatzbereite Lösung. Sie sehen, wie Sie **ein Rechteck hinzufügen**, seine Größe anpassen, Formabmessungen festlegen und schließlich eine DOCX‑Datei speichern, die ein gruppiertes Rechteck und eine Ellipse enthält.

Das Gruppieren von Formen in Word ist nützlich, um komplexe Diagramme zu erstellen, wiederverwendbare Grafikkomponenten zu bauen oder einfach zusammengehörige Objekte beizubehalten, wenn das Dokument später bearbeitet wird. Der Code verwendet die Aspose.Words for Java‑Bibliothek, die mit jedem aktuellen JDK funktioniert und nicht erfordert, dass Microsoft Word installiert ist.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

| Anforderung | Grund |
|-------------|-------|
| Java 17 (oder neuer) | Die Bibliothek richtet sich an moderne Java‑Laufzeiten. |
| Aspose.Words for Java (neueste Version) | Stellt die im Beispiel verwendeten Klassen `Document`, `DocumentBuilder`, `GroupShape` und `Shape` bereit. |
| Eine IDE oder ein Build‑Tool (Maven/Gradle) | Zum Kompilieren und Ausführen des Beispiels. |
| Grundkenntnisse der Java‑Syntax | Erforderlich, um den Codeablauf zu verstehen. |

Fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrem Projekt hinzu. Für Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Oder für Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Überblick über die Lösung

Das Tutorial folgt einem klaren **Problem → Lösung → Erklärung**‑Muster:

1. **Erstellen Sie ein neues Word‑Dokument** und erhalten Sie einen `DocumentBuilder`.  
2. **Fügen Sie einen `GroupShape`‑Container** ein, der mehrere Formen enthält.  
3. **Fügen Sie ein Rechteck hinzu**, setzen Sie seine Breite/Höhe (der Schritt **set shape size**), und hängen Sie es an die Gruppe an.  
4. **Fügen Sie eine Ellipse hinzu**, positionieren Sie sie innerhalb derselben Gruppe und setzen Sie ebenfalls ihre Abmessungen.  
5. **Speichern** Sie das Dokument auf dem Datenträger.

Jeder Schritt enthält das **Warum** des Codes, sodass Sie verstehen, was die API tut und wie Sie sie an andere Szenarien anpassen können.

## Schritt 1: Erstellen des Dokuments und eines DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Warum das wichtig ist:** `Document` repräsentiert die gesamte DOCX‑Datei, während `DocumentBuilder` ein Hilfswerkzeug ist, das das Einfügen von Inhalten ermöglicht, ohne sich mit der Low‑Level‑Knotenverwaltung befassen zu müssen. Sie zuerst zu erstellen gibt Ihnen eine saubere Leinwand für alle nachfolgenden Form‑Operationen.

## Schritt 2: Einfügen eines GroupShape‑Containers

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Ein `GroupShape` funktioniert wie ein **Ordner** für Zeichenobjekte. Wenn Sie die Gruppe verschieben, drehen oder löschen, folgen alle Kindformen automatisch. Das ist das Kernprinzip von **group shapes in word**.

## Schritt 3: Hinzufügen einer Rechteckform – der Rechteck‑Code

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Der `Shape`‑Konstruktor erhält `ShapeType.RECTANGLE`, was Aspose.Words anweist, eine rechteckige Kontur zu rendern.  
- **set shape size** – `setWidth` und `setHeight` definieren die **Formabmessungen** in Punkten (1 pt = 1/72 in). Dies ist die gängigste Methode, die visuelle Größe zu steuern.  
- **Why we use `appendChild`** – Es fügt das Rechteck dem `GroupShape` hinzu, sodass es zusammen mit der Gruppe bewegt wird.

## Schritt 4: Hinzufügen einer Ellipse und Positionierung innerhalb der Gruppe

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

Die Ellipse demonstriert **set shape dimensions** über ein einfaches Rechteck hinaus. Durch Aufruf von `setLeft` steuern wir den horizontalen Versatz innerhalb der Gruppe, was beim Anordnen mehrerer Objekte nützlich ist.

## Schritt 5: Dokument speichern

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Wenn Sie *GroupShapeDemo.docx* in Microsoft Word öffnen, sehen Sie ein Rechteck und eine Ellipse, die zusammen in einer einzigen Gruppe gesperrt sind. Das Auswählen einer der Formen wählt die gesamte Gruppe aus – genau das, was Sie von **group shapes in word** erwarten.

## Vollständiges, ausführbares Beispiel

Wenn Sie alle Teile zusammenfügen, finden Sie hier die komplette Quelldatei, die Sie in Ihre IDE kopieren können:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Erwartete Ausgabe

- Eine Datei namens **GroupShapeDemo.docx** erscheint im Projektordner.  
- Beim Öffnen der Datei in Word werden zwei Formen (ein Rechteck und eine Ellipse) angezeigt, die zusammen gruppiert sind.  
- Das Ziehen einer der Formen bewegt die gesamte Gruppe und bestätigt, dass **group shapes in word** wie beabsichtigt funktioniert.

## Häufige Variationen und Sonderfälle

| Szenario | Was zu ändern ist | Warum |
|----------|-------------------|-------|
| **Different shape types** (z.B. Dreieck) | Verwenden Sie `ShapeType.TRIANGLE` oder einen anderen Enum‑Wert beim Erzeugen von `Shape`. | Ermöglicht das Erstellen komplexerer Diagramme. |
| **Setting fill color** | Rufen Sie nach dem Erstellen der Form `shape.getFillColor().setColor(Color.BLUE);` auf. | Verbessert das visuelle Erscheinungsbild, ohne die Gruppierung zu beeinflussen. |
| **Rotating the group** | `groupShape.setRotationAngle(45);` | Dreht alle Kindformen zusammen, nützlich für Symbole. |
| **Adding text inside a shape** | `shape.appendChild(new Paragraph(document));` und fügen Sie anschließend einen `Run` mit Text hinzu. | Lässt die Form wie ein Etikett oder Hinweis wirken. |
| **Saving to a stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Nützlich für Web‑Services, die das Dokument direkt zurückgeben. |

### Profi‑Tipp

Wenn Sie **set shape dimensions** basierend auf dynamischen Daten (z.B. einer Barcode‑Länge) festlegen müssen, berechnen Sie zuerst die Breite/Höhe in Punkten:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## Fazit

Sie wissen jetzt, wie Sie **group shapes in Word** mit Java **gruppieren**, wie Sie **add rectangle shape** hinzufügen und wie Sie **set shape size** und **set shape dimensions** mit prägnantem, produktionsreifem Code festlegen. Wenn Sie die obigen Schritte befolgen, können Sie wiederverwendbare Grafikgruppen erstellen, sie in automatisierten Berichten einbetten oder benutzerdefinierte Diagramm‑Tools bauen, ohne Word manuell zu öffnen.

### Was kommt als Nächstes?

- Erkunden Sie **add rectangle shape**‑Varianten wie abgerundete Ecken (`ShapeType.RECTANGLE` mit `setCornerRadius`).  
- Kombinieren Sie **group shapes in word** mit Tabellen oder Diagrammen für umfangreichere Dokumente.  
- Schauen Sie sich die Aspose.Words‑API für **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) an, um zu steuern, wie umgebender Text mit Ihren gruppierten Grafiken interagiert.

Fühlen Sie sich frei zu experimentieren, den **rectangle shape code** anzupassen und Ihre Ergebnisse zu teilen


## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Dokument mit Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rechteckform in Word mit Java erstellen – Vollständige Anleitung](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}