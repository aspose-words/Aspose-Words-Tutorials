---
category: general
date: 2026-07-26
description: Wie man mit Aspose.Words eine ActiveX-Schaltfläche in ein Word‑Dokument
  einfügt – lernen Sie, die Beschriftung, Position und Größe der Schaltfläche in nur
  wenigen Zeilen festzulegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: de
lastmod: 2026-07-26
og_description: Wie man mit Aspose.Words eine ActiveX-Schaltfläche in ein Word-Dokument
  einfügt. Folgen Sie diesem Schritt‑für‑Schritt‑Tutorial, um die Beschriftung, Position
  und Größe der Schaltfläche festzulegen.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Wie man einen ActiveX-Button in Word einfügt – Schnellleitfaden
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Wie man in Word eine ActiveX-Schaltfläche einfügt – Schaltflächenbeschriftung
  festlegen
url: /de/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine ActiveX-Schaltfläche in Word einfügt – Beschriftung der Schaltfläche festlegen

Haben Sie sich jemals gefragt, **wie man ActiveX**‑Steuerelemente in eine Word‑Datei einfügt, ohne die Benutzeroberfläche zu öffnen? Sie sind nicht allein. In vielen Unternehmensanwendungen benötigen Sie eine anklickbare Schaltfläche, die ein Makro ausführt, und das programmgesteuerte Einfügen spart Stunden. Dieser Leitfaden zeigt Ihnen genau, **wie man eine ActiveX** CommandButton‑Schaltfläche mit Aspose.Words für Java einfügt und – ja – **wie man die Schaltflächenbeschriftung festlegt**, damit der Benutzer weiß, worauf er klicken soll.

Wir gehen den gesamten Prozess durch: von der Einrichtung der Bibliothek, über das Erstellen eines neuen Dokuments, das Einfügen der Schaltfläche, das Anpassen von Größe und Position, das Hinzufügen einer freundlichen Beschriftung bis hin zum Speichern der Datei. Am Ende haben Sie eine ausführbare `.docx`, die in Word mit einer voll funktionsfähigen ActiveX‑Schaltfläche geöffnet wird, die Ihr Makro auslöst.

---

## Was Sie lernen werden

- Aspose.Words in einem Java‑Projekt installieren und referenzieren.  
- Ein neues `Document` und `DocumentBuilder` erstellen.  
- **ActiveX** CommandButton‑Steuerelement mit einer einzigen Codezeile einfügen.  
- **Schaltflächenbeschriftung festlegen**, Position anpassen und Abmessungen definieren.  
- Das Dokument speichern und in Word öffnen, um das Ergebnis zu sehen.

Vorkenntnisse zu ActiveX sind nicht erforderlich; Sie benötigen lediglich Grundkenntnisse in Java und eine Kopie von Aspose.Words.

---

## Voraussetzungen

- Java 8 oder neuer auf Ihrem Rechner installiert.  
- Maven oder Gradle für das Abhängigkeitsmanagement (wir zeigen das Maven‑Snippet).  
- Eine lizenzierte oder Evaluierungskopie von **Aspose.Words für Java** (die kostenlose Testversion funktioniert für diese Demo).  
- Microsoft Word (beliebige aktuelle Version), um die erzeugte Datei zu testen.

---

## Schritt 1: Aspose.Words in Ihrem Projekt einrichten

Zuerst das Aspose.Words‑Dependency hinzufügen. Wenn Sie Maven verwenden, fügen Sie das Folgende in Ihre `pom.xml` ein:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle‑Nutzer können hinzufügen:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Nach einem schnellen `mvn clean install` (oder `gradle build`) befindet sich die Bibliothek im Klassenpfad und Sie können loslegen.

---

## Schritt 2: Ein neues Dokument und einen Builder erstellen

Ein `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` Ihnen das Bearbeiten ermöglicht. Denken Sie an den Builder wie an einen Stift, der auf einer frischen Leinwand zeichnet.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Warum mit einem leeren Dokument beginnen? Es garantiert Ihnen volle Kontrolle über jedes Element, das Sie hinzufügen, und es gibt keine versteckten Formatierungen, die Sie später überraschen könnten.

---

## Schritt 3: Das ActiveX CommandButton‑Steuerelement einfügen

Jetzt kommt der Star der Show. Aspose.Words stellt `insertForms2OleControl` bereit, mit dem Sie jedes gewünschte ActiveX‑Steuerelement platzieren können. Hier fragen wir nach einem **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Die Methode gibt ein `Forms2OleControl`‑Objekt zurück, das Ihnen programmgesteuerten Zugriff auf die Eigenschaften der Schaltfläche gibt. Hier wird **wie man ActiveX einfügt** zu einem Einzeiler – kein Herumfummeln mit low‑level COM‑APIs.

---

## Schritt 4: Position, Größe und Schaltflächenbeschriftung festlegen

Eine Schaltfläche, die mitten auf der Seite schwebt, ist nicht sehr nützlich. Sie sollten sie dort platzieren, wo Benutzer sie erwarten, ihr eine sinnvolle Größe geben und – am wichtigsten – **die Schaltflächenbeschriftung festlegen**, damit sie wissen, was ein Klick bewirkt.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Warum diese Zahlen?** Word verwendet Punkte (1 pt ≈ 1/72 Zoll). `100 pt` ≈ 1,4 in von links, `150 pt` ≈ 2,1 in von oben – etwa die Mitte einer Standard‑A4‑Seite. Passen Sie sie an Ihr Layout an.

Die Festlegung der Beschriftung ist entscheidend; ohne sie sieht die Schaltfläche aus wie ein leeres Rechteck. Die Methode `setCaption` akzeptiert jede Zeichenkette, sodass Sie sie später bei Bedarf lokalisieren können.

---

## Schritt 5: Das Dokument speichern

Zum Schluss das Dokument auf die Festplatte schreiben. Sie können jeden gewünschten Ordner wählen; stellen Sie nur sicher, dass der Pfad existiert.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Wenn Sie `ActiveXButton.docx` in Word öffnen, sehen Sie eine schön platzierte Schaltfläche mit der Aufschrift **„Click Me.“** Wenn Sie sie doppelklicken, fordert Word Sie auf, Makros zu aktivieren (da ActiveX‑Steuerelemente als makro‑aktiviert gelten). Anschließend können Sie ein VBA‑Routinen‑Makro an das `Click`‑Ereignis der Schaltfläche binden.

---

## Sonderfälle & Tipps, die leicht übersehen werden

- **Makro‑aktiviertes Format**: Word deaktiviert ActiveX‑Steuerelemente in normalen `.docx`‑Dateien, sofern der Benutzer keine Makros aktiviert. Wenn die Schaltfläche sofort funktionieren soll, speichern Sie als `.docm` (makro‑aktiviert) mittels `doc.save(outputPath, SaveFormat.DOCM);`.
- **Kompatibilität**: Ältere Word‑Versionen (vor 2007) verwenden das binäre `.doc`‑Format. Aspose.Words kann in dieses Format speichern, aber die Eigenschaften des Steuerelements können leicht abweichen.
- **Sicherheitseinstellungen**: In manchen Unternehmensumgebungen sind ActiveX‑Steuerelemente gesperrt. Wenn Ihre Schaltfläche nicht erscheint, prüfen Sie Word → Trust Center → ActiveX‑Einstellungen.
- **Mehrere Schaltflächen**: Mehr als eine benötigen? Wiederholen Sie einfach den Aufruf von `insertForms2OleControl` und passen Sie die `Left`/`Top`‑Werte jeder Schaltfläche an. Behalten Sie die zurückgegebenen Objekte, um individuelle Beschriftungen zu setzen.
- **Beschriftungsstil**: Die Beschriftung erbt die Standardschriftart. Um sie zu ändern, müssten Sie das zugrunde liegende XML bearbeiten oder nach dem Einfügen einen Word‑Stil anwenden – außerhalb des Umfangs dieses kurzen Leitfadens, aber mit Aspose.Words `ParagraphFormat`‑API machbar.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie die komplette, sofort ausführbare Java‑Klasse. Kopieren Sie sie in Ihre IDE, passen Sie den Ausgabepfad an und klicken Sie auf **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Erwartete Ausgabe**: Nach dem Ausführen gibt die Konsole den Speicherort aus. Öffnen Sie die erzeugte Datei in Word, und Sie sehen eine Schaltfläche, die etwa in der Mitte der Seite platziert ist und „Click Me“ beschriftet ist. Ein Klick löst das Standard‑ActiveX‑Click‑Ereignis aus (Sie müssen ein VBA‑Makro anhängen, um zu reagieren).

---

## Fazit

Sie wissen jetzt **wie man ActiveX** CommandButton‑Steuerelemente programmgesteuert in ein Word‑Dokument einfügt und haben genau gesehen, **wie man die Schaltflächenbeschriftung festlegt**, die Position und Größe des Steuerelements definiert. Dieser Ansatz eliminiert manuelle UI‑Arbeit, lässt sich sauber in automatisierte Berichtsgeneratoren integrieren und gibt Ihnen volle Kontrolle über das Ergebnis.

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}