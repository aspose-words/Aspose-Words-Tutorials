---
category: general
date: 2026-07-16
description: Setzen Sie die Schaltflächengröße programmgesteuert in einem Word‑Dokument
  mit Aspose.Words für Java. Erfahren Sie, wie Sie eine ActiveX‑Schaltfläche einfügen,
  die Position der Schaltfläche festlegen und mehr.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: de
lastmod: 2026-07-16
og_description: Stelle die Button‑Größe in einem Word‑Dokument mit Java ein. Diese
  Schritt‑für‑Schritt‑Anleitung zeigt, wie man einen ActiveX‑Button einfügt, die Position
  des Buttons festlegt und den Button programmgesteuert hinzufügt.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Buttongröße in Word mit Java festlegen – Vollständiges Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Buttongröße in Word mit Java festlegen – Vollständiger Aspose.Words‑Leitfaden
url: /de/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Button-Größe in Word mit Java festlegen – Vollständige Aspose.Words-Anleitung

Haben Sie sich jemals gefragt, wie man die **Button-Größe** in einer Word‑Datei festlegt, ohne die Benutzeroberfläche zu öffnen? Sie sind nicht allein. Wenn Sie ein ausgefülltes Formular‑Dokument on‑the‑fly erzeugen müssen – zum Beispiel ein Onboarding‑Paket mit einem „Submit“-Button – spart die programmatische Vorgehensweise Stunden manueller Arbeit.

In diesem Tutorial führen wir Sie Schritt für Schritt durch die genauen Vorgänge, um einen **ActiveX‑Button einzufügen**, seine Abmessungen anzupassen, ihn korrekt zu positionieren und schließlich die Datei zu speichern. Am Ende können Sie **programmgesteuert Button‑Steuerelemente** zu jedem Word‑Dokument hinzufügen, indem Sie Aspose.Words für Java verwenden.

## Voraussetzungen – Was Sie vor dem Start benötigen

- **Java Development Kit (JDK) 8+** – der Code läuft auf jedem aktuellen JDK.
- **Aspose.Words for Java** Bibliothek (laden Sie die neueste JAR von der offiziellen Website herunter).  
- Eine **IDE** Ihrer Wahl – IntelliJ IDEA, Eclipse oder sogar ein einfacher Texteditor funktioniert.
- Grundlegende Kenntnisse der Java‑Syntax; tiefgehendes Word‑Automatisierungswissen ist nicht erforderlich.

> *Pro‑Tipp:* Halten Sie die Aspose.Words‑JAR im Klassenpfad Ihres Projekts, sonst erhalten Sie sofort eine `ClassNotFoundException`, wenn Sie versuchen, `com.aspose.words.*` zu importieren.

## Schritt 1: Ein neues Word‑Dokument erstellen

Das Erste, was wir tun, ist ein leeres Dokument und einen `DocumentBuilder` zu erstellen. Denken Sie an den Builder wie an einen Stift, mit dem wir alles im Dokument zeichnen können.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Warum das wichtig ist:** Das `Document`‑Objekt repräsentiert die gesamte .docx‑Datei, während der `DocumentBuilder` das Arbeitspferd ist, das uns das Einfügen von Absätzen, Tabellen und – ja – ActiveX‑Steuerelementen ermöglicht.

## Schritt 2: ActiveX‑Button einfügen – Der „Insert ActiveX Button“-Moment

Jetzt fügen wir tatsächlich einen **ActiveX‑Button ein** in das Dokument. Aspose.Words stellt eine praktische Methode `insertForms2OleControl` bereit, die ein `Forms2OleControl`‑Objekt zurückgibt.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Was passiert im Hintergrund?* `Forms2OleControlType.COMMAND_BUTTON` teilt Word mit, dass wir einen klassischen CommandButton wollen, dieselbe Art, die Sie aus der Registerkarte „Entwicklertools“ in der UI ziehen würden.

## Schritt 3: Button‑Größe und -Position festlegen – Die Kernlogik zum „Set Button Size“

Hier kommt das Hauptkeyword zum Einsatz. Wir werden **die Button‑Größe festlegen** und zudem **die Button‑Position setzen**, sodass das Steuerelement genau dort erscheint, wo wir es auf der Seite haben möchten.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Warum das wichtig ist:** Punkte sind die native Maßeinheit in Word (1 Punkt = 1/72 Zoll). Durch Anpassen von `setLeft`, `setTop`, `setWidth` und `setHeight` erhalten Sie pixelgenaue Kontrolle – kein „Sieht auf meinem Bildschirm gut aus, aber nicht beim Druck“ mehr.  
> *Häufiges Problem:* Wenn Sie vergessen, Breite oder Höhe zu setzen, bleibt der Button in der Standardgröße, die möglicherweise zu klein zum Anklicken ist. Geben Sie immer beide Werte an.

