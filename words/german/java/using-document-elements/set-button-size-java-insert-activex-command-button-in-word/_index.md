---
category: general
date: 2026-07-29
description: 'Button-Größe festlegen Java‑Tutorial: Erfahren Sie, wie Sie mit Java
  und Aspose.Words ein ActiveX‑Befehlsschaltfeld in ein Word‑Dokument einfügen, einschließlich
  Größenanpassung und Erstellung eines leeren Dokuments.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: de
lastmod: 2026-07-29
og_description: Der Leitfaden „Set Button Size Java“ zeigt, wie man mit Java einen
  ActiveX‑Befehlsschalter in eine Word‑Datei einfügt, dessen Größe anpasst und das
  Dokument programmgesteuert speichert.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Buttongröße festlegen Java – ActiveX-Befehlsschaltfläche zu Word mit Java
  hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Buttongröße festlegen in Java – ActiveX‑Befehlsschaltfläche in Word einfügen
url: /de/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – ActiveX‑Befehlsschaltfläche in Word einfügen

Haben Sie sich schon einmal gefragt, **wie man die Button‑Größe in Java festlegt**, wenn Sie Word‑Dokumente automatisieren? Vielleicht bauen Sie ein Reporting‑Tool, das einen anklickbaren „Submit“-Button direkt in der .docx‑Datei benötigt. In diesem Tutorial führen wir Sie durch den gesamten Prozess – ein leeres Word‑Dokument erstellen, eine ActiveX‑Befehlsschaltfläche einfügen und ihre Breite sowie Höhe explizit festlegen – alles mit Java und Aspose.Words.

Wir beantworten zudem die häufig gestellte Frage „**wie man ActiveX einfügt**“, die bei vielen Entwicklern auftaucht. Am Ende haben Sie ein lauffähiges Programm, das eine Word‑Datei mit einer perfekt dimensionierten Schaltfläche erzeugt, bereit für weitere Anpassungen.

---

## Was Sie benötigen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

- **Java Development Kit (JDK) 8 oder neuer** – der Code kompiliert mit jeder aktuellen JDK‑Version.
- **Aspose.Words for Java** (die neueste Version ab Juli 2026). Laden Sie das JAR von der [Aspose-Website](https://products.aspose.com/words/java) herunter oder beziehen Sie es via Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Eine IDE oder ein einfacher Texteditor – IntelliJ IDEA, Eclipse oder VS Code reichen aus.
- Einen Ordner, in dem die erzeugte **CommandButton.docx** abgelegt werden soll.

Das war’s. Keine zusätzlichen Office‑Interop‑Bibliotheken, keine COM‑Tricks, nur reines Java.

---

## Schritt‑für‑Schritt‑Implementierung

Wir teilen die Lösung in fünf logische Schritte auf. Jeder Schritt hat eine eigene H2‑Überschrift; einer davon enthält unser **primäres Schlüsselwort**, um SEO‑Anforderungen zu erfüllen.

### 1. Projekt einrichten und Aspose.Words importieren

Erstellen Sie zunächst ein neues Maven‑ (oder Gradle‑)Projekt und fügen Sie die oben gezeigte Aspose.Words‑Abhängigkeit hinzu. Importieren Sie dann die benötigten Klassen in Ihrer Java‑Quelldatei:

```java
import com.aspose.words.*;
```

> **Pro‑Tipp:** Wenn Sie eine IDE verwenden, lassen Sie sie die Klassen automatisch importieren. Das spart viel Tipparbeit und verhindert Tippfehler.

### 2. java create blank word Document

Jetzt erstellen wir tatsächlich ein **java create blank word**‑Dokument. Das ist die Basis, auf der wir später **insert command button word** einfügen.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Das `Document`‑Objekt repräsentiert die gesamte Word‑Datei im Speicher. Zu diesem Zeitpunkt hat die Datei noch keine Seiten, keinen Text – nur ein leeres Blatt.

### 3. DocumentBuilder initialisieren und das ActiveX‑Steuerelement einfügen

Der `DocumentBuilder` ist ein Helfer, mit dem wir Inhalte, Absätze, Tabellen und, ja, ActiveX‑Steuerelemente hinzufügen können. Hier beantworten wir **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` ist Asposes Wrapper um ein OLE‑Objekt. Durch Angabe von `COMMANDBUTTON` teilen wir Word mit, dass ein klassischer ActiveX‑Befehlsknopf eingebettet werden soll.

### 4. How to Set Button Size Java – Breite und Höhe anpassen

Jetzt kommt der Kern des Tutorials: **how to set button size java**. Das Steuerelement stellt mehrere Layout‑Eigenschaften bereit – `Left`, `Top`, `Width` und `Height`. Durch direktes Setzen dieser Werte steuern Sie das Aussehen des Buttons auf der Seite.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Warum diese Zahlen? In Word entspricht ein Punkt 1/72 Zoll. Eine Breite von `120` Punkten entspricht also etwa 1,67 Zoll – groß genug für eine lesbare Beschriftung, aber nicht überwältigend. Passen Sie die Werte an Ihr Layout an; dieselben Eigenschaften beantworten auch die **how to set button**‑Frage, die Sie möglicherweise haben.

> **Hinweis:** Wenn Sie einen anderen Button‑Typ benötigen (z. B. ein Kontrollkästchen), ersetzen Sie `Forms2OleControlType.COMMANDBUTTON` durch den entsprechenden Enum‑Wert.

### 5. Dokument speichern

Zum Schluss das Dokument auf die Festplatte schreiben:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Ersetzen Sie `YOUR_DIRECTORY` durch einen absoluten oder relativen Pfad auf Ihrem Rechner. Nach dem Ausführen des Programms öffnen Sie die erzeugte Datei in Microsoft Word. Sie sehen einen Button mit der Aufschrift „Click Me“, der 100 pts vom linken Rand und 200 pts vom oberen Rand positioniert ist und exakt die von Ihnen festgelegten Abmessungen hat.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie die komplette, sofort ausführbare Java‑Klasse. Kopieren Sie sie nach `CommandButtonActiveX.java`, passen Sie den Ausgabepfad an und klicken Sie auf **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Erwartete Ausgabe:** Beim Öffnen von `CommandButton.docx` in Word wird eine einzelne Seite mit einem anklickbaren „Click Me“-Button angezeigt, der etwa mittig positioniert ist. Die Button‑Abmessungen entsprechen den von Ihnen gesetzten Werten, was bestätigt, dass **set button size java** wie gewünscht funktioniert.

---

## Häufige Fragen & Sonderfälle

### Was tun, wenn der Button in Word nicht angezeigt wird?

- **Überprüfen Sie die Word‑Version.** ActiveX‑Steuerelemente benötigen die Desktop‑Version von Word; Word Online entfernt sie.
- **Stellen Sie sicher, dass die Aspose.Words‑Lizenz angewendet wurde** (falls Sie eine kostenpflichtige Edition nutzen). Eine nicht lizenzierte Evaluierungsversion kann ein Wasserzeichen einfügen, zeigt das Steuerelement aber weiterhin an.

### Kann ich die Schriftart oder Farbe des Buttons ändern?

Ja. Nach dem Einfügen des Steuerelements können Sie auf das zugrunde liegende OLE‑Objekt zugreifen und die VBA‑Eigenschaften manipulieren. Das ist ein fortgeschritteneres Thema – schauen Sie sich z. B. `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` für eine rote Beschriftung an.

### Wie gehe ich mit dem Klick‑Ereignis des Buttons um?

ActiveX‑Befehlsschaltflächen lösen ein VBA‑`Click`‑Ereignis aus. Damit der Button funktional wird, müssen Sie ein Makro im selben Dokument einbetten. Aspose.Words kann ein Makro‑Modul über die `Document.getMacros()`‑API hinzufügen, aber der Makro‑Code selbst muss in VBA geschrieben werden.

### Was ist mit anderen Button‑Typen?

Aspose.Words unterstützt zahlreiche `Forms2OleControlType`‑Werte: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` usw. Tauschen Sie einfach die Enum‑Konstante im Aufruf von `insertForms2OleControl` aus, um zu experimentieren.

---

## Pro‑Tipps für produktionsreife Code

1. **Konstanten für Layout‑Werte verwenden** – erleichtert zukünftige Anpassungen.
2. **Den Speicherpfad in ein `Path`‑Objekt einbetten**, um plattformspezifische Trennzeichen zu vermeiden.
3. **Das Document‑Objekt freigeben** (oder `try‑with‑resources` nutzen), wenn Sie viele Dateien in einer Schleife verarbeiten.
4. **Den Ausgabepfad prüfen**, bevor Sie `save` aufrufen, um `FileNotFoundException` zu verhindern.

---

## Fazit

Sie haben gerade **set button size java** gelernt, indem Sie ein leeres Word‑Dokument erstellt, ein ActiveX‑Befehlsknopf eingefügt und dessen Abmessungen präzise konfiguriert haben – alles mit wenigen Zeilen Java‑Code. Damit decken Sie die Kernaspekte von **how to insert activex**, **how to set button**, **java create blank word** und **insert command button word** in einem einzigen, eigenständigen Beispiel ab.

Nächste Schritte? Passen Sie die Beschriftung des Buttons an, fügen Sie ein Makro hinzu, das auf Klicks reagiert, oder betten Sie mehrere Steuerelemente auf derselben Seite ein. Sie können zudem das resultierende .docx mit Aspose.Words in PDF konvertieren und den Button als statisches Bild erhalten.

Experimentieren Sie gern, und falls Sie auf Probleme stoßen, hinterlassen Sie einen Kommentar unten. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}