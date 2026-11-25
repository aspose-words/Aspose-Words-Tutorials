---
category: general
date: 2026-11-25
description: Verstecken Sie Formen in Word mit Aspose.Words und lernen Sie, ein Word‑Dokument
  mit Aspose zu erstellen, während Sie ein Rechteck in Word einfügen – alles in nur
  wenigen Codezeilen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: de
lastmod: 2026-11-25
og_description: Form in Word mit Aspose.Words ausblenden. Dieses Tutorial zeigt, wie
  man ein Word‑Dokument mit Aspose erstellt, ein Rechteck‑Shape in Word einfügt und
  es programmgesteuert ausblendet.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Form in Word mit Aspose.Words ausblenden – schnelle Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Wie man eine Form in Word mit Aspose.Words ausblendet
url: /de/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine Form in Word mit Aspose.Words ausblendet

Wenn Sie **eine Form in Word ausblenden** müssen, während Sie Dokumente programmgesteuert erzeugen, macht Aspose.Words das mühelos. In diesem Leitfaden sehen Sie genau, wie Sie ein Word‑Dokument mit Aspose erstellen, ein Rechteck‑Shape in Word einfügen und dann diese Form ausblenden, sodass sie im Layout nicht erscheint. Das vollständige, ausführbare Beispiel ist enthalten, sodass Sie es einfach in Ihre IDE kopieren und das Ergebnis sofort sehen können.

Am Ende dieses Tutorials haben Sie eine Word‑Datei, die ein verstecktes Rechteck enthält – nützlich für Platzhalter, bedingten Inhalt oder Metadaten, die für den Leser unsichtbar bleiben sollen. Es werden keine externen Werkzeuge benötigt, außer der Aspose.Words‑Bibliothek für Java (oder .NET).

## Was Sie lernen werden

* Wie man **ein Word‑Dokument mit Aspose** von Grund auf erstellt.  
* Wie man **ein Rechteck‑Shape in Word** mit dem `DocumentBuilder` einfügt.  
* Wie man die Eigenschaft `hidden` der Form setzt, sodass sie im endgültigen Layout nicht gerendert wird.  
* Wie man überprüft, dass die Form ausgeblendet ist, und wie man sie bei Bedarf wieder einblendet.  

### Voraussetzungen

