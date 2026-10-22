---
category: general
date: 2026-10-16
description: Erstellen Sie ein leeres Word‑Dokument mit Java und lernen Sie, wie Sie
  eine ActiveX‑Schaltfläche hinzufügen, deren Beschriftung festlegen und ihre Abmessungen
  mit Aspose.Words anpassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: de
lastmod: 2026-10-16
og_description: Erstellen Sie ein leeres Word‑Dokument mit Java, fügen Sie dann eine
  ActiveX‑Schaltfläche hinzu, setzen Sie deren Beschriftung und definieren Sie deren
  Abmessungen mit Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Erstellen Sie ein leeres Word‑Dokument und betten Sie einen ActiveX‑Button
  ein – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Erstelle ein leeres Word‑Dokument und füge einen ActiveX‑Button (Java) hinzu.
url: /de/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word‑Dokument und fügen Sie eine ActiveX‑Schaltfläche hinzu (Java)

Wenn Sie **programmgesteuert ein leeres Word‑Dokument erstellen** möchten, zeigt Ihnen diese Anleitung, wie Sie das mit Java und Aspose.Words erledigen. Sie lernen außerdem, wie Sie **eine ActiveX‑Schaltfläche hinzufügen**, **die Beschriftung der Schaltfläche festlegen** und **die Abmessungen der Schaltfläche einstellen**, sodass das Steuerelement exakt so aussieht, wie Sie es erwarten.

Dieser Leitfaden behandelt:

* Initialisierung einer leeren Word‑Datei mit Aspose.Words für Java.  
* Einfügen eines ActiveX‑`CommandButton`‑Steuerelements.  
* Konfiguration der Beschriftung und Größe der Schaltfläche.  
* Speichern der finalen `.docx`‑Datei.

Sie sollten Grundkenntnisse in Java besitzen und eine aktuelle Version der Aspose.Words für Java‑Bibliothek (der Code funktioniert mit 23.9 und neuer). Keine zusätzlichen Abhängigkeiten sind erforderlich.

![Erstellen Sie ein leeres Word‑Dokument mit einer ActiveX‑Schaltfläche](/images/activex-button-example.png){: .align-center alt="Erstellen Sie ein leeres Word‑Dokument mit einer ActiveX‑Schaltfläche"}

## Erstellen Sie ein leeres Word‑Dokument mit Aspose.Words

