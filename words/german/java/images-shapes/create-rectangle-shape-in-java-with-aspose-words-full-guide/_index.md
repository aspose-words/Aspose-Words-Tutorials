---
category: general
date: 2026-07-06
description: Erstellen Sie ein Rechteck‑Shape in Java mit Aspose.Words – erfahren
  Sie, wie Sie dem Shape einen Schatten hinzufügen, die Transparenz des Shapes festlegen
  und das Dokument als PDF speichern.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: de
og_description: Erstellen Sie ein Rechteck-Shape in Java mit Aspose.Words. Dieser
  Leitfaden zeigt, wie man dem Shape einen Schatten hinzufügt, die Transparenz des
  Shapes einstellt und das Dokument als PDF speichert.
og_title: Rechteckform in Java erstellen – Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Rechteckform in Java mit Aspose.Words erstellen – Vollständige Anleitung
url: /de/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Java mit Aspose.Words erstellen – Vollständige Anleitung

Haben Sie sich jemals gefragt, wie man in Java **eine Rechteckform erstellt** ohne sich mit Low‑Level‑Zeichnungs‑APIs herumzuschlagen? Sie sind nicht allein. Viele Entwickler benötigen eine schnelle, zuverlässige Möglichkeit, ein Rechteck in ein Word‑Dokument einzufügen, ihm einen dezenten Schatten zu geben, die Transparenz anzupassen und das Ergebnis dann als PDF auszugeben.  

In diesem Tutorial führen wir Sie Schritt für Schritt durch genau das – mit vollständigem, ausführbarem Code. Am Ende wissen Sie, **wie man einem Shape einen Schatten hinzufügt**, wie man **die Transparenz eines Shapes einstellt** und wie man **ein Dokument als PDF speichert** mit Aspose.Words für Java. Kein Schnickschnack, nur praktische Anleitungen, die Sie noch heute in Ihr Projekt kopieren‑und‑einfügen können.

## Was Sie lernen werden

- Die minimale Einrichtung, die erforderlich ist, um mit Aspose.Words in einem Java‑Projekt zu arbeiten.  
- Wie man **Rechteckform erstellt** programmgesteuert.  
- Die genauen Aufrufe, die nötig sind, um **einem Shape einen Schatten hinzuzufügen** und dessen Unschärfe, Versatz und Deckkraft anzupassen.  
- Möglichkeiten, **die Transparenz eines Shapes einzustellen**, damit das Rechteck gut mit dem umgebenden Inhalt harmoniert.  
- Die einfachste Methode, **ein Dokument als PDF zu speichern**, ohne zusätzliche Konvertierungsschritte.  

Wenn Sie mit grundlegenden Java‑Kenntnissen vertraut sind und ein Maven‑ oder Gradle‑Build haben, können Sie loslegen.

## Voraussetzungen

- Java 8 oder neuer.  
- Aspose.Words für Java 23.x (oder die neueste Version zum Zeitpunkt des Lesens).  
- Eine IDE oder ein Befehlszeilen‑Build‑Tool (IntelliJ, Eclipse, Maven, Gradle – wählen Sie, was Ihnen gefällt).  

> **Profi‑Tipp:** Aspose bietet eine kostenlose temporäre Lizenz für die Evaluierung an. Holen Sie sie aus Ihrem Konten‑Portal und legen Sie die Datei `license.xml` in Ihren Klassenpfad; andernfalls sehen Sie ein Wasserzeichen im PDF.

---

## Schritt 1: **Rechteckform erstellen** mit Aspose.Words

Das Erste, was wir benötigen, ist ein leeres `Document` und ein `DocumentBuilder`. Der Builder ist das Arbeitspferd, das es uns ermöglicht, Shapes direkt in den Fluss des Dokuments einzufügen.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Warum das wichtig ist:** `ShapeType.RECTANGLE` teilt Aspose mit, dass wir ein perfektes Rechteck wollen. Breite und Höhe werden in Punkten angegeben (1 pt ≈ 1/72 in), was Ihnen eine feine Kontrolle über die endgültige Größe ermöglicht.

---

## Schritt 2: **Schatten zum Shape hinzufügen**

Jetzt, wo wir ein Rechteck haben, geben wir ihm einen dezenten Abwurfschatten. Das Objekt `ShadowFormat` stellt alles bereit, was wir benötigen – Unschärferadius, X/Y‑Versatz und sogar Transparenz.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Warum das wichtig ist:** Ein Schatten ohne Unschärfe sieht aus wie eine harte Linie, was Designer selten wollen. Der Aufruf `setBlur` glättet die Kanten, während `setTransparency` den Schatten in den Hintergrund verblassen lässt. Passen Sie diese Werte an Ihre UI‑Richtlinien an.

---

## Schritt 3: **Transparenz des Shapes einstellen**