* Java 17+ (oder .NET 6+ bei C#‑Präferenz – die API‑Aufrufe sind analog).  
* Aspose.Words für Java 24.x (die aktuelle Version zum Zeitpunkt des Schreibens).  
* Eine IDE wie IntelliJ IDEA, Eclipse oder VS Code.  

> **Pro‑Tipp:** Nutzen Sie die kostenlose temporäre Lizenz von Aspose, falls Sie noch keine kommerzielle Lizenz besitzen. Die Bibliothek funktioniert ohne Lizenz zur Evaluierung, jedoch entfernt eine Lizenz die Evaluierungs‑Wasserzeichen.

## Form in Word mit Aspose.Words ausblenden

Die Kernschritte sind:

1. **Ein neues `Document` erstellen.**  
2. **Ein Rechteck‑Shape einfügen** mit `DocumentBuilder`.  
3. **Die Form als hidden markieren**, sodass sie beim Öffnen der Datei nicht erscheint.  

Jeder Schritt wird unten mit Code und Erläuterungen beschrieben.

### Schritt 1: Ein Word‑Dokument mit Aspose erstellen

Zuerst erzeugen Sie ein leeres `Document` und einen `DocumentBuilder`. Der Builder stellt eine fluente API zum Hinzufügen von Inhalten bereit, einschließlich Shapes.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:**  
Ein frisches `Document` gibt Ihnen eine saubere Leinwand. Der `DocumentBuilder` ist der empfohlene Weg, das Dokument zu verändern, weil er automatisch den aktuellen Einfügepunkt verfolgt und das Abschnitts‑/Seiten‑Management für Sie übernimmt.

### Schritt 2: Rechteck‑Shape in Word einfügen

Jetzt fügen wir ein Rechteck‑Shape hinzu. Die Methode `insertShape` benötigt den Shape‑Typ und seine Abmessungen in Punkten (1 Punkt = 1/72 Zoll).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Warum das wichtig ist:**  
`insertShape` erzeugt ein Zeichenobjekt, das im *drawing*‑Teil des Dokuments lebt. Durch Angabe der Größe bestimmen Sie, wie viel Platz die Form einnehmen würde, wenn sie sichtbar wäre. Das optionale Styling hilft Ihnen, die Form zu prüfen, bevor Sie sie ausblenden.

### Schritt 3: Die Form ausblenden, sodass sie nicht im Layout erscheint

Aspose.Words spiegelt das Microsoft‑Word‑Attribut *Hidden* wider. Wird es auf `true` gesetzt, lässt Word die Form beim Rendern weg, während das Objekt in der Dokumentenstruktur erhalten bleibt.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Warum das wichtig ist:**  
Eine ausgeblendete Form kann weiterhin programmgesteuert angesprochen werden (z. B. für bedingte Verarbeitung) und später wieder eingeblendet werden, indem die Eigenschaft umgeschaltet wird. Das ist ideal für Szenarien wie **bedingte Platzhalter**, die nur für bestimmte Zielgruppen sichtbar sein sollen.

### Schritt 4: Speichern und Ergebnis prüfen

Abschließend schreiben Sie das Dokument auf die Festplatte. Öffnen Sie die Datei in Microsoft Word, um zu bestätigen, dass das Rechteck nicht sichtbar ist. Sie können auch das zugrunde liegende XML inspizieren, um das hidden‑Flag zu sehen.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Erwartete Ausgabe:**  
Das Ausführen des Programms gibt aus:

```
Document saved to HideShapeResult.docx
```

Wenn Sie *HideShapeResult.docx* in Word öffnen, erscheint die Seite leer (oder enthält sonstigen Inhalt, den Sie vor dem Shape hinzugefügt haben). Das Rechteck ist im XML des Dokuments (`<w:hidden>`‑Attribut) vorhanden, wird jedoch nicht gerendert.

### Schritt 5: (Optional) Die Form später wieder einblenden

Falls Sie die Form wieder sichtbar machen müssen, laden Sie das Dokument, finden das Shape und setzen `hidden` auf `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Warum das wichtig ist:**  
Die Möglichkeit, das hidden‑Flag zu toggeln, gibt Ihnen volle Kontrolle über die dynamische Dokumentenerstellung – z. B. können Sie ein Master‑Dokument mit allen optionalen Elementen ausgeblendet erzeugen und dann selektiv einblenden, basierend auf Benutzerpräferenzen.

## Vollständiges, ausführbares Beispiel (Word‑Dokument erstellen, Rechteck‑Shape einfügen, Shape ausblenden)

Unten finden Sie das komplette Programm, das Sie direkt kompilieren und ausführen können.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Ausführen des Codes**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Ersetzen Sie `aspose-words-24.10.jar` durch die tatsächlich heruntergeladene Version.

### Was die Ausgabedateien enthalten

* **HideShapeResult.docx** – das Rechteck ist ausgeblendet; die Seite wirkt leer.  
* **UnhiddenShape.docx** – dasselbe Rechteck ist sichtbar und erscheint als rotes Kästchen mit schwarzer Kontur.

## Häufige Fragen & Edge‑Case‑Behandlung

| Frage | Antwort |
|----------|--------|
| *Beeinflusst die ausgeblendete Form die Seitennummerierung?* | Nein. Ausgeblendete Objekte werden vom Layout‑Engine ignoriert und schieben keinen Text auf eine neue Seite. |
| *Kann ich andere Word‑Objekte (z. B. Bilder, Tabellen) ausblenden?* | Ja. Die meisten `Node`‑Unterklassen (inkl. `Shape`, `Paragraph`, `Run`) bieten eine `setHidden(boolean)`‑Methode. |
| *Was, wenn das Dokument bereits Shapes enthält?* | Verwenden Sie `doc.getChildNodes(NodeType.SHAPE, true)`, um zu iterieren und nur die gewünschten Shapes auszublenden. |
| *Vergrößert das Ausblenden einer Form die Dateigröße?* | Leicht, da das Shape‑XML erhalten bleibt. Der Einfluss ist bei üblichen Dokumenten vernachlässigbar. |
| *Überlebt das hidden‑Flag beim Speichern als PDF?* | Beim Konvertieren nach PDF werden ausgeblendete Shapes standardmäßig weggelassen. Sie können dies mit `PdfSaveOptions` steuern, falls nötig. |

## Best Practices beim Arbeiten mit ausgeblendeten Objekten

* **Benennen Sie Ihre Shapes** mit `setName("MyPlaceholder")`. Das erleichtert das spätere Auffinden.  
* **Gruppieren Sie zusammengehörige ausgeblendete Objekte** in einem `GroupShape`, wenn Sie die Sichtbarkeit mehrerer Elemente gleichzeitig toggeln wollen.  
* **Dokumentieren Sie den Zweck** ausgeblendeter Elemente in Kommentaren oder einer separaten Spezifikationsdatei – zukünftige Wartende werden den Kontext zu schätzen wissen.  
* **Vermeiden Sie übermäßigen Einsatz** ausgeblendeter Objekte; sie erhöhen die Dokumenten‑Komplexität und können End‑User verwirren, die das XML manuell prüfen.

## Fazit

Sie wissen jetzt, wie man **eine Form in Word ausblendet** mit Aspose.Words, wie man **ein Word‑Dokument mit Aspose erstellt** und wie man **ein Rechteck‑Shape in Word einfügt**, bevor man es ausblendet. Das Beispiel demonstriert den gesamten Lebenszyklus: Erstellen, Einfügen, Ausblenden, Speichern und optionales Wieder‑Einblenden. Nutzen Sie diese Techniken, um dynamische Berichte, bedingte Vorlagen oder jede automatisierte Word‑Workflow‑Lösung zu bauen, bei der unsichtbare Platzhalter nötig sind.

### Nächste Schritte

* Erkunden Sie **bedingten Inhalt**, indem Sie ausgeblendete Shapes mit Mail‑Merge‑Feldern kombinieren.  
* Lernen Sie, **Text‑Runs auszublenden** (`Run.setHidden(true)`) für noch granularere Kontrolle.  
* Werfen Sie einen Blick in die Aspose.Words‑Dokumentation zu **Dokumentschutz**, um zu verhindern, dass Benutzer versehentlich Shapes wieder einblenden.

Viel Spaß beim Coden, und lassen Sie Ihre generierten Word‑Dateien sauber bleiben, während sie die verborgenen Daten tragen, die Sie benötigen!

### Was Sie als Nächstes lernen sollten


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Features meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}