---
category: general
date: 2026-07-29
description: Erstelle ein Word-Dokument in Java mit Aspose.Words. Lerne, ein Rechteck-Shape
  einzufügen, Shapes in Word zu gruppieren und das Dokument schnell als DOCX zu speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: de
lastmod: 2026-07-29
og_description: Erstellen Sie ein Word-Dokument in Java mit Aspose.Words. Fügen Sie
  eine Rechteckform ein, gruppieren Sie Formen in Word und speichern Sie das Dokument
  innerhalb von Minuten als DOCX.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Word-Dokument mit Formen erstellen – Java Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Word-Dokument mit Formen in Java erstellen – Vollständige Aspose.Words-Anleitung
url: /de/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument mit Formen in Java erstellen – Vollständige Aspose.Words-Anleitung

Haben Sie sich jemals gefragt, wie man **create word document** programmgesteuert erstellt und mit benutzerdefinierten Grafiken versieht? Sie sind nicht allein. Egal, ob Sie einen Bericht mit hervorgehobenen Abschnitten generieren oder im Handumdrehen einen Flyer entwerfen müssen, das Beherrschen der Formenbearbeitung in Word kann Ihnen Stunden manueller Arbeit ersparen.

In diesem Tutorial gehen wir die genauen Schritte durch, um **create word document** mit Aspose.Words für Java zu **insert rectangle shape**, **group shapes in Word** zu verwenden und schließlich **save document as docx** zu erledigen. Am Ende haben Sie ein vollständig ausführbares Beispiel, das Sie in jedes Projekt einbinden können.

## Was Sie am Ende haben werden

- Eine frische Word-Datei, die vollständig aus Java-Code generiert wird.  
- Zwei unterschiedliche Formen (ein Rechteck und eine Ellipse) zur Seite hinzugefügt.  
- Diese Formen werden mit der **group shapes in word** API zusammengefasst, sodass sie sich wie ein einzelnes Objekt verhalten.  
- Die Datei wird auf der Festplatte als Standard-`.docx` gespeichert, das sich ohne Probleme in Microsoft Word öffnen lässt.  

Keine externen Werkzeuge, keine umständlichen XML‑Hacks – nur sauberer, typisierter Java‑Code und Aspose.Words.

---

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

1. **Java Development Kit (JDK) 8 oder neuer** – der Code zielt auf Java 8+ ab.  
2. **Aspose.Words for Java** JAR (Sie können die neueste Version aus dem Maven Central Repository beziehen).  
3. Eine einfache IDE (IntelliJ IDEA, Eclipse oder sogar ein einfacher Texteditor).  

Wenn Sie das alles haben, großartig – lassen Sie uns loslegen.

---

## Schritt‑für‑Schritt‑Implementierung

Im Folgenden zerlegen wir den Prozess in handliche Schritte. Jeder Schritt enthält ein Code‑Snippet, eine kurze Erklärung und einen Tipp, den Sie in der offiziellen Dokumentation vielleicht nicht finden.

### ## Word-Dokument mit Formen mit Aspose.Words erstellen

Das Erste, was Sie benötigen, ist eine leere Word‑Datei, mit der Sie arbeiten können. Aspose.Words macht das zu einem Einzeiler.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:**  
`Document` ist der Container für alles – Text, Tabellen, Bilder und Formen. `DocumentBuilder` ist der freundliche Helfer, der Ihnen das Hinzufügen von Inhalten ermöglicht, ohne sich mit Low‑Level‑Objekten herumschlagen zu müssen. Denken Sie daran wie an einen Stift, der direkt auf die Seite schreibt.

> **Pro tip:** Wenn Sie mit einer Vorlage beginnen möchten (z. B. einem Firmenbriefkopf), ersetzen Sie `new Document()` durch `new Document("template.docx")`.

### ## Rechteckform einfügen und andere Formen

Jetzt fügen wir ein blaues Rechteck und eine grüne Ellipse hinzu. Das Rechteck demonstriert das **insert rectangle shape** Schlüsselwort, während die Ellipse zeigt, dass Sie Formtypen frei mischen können.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Was unter der Haube passiert:**  
Jeder Aufruf von `insertShape` erzeugt ein `Shape`‑Objekt und fügt es automatisch dem aktuellen Absatz hinzu. Die Methoden `setLeft`/`setTop` positionieren die Form relativ zu den Seitenrändern, gemessen in Punkten (1 pt = 1/72 in). Durch Anpassen dieser Werte können Sie Formen überall platzieren, wo Sie möchten.