Manchmal muss das Rechteck selbst halbtransparent sein – vielleicht um ein Logo oder Wasserzeichen zu überlagern. Aspose macht das mit einer einzigen Zeile.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Warum das wichtig ist:** Transparenz kann ein Lebensretter sein, wenn Sie Shapes schichten. Beachten Sie, dass die Transparenz des Schattens unabhängig ist, sodass Sie ein schwaches Shape mit einem dunkleren Schatten haben können, wenn das zu Ihrem Design passt.

---

## Schritt 4: **Dokument als PDF speichern**

Alle visuellen Arbeiten sind erledigt; der letzte Schritt ist das Persistieren des Dokuments. Aspose.Words kann direkt nach PDF schreiben und damit die Notwendigkeit einer separaten Konvertierungsbibliothek eliminieren.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Warum das wichtig ist:** Durch Angabe von `SaveFormat.PDF` übernimmt die Bibliothek die Schriftart‑Einbettung, Bildkompression und PDF/A‑Konformität im Hintergrund. Die resultierende Datei ist bereit für Verteilung, Druck oder Archivierung.

---

## Vollständiges funktionierendes Beispiel

Alles zusammengefügt, hier ist die komplette, sofort ausführbare Klasse. Kopieren‑und‑einfügen, passen Sie den Ausgabepfad an, und Sie erhalten ein PDF mit einem Rechteck, das einen realistischen Schatten wirft.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Erwartete Ausgabe:** Wenn Sie `RectangleWithShadow.pdf` öffnen, sehen Sie ein hellgraues Rechteck, das zentriert auf der ersten Seite liegt und durch einen weichen, halbtransparenten Schatten leicht von der Seite gehoben ist. Das Shape selbst ist zu 20 % transparent, sodass darunterliegender Text (falls Sie welchen hinzugefügt haben) durchscheint.

---

## Häufige Fragen & Sonderfälle

### 1️⃣ Was, wenn ich ein größeres Rechteck benötige?

Ändern Sie einfach die Breiten‑ und Höhenparameter in `insertShape`. Denken Sie daran, dass 72 pt = 1 in, also würde `400.0, 200.0` Ihnen ein 5,5 × 2,8 Zoll‑Rechteck geben.

### 2️⃣ Kann ich eine andere Farbe für den Schatten verwenden?

Absolut. Die Klasse `ShadowFormat` stellt ebenfalls `setColor(java.awt.Color)` zur Verfügung. Für einen dezenten grauen Schatten probieren Sie `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ Funktioniert `save document as pdf` auf allen Plattformen?

Ja. Aspose.Words für Java ist plattformunabhängig; derselbe Code läuft unter Windows, macOS und Linux, solange Sie eine kompatible JRE haben.

### 4️⃣ Wie entferne ich später den Schatten?

Rufen Sie `rect.getShadowFormat().clear();` auf oder setzen Sie die Eigenschaft `Visible` auf `false` (`shadow.setVisible(false);`).

### 5️⃣ Was ist mit DPI und Bildqualität?

Beim Speichern als PDF verwendet Aspose automatisch 300 DPI für Vektorgrafiken wie Shapes, sodass Sie gestochen scharfe Ergebnisse erhalten, unabhängig vom Zoom‑Level.

---

## Profi‑Tipps & bewährte Methoden

- **Batchverarbeitung:** Wenn Sie Dutzende PDFs erzeugen müssen, verwenden Sie eine einzelne `Document`‑Instanz und leeren Sie nur deren Abschnitte zwischen den Durchläufen, um den GC‑Druck zu reduzieren.  
- **Lizenzierung:** Setzen Sie `License license = new License(); license.setLicense("license.xml");` zu Beginn von `main`, um das Evaluations‑Wasserzeichen zu vermeiden.  
- **Performance:** Das Rendern von Schatten ist bei einfachen Shapes günstig, aber komplexe Pfade können die PDF‑Erstellung verlangsamen. Profilieren Sie, wenn Sie große Stapel verarbeiten.  
- **Testing:** Verwenden Sie zuerst Asposes `Document.save(..., SaveFormat.DOCX)`, um zu prüfen, ob das Shape korrekt in Word erscheint, bevor Sie zu PDF konvertieren.

---

## Fazit

Sie wissen jetzt, wie man in Java mit Aspose.Words **eine Rechteckform erstellt**, **einem Shape einen Schatten hinzufügt**, **die Transparenz eines Shapes einstellt** und schließlich **ein Dokument als PDF speichert**. Der Code ist eigenständig, funktioniert mit der neuesten Aspose‑Bibliothek und demonstriert die wesentlichen API‑Aufrufe, die Sie für die meisten Dokument‑Automatisierungsszenarien benötigen.

Bereit für die nächste Herausforderung? Versuchen Sie, das Rechteck durch eine Ellipse zu ersetzen, experimentieren Sie mit Farbverläufen oder erkunden Sie, wie man **Schatten zu Textfeldern hinzufügt**. Die gleichen Prinzipien gelten, und die Aspose‑API macht es zu einem Kinderspiel.

Viel Spaß beim Coden, und hinterlassen Sie gerne einen Kommentar, falls Sie auf Probleme stoßen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}