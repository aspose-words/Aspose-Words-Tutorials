---
category: general
date: 2026-11-15
description: Erstelle ein Rechteck in Word mit Java und lerne, wie man Formen zu Word
  hinzufügt, die Formabmessungen festlegt und das Word‑Dokument effizient speichert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: de
lastmod: 2026-11-15
og_description: Erstelle ein Rechteck in einem Word-Dokument mit Java. Lerne, Formen
  zu Word hinzuzufügen, die Formabmessungen festzulegen und das Word-Dokument in wenigen
  Minuten zu speichern.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Rechteckform in Word mit Java erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Erstelle ein Rechteck in einem Word-Dokument mit Java
url: /de/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in einem Word-Dokument mit Java erstellen

Wenn Sie **eine Rechteckform** in einer Word-Datei erstellen müssen, zeigt Ihnen diese Anleitung genau, wie Sie dies mit Java tun. Sie sehen, wie Sie **Formen zu Word hinzufügen**, die **Formabmessungen festlegen** steuern und schließlich **das Word-Dokument speichern**, ohne Ihre IDE zu verlassen.

In den folgenden Abschnitten erhalten Sie ein vollständiges, ausführbares Beispiel, eine Erklärung jeder Zeile und Tipps zu häufigen Fallstricken wie Größenproblemen und Dokumentenkompatibilität. Es werden keine externen Referenzen benötigt – nur die Aspose.Words for Java-Bibliothek.

## Was Sie lernen werden

* Wie man ein `Document` und einen `DocumentBuilder` initialisiert.
* Wie man eine **Gruppenform** einfügt und ein Rechteck darin platziert.
* Wie man **die Formgröße definiert** mit `setWidth` und `setHeight`.
* Wie man **das Word-Dokument speichert** im `.docx`-Format.
* Umgang mit Randfällen für verschiedene Seitengrößen und DPI-Einstellungen.

### Voraussetzungen

* Java 17 oder neuer (der Code kompiliert auch mit Java 8).
* Aspose.Words for Java 23.10 oder neuer – Sie können es von Maven Central beziehen.
* Ein grundlegendes Verständnis von Java-Syntax und objektorientierten Konzepten.

> **Profi‑Tipp:** Wenn Sie später weitere Formen hinzufügen möchten (z. B. Kreise oder Textfelder), behalten Sie sie in derselben `GroupShape`. Das erleichtert das Verschieben, Drehen oder Formatieren der gesamten Sammlung erheblich.

## Schritt 1: Dokument und Builder initialisieren

Der erste Schritt besteht darin, eine leere Word-Datei und einen `DocumentBuilder` zu erstellen, der Ihnen das Schreiben von Inhalten ermöglicht.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum das wichtig ist:* Ein `Document` repräsentiert die gesamte Datei, während `DocumentBuilder` hoch‑level Methoden zum Einfügen von Text, Tabellen und **Formen** bereitstellt. Ohne den Builder müssten Sie niedrige Knoten manuell manipulieren.

## Schritt 2: Eine Gruppenform einfügen, um mehrere Formen zu halten

Eine **Gruppenform** wirkt wie ein Container; Sie können mehrere Formen hinzufügen und später als ein einzelnes Objekt behandeln (z. B. zusammen verschieben oder drehen).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Warum eine Gruppenform verwenden?* Wenn Sie später Pfeile, Kreise oder Beschriftungen um das Rechteck hinzufügen, hält die Gruppe alles ausgerichtet. Sie vereinfacht zudem den **add shapes to Word**‑Workflow, weil Sie nur einen Aufruf von `appendChild` für jede neue Form benötigen.

## Schritt 3: Das Rechteck erstellen

Jetzt erstellen wir das eigentliche Rechteck, das innerhalb der Gruppe liegen wird. Der `Shape`‑Konstruktor benötigt das zugehörige `Document` und den gewünschten Formtyp.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Warum ein Rechteck?* `ShapeType.RECTANGLE` ist das am häufigsten verwendete Primitive zum Hervorheben von Abschnitten, Erstellen von Platzhaltern oder Zeichnen einfacher UI‑Mock‑Ups direkt in Word.

## Schritt 4: Größe des Rechtecks festlegen

