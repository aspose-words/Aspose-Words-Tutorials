---
category: general
date: 2026-10-07
description: Erstellen Sie eine ActiveX‑Schaltfläche in Java und fügen Sie programmgesteuert
  eine Schaltfläche zu Word‑Dokumenten hinzu. Erfahren Sie, wie Sie die linke obere
  Position der Schaltfläche festlegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: de
lastmod: 2026-10-07
og_description: Erstellen Sie eine ActiveX-Schaltfläche in Java, um interaktive Steuerelemente
  in Ihre Word‑Dokumente einzubetten. Erfahren Sie, wie Sie programmgesteuert eine
  Schaltfläche hinzufügen, ihre Position festlegen und ihr Aussehen anpassen.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: ActiveX‑Befehlsschaltfläche in Java erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Wie man in Java einen ActiveX‑Befehlsschalter erstellt
url: /de/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine ActiveX command button in Java erstellt

Wenn Sie **eine ActiveX command button** in einem Word‑Dokument mit Java erstellen müssen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen ein vollständiges, ausführbares Beispiel, das **programmgesteuert eine command button hinzufügt**, sie mit `setLeft` und `setTop` positioniert und das Ergebnis als `.docx`‑Datei speichert.

Das Einbetten einer interaktiven Schaltfläche ermöglicht es Ihnen, Formulare zu erstellen, Workflows zu automatisieren oder Benutzereingaben direkt in einer Word‑Datei zu sammeln. Die nachfolgenden Schritte decken alles von der Projekt‑Einrichtung bis zur abschließenden Überprüfung ab, sodass Sie den Code problemlos in Ihr eigenes Projekt übernehmen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- JDK 17 oder neuer installiert  
- Maven 3.8+ (oder Ihr bevorzugtes Build‑Tool)  
- Aspose.Words for Java 23.9 oder später – die Bibliothek, die `DocumentBuilder` und OLE‑Steuerungsunterstützung bereitstellt  
- Grundlegende Kenntnisse der Java‑Syntax und objektorientierter Konzepte  

Wenn Sie Maven verwenden, fügen Sie die Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Pro‑Tipp:** Verwenden Sie die neueste Aspose.Words‑Version, um von Fehlerbehebungen und neuen OLE‑Funktionen zu profitieren.

## Schritt 1: Erstellen eines neuen leeren Dokuments und eines DocumentBuilder

Der erste Schritt, um **eine ActiveX command button zu erstellen**, besteht darin, ein leeres `Document` und einen `DocumentBuilder` zu instanziieren. Der Builder bietet Ihnen eine fluente API zum Einfügen von Inhalten, einschließlich OLE‑Steuerelementen.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` repräsentiert die Word‑Datei im Speicher, während `DocumentBuilder` als Cursor fungiert, der es Ihnen ermöglicht, Elemente genau dort zu platzieren, wo Sie sie benötigen.

## Schritt 2: Einfügen eines OLE‑command‑button‑Steuerelements

ActiveX‑Steuerelemente werden als OLE‑Objekte eingefügt. Aspose.Words stellt dafür die Klasse `Forms2OleControl` bereit.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Wenn Sie `insertForms2OleControl()` aufrufen, erzeugt Aspose automatisch eine Platzhalter‑Form, die den ActiveX‑Button hosten wird.

## Schritt 3: Konfigurieren der Eigenschaften der Schaltfläche

Jetzt **fügen Sie programmgesteuert die Details der command button** hinzu, wie ProgID, Beschriftung und Größe. Die am häufigsten verwendete ProgID für eine command button ist `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Wie man die linke obere Position der Schaltfläche festlegt

Die Positionierung der Schaltfläche ist der Punkt, an dem das sekundäre Schlüsselwort **how to set button left top** relevant wird. Die Methoden `setLeft` und `setTop` akzeptieren Werte in Punkten (1 Punkt = 1/72 Zoll).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Passen Sie diese Zahlen an Ihr Layout an. Wenn Sie beispielsweise die Schaltfläche an einer Tabellenzelle ausrichten möchten, berechnen Sie die Koordinaten der Zelle und übergeben Sie sie an `setLeft`/`setTop`.

## Schritt 4: Dokument speichern

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Die Datei enthält die ActiveX‑Schaltfläche, die bei Öffnung in Microsoft Word interaktiv ist.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Das Ausführen der `main`‑Methode erzeugt `CommandButton.docx`. Öffnen Sie die Datei in Word, aktivieren Sie den Inhalt, falls Sie dazu aufgefordert werden, und Sie sehen eine anklickbare Schaltfläche mit der Aufschrift **Click Me**, die an den von Ihnen angegebenen Koordinaten positioniert ist.

![Erstelle ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="Screenshot, der die ActiveX command button in Java zeigt, mit der Schaltfläche im Word‑Dokument"}

## Häufige Variationen und Sonderfälle

### Mehrere Schaltflächen hinzufügen

Wenn Sie mehrere Schaltflächen benötigen, wiederholen Sie **Schritt 2** und **Schritt 3** für jedes Steuerelement. Denken Sie daran, `setLeft` und `setTop` anzupassen, damit sich die Schaltflächen nicht überlappen.

### Verhalten der Schaltfläche ändern

ActiveX‑Schaltflächen können beim Klicken VBA‑Makros ausführen. Um ein Makro zuzuweisen, setzen Sie die Eigenschaft `setOnAction` auf den Makronamen:

```java
commandButton.setOnAction("MyMacro");
```

Stellen Sie sicher, dass das Ziel‑Dokument das entsprechende VBA‑Modul enthält; andernfalls zeigt Word einen Fehler an.

### Kompatibilitätshinweise

- Die Schaltfläche funktioniert nur in Desktop‑Versionen von Word, die ActiveX unterstützen (z. B. Word für Windows). In Word für Mac oder Online‑Editoren erscheint sie als statisches Bild.  
- Wenn Sie eine gemischte Umgebung anvisieren, sollten Sie stattdessen ein **Content Control** (`RichTextContentControl`) verwenden.

## Vollständiger Quellcode zum Nachschlagen

Unten finden Sie das komplette, eigenständige Beispiel, das Sie in ein neues Maven‑Projekt kopieren und sofort ausführen können.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Erwartete Ausgabe:** Nach der Ausführung finden Sie `CommandButton.docx` im Arbeitsverzeichnis Ihres Projekts. Öffnet man die Datei in Microsoft Word, wird eine Schaltfläche an der angegebenen Position mit der Aufschrift „Click Me“ angezeigt.

## Fazit

Sie wissen jetzt, wie man **eine ActiveX command button in Java erstellt**, **programmgesteuert eine command button** zu einem Word‑Dokument hinzufügt und ihr Layout mit **how to set button left top**‑Methoden präzise steuert. Diese Technik eröffnet die Möglichkeit, reichhaltige, interaktive Word‑Formulare zu erstellen, die Makros auslösen, externe Anwendungen starten oder Benutzereingaben direkt im Dokument sammeln können.

### Nächste Schritte

- Erkunden Sie weitere ActiveX‑Steuerelemente wie `Forms.TextBox.1` oder `Forms.CheckBox.1`.  
- Kombinieren Sie mehrere Steuerelemente mit einem VBA‑Modul, um vollwertige Formulare zu implementieren.  
- Ersetzen Sie ActiveX durch Content Controls, wenn Sie plattformübergreifende Kompatibilität benötigen.  

Experimentieren Sie gern mit Größe, Beschriftung und Positionierung, um Ihr UI‑Design zu treffen. Bei Problemen prüfen Sie, ob die von Ihnen verwendete Aspose.Words‑Version OLE‑Steuerelemente unterstützt, und vergewissern Sie sich, dass die Sicherheitseinstellungen von Word die Ausführung von ActiveX zulassen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}