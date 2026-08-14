---
category: general
date: 2026-08-14
description: Erstellen Sie eine docx‑ActiveX-Schaltfläche in Java mit Aspose.Words.
  Erfahren Sie, wie Sie programmgesteuert eine Formularschaltfläche in Word hinzufügen
  und das Dokument speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: de
lastmod: 2026-08-14
og_description: Erstellen Sie einen ActiveX‑Button in einer DOCX‑Datei mit Java und
  Aspose.Words. Dieser Leitfaden zeigt, wie man einen Formular‑Button in Word hinzufügt,
  konfiguriert und die Datei speichert.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Erstelle einen docx ActiveX‑Button in Java – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: docx‑ActiveX‑Button in Java erstellen – vollständiger Programmierleitfaden
url: /de/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines docx ActiveX-Buttons in Java – vollständiger Programmierleitfaden

Wenn Sie in Java **docx ActiveX-Button erstellen** müssen, führt Sie dieser Leitfaden durch den gesamten Prozess. Sie sehen, wie Sie einen Formular‑Button in Word hinzufügen, seine Eigenschaften konfigurieren und eine einsatzbereite .docx‑Datei erzeugen.

Die Arbeit mit ActiveX‑Steuerelementen ist ein häufiges Erfordernis beim Automatisieren von Legacy‑Word‑Formularen. In diesem Tutorial lernen Sie, **Formular‑Button‑Word**‑Dokumente mit der Aspose.Words for Java‑Bibliothek hinzuzufügen, sodass Sie interaktive Steuerelemente einbetten können, ohne manuell zu bearbeiten.

## Was Sie benötigen

* Java 17 oder höher (der Code kompiliert mit früheren Versionen, aber Java 17 wird empfohlen).
* Aspose.Words for Java 23.10 oder neuer – laden Sie das JAR von der Aspose‑Website herunter oder fügen Sie die Maven‑Abhängigkeit hinzu.
* Eine IDE (IntelliJ IDEA, Eclipse oder VS Code) oder ein einfacher Texteditor und Befehlszeilen‑Build‑Tools.
* Grundkenntnisse der Java‑Syntax und objektorientierten Programmierung.

## So erstellen Sie einen docx ActiveX‑Button mit Aspose.Words

Die folgenden Schritte zeigen die genaue Reihenfolge, die erforderlich ist, um **docx ActiveX‑Button**‑Objekte zu **erstellen** und in ein Word‑Dokument einzubetten.

### Schritt 1: Projekt einrichten und Aspose.Words importieren

Fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` hinzu, wenn Sie Maven verwenden:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Oder, wenn Sie Gradle bevorzugen:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Nachdem die Abhängigkeit aufgelöst ist, importieren Sie die erforderlichen Klassen in Ihrer Java‑Quelldatei:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Diese Importe geben Ihnen Zugriff auf `Document`, `DocumentBuilder` und die `Forms2OleControl`‑API, die zum Einfügen von ActiveX‑Steuerelementen verwendet wird.

### Schritt 2: Neues leeres Dokument erstellen

Instanziieren Sie ein `Document`‑Objekt, das eine leere Word‑Datei darstellt, die bereit ist, Inhalte zu erhalten.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Das Erstellen des Dokuments zuerst stellt sicher, dass der nachfolgende Builder auf einer sauberen Leinwand arbeitet.

### Schritt 3: DocumentBuilder initialisieren

`DocumentBuilder` bietet eine fluente Schnittstelle zum Einfügen von Text, Bildern und Steuerelementen. Binden Sie ihn an das Dokument, das Sie gerade erstellt haben.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Der Builder verfolgt die aktuelle Cursor‑Position im Dokument, sodass die nächste Einfügung genau dort erfolgt, wo Sie sie benötigen.

### Schritt 4: Ein ActiveX‑CommandButton‑Steuerelement einfügen

Verwenden Sie die Methode `insertForms2OleControl`, um ein ActiveX‑`CommandButton`‑Steuerelement einzubetten. Diese Methode gibt eine `Forms2OleControl`‑Instanz zurück, die Sie weiter konfigurieren können.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Zu diesem Zeitpunkt enthält die .docx‑Datei einen Platzhalter für einen Button, hat jedoch noch keine sichtbare Beschriftung oder Größe.

### Schritt 5: Eigenschaften des Buttons konfigurieren

Setzen Sie den Namen, die Beschriftung und die Layout‑Attribute des Steuerelements. Diese Werte bestimmen, wie der Button in Word erscheint und wie Sie später über VBA oder Automatisierungsskripte darauf verweisen können.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro‑Tipp:** Word misst Positionen in Punkten (1 pt ≈ 1/72 in). Passen Sie `setTop` und `setLeft` an, um den Button mit dem umgebenden Inhalt auszurichten.

### Schritt 6: Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Verwenden Sie die Erweiterung `.docx`, um die Datei im modernen Office Open XML‑Format zu behalten.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Wenn Sie die resultierende Datei in Microsoft Word öffnen, sehen Sie einen **Submit**‑Button, der an den von Ihnen angegebenen Koordinaten positioniert ist. Das Klicken des Buttons in Word löst keine Aktion aus, sofern Sie keinen VBA‑Code anhängen, aber das Steuerelement ist vollständig funktionsfähig für formularbasierte Workflows.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Benötige ich eine spezielle Word-Version?** | ActiveX‑Steuerelemente werden in der Desktop‑Version von Microsoft Word unter Windows unterstützt. Sie sind in Word für Mac oder Word Online nicht verfügbar. |
| **Kann ich das mit `.doc`‑Dateien verwenden?** | Ja. Speichern Sie das Dokument mit der Erweiterung `.doc` (`document.save("ActiveXButton.doc")`). Die gleiche API funktioniert für das ältere Binärformat. |
| **Was ist, wenn der Button nicht angezeigt wird?** | Stellen Sie sicher, dass **Datei → Optionen → Trust Center → Trust Center‑Einstellungen → ActiveX‑Einstellungen** ActiveX‑Steuerelemente zulassen. Überprüfen Sie außerdem, dass das Dokument nicht im „Geschützten Modus“ geöffnet wird. |
| **Kann ich andere ActiveX‑Steuerelemente hinzufügen?** | Absolut. Ersetzen Sie `Forms2OleControlType.COMMAND_BUTTON` durch `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` usw. |
| **Gibt es ein Größenlimit?** | Die Größe des Steuerelements ist nur durch das Seitenlayout begrenzt. Sehr große Abmessungen können zu Layout‑Überläufen führen. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie eine vollständige Java‑Klasse, die Sie kopieren, kompilieren und ausführen können. Sie enthält alle Importe, die `main`‑Methode und Inline‑Kommentare zur Klarheit.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Erwartetes Ergebnis:** Nach dem Ausführen des Programms erscheint `ActiveXButton.docx` im Arbeitsverzeichnis. Beim Öffnen in Microsoft Word wird ein anklickbarer **Submit**‑Button angezeigt, der sich nahe der oberen linken Ecke der ersten Seite befindet.

## Fazit

Sie wissen jetzt, wie Sie in Java mit Aspose.Words **docx ActiveX‑Button**‑Objekte **erstellen**, und Sie haben gesehen, wie Sie **Formular‑Button‑Word**‑Dokumente programmgesteuert **hinzufügen**. Die Schritte – Projekt einrichten, Dokument erstellen, Steuerelement einfügen, Eigenschaften konfigurieren und speichern – decken den gesamten Workflow von Anfang bis Ende ab.

Als Nächstes könnten Sie erkunden:

* Hinzufügen von VBA‑Makros, die auf das Klicken des Buttons reagieren.
* Einbetten anderer ActiveX‑Steuerelemente wie Kontrollkästchen oder Listboxen.
* Automatisieren der Erstellung von mehrseitigen Formularen mit mehreren interaktiven Elementen.

Fühlen Sie sich frei, mit Größen, Positionen und Beschriftungen zu experimentieren, um Ihre spezifischen Formulargestaltungsanforderungen zu erfüllen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wie man HTML lädt und mit Aspose.Words für Java als DOCX speichert](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Wie man PDF‑Dokumente mit Aspose.Words für Java erstellt | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}