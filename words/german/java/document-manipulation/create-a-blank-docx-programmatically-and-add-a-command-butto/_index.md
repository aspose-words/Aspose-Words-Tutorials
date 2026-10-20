---
category: general
date: 2026-10-20
description: Erstelle ein leeres DOCX programmatisch und bette mit Java einen Befehlsbutton
  ein. Lerne den vollständigen Code zum Erstellen eines Word‑Dokuments, um das Word‑Dokument
  mit einem Button zu speichern und die Beschriftung des Befehlsbuttons festzulegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: de
lastmod: 2026-10-20
og_description: Erstellen Sie programmgesteuert ein leeres DOCX und betten Sie einen
  Befehlsbutton ein. Folgen Sie dieser schrittweisen Java‑Anleitung, um Word mit dem
  Button zu speichern und die Beschriftung des Befehlsbuttons festzulegen.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Ein leeres DOCX programmatisch erstellen – eine Befehlsschaltfläche hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Erstelle ein leeres DOCX programmgesteuert und füge einen Befehlsbutton hinzu
url: /de/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ein leeres DOCX programmatisch erstellen und einen Befehlsbutton hinzufügen

Wenn Sie **ein leeres DOCX programmatisch erstellen** müssen, zeigt Ihnen dieses Tutorial, wie Sie einen Befehlsbutton direkt in die Datei einbetten. Sie erhalten den vollständigen *create word document code*, der ein Word‑Dokument mit einem Button speichert, Ihnen ermöglicht, die **Beschriftung des Befehlsbuttons** festzulegen, und mit der neuesten Aspose.Words for Java‑Bibliothek funktioniert.

Das Einbetten interaktiver Steuerelemente in eine DOCX‑Datei ist nützlich, wenn Sie Vorlagen verteilen möchten, die Makros auslösen, externe Programme starten oder Benutzer einfach mit einem anklickbaren „Click Me“-Button führen. Die nachfolgenden Schritte decken alles ab, von der Initialisierung eines leeren Dokuments bis zum Persistieren der finalen Datei auf dem Datenträger.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder neuer installiert.
* Maven (oder Ihr bevorzugtes Build‑Tool) zur Verwaltung von Abhängigkeiten.
* Aspose.Words for Java 23.9 oder später. Fügen Sie die Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Eine IDE wie IntelliJ IDEA oder VS Code (jeder Editor, der Java unterstützt, ist geeignet).

## Ein leeres DOCX programmatisch erstellen – Schritt für Schritt

Die folgenden Abschnitte unterteilen den Prozess in klare, nummerierte Schritte. Jeder Schritt erklärt **warum** er nötig ist, nicht nur **was** Sie tippen sollen.

### Schritt 1: Ein neues leeres Dokument initialisieren

Ein leeres Dokument ist die Leinwand, auf der Sie den Befehlsbutton platzieren. Aspose.Words stellt dafür die Klasse `Document` bereit.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Warum das wichtig ist*: Das Starten mit einem leeren `Document` stellt sicher, dass keine versteckten Formatierungen oder vorhandenen Steuerelemente die später hinzuzufügende Schaltfläche beeinträchtigen.

### Schritt 2: Einen `DocumentBuilder` einrichten

`DocumentBuilder` ist ein Helfer, mit dem Sie Inhalte einfügen können, einschließlich OLE‑Steuerelementen, ohne sich mit Low‑Level‑Knotenmanipulationen befassen zu müssen.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum das wichtig ist*: Der Builder behält die aktuelle Cursor‑Position bei, sodass die Schaltfläche genau dort platziert wird, wo Sie sie angeben.

### Schritt 3: Einen OLE‑Befehlsbutton einfügen

Word behandelt interaktive Steuerelemente als OLE‑Objekte (Object Linking and Embedding). Aspose.Words stellt dafür `Forms2OleControl` bereit.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Warum das wichtig ist*: Das Einfügen des Steuerelements erzeugt einen Platzhalter, den Sie später konfigurieren können (Typ, Beschriftung, Position).

### Schritt 4: Den Button konfigurieren – Typ, Beschriftung und Position

Sie müssen den Steuerelementtyp (`COMMANDBUTTON`) festlegen, eine für den Benutzer sichtbare Beschriftung setzen und ihn auf der Seite platzieren.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Warum das wichtig ist*:  
* **Typ** teilt Word mit, dass sich das Steuerelement wie ein anklickbarer Button verhält.  
* **Beschriftung** ist der Text, den der Benutzer sieht; das Ändern ist der Weg, **die Beschriftung des Befehlsbuttons** festzulegen.  
* **Left** und **Top** bestimmen die genaue Platzierung, was entscheidend ist, wenn Sie **Befehlsbutton‑Word‑Dokumente** erstellen, die ein präzises Layout benötigen.

### Schritt 5: Das Dokument mit dem eingebetteten Button speichern

Zum Schluss schreiben Sie die Datei auf die Festplatte. Die resultierende Datei kann in Microsoft Word geöffnet werden, wo der Button voll funktionsfähig ist.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Warum das wichtig ist*: Dieser Schritt **speichert Word mit Button**, sodass das Steuerelement auf anderen Rechnern erhalten bleibt. Die Datei kann als Vorlage verteilt oder in automatisierten Bericht‑Generierungspipelines verwendet werden.

## Vollständiges funktionierendes Beispiel

Kopieren Sie die gesamte Klasse unten in eine Datei namens `CommandButtonDemo.java`, passen Sie `YOUR_DIRECTORY` zu einem echten Pfad an und führen Sie sie mit `mvn compile exec:java` aus.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Erwartetes Ergebnis

Wenn Sie `CommandButton.docx` in Microsoft Word öffnen:

* Das Dokument ist vollständig leer, bis auf einen Button mit der Aufschrift **Click Me**.  
* Ein Klick auf den Button zeigt das Standard‑Word‑Verhalten (er tut nichts, solange kein Makro zugeordnet ist) und bestätigt, dass das OLE‑Steuerelement korrekt eingebettet wurde.

## Häufige Fragen & Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich die Größe des Buttons ändern?** | Ja. Verwenden Sie `commandButton.setWidth(double)` und `commandButton.setHeight(double)`, um die Abmessungen in Punkten anzupassen. |
| **Was, wenn ich ein Makro an den Button anhängen muss?** | Der Button selbst ist nur ein OLE‑Steuerelement. Sie müssen ein VBA‑Makro manuell oder über die Aspose.Words `Document`‑API‑Funktion `addMacro` hinzufügen. |
| **Funktioniert der Button in LibreOffice?** | LibreOffice unterstützt nur eingeschränkte OLE‑Steuerelemente. Der Button wird angezeigt, aber das Klick‑Verhalten kann abweichen. |
| **Wie füge ich mehrere Buttons hinzu?** | Wiederholen Sie die Schritte 3‑4 mit einer neuen `Forms2OleControl`‑Instanz. Passen Sie `setLeft`/`setTop` für jeden Button an, um Überlappungen zu vermeiden. |
| **Ist der Code mit .NET kompatibel?** | Die Logik ist gleich, Sie würden jedoch `Aspose.Words` für .NET‑Klassen (`Document`, `DocumentBuilder`, `Forms2OleControl`) verwenden. |

## Tipps aus der Praxis

* **Pro‑Tipp:** Verwenden Sie `builder.moveToDocumentEnd()` bevor Sie den Button einfügen, wenn er ganz am Ende des Dokuments stehen soll, unabhängig vom vorherigen Inhalt.  
* **Achten Sie darauf:** Sehr kleine Werte für `Left`/`Top` können den Button außerhalb des druckbaren Bereichs platzieren, sodass er in Word‑Layout‑Ansicht unsichtbar wird.  
* **Leistungshinweis:** Das Einfügen vieler OLE‑Steuerelemente kann die Dateigröße erhöhen. Wenn Sie nur einen visuellen Hinweis benötigen, überlegen Sie, stattdessen eine einfache `Shape`‑Grafik mit Hyperlink zu verwenden.

## Fazit

Sie wissen jetzt, wie Sie **ein leeres DOCX programmatisch erstellen** und mit Java einen voll funktionsfähigen Befehlsbutton einbetten. Das Tutorial hat den gesamten *create word document code*‑Workflow abgedeckt, gezeigt, wie Sie **Word mit Button speichern**, die korrekte Vorgehensweise zum **Hinzufügen von Befehlsbutton‑Word‑Elementen** demonstriert und erklärt, wie Sie **die Beschriftung des Befehlsbuttons** festlegen.

Ab hier können Sie:

* Weitere OLE‑Steuerelemente (Checkboxen, Kombinationsfelder) für komplexere Formulare hinzufügen.  
* VBA‑Makros anhängen, um dem Button benutzerdefinierte Aktionen zuzuweisen.  
* Diese Technik mit Mail‑Merge kombinieren, um dynamische, interaktive Vorlagen zu erstellen.

Experimentieren Sie gern mit Button‑Stilen, Positionen und zusätzlichen Steuerelementen, um Ihre spezifischen Geschäftsanforderungen zu erfüllen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Create blank word document with a command button – step‑by‑step guide](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Create Blank Word Document with Java – Full Aspose.Words Guide](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}