> **Common question:** *Can I add a picture instead of a solid color?*  
> Absolutely—just replace the fill color with an image using `shape.getFill().setImage("path/to/image.png")`.

### ## Formen in Word gruppieren für einfache Manipulation

Zwei separate Objekte zu haben ist in Ordnung, aber oft möchte man sie zusammen bewegen. Genau hier glänzt **group shapes in word**.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Warum gruppieren?**  
Wenn Formen gruppiert werden, gilt jede Transformation – Verschieben, Drehen, Skalieren – auf die gesamte Sammlung. Das spiegelt das Verhalten wider, das Sie erhalten, wenn Sie im Word‑UI mehrere Formen manuell auswählen und *Group* klicken. Es vereinfacht späteren Code, weil Sie nur ein Objekt anpassen müssen statt vieler.

> **Edge case:** Wenn Sie später entgruppieren müssen, rufen Sie `group.getParentNode().removeChild(group)` auf und fügen die Kinder einzeln wieder ein.

### ## Dokument als DOCX speichern und Ausgabe überprüfen

Schließlich persistieren wir die Datei. Dieser Schritt erfüllt die **save document as docx** Anforderung.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Was Sie erwarten können:**  
Öffnen Sie das erzeugte `GroupShapeExample.docx` in Microsoft Word. Sie sehen ein blaues Rechteck und eine grüne Ellipse, ordentlich gruppiert. Ziehen Sie die Gruppe – beide Formen bewegen sich zusammen, genau wie im UI erwartet.

> **Tip:** Verwenden Sie `SaveFormat.PDF`, wenn Sie eine PDF‑Version benötigen; derselbe Code funktioniert ohne Änderungen.

### ## Vollständiges funktionierendes Beispiel und häufige Fallstricke

Unten finden Sie die komplette, sofort ausführbare Java‑Klasse. Kopieren Sie sie in Ihr Projekt, passen Sie den Ausgabepfad an und klicken Sie auf *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Häufige Fallstricke & wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| **`NullPointerException` on `builder`** | Vergessen, `DocumentBuilder` nach dem Erzeugen von `Document` zu instanziieren. | Sicherstellen, dass `new DocumentBuilder(doc)` vor jeder Form‑Einfügung ausgeführt wird. |
| **Shapes appear off‑page** | Verwendung von Pixelwerten statt Punkten oder fehlende Berücksichtigung der Ränder. | Denken Sie daran, dass Aspose.Words Punkte erwartet; 72 pt = 1 in. Passen Sie `setLeft`/`setTop` entsprechend an. |
| **Group disappears after save** | Formen werden *nach* dem Speichern der Gruppe zur Gruppe hinzugefügt. | Immer gruppieren, bevor `doc.save()` aufgerufen wird. |
| **File not found on save** | Ausgabeverzeichnis existiert nicht. | Das Verzeichnis programmgesteuert erstellen (`new File("output").mkdirs();`) oder einen vorhandenen Pfad verwenden. |

---

## Fazit

Wir haben gerade **create word document** von Grund auf neu erstellt, **add shapes to word**, **insert rectangle shape**, **group shapes in word** und schließlich **save document as docx** – alles mit ein paar Zeilen Java. Die Stärke von Aspose.Words liegt in seinem klaren Objektmodell; Sie können eine Word‑Datei wie eine Leinwand behandeln, mit Formen darauf malen und sie dann überall dort exportieren, wo Sie sie benötigen.

Abenteuerlustig? Versuchen Sie, das Rechteck durch einen Stern zu ersetzen, fügen Sie Text in die Formen mit `Shape.getTextBox()` ein oder experimentieren Sie mit Rotation (`shape.setRotationAngle(45)`). Die API ist umfangreich und die Möglichkeiten praktisch unbegrenzt.

Haben Sie Fragen zu fortgeschritteneren Szenarien – etwa dem Verknüpfen von Formen mit Lesezeichen oder dem Exportieren zu PDF mit eingebetteten Schriften? Hinterlassen Sie einen Kommentar unten, und wir tauchen gemeinsam tiefer ein. Happy coding!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument in Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Gruppenform in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}