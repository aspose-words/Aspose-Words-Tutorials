---
category: general
date: 2026-09-21
description: Erstelle ein Word‑Dokument programmgesteuert mit Java. Lerne, wie man
  Formen in Word gruppiert, ein Rechteck einfügt, die Formgröße festlegt und Formen
  zu einem Word‑Dokument hinzufügt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: de
lastmod: 2026-09-21
og_description: 'Word-Dokument programmgesteuert mit Java erstellen: Dieser Leitfaden
  zeigt, wie man Formen in Word gruppiert, Rechteckformen einfügt, die Größe von Formen
  festlegt und Formen zu einem Word-Dokument hinzufügt.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Word‑Dokument programmgesteuert erstellen, Formen in Java gruppieren
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Word‑Dokument programmgesteuert erstellen, Formen in Java gruppieren
url: /de/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert erstellen, Formen in Java gruppieren

Wenn Sie **ein Word-Dokument programmgesteuert erstellen** müssen, führt Sie diese Anleitung durch eine vollständige Lösung. Sie sehen, wie Sie **Formen in Word gruppieren**, ein Rechteck einfügen, seine Größe festlegen und weitere Formen hinzufügen – alles mit Java und der Aspose.Words for Java-Bibliothek.

Das Tutorial deckt jeden Schritt von der Projektkonfiguration bis zum Speichern der finalen .docx‑Datei ab. Am Ende können Sie ein Word‑Dokument erzeugen, das ein Rechteck und ein Bild enthält, die in einer einzigen Gruppe zusammengefasst sind, sodass sie gemeinsam verschoben oder skaliert werden können. Vorkenntnisse mit der Aspose.Words‑API sind nicht erforderlich, jedoch sollten Sie eine grundlegende Java‑Entwicklungsumgebung besitzen.

## Voraussetzungen

* Java Development Kit (JDK) 8 oder neuer  
* Maven oder Gradle für die Abhängigkeitsverwaltung  
* Aspose.Words for Java 23.9 (oder die neueste Version) – die Bibliothek ist für Evaluierung kostenlos  
* Eine Bilddatei (z. B. `sample.jpg`) in einem bekannten Verzeichnis abgelegt  

Wenn diese Punkte bereitstehen, läuft der Code ohne zusätzliche Konfiguration.

## Schritt 1: Projekt einrichten und Aspose.Words importieren

Erstellen Sie ein Maven‑Projekt (oder fügen Sie die Abhängigkeit zu Ihrer bestehenden `pom.xml` hinzu):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Falls Sie Gradle bevorzugen, fügen Sie Folgendes zu `build.gradle` hinzu:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Nachdem die Abhängigkeit aufgelöst ist, importieren Sie die benötigten Klassen in Ihrer Java‑Quelldatei:

```java
import com.aspose.words.*;
import java.io.File;
```

## Schritt 2: Word-Dokument programmgesteuert erstellen

Der erste Vorgang in jedem Automatisierungsszenario besteht darin, ein `Document`‑Objekt und einen `DocumentBuilder` zu instanziieren. Der Builder vereinfacht das Einfügen von Text, Bildern und Formen.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Zu diesem Zeitpunkt existiert das Dokument nur im Speicher. Sie können nun beginnen, Formen hinzuzufügen.

## Schritt 3: Rechteckform einfügen – wie man ein Rechteck einfügt

Ein Rechteck ist eine grundlegende `Shape` mit `ShapeType.RECTANGLE`. Sie steuern seine Abmessungen mit `setWidth`, `setHeight` und positionieren es mit `setTop` und `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Warum das wichtig ist:** Das explizite Festlegen von Größe und Position (`set shape size word`) stellt sicher, dass das Rechteck genau dort erscheint, wo Sie es erwarten, unabhängig vom Standard‑Layout des Dokuments.

## Schritt 4: Bild einfügen – Formen zum Word-Dokument hinzufügen

Der `DocumentBuilder` kann ein Bild direkt aus einem Dateipfad einfügen. Nach dem Einfügen können Sie das Bild genauso wie jede andere Form neu positionieren.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Sowohl das Rechteck als auch das Bild sind nun unabhängige Formen im Dokument.

## Schritt 5: Formen gruppieren – wie man Formen in Word gruppiert

Formen zu gruppieren ist nützlich, wenn Sie sie als Einheit verschieben oder skalieren möchten. Aspose.Words stellt dafür einen `GroupShape`‑Container bereit.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Wenn die Gruppe gespeichert wird, behandelt Word die beiden Kinder als ein logisches Objekt. Sie können die Gruppe später auswählen und ziehen; sowohl das Rechteck als auch das Bild folgen dann.

## Schritt 6: Dokument speichern

Schreiben Sie schließlich das Dokument auf die Festplatte. Der Pfad muss vom Java‑Prozess beschreibbar sein.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Durch das Ausführen der `main`‑Methode entsteht eine Datei namens **GroupShapeExample.docx**. Öffnen Sie sie in Microsoft Word, um ein Rechteck und ein Bild zu sehen, die zusammen in einer Gruppe gesperrt sind. Das Auswählen der Gruppe ermöglicht das gleichzeitige Verschieben beider Objekte und bestätigt, dass das Gruppieren erfolgreich war.

## Erwartete Ausgabe

* Eine Word‑Datei (`GroupShapeExample.docx`) im von Ihnen angegebenen Verzeichnis.  
* In der Datei erscheint ein Rechteck (hellgraue Füllung) in der oberen linken Ecke, und das Bild befindet sich direkt darunter.  
* Beide Objekte gehören zu einer einzigen Gruppe, sodass das Ziehen eines Objekts das andere bewegt.

## Häufige Varianten und Randfälle

| Situation | Empfehlung |
|-----------|------------|
| **Verschiedene Bildformate** | Aspose.Words unterstützt PNG, BMP, GIF und TIFF. Verwenden Sie die passende Dateierweiterung in `insertImage`. |
| **Negative Abmessungen** | Die API wirft `ArgumentException`. Validieren Sie stets Breite und Höhe, bevor Sie `setWidth` / `setHeight` aufrufen. |
| **Große Dokumente** | Das Gruppieren vieler Formen kann die Dateigröße erhöhen. Ziehen Sie in Betracht, Formen zu einem einzigen Bild zusammenzuführen, wenn die Leistung wichtig ist. |
| **Kompatibilität mit Word-Versionen** | GroupShape funktioniert mit Word 2007 (`.docx`) und später. Für ältere `.doc`‑Dateien wird die Gruppe flachgelegt. |
| **Dynamische Positionierung** | Verwenden Sie Berechnungen basierend auf der Seitengröße (`doc.getFirstSection().getPageSetup().getPageWidth()`), wenn Sie eine adaptive Platzierung benötigen. |

**Pro Tipp:** Nachdem Sie die Gruppe erstellt haben, können Sie ändern

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in dieser Anleitung gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument in Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rechteckform in Word mit Java erstellen – Vollständige Anleitung](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Gruppenform in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}