Der erste Schritt besteht darin, ein leeres `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte Word‑Datei im Speicher und stellt die Klasse `DocumentBuilder` zum Bearbeiten bereit.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Warum das wichtig ist:**  
Ein leeres Dokument liefert Ihnen eine saubere Leinwand und verhindert versteckte Formatvorlagen oder Abschnitte, die spätere Layout‑Berechnungen beeinträchtigen könnten.

## Fügen Sie dem Dokument eine ActiveX‑Schaltfläche hinzu

Aspose.Words ermöglicht das Einbetten von Legacy‑ActiveX‑Steuerelementen über die Klasse `Forms2OleControl`. Der folgende Code fügt an der aktuellen Cursor‑Position ein `CommandButton`‑Steuerelement ein.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tipp:** Der Wert `setOleClassName` `"Forms.CommandButton.1"` ist die ProgID für die Standard‑Microsoft‑Forms‑Schaltfläche. Die Verwendung einer anderen ProgID (z. B. `"Forms.CheckBox.1"`) würde ein anderes Steuerelement einfügen.

## Beschriftung der Schaltfläche festlegen

Eine Beschriftung ist der Text, der auf der Schaltfläche angezeigt wird. Sie können sie jederzeit vor dem Speichern des Dokuments ändern.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Warum Sie das benötigen:** Benutzer verstehen ein Steuerelement nur, wenn dessen Zweck klar ist. Eine aussagekräftige Beschriftung verbessert die Benutzerfreundlichkeit, insbesondere wenn das Dokument in Word unter Windows geöffnet wird.

## Abmessungen der Schaltfläche festlegen

Position und Größe werden in Punkten angegeben (1 Punkt = 1/72 Zoll). Passen Sie die Werte an Ihr Layout an.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Übliche Variationen:**

| Szenario | Anpassung |
|----------|-----------|
| Größere Schaltfläche für Touch‑Bildschirme | `setWidth` und `setHeight` proportional erhöhen |
| Zentrierte Schaltfläche auf der Seite | `left = (pageWidth - width) / 2` berechnen |
| Mehrere Schaltflächen in einer Spalte | `setTop` für jede neue Schaltfläche inkrementieren |

## Speichern des Dokuments mit der ActiveX‑Schaltfläche

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Das `.docx`‑Format bewahrt das ActiveX‑Steuerelement für Windows‑Versionen von Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Erwartetes Ergebnis:** Das Öffnen von `ActiveXCommandButton.docx` in Word (Windows) zeigt eine leere Seite mit einer anklickbaren Schaltfläche, die **Click Me** lautet und 100 pt vom linken Rand sowie 200 pt vom oberen Rand positioniert ist.

## Vollständiges, ausführbares Beispiel

Kopieren Sie die gesamte Klasse unten in Ihre IDE, fügen Sie das Aspose.Words‑für‑Java‑JAR dem Projekt‑Klassenpfad hinzu und führen Sie sie aus.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Das Ausführen des Programms erzeugt `ActiveXCommandButton.docx` im Arbeitsverzeichnis. Öffnen Sie die Datei mit Microsoft Word (Windows), um zu überprüfen, dass die Schaltfläche exakt wie konfiguriert erscheint.

## Warum dieser Ansatz empfohlen wird

* **Einfachheit:** Es wird nur die Kern‑API von Aspose.Words verwendet; kein COM‑Interop oder zusätzliche Bibliotheken sind nötig.  
* **Portabilität:** Der Code läuft auf jeder Plattform, die Java unterstützt, wobei das ActiveX‑Steuerelement selbst nur in Windows‑Versionen von Word funktioniert.  
* **Wartbarkeit:** Alle Eigenschaften (Beschriftung, Abmessungen, Position) werden über klare, selbsterklärende Methoden gesetzt, wodurch zukünftige Anpassungen unkompliziert sind.

## Häufige Stolperfallen und wie man sie vermeidet

| Stolperfalle | Lösung |
|--------------|--------|
| Die Schaltfläche erscheint in Word auf macOS oder Linux nicht | ActiveX‑Steuerelemente funktionieren nur unter Windows. Verwenden Sie ein alternatives Steuerelement (z. B. ein Inhaltssteuerelement) für plattformübergreifende Dokumente. |
| Beschriftung wird abgeschnitten | Stellen Sie sicher, dass die Schaltflächenbreite breit genug für den Text ist; `setWidth` erhöhen oder eine kürzere Beschriftung verwenden. |
| Schaltfläche überlappt anderen Inhalt | `setTop`‑ und `setLeft`‑Werte anpassen oder einen neuen Absatz vor dem Steuerelement einfügen, um ihm eigenen Platz zu geben. |

## Nächste Schritte

Jetzt, da Sie **ein leeres Word‑Dokument erstellen**, **eine ActiveX‑Schaltfläche hinzufügen**, **die Beschriftung festlegen** und **die Abmessungen einstellen** können, könnten Sie Folgendes erkunden:

* Hinzufügen von Ereignis‑Handling‑Code über VBA‑Makros (erfordert das Einbetten eines Makro‑Moduls).  
* Einfügen mehrerer Steuerelemente in einem Tabellenlayout für formularähnliche Dokumente.  
* Nutzung der **FormField**‑APIs von Aspose.Words für plattformübergreifende Formularlösungen.

Experimentieren Sie mit verschiedenen Größen, Positionen und Beschriftungen, um Ihr spezifisches Dokumentdesign zu realisieren. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}