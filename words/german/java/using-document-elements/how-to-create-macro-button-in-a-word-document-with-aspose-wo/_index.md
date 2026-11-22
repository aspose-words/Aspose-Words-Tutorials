---
category: general
date: 2026-11-22
description: Erstellen Sie eine Makrotaste in einem Word-Dokument mit Java. Erfahren
  Sie, wie Sie eine Schaltfläche einfügen, den Text der Schaltfläche festlegen und
  das Makro mit der Schaltfläche verknüpfen, um interaktive Dokumente zu erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: de
lastmod: 2026-11-22
og_description: Erstelle einen Makro‑Button in einem Word‑Dokument mit Java. Dieses
  Tutorial zeigt, wie man einen Befehls‑Button einfügt, den Button‑Text festlegt und
  das Makro mit dem Button verknüpft, um vollständige Interaktivität zu ermöglichen.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Erstelle einen Makro‑Button in einem Word‑Dokument mit Java – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Wie man eine Makrotaste in einem Word‑Dokument mit Aspose.Words für Java erstellt
url: /de/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine Makro‑Schaltfläche in einem Word‑Dokument mit Aspose.Words für Java erstellt

Wenn Sie eine **Makro‑Schaltfläche** in einer Word‑Datei erstellen müssen, führt Sie dieser Leitfaden durch die erforderlichen Schritte. Sie lernen, wie man **Befehlsschaltfläche einfügt**, **Schaltflächentext festlegt** und **Makro mit Schaltfläche verknüpft**, sodass das Dokument vollständig interaktiv wird.

Entwickler betten häufig OLE‑Steuerelemente ein, um VBA‑Makros aus einem Dokument heraus auszulösen. Dieses Tutorial behandelt den kompletten Workflow, von der Projektkonfiguration bis zu einem ausführbaren Java‑Beispiel, das eine **interaktive Schaltfläche** zu einer .docx‑Datei hinzufügt. Es werden keine externen Skripte benötigt – alles läuft innerhalb des Java‑Prozesses.

## Voraussetzungen

* JDK 17 oder höher installiert.
* Maven 3.8+ (oder Gradle) für die Abhängigkeitsverwaltung.
* Aspose.Words für Java 23.9 oder neuer – die Bibliothek stellt `DocumentBuilder` und OLE‑Steuerungs‑APIs bereit.
* Grundlegende Kenntnisse in Java und VBA‑Makros.

Falls einer dieser Punkte fehlt, installieren Sie ihn zuerst; der Rest des Tutorials geht davon aus, dass sie verfügbar sind.

## Wie man eine Makro‑Schaltfläche mit Aspose.Words für Java erstellt

Der Kern der Lösung besteht aus vier Aktionen:

1. **Befehlsschaltfläche** OLE‑Steuerelement in das Dokument einfügen.
2. **Schaltflächentext** (Beschriftung) festlegen, die der Benutzer sieht.
3. **Makro mit Schaltfläche verknüpfen**, sodass ein Klick die gewünschte VBA‑Routine ausführt.
4. **Dokument speichern** mit dem eingebetteten Makro.

Jede Aktion wird im Folgenden in einem eigenen Abschnitt erklärt.

### Schritt 1: Befehlsschaltfläche in das Dokument einfügen

`DocumentBuilder.insertForms2OleControl` erstellt ein OLE‑Steuerelement des angegebenen Typs. Die Konstante `Forms2OleControlType.COMMAND_BUTTON` weist Aspose.Words an, eine Befehlsschaltfläche zu erzeugen, die ein Makro hosten kann.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Warum das wichtig ist:** Das OLE‑Steuerelement dient als Container für das Makro. Ohne es einzufügen gibt es kein visuelles Element, das der Benutzer anklicken kann.

### Schritt 2: Schaltflächentext (Beschriftung) festlegen

Die Beschriftung ist die sichtbare Bezeichnung auf der Schaltfläche. Verwenden Sie `setCaption`, um festzulegen, was der Benutzer sieht.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Warum das wichtig ist:** Klarer Schaltflächentext verbessert die Benutzerfreundlichkeit. Die Methode `setCaption` aktualisiert die `Caption`‑Eigenschaft des OLE‑Steuerelements, die Word als Schaltflächenbeschriftung darstellt.

### Schritt 3: Makro mit Schaltfläche verknüpfen

Ein Makro wird durch seinen Namen identifiziert, zum Beispiel `MyMacro`. Die Methode `setOnClick` speichert diesen Namen im `OnClick`‑Ereignishandler der Schaltfläche.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Warum das wichtig ist:** Das Verknüpfen eines Makros erzeugt das interaktive Verhalten. Wenn der Benutzer die Schaltfläche in Word anklickt, wird die zugehörige VBA‑Routine ausgeführt.

### Schritt 4: Interaktive Schaltfläche zu einem Word‑Dokument hinzufügen

Nach der Konfiguration des OLE‑Steuerelements möchten Sie es möglicherweise positionieren, die Größe ändern oder umgebenden Text hinzufügen. Der `DocumentBuilder` arbeitet weiterhin am Dokument, sodass Sie Absätze vor oder nach der Schaltfläche einfügen können.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Warum das wichtig ist:** Das Speichern als `.docm` bewahrt den Makrocode. Wenn Sie als `.docx` speichern, geht die Makroreferenz verloren.

## Vollständiges ausführbares Beispiel

Unten finden Sie das vollständige Java‑Programm, inklusive Importen, Ausnahmebehandlung und Kommentaren, die jeden Schritt erklären. Kopieren Sie den Code in ein Maven‑Projekt mit der Aspose.Words‑Abhängigkeit und führen Sie ihn aus.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Erwartete Ausgabe

Das Ausführen des Programms erzeugt `MacroButtonDemo.docm`. Beim Öffnen der Datei in Microsoft Word wird angezeigt:

* Ein Absatz, der *„Drücken Sie die Schaltfläche, um das Makro auszuführen:“*.
* Eine Schaltfläche mit der Beschriftung **Run Report** direkt unter dem Absatz.
* Wenn Sie die Schaltfläche anklicken, versucht Word, das Makro `MyMacro` auszuführen. (Sie müssen den tatsächlichen VBA‑Code manuell oder über einen anderen Automatisierungsschritt zum Dokument hinzufügen.)

Falls das Makro nicht existiert, zeigt Word eine Sicherheitswarnung an, was das Standardverhalten für makro‑aktivierte Dokumente ist.

## Häufige Varianten und Sonderfälle

| Szenario | Wie man den Code anpasst |
|----------|--------------------------|
| **Andere Schaltflächenbeschriftung** | Ändern Sie die an `setCaption` übergebene Zeichenkette. |
| **Mehrere Schaltflächen** | Rufen Sie `insertForms2OleControl` wiederholt auf, jeweils mit eigenem `setCaption` und `setOnClick`. |
| **Benutzerdefinierte Makronamen** | Ersetzen Sie `"MyMacro"` durch einen beliebigen gültigen VBA‑Prozedurnamen, z. B. `"ExportToExcel"`. |
| **Beschränkungen der Schaltflächengröße** | Passen Sie die Werte von `setWidth` und `setHeight` an; Word respektiert die angegebenen Punkte. |
| **Makro programmgesteuert einbetten** | Verwenden Sie `Document.getBuiltInDocumentProperties().add("Macros", …)` oder einen separaten VBA‑Injektionsschritt; Aspose.Words schreibt keinen VBA‑Code selbst. |

**Profi‑Tipp:** Testen Sie die erzeugte `.docm` stets auf einem Rechner, bei dem die Makrosicherheit auf *Alle Makros aktivieren* eingestellt ist, während der Entwicklung. In der Produktion signieren Sie das Makro mit einem vertrauenswürdigen Zertifikat, um Sicherheitsabfragen zu vermeiden.

## Fehlersuch‑Checkliste

* **Schaltfläche erscheint nicht** – Stellen Sie sicher, dass das Dokument als `.docm` gespeichert und in einer Word‑Version geöffnet wird, die OLE‑Steuerelemente unterstützt.
* **Makro wird nicht ausgeführt** – Vergewissern Sie sich, dass der Makroname exakt übereinstimmt, einschließlich Groß‑/Kleinschreibung, und dass das Makro im VBA‑Projekt des Dokuments vorhanden ist.
* **Schaltflächenbeschriftung wird abgeschnitten** – Erhöhen Sie die Schaltflächenbreite mit `setWidth`, um längeren Text aufzunehmen.
* **Unerwartete Layoutverschiebung** – Verwenden Sie `builder.moveTo`, um den Cursor präzise zu positionieren, bevor das Steuerelement eingefügt wird.

## Fazit

Sie wissen nun, wie man eine **Makro‑Schaltfläche** in einem Word‑Dokument mit Java **erstellt**, **Befehlsschaltfläche einfügt**, **Schaltflächentext festlegt** und **Makro mit Schaltfläche verknüpft**, um volle Interaktivität zu erreichen. Das vollständige Beispiel demonstriert jeden erforderlichen API‑Aufruf, erklärt, warum jeder Schritt wichtig ist, und bietet Hinweise zu gängigen Varianten.

Als Nächstes könnten Sie erkunden:

* **Interaktive Schaltfläche** zu bestehenden Vorlagen hinzufügen statt zu einem neuen Dokument.
* **VBA‑Code programmgesteuert einfügen** mit dem Open XML SDK oder einem sekundären Automatisierungstool.
* **Mehrere OLE‑Steuerelemente kombinieren** (Kontrollkästchen, Listboxen), um umfangreiche Formulare zu erstellen.

Experimentieren Sie mit verschiedenen Beschriftungen, Makronamen und Schaltflächengrößen, um Ihren konkreten Anwendungsfall zu erfüllen. Viel Spaß beim Programmieren!

## Was Sie als Nächstes lernen sollten?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man eine Befehlsschaltfläche in ein Word‑Dokument mit Java einfügt](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Wie man die Schaltflächenposition in einem Word‑Dokument mit Java festlegt](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Wie man eine ActiveX‑Schaltfläche in Word einfügt – Schaltflächenbeschriftung festlegen](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}