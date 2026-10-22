---
category: general
date: 2026-09-18
description: Erstelle ein leeres Dokument in Java und füge einen ActiveX‑Button hinzu.
  Lerne, wie man einen Befehls‑Button einfügt, ein interaktives Formular erstellt
  und ein Word‑Dokument speichert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: de
lastmod: 2026-09-18
og_description: Erstellen Sie ein leeres Dokument in Java und betten Sie einen ActiveX‑Befehlsschalter
  ein. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung, um ein interaktives Formular
  zu erstellen und die Word‑Datei zu speichern.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Leeres Dokument mit einer interaktiven Schaltfläche in Word erstellen
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Ein leeres Dokument mit einer interaktiven Befehlsschaltfläche in Word mit
  Java erstellen
url: /de/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines leeren Dokuments mit einer interaktiven Schaltfläche in Word mit Java

Wenn Sie ein **leeres Dokument erstellen** müssen, das eine anklickbare Schaltfläche enthält, zeigt Ihnen diese Anleitung genau, wie Sie dies mit Aspose.Words für Java tun. Sie lernen, ein interaktives Formular zu erstellen, eine ActiveX‑Schaltfläche hinzuzufügen und schließlich die Word‑Datei zu speichern – alles in wenigen prägnanten Schritten.

Das Einbetten einer Schaltfläche verwandelt ein statisches .docx in ein funktionales Formular, mit dem Endbenutzer direkt in Microsoft Word interagieren können. Dieses Tutorial behandelt außerdem **wie man eine Schaltfläche einfügt**, behandelt gängige Stolpersteine und erweitert die Lösung für komplexere Formulare.

## Voraussetzungen

* Java 17 oder höher (der Code kompiliert mit JDK 17+)
* Aspose.Words für Java 23.9 oder neuer – die Bibliothek stellt `Document`, `DocumentBuilder` und `Forms2OleControl` bereit.
* Eine IDE oder ein Build‑Tool (Maven/Gradle), das die Aspose.Words‑Abhängigkeit hinzufügen kann.
* Grundkenntnisse der Java‑Syntax und von Word‑Dokumentkonzepten.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Schritt 1: Leeres Dokument erstellen

Der erste Vorgang besteht darin, ein neues `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine leere Word‑Datei dar, die bereit für Inhalte ist.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Ein leeres Dokument zu erstellen gibt Ihnen eine saubere Leinwand, was wichtig ist, wenn Sie **Word‑Dokument erstellen** programmgesteuert ohne vorhandene Vorlage erzeugen möchten.

## Schritt 2: DocumentBuilder initialisieren

`DocumentBuilder` ist die Hauptklasse zum Hinzufügen von Text, Tabellen und Formularsteuerelementen. Sie arbeitet auf dem `Document`, das Sie gerade erstellt haben.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder behält den aktuellen Einfügepunkt bei, sodass nachfolgende Befehle die richtige Stelle in der Datei betreffen.

## Schritt 3: Ein Forms2Ole‑Befehlsschaltflächen‑Steuerelement einfügen

Aspose.Words stellt die Klasse `Forms2OleControl` für ActiveX‑Steuerelemente bereit. Um **ActiveX‑Schaltfläche hinzufügen** zu erledigen, fordern Sie vom Builder einen Typ `COMMANDBUTTON` an.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Die Methode `insertForms2OleControl` fügt das Steuerelement an der aktuellen Cursorposition des Builders ein. Da das Steuerelement ein ActiveX‑Objekt ist, funktioniert es nur in der Desktop‑Version von Microsoft Word, nicht in Word Online.

## Schritt 4: Aussehen und Position der Schaltfläche konfigurieren

Sie können die Beschriftung, Größe und Position der Schaltfläche über die Setter des Steuerelements festlegen. Positionswerte werden in Punkten gemessen (1 Punkt = 1/72 Zoll).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Warum diese Eigenschaften konfigurieren?* Das Setzen von `Top` und `Left` stellt sicher, dass die Schaltfläche dort erscheint, wo Sie sie auf der Seite erwarten, während `Caption` die für den Benutzer sichtbare Beschriftung definiert. Wenn Sie Breite/Höhe weglassen, weist Word Standardmaße zu, die möglicherweise nicht Ihrem Design entsprechen.

### Profi‑Tipp
Wenn Sie mehrere Steuerelemente hinzufügen möchten, rufen Sie vor jeder Einfügung `builder.moveToDocumentEnd()` auf, um überlappende Objekte zu vermeiden.

## Schritt 5: Dokument mit eingebetteter Schaltfläche speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Die Dateierweiterung muss `.docx` sein (oder `.doc` für ältere Word‑Versionen), um das ActiveX‑Steuerelement zu erhalten.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Wenn Sie `CommandButton.docx` in Microsoft Word öffnen, sehen Sie eine Schaltfläche mit der Beschriftung **Click Me**. Ein Klick darauf löst die Standard‑ActiveX‑Aktion aus (die standardmäßig nichts tut). Sie können später ein Makro oder VBA‑Skript anhängen, um benutzerdefiniertes Verhalten zu definieren.

## So fügen Sie eine Schaltfläche in ein bestehendes Formular ein (optional)

Wenn Sie bereits ein Formular mit Textfeldern haben und ein **interaktives Formular erstellen** möchten, das eine Schaltfläche enthält, folgen Sie diesen zusätzlichen Schritten:

1. Laden Sie das vorhandene Dokument: `Document doc = new Document("ExistingForm.docx");`
2. Verschieben Sie den Builder an die gewünschte Position: `builder.moveToParagraph(5, 0); // 6. Absatz, erster Knoten`
3. Fügen Sie die Schaltfläche wie in Schritt 3 gezeigt ein.
4. Passen Sie `Top`/`Left` der Schaltfläche basierend auf dem Layout des Absatzes an.

Dieser Ansatz ermöglicht es Ihnen, jede vorgefertigte Word‑Vorlage mit einer ActiveX‑Schaltfläche zu erweitern, ohne die gesamte Datei neu zu erstellen.

## Randfälle und Fehlersuche

| Situation | Was zu prüfen ist | Empfohlene Lösung |
|-----------|-------------------|-------------------|
| Schaltfläche erscheint nicht in Word | Stellen Sie sicher, dass Sie die Datei in der Desktop‑Version von Word geöffnet haben (Word Online entfernt ActiveX). | Öffnen Sie die Datei in Word 2016+ Desktop. |
| Beschriftung ist abgeschnitten | Prüfen Sie, ob die Schaltflächenbreite groß genug ist, um den Text zu enthalten. | Erhöhen Sie `setWidth`, bis die Beschriftung passt. |
| Save wirft `IOException` | Bestätigen Sie, dass das Ausgabeverzeichnis existiert und Sie Schreibrechte haben. | Erstellen Sie das Verzeichnis oder führen Sie das Programm mit erhöhten Rechten aus. |
| Mehrere Schaltflächen überlappen | Der Cursor des Builders hat sich nach der vorherigen Einfügung möglicherweise nicht bewegt. | Rufen Sie `builder.moveToDocumentEnd()` vor dem Einfügen jedes neuen Steuerelements auf. |

## Vollständiges ausführbares Beispiel

Unten finden Sie ein vollständiges, eigenständiges Java‑Programm, das Sie kopieren, kompilieren und ausführen können. Es demonstriert **leeres Dokument erstellen**, **ActiveX‑Schaltfläche hinzufügen** und **Word‑Dokument speichern** in einem Durchlauf.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document created: CommandButton.docx
```

Das Öffnen von `CommandButton.docx` zeigt eine einzelne Seite mit einer Schaltfläche, die mit **Click Me** beschriftet ist und 100 pt vom oberen und linken Rand positioniert ist.

## Fazit

Sie wissen jetzt, wie Sie ein **leeres Dokument erstellen**, eine **ActiveX‑Schaltfläche** einbetten und eine einfache Word‑Datei in ein **interaktives Formular** verwandeln. Durch das Beherrschen von **wie man eine Schaltfläche einfügt** können Sie dieses Muster erweitern, um Kontrollkästchen, Kombinationsfelder oder sogar benutzerdefinierte VBA‑gesteuerte Logik hinzuzufügen.

Als Nächstes sollten Sie diese verwandten Themen erkunden:

* **Interaktives Formular erstellen** mit Textfeldern (`builder.insertField`)  
* **ActiveX‑Schaltfläche hinzufügen**, die ein VBA‑Makro ausführt (`builder.insertOleObject`)  
* **Word‑Dokument erstellen** aus einer Vorlage mit `Document(docTemplatePath)`  
* Konvertieren der resultierenden .docx in PDF, wobei die Schaltfläche erhalten bleibt (Hinweis: PDF rendert die Schaltfläche als statisches Bild).

Experimentieren Sie gern mit der Größe, Position und Beschriftung der Schaltfläche, um Ihr UI‑Design anzupassen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}