Das Festlegen der Abmessungen ist der Punkt, an dem **set shape dimensions** wichtig wird. Sie können jede von Aspose.Words unterstützte Maßeinheit verwenden; standardmäßig sind es Punkte (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Hinweis:** Wenn Sie Millimeter bevorzugen, rufen Sie `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` auf, wobei `1.39 in ≈ 35 mm`. Das demonstriert die **define shape size**‑Flexibilität.

## Schritt 5: Das Rechteck zur Gruppenform hinzufügen

Das Anhängen des Rechtecks an die zuvor erstellte Gruppe lässt es im Dokument erscheinen.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

An diesem Punkt ist das Rechteck in der oberen linken Ecke der Gruppe positioniert. Sie können es später mit `rectangle.setLeft(...)` und `rectangle.setTop(...)` verschieben, falls Sie eine präzise Platzierung benötigen.

## Schritt 6: (Optional) Dokument speichern, um das Ergebnis zu sehen

Abschließend schreiben Sie das Dokument auf die Festplatte. Dies ist der **save Word document**‑Schritt, der eine `.docx`‑Datei erzeugt, die Sie in Microsoft Word, LibreOffice oder Google Docs öffnen können.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Das Ausführen des Programms erzeugt `RectangleShapeDemo.docx`, das ein einzelnes Rechteck innerhalb einer Gruppenform enthält. Beim Öffnen der Datei sehen Sie ein schlichtes weißes Rechteck – exakt in der von Ihnen definierten Größe.

### Erwartete Ausgabe

* Eine Word-Datei namens `RectangleShapeDemo.docx`.
* Im ersten Absatz eine Gruppenform, die ein 100 pt × 50 pt‑Rechteck enthält.
* Kein Text wurde hinzugefügt, sodass das Rechteck auf einer leeren Seite erscheint.

## Häufige Variationen und Randfälle

| Situation | Wie man den Code anpasst |
|-----------|--------------------------|
| **Andere Seitengröße** (z. B. A4) | Rufen Sie `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` auf, bevor Sie die Form einfügen. |
| **Höhere DPI für den Druck** | Multiplizieren Sie Breite/Höhe mit dem gewünschten DPI‑Faktor, z. B. `rectangle.setWidth(200 * 2);` für doppelte Auflösung. |
| **Textbeschriftung innerhalb des Rechtecks hinzufügen** | Erstellen Sie ein `Shape` vom Typ `TEXT_BOX`, setzen Sie dessen `setWidth`/`setHeight` auf die Größe des Rechtecks und fügen Sie es derselben `GroupShape` hinzu. |
| **Das Rechteck drehen** | Verwenden Sie `rectangle.setRotationAngle(45);`, um das Rechteck um 45 Grad im Uhrzeigersinn zu drehen. |
| **Als PDF statt DOCX speichern** | Ersetzen Sie `document.save("output.docx");` durch `document.save("output.pdf");` – dieselbe API funktioniert für PDF und erhält das Rechteck. |

## Profi‑Tipps für eine robuste Implementierung

1. **Builder wiederverwenden** – nach dem Einfügen der Gruppenform können Sie weiterhin Absätze oder Tabellen hinzufügen, ohne eine neue Builder‑Instanz zu erstellen.
2. **Ressourcen freigeben** – obwohl der Java‑Garbage‑Collector die meisten Objekte verwaltet, verhindert ein expliziter Aufruf von `document.close();` (bei Verwendung von Streams) Dateihandle‑Lecks.
3. **Abmessungen validieren** – bevor Sie `setWidth`/`setHeight` aufrufen, stellen Sie sicher, dass die Werte positiv sind; negative Werte werfen eine `IllegalArgumentException`.
4. **Versionskompatibilität** – der Code funktioniert mit Aspose.Words 23.x und neuer. Ältere Versionen könnten `Shape.setSize(width, height)` anstelle separater Setter benötigen.

## Vollständiges, ausführbares Beispiel

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Ergebnisprüfung:** Öffnen Sie `output/RectangleShapeDemo.docx` in Microsoft Word. Sie sollten ein Rechteck der angegebenen Größe oben in der Mitte der ersten Seite sehen. Wenn das Rechteck zu klein erscheint, passen Sie die an `setWidth` und `setHeight` übergebenen Werte an.

## Fazit

Sie wissen nun, wie Sie **eine Rechteckform** in einer Word-Datei mit Java erstellen, wie Sie **Formen zu Word hinzufügen** über eine `GroupShape`, wie Sie **Formabmessungen festlegen** und **die Formgröße definieren**, und schließlich, wie Sie **das Word-Dokument speichern** für die weitere Verteilung. Das gleiche Muster funktioniert für andere Formtypen und ermöglicht Ihnen, komplexe Diagramme programmgesteuert zu erstellen.

### Was kommt als Nächstes?

* Erkunden Sie **add shapes to Word**, indem Sie Kreise, Pfeile oder Textfelder einfügen.
* Kombinieren Sie mehrere Formen zu einer einzigen `GroupShape` und wenden Sie Transformationen an (drehen, spiegeln).
* Erzeugen Sie Berichte, die Diagramme als Formen einbetten, und speichern Sie das **Word-Dokument** anschließend als PDF zum Teilen.

Experimentieren Sie gern mit den Abmessungen, Farben und Positionen, um sie an Ihr konkretes Szenario anzupassen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument mit Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rechteckform in Java-Word-Dokument erstellen – Vollständige Schritt‑für‑Schritt‑Anleitung](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Word-Dokument mit Java erstellen – Form ausblenden und Füllfarbe setzen](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}