## Schritt 4: Dokument speichern – „Create Word Document Button“ abgeschlossen

Abschließend schreiben wir die Datei auf die Festplatte. Der Name deutet darauf hin, dass wir einen **Word‑Document‑Button** innerhalb einer .docx erstellen.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Wenn Sie `CommandButtonDemo.docx` in Microsoft Word öffnen, sehen Sie einen **Submit**‑Button, der 100 pt vom linken Rand und 150 pt vom oberen Rand platziert ist und die Größe 80 × 30 pt hat. Ein Klick darauf in der UI löst das Standard‑ActiveX‑Verhalten aus (das Sie später bei Bedarf mit VBA verknüpfen können).

### Erwarteter Screenshot der Ausgabe

![Button-Größe in einem Word-Dokument mit Java festlegen](https://example.com/images/set-button-size.png "Screenshot einer Word-Datei, in der die Button-Größe mit Aspose.Words für Java festgelegt wurde")

*Alt-Text:* Button-Größe in einem Word-Dokument mit Java festlegen

## Schritt 5 (Optional): Weitere Steuerelemente hinzufügen oder den Button stylen

Wenn Sie **programmgesteuert Button‑Steuerelemente** über einen einzelnen Submit‑Button hinaus hinzufügen müssen, wiederholen Sie einfach den Einfüge‑Block mit neuen Namen und Beschriftungen. Sie können außerdem Schriftart, Hintergrundfarbe anpassen oder später VBA‑Makros binden.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tipp:* Halten Sie alle Button‑Abmessungen konsistent für ein professionelles Erscheinungsbild. Eine schnelle Methode ist, Breite/Höhe in Konstanten zu speichern.

## Häufige Fragen & Sonderfälle

### „Kann ich die Button‑Größe in Zentimetern statt Punkten festlegen?“

Die Word‑API akzeptiert nur Punkte, aber Sie können Zentimeter in Punkte umrechnen (`points = cm * 28.3465`). Schreiben Sie eine kleine Hilfsmethode, wenn Sie metrische Einheiten bevorzugen.

### „Was, wenn der Button auf einer bestimmten Seite erscheinen soll?“

Nachdem Sie den Button eingefügt haben, können Sie den Cursor mit `builder.moveToPage(pageNumber)` zu einer bestimmten Seite bewegen. Fügen Sie das Steuerelement unmittelbar nach dem Sprung ein und setzen Sie dann seine Position wie oben gezeigt.

### „Funktioniert das mit .doc (Word 97‑2003) Dateien?“

Ja – Aspose.Words verarbeitet ältere Formate automatisch. Ändern Sie einfach die Dateierweiterung in `doc.save("Demo.doc")`.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das gesamte Programm, das Sie in eine Java‑Klasse kopieren und sofort ausführen können (vorausgesetzt, die Aspose.Words‑JAR befindet sich im Klassenpfad).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Führen Sie das Programm aus, öffnen Sie das erzeugte `CommandButtonDemo.docx` und Sie sehen zwei ordentlich dimensionierte Buttons, die zur Interaktion bereitstehen.

## Fazit – Sie haben das Festlegen der Button‑Größe in Word gemeistert

Wir haben gerade eine vollständige End‑zu‑End‑Lösung für **Button‑Größe festlegen** und **Button‑Position festlegen** mit Aspose.Words für Java durchgegangen. Wenn Sie die Schritte befolgen, können Sie **ActiveX‑Button einfügen**, **programmgesteuert Button‑Steuerelemente hinzufügen** und letztlich **Word‑Document‑Button**‑Elemente erstellen, die sich exakt so verhalten, wie Sie es benötigen.

Was kommt als Nächstes? Versuchen Sie, den Button in eine Tabellenzelle einzubetten oder ein VBA‑Makro anzuhängen, das Formularfelder vor dem Absenden validiert. Das gleiche Muster funktioniert für andere ActiveX‑Steuerelemente wie Kontrollkästchen oder Kombinationsfelder – ersetzen Sie einfach `Forms2OleControlType.COMMAND_BUTTON` durch den entsprechenden Enum‑Wert.

Wenn Sie auf Probleme stoßen, hinterlassen Sie unten einen Kommentar. Viel Spaß beim Programmieren und genießen Sie die Möglichkeiten der automatisierten Word‑Dokumentenerstellung!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, die Ihnen helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man LoadOptions in Aspose.Words für Java festlegt](/words/english/java/document-loading-and-saving/using-load-options/)
- [Wie man Fußzeilen aus Word‑Dokumenten mit Aspose.Words für Java entfernt](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Umfassender Leitfaden zur Word‑Dokumentenverarbeitung](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}