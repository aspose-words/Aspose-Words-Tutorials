---
category: general
date: 2026-11-15
description: Bearbeiten Sie ein Word-Dokument programmgesteuert, um eine Befehls-Schaltfläche
  einzufügen. Erfahren Sie, wie Sie eine Schaltfläche hinzufügen, den Namen der Befehls-Schaltfläche
  festlegen und in wenigen Minuten eine Formular-Schaltfläche in Word erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: de
lastmod: 2026-11-15
og_description: Bearbeiten Sie ein Word-Dokument programmgesteuert und fügen Sie eine
  Befehls-Schaltfläche ein. Diese Anleitung zeigt, wie man eine Schaltfläche hinzufügt,
  den Namen der Befehls-Schaltfläche festlegt und schnell eine Formularschaltfläche
  in Word erstellt.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Word‑Dokument programmgesteuert bearbeiten – eine Befehlsschaltfläche hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Word‑Dokument programmgesteuert bearbeiten und eine Befehlsschaltfläche hinzufügen
url: /de/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert bearbeiten und einen Befehlsbutton hinzufügen

Wenn Sie **Word-Dokument programmgesteuert bearbeiten** müssen, ist der schnellste Weg die Verwendung der Aspose.Words API. Dieses Tutorial zeigt Ihnen genau **wie man Schaltfläche hinzufügt**, deren Beschriftung konfiguriert und **den Befehlsbutton-Namen festlegt**, sodass das Dokument als einfaches Formular fungieren kann. Am Ende haben Sie ein vollständig editierbares *.docx*, das einen funktionalen Befehlsbutton enthält, bereit für die nachgelagerte Verarbeitung.

Sie lernen, wie man **Befehlsschaltflächen-Text einfügt**, **Formularschaltflächen-Text erstellt** und die Eigenschaften von Schaltflächen verwaltet, ohne Word manuell zu öffnen. Die einzige Voraussetzung ist eine grundlegende Java-Entwicklungsumgebung und die Aspose.Words for Java-Bibliothek.

## Voraussetzungen

- Java 17 oder höher (der Code funktioniert auch mit Java 8+)
- Aspose.Words for Java (Download von [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Ein vorhandenes Word-Dokument (`input.docx`), das Sie ändern möchten
- Vertrautheit mit Maven oder Gradle, um die Aspose.Words-Abhängigkeit hinzuzufügen

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Schritt 1: Word-Dokument laden

Der erste Vorgang, wenn Sie **Word-Dokument programmgesteuert bearbeiten**, besteht darin, die Quelldatei in ein `Document`‑Objekt zu laden. Dieses Objekt repräsentiert die gesamte Word‑Datei im Speicher und ermöglicht es Ihnen, deren Inhalt zu manipulieren.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Warum das wichtig ist:** Das Laden des Dokuments erzeugt eine DOM‑ähnliche Struktur, die Aspose.Words traversieren und ändern kann. Das Überspringen dieses Schrittes würde Sie ohne Ziel für das Einfügen der Schaltfläche lassen.

## Schritt 2: Einen `DocumentBuilder` erstellen, um das Dokument zu bearbeiten

Ein `DocumentBuilder` fungiert wie ein Cursor innerhalb der Word‑Datei. Er ermöglicht das Einfügen von Text, Bildern und Formularsteuerelementen an der aktuellen Position.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tipp:** Wenn Sie die Schaltfläche in einem bestimmten Absatz benötigen, bewegen Sie den Builder zuerst mit `builder.moveToParagraph(index, true);`.

## Schritt 3: Ein Forms2OleControl (Befehlsbutton) einfügen

Jetzt beantworten wir die zentrale Frage **wie man Schaltfläche hinzufügt** in einer Word‑Datei. Die Methode `insertForms2OleControl()` erstellt einen Legacy‑*Forms2.0*-Befehlsbutton, der das kompatibelste Steuerelement über alle Word‑Versionen hinweg ist.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Sonderfall:** Das Forms2.0‑Steuerelement ist nur im *Entwurfsmodus* von Word sichtbar. Wenn Sie einen neueren ActiveX‑Button benötigen, sollten Sie stattdessen `insertOleControl()` in Betracht ziehen, aber das Legacy‑Steuerelement funktioniert für die meisten Automatisierungsszenarien.

## Schritt 4: Die Eigenschaften der Schaltfläche konfigurieren

Nach dem Einfügen des Steuerelements können Sie **den Befehlsbutton-Namen festlegen** und **den Befehlsschaltflächen-Text einfügen** (Beschriftung), um es benutzerfreundlich zu machen.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Warum diese Eigenschaften?**  
> - `setName` gibt der Schaltfläche einen Bezeichner, den VBA oder externe Tools referenzieren können.  
> - `setCaption` ist die sichtbare Beschriftung und erstellt effektiv **Formularschaltflächen-Text**, den Endbenutzer anklicken.

Sie können außerdem Größe, Position anpassen oder ein Makro hinzufügen, indem Sie auf das zugrunde liegende OLE‑Objekt zugreifen, aber diese Themen liegen außerhalb des Umfangs dieses kurzen Leitfadens.

## Schritt 5: Das geänderte Dokument speichern

Abschließend speichern Sie die Änderungen in einer neuen Datei. Dieser Schritt **erstellt Formularschaltflächen-Text** im Ausgabedokument.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Ergebnis:** Beim Öffnen von `output.docx` in Microsoft Word sehen Sie eine Schaltfläche mit der Aufschrift „Submit“. Wenn Sie Word in den *Entwurfsmodus* (Entwickler → Entwurfsmodus) schalten, können Sie die Schaltfläche doppelklicken, um ein Makro anzuhängen oder sie einfach als Platzhalter in einem Formular zu verwenden.

### Erwartete Ausgabe

Wenn Sie die gespeicherte Datei öffnen:

- Der Einfügepunkt des Cursors wird durch eine Schaltfläche ersetzt.
- Die Schaltfläche zeigt die Beschriftung **Submit** an.
- Der interne Name der Schaltfläche ist **cmdSubmit**, den Sie in VBA oder externen Automatisierungsskripten referenzieren können.

## Häufige Fragen und Variationen

### Wie fügt man eine Schaltfläche zu einem bestimmten Absatz hinzu?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Wie fügt man eine Schaltfläche in eine Tabellenzelle ein?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Was tun, wenn ich eine größere Schaltfläche benötige?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Wie **Befehlsschaltflächen-Text einfügt** man mit einer anderen Sprache (z. B. C#)?

Die gleiche Logik gilt; ersetzen Sie die Java‑Syntax durch die entsprechenden C#‑Entsprechungen:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Pro‑Tipps und Fallstricke

- **Pro‑Tipp:** Rufen Sie immer `builder.moveToDocumentEnd()` auf, bevor Sie eine Schaltfläche einfügen, wenn Sie sie am absoluten Ende des Dokuments haben möchten.  
- **Achten Sie auf:** Das Speichern in dieselbe Datei, die Sie geöffnet haben, kann das Dokument beschädigen, wenn eine Ausnahme auftritt. Verwenden Sie einen separaten Ausgabepfad wie gezeigt.  
- **Kompatibilität:** Der Legacy‑Forms2.0‑Button funktioniert in Word 2007‑2021. Für Word im Web sollten Sie stattdessen Inhaltssteuerelemente verwenden.  
- **Performance:** Das Laden sehr großer Dokumente (> 100 MB) kann viel Speicher verbrauchen. Verwenden Sie `Document.load(InputStream, LoadOptions)` mit `LoadOptions.setLoadFormat(LoadFormat.DOCX)`, um den Ressourcenverbrauch zu begrenzen.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige, sofort ausführbare Java‑Programm. Kopieren Sie es in eine Klasse mit dem Namen `WordButtonDemo.java`, passen Sie die Dateipfade an und führen Sie `mvn compile exec:java` aus.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Führen Sie das Programm aus und öffnen Sie `output.docx`, um zu überprüfen, ob die Schaltfläche wie erwartet erscheint.

## Fazit

Sie wissen jetzt, wie man **Word-Dokument programmgesteuert bearbeitet**, um **Befehlsschaltflächen-Text einzufügen**, **Formularschaltflächen-Text zu erstellen** und **den Befehlsbutton-Namen festzulegen** mit Aspose.Words für Java. Dieser Ansatz eliminiert manuelle Bearbeitung, ermöglicht die Stapelverarbeitung von Formularen und lässt sich nahtlos in automatisierte Workflows integrieren.

Als Nächstes könnten Sie erkunden:

- Hinzufügen von VBA‑Makros zum Button (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Verwendung von **Inhaltssteuerelementen** für umfangreichere Formulare (`builder.insertCheckBox()` usw.)  
- Automatisierung der Massen‑Einfügung über mehrere Dokumente hinweg mit einer Schleife

Fühlen Sie sich frei, mit der Größe, Position und Ereignisbehandlung der Schaltfläche zu experimentieren, um sie an Ihr spezifisches Szenario anzupassen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man programmgesteuert einen Befehlsbutton in ein Word‑Dokument hinzufügt](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Word‑Dokument programmgesteuert erstellen und ActiveX‑Button hinzufügen](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Befehlsbutton zu Word‑Dokument mit Aspose.Words hinzufügen – Komplett‑Leitfaden](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}