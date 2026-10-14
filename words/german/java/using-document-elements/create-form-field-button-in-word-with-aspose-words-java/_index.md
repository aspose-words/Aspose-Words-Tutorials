---
category: general
date: 2026-10-13
description: Erstellen Sie ein Formularfeld‑Button in Word mit Aspose.Words für Java.
  Lernen Sie, wie Sie Befehls‑Button‑Formularfelder einfügen und die Beschriftung
  des Befehls‑Buttons in wenigen einfachen Schritten festlegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: de
lastmod: 2026-10-13
og_description: Erstellen Sie ein Formularfeld‑Button in Word mit Aspose.Words für
  Java. Dieses Tutorial zeigt, wie man Befehls‑Button‑Word‑Felder einfügt und die
  Beschriftung des Befehls‑Buttons schnell festlegt.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Formularfeld-Schaltfläche in Word erstellen – Aspose.Words Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Formularfeld‑Schaltfläche in Word mit Aspose.Words Java erstellen
url: /de/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formularfeld‑Schaltfläche in Word mit Aspose.Words Java erstellen

Wenn Sie **ein Formularfeld‑Schaltfläche** in einem Word‑Dokument erstellen müssen, führt Sie diese Anleitung durch den gesamten Prozess mit Aspose.Words für Java. Egal, ob Sie eine ausfüllbare Formularvorlage bauen oder interaktive Steuerelemente zu einem Bericht hinzufügen – Sie lernen, wie Sie **command button word**‑Formularfelder einfügen und **command button caption** mit minimalem Code setzen.

Das Tutorial deckt alles von der Maven‑Einrichtung bis zu einem vollständig ausführbaren Beispiel ab, sodass Sie den Code kopieren‑einfügen, ausführen und eine `.docx`‑Datei erhalten können, die eine anklickbare Schaltfläche enthält und weiter angepasst werden kann.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- Java 17 (oder neuer) installiert und konfiguriert.
- Maven 3.6+ für das Abhängigkeits‑Management.
- Eine IDE oder einen Text‑Editor Ihrer Wahl (z. B. IntelliJ IDEA, VS Code).
- Eine gültige Aspose.Words‑für‑Java‑Lizenz (die kostenlose Testversion funktioniert für Evaluierungen).

## Schritt 1: Aspose.Words zu Ihrem Maven‑Projekt hinzufügen

Erstellen Sie eine `pom.xml` (oder bearbeiten Sie die bestehende) und fügen Sie die Aspose.Words‑Abhängigkeit ein:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro‑Tipp:** Halten Sie die Versionsnummer aktuell. Neue Releases bringen Unterstützung für die neuesten Word‑Funktionen und verbessern die Performance.

## Schritt 2: Ein leeres Dokument und einen `DocumentBuilder` initialisieren

Die Klasse `DocumentBuilder` bietet eine fluente API zum Bearbeiten eines Word‑Dokuments. In diesem Schritt erstellen wir ein leeres `Document` und binden einen Builder daran.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Das Erstellen des Dokuments ist die Grundlage für das **Erstellen von Formularfeld‑Schaltflächen** später im Tutorial.

## Schritt 3: Ein command button‑Formularfeld einfügen

Aspose.Words stellt die Klasse `Forms2OleControl` für OLE‑Formularsteuerelemente bereit. Um **command button word**‑Formularfelder einzufügen, rufen Sie `insertForms2OleControl` mit dem Enum‑Wert `COMMANDBUTTON` auf.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Die Methode liefert eine Instanz von `Forms2OleControl`, die wir vor dem Speichern konfigurieren können.

## Schritt 4: Größe und Position der Schaltfläche festlegen

Eine command button‑Schaltfläche benötigt explizite Abmessungen und eine Platzierung auf der Seite. Passen Sie Breite, Höhe und Koordinaten an Ihr Layout an.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Das Feintuning dieser Werte stellt sicher, dass die Schaltfläche genau dort erscheint, wo Sie sie im endgültigen Dokument haben möchten.

## Schritt 5: **command button caption** setzen

Der sichtbare Text auf der Schaltfläche wird über die Methode `setCaption` gesteuert. Hier setzen wir die **command button caption**, um den Benutzer zu leiten.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Sie können `"Click Me"` durch jede Beschriftung ersetzen, die zum Zweck Ihres Formulars passt, z. B. `"Submit"` oder `"Approve"`.

## Schritt 6: Das Dokument speichern

Zum Schluss schreiben wir das Dokument auf die Festplatte. Die resultierende Datei enthält die interaktive Schaltfläche und kann in Microsoft Word oder LibreOffice geöffnet werden.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Das Ausführen des Programms erzeugt `CommandButtonDemo.docx`. Öffnet man die Datei in Word, sieht man eine Schaltfläche mit der Beschriftung **Click Me**, positioniert 50 pt vom linken Rand und 100 pt vom oberen Rand der Seite.

### Erwartete Ausgabe

- Eine `.docx`‑Datei namens `CommandButtonDemo.docx`.
- Das Dokument enthält eine einzelne Seite mit einem command button‑Formularfeld.
- Die Schaltfläche zeigt die von Ihnen gesetzte Beschriftung (z. B. **Click Me**).

## Häufige Varianten und Sonderfälle

| Situation | Wie anpassen |
|-----------|--------------|
| **Mehrere Schaltflächen** | Rufen Sie `insertForms2OleControl` wiederholt auf und passen Sie `setLeft`/`setTop` für jede neue Schaltfläche an. |
| **Unterschiedliche Beschriftungen pro Schaltfläche** | Verwenden Sie `setCaption` mit einem eindeutigen String nach jeder Einfügung. |
| **Schaltfläche in einer Tabellenzelle** | Bewegen Sie den Cursor mit `builder.moveTo(cell.getFirstParagraph())` in die gewünschte Zelle, bevor Sie das Steuerelement einfügen. |
| **Legacy‑Word‑Formate (.doc)** | Speichern Sie mit `doc.save("Demo.doc", SaveFormat.DOC);` – die command button‑Schaltfläche bleibt erhalten. |
| **Nur‑Lese‑Formulare** | Nach dem Einfügen `commandButton.setEnabled(false);` setzen, um Benutzerinteraktionen zu verhindern. |

## Tipps für eine robuste Implementierung

- **Abmessungen validieren**: Sehr große Breiten können dazu führen, dass die Schaltfläche über die Seitenränder hinausläuft.
- **Lizenzdurchsetzung**: Ohne gültige Lizenz fügt Aspose.Words dem erzeugten Dokument ein Wasserzeichen hinzu. Laden Sie Ihre Lizenz frühzeitig mit `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testen**: Öffnen Sie die erzeugte Datei in Word und schalten Sie **Design‑Modus** (Entwicklertools → Design‑Modus) ein, um die Eigenschaften der Schaltfläche zu sehen.

## Vollständiger Quellcode‑Rückblick

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Kopieren Sie den Code in eine Datei namens `InsertCommandButtonDemo.java`, kompilieren Sie mit Maven (`mvn compile`) und führen Sie aus (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Das erzeugte Dokument erscheint im Stammverzeichnis Ihres Projekts.

## Fazit

Sie wissen jetzt, wie Sie **ein Formularfeld‑Schaltfläche** in Word mit Aspose.Words für Java **einfügen**, **command button word**‑Formularfelder hinzufügen und **command button caption** programmgesteuert setzen. Dieses End‑zu‑End‑Beispiel bietet Ihnen eine solide Basis für die Erstellung reichhaltiger, interaktiver Word‑Dokumente – egal, ob Sie eine einzelne Submit‑Schaltfläche oder ein komplettes Set von Formularsteuerelementen benötigen.

### Was kommt als Nächstes?

- Erkunden Sie weitere Formularsteuerelemente wie Kontrollkästchen (`Forms2OleControlType.CHECKBOX`) und Textfelder (`Forms2OleControlType.TEXTBOX`).
- Kombinieren Sie Formularfelder mit Seriendruck, um personalisierte Fragebögen zu erzeugen.
- Nutzen Sie die Aspose.Words‑`FormField`‑API, um vom Benutzer eingegebene Daten nach dem Ausfüllen des Dokuments auszulesen.

Experimentieren Sie gern mit verschiedenen Größen, Beschriftungen und Platzierungen. Sobald Sie command buttons beherrschen, wird das Hinzufügen vollwertiger Formulare zu Ihren Word‑Automatisierungspipelines zu einer einfachen Aufgabe. Viel Spaß beim Coden!

### Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}