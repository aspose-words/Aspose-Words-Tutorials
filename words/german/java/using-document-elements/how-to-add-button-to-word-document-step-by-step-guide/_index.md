---
category: general
date: 2026-07-20
description: Wie man mit Aspose.Words einen Button zu einem Word-Dokument hinzufügt.
  Lernen Sie, in wenigen Minuten einen Forms2OleControl‑Button mit DocumentBuilder
  einzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: de
lastmod: 2026-07-20
og_description: Wie man einen Button zu einem Word‑Dokument mit Aspose.Words hinzufügt.
  Folgen Sie dieser praktischen Anleitung, um einen Forms2OleControl‑CommandButton
  mit Java einzubetten.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Wie man einen Button zu einem Word‑Dokument hinzufügt – Komplettes Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Wie man einen Button zu einem Word‑Dokument hinzufügt – Schritt‑für‑Schritt‑Leitfaden
url: /de/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man einen Button zu einem Word-Dokument hinzufügt – Vollständiges Aspose.Words Tutorial

Haben Sie sich jemals gefragt, **wie man einen Button zu einem Word-Dokument hinzufügt**, ohne die UI zu öffnen und herumzuklicken? Sie sind nicht der Einzige. Viele Entwickler müssen interaktive Steuerelemente programmgesteuert einbetten – denken Sie an einen „Submit“-Button in einer Vorlage, die später von einem End‑User ausgefüllt wird. Die gute Nachricht? Mit Aspose.Words für Java können Sie das in ein paar Zeilen erledigen.

In diesem Tutorial gehen wir die genauen Schritte durch, um ein `Forms2OleControl` vom Typ **CommandButton** mit dem `DocumentBuilder` einzufügen. Am Ende haben Sie eine einsatzbereite `.docx`‑Datei, die einen anklickbaren Button mit der Aufschrift „Click Me“ zeigt. Keine Geheimnisse, nur klarer Code und die Begründung hinter jeder Zeile.

## Was Sie lernen werden

- Wie man ein neues Word‑Dokument von Grund auf erstellt.
- Wie man **DocumentBuilder** verwendet, um ein **Forms2OleControl** zu platzieren.
- Warum Sie die Beschriftung des Buttons setzen und die Größe so wählen, wie wir es tun.
- Wie man das Ergebnis speichert und überprüft.
- Häufige Stolperfallen (z. B. fehlende Bibliotheken, nicht unterstützte Steuerelementtypen) und wie man sie vermeidet.

**Voraussetzungen** – Sie benötigen Java 8+ (oder neuer) und die Aspose.Words‑Bibliothek für Java (Version 23.12 oder später). Eine IDE wie IntelliJ IDEA oder Eclipse erleichtert die Arbeit, aber jeder Texteditor reicht aus.

---

## Schritt 1: Projekt einrichten und Abhängigkeiten importieren

Bevor irgendein Code ausgeführt wird, muss Maven (oder Gradle) wissen, wo Aspose.Words heruntergeladen werden kann. Fügen Sie diesen Ausschnitt zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Wenn Sie Gradle bevorzugen, lautet das Äquivalent:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Profi‑Tipp:** Verwenden Sie die neueste Version; ältere Releases könnten die `Forms2OleControl`‑API nicht enthalten.

Sobald die Abhängigkeit aufgelöst ist, können Sie Java‑Code schreiben.

## Schritt 2: Ein neues Dokument erstellen und einen DocumentBuilder erhalten

Die Klasse `Document` repräsentiert das gesamte `.docx`‑Paket, während `DocumentBuilder` der Pinsel ist, mit dem Sie Inhalt darauf malen. Denken Sie an `DocumentBuilder` als den „Cursor“, der weiß, wo das nächste Element hin soll.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:** Das Initialisieren eines frischen `Document` gibt Ihnen eine leere Leinwand. Der Builder zeigt automatisch auf den ersten Absatz, sodass Sie Abschnitte oder Seiten nicht manuell verwalten müssen.

## Schritt 3: Ein Forms2OleControl vom Typ CommandButton einfügen

Jetzt kommt der Star der Show: `insertForms2OleControl`. Diese Methode erstellt ein OLE (Object Linking and Embedding)‑Steuerelement, das Word als Formularelement behandelt. Wir übergeben drei Argumente:

1. `Forms2OleControlType.COMMANDBUTTON` – sagt Word, dass wir einen Button wollen.
2. `100` – Breite in Punkten (≈1,39 Zoll).
3. `30` – Höhe in Punkten (≈0,42 Zoll).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Wie es funktioniert:** Im Hintergrund erzeugt Aspose.Words das passende XML im Teil `word/document.xml` und referenziert das OLE‑Objekt. Die von Ihnen angegebenen Abmessungen werden vom Layout‑Engine von Word respektiert, sodass der Button genau dort erscheint, wo der Builder‑Cursor positioniert ist.

## Schritt 4: Die Beschriftung (Text) des Buttons festlegen

Ein Button ohne Beschriftung ist verwirrend – stellen Sie sich einen stillen Aufzug‑Button vor. Die Methode `setCaption` legt den sichtbaren Text fest:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Sie können die Beschriftung beliebig ändern: „Submit“, „Approve“ oder sogar einen lokalisierten String. Die Beschriftung wird in den Eigenschaften des OLE‑Objekts gespeichert, sodass Word sie nativ rendert.

## Schritt 5: Das Dokument speichern und das Ergebnis überprüfen

Zum Schluss schreiben Sie die Datei auf die Festplatte. Wählen Sie einen Ordner, in den Sie Schreibrechte haben; sonst erhalten Sie eine `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Öffnen Sie `button-demo.docx` in Microsoft Word. Sie sollten einen Button mit der Aufschrift **Click Me** oben im Dokument sehen. Ein Klick darauf löst das Standard‑OLE‑Verhalten aus (in der Regel eine Platzhalter‑Meldung, es sei denn, Sie binden ein Makro ein).

## Häufige Randfälle und wie man sie behandelt

| Situation | Warum es passiert | Lösung |
|-----------|-------------------|--------|
| **Missing `Forms2OleControl` type** | Ältere Aspose.Words‑Versionen haben dieses Enum nicht bereitgestellt. | Auf 23.12+ oder neuer aktualisieren. |
| **Button appears as a picture** | Word‑Sicherheitseinstellungen blockieren OLE‑Steuerelemente. | „Zugriff auf das VBA‑Projektobjektmodell vertrauen“ im Trust Center aktivieren oder ein makro‑aktiviertes `.docm` verwenden. |
| **Incorrect size** | Verwechslung zwischen Punkten und Pixeln. | Denken Sie daran: 1 Punkt = 1/72 Zoll. Zahlen entsprechend anpassen. |
| **Saving throws `FileNotFoundException`** | Pfad existiert nicht. | Sicherstellen, dass das Verzeichnis (`output/`) vor `doc.save` erstellt wird. Verwenden Sie `new File("output").mkdirs();`. |

## Erweiterung des Beispiels: Mehrere Buttons oder andere Steuerelemente hinzufügen

Wenn Sie mehr als einen Button benötigen, bewegen Sie den Builder‑Cursor einfach mit `builder.moveTo` oder `builder.writeln()` bevor Sie erneut `insertForms2OleControl` aufrufen.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Sie können auch ein **CheckBox**, **ComboBox** oder **ListBox** einfügen, indem Sie `Forms2OleControlType.COMMANDBUTTON` durch den passenden Enum‑Wert (`CHECKBOX`, `COMBOBOX` usw.) ersetzen. Die gleichen Breiten‑/Höhen‑Parameter gelten.

## Wie das in größere Word‑Automatisierungs‑Workflows passt

- **Template Generation:** Erstellen Sie eine Vertragsvorlage, die einen „Approve“-Button für nachgelagerte Freigaben enthält.
- **Reporting:** Generieren Sie einen Tagesbericht mit einem „Refresh Data“-Button, der ein Makro auslöst.
- **Form Distribution:** Versenden Sie einen Fragebogen mit vorab ausgefüllten interaktiven Steuerelementen.

All diese Szenarien profitieren von dem **Word‑Automation**‑Ansatz, den wir demonstriert haben. Durch das programmgesteuerte Einbetten von Steuerelementen eliminieren Sie manuelle Bearbeitung und reduzieren menschliche Fehler.

## Vollständiger Quellcode (zum Kopieren‑Einfügen bereit)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Erwartete Ausgabe:** Wenn Sie `output/button-demo.docx` in Microsoft Word öffnen, sehen Sie zwei Buttons – „Click Me“ und „Submit“ – vertikal gestapelt oben in der Datei.

## Fazit

Wir haben **wie man einen Button zu einem Word‑Dokument hinzufügt** mit Aspose.Words für Java Schritt für Schritt beantwortet. Ausgehend von einem leeren `Document` haben wir **DocumentBuilder** genutzt, um ein `Forms2OleControl` vom Typ **CommandButton** einzufügen, eine freundliche Beschriftung zu setzen und das Ergebnis zu speichern. Der Ansatz skaliert auf mehrere Steuerelemente und lässt sich nahtlos in breitere **Word‑Automation**‑Pipelines integrieren.

Bereit für die nächste Herausforderung? Versuchen Sie, den Button durch eine **CheckBox** zu ersetzen oder binden Sie ein Makro ein, das reagiert, wenn der Benutzer den Button in einer `.docm`‑Datei anklickt. Das gleiche Muster gilt – einfach das Enum ändern und die Beschriftung anpassen.

Falls Sie Probleme haben, prüfen Sie noch einmal Ihre Bibliotheks‑Version und die Zugriffsrechte des Ausgabeverzeichnisses. Hinterlassen Sie gern einen Kommentar unten mit Fragen oder teilen Sie Ihren eigenen Anwendungsfall. Viel Spaß beim Coden!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Features meistern und alternative Implementierungs‑Ansätze in Ihren eigenen Projekten erkunden können.

- [Wie man Formularelemente erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Inline‑Bild in Word‑Dokument mit Aspose.Words einfügen](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Gruppiertes Shape in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}