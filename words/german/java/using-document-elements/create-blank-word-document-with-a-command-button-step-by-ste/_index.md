---
category: general
date: 2026-08-04
description: Erstellen Sie ein leeres Word‑Dokument und fügen Sie eine Schaltfläche
  mit Aspose.Words ein. Erfahren Sie, wie Sie die Größe der Schaltfläche festlegen
  und eine anklickbare Schaltfläche in C# hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: de
lastmod: 2026-08-04
og_description: Erstellen Sie ein leeres Word-Dokument mit Aspose.Words und fügen
  Sie eine Schaltfläche ein. Diese Anleitung zeigt, wie Sie die Größe der Schaltfläche
  festlegen, eine anklickbare Schaltfläche hinzufügen und die Datei speichern.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Erstelle ein leeres Word‑Dokument und füge eine Schaltfläche hinzu – vollständiges
  C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Leeres Word‑Dokument mit einem Schaltflächenbefehl erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Leeres Word-Dokument mit einem Befehlsbutton erstellen – Schritt‑für‑Schritt‑Anleitung

Wenn Sie ein **blank word document** erstellen müssen, das einen interaktiven Button enthält, zeigt Ihnen dieses Tutorial genau, wie Sie das mit Aspose.Words für .NET erledigen. Sie lernen, **insert command button** einzufügen, das Aussehen anzupassen und es anklickbar zu machen – alles in wenigen Zeilen C#.

Der Leitfaden deckt alles ab, von der Projektkonfiguration bis zum Speichern der finalen Datei, sodass Sie die komplette Lösung in Ihre eigene Anwendung copy‑paste können. Auf dem Weg erklären wir außerdem, wie man **add clickable button**, **set button size** und **create command button** programmgesteuert umsetzt.

## Voraussetzungen

* .NET 6.0 SDK oder neuer installiert.
* Visual Studio 2022 (oder eine IDE, die .NET unterstützt).
* Aspose.Words for .NET NuGet‑Paket (`Aspose.Words` Version 23.12 oder neuer).
* Grundlegende Kenntnisse in C# und objektorientierter Programmierung.

Keine zusätzlichen Office‑Interop‑Assemblies sind erforderlich, da Aspose.Words vollständig unabhängig von Microsoft Word funktioniert.

## Schritt 1: .NET‑Projekt einrichten

Erstellen Sie eine Konsolenanwendung, die den Word‑Automatisierungscode hostet.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Dieser Befehl erstellt einen neuen Ordner `WordButtonDemo` mit einer sofort ausführbaren `Program.cs` und fügt die Aspose.Words‑Bibliothek hinzu.

## Schritt 2: Leeres Word‑Dokument erstellen

Der erste Vorgang ist das **create blank word document**. Aspose.Words stellt die Klasse `Document` bereit, die ein leeres Word‑Dokument sofort bereitstellt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Ein leeres Dokument zu erstellen gibt Ihnen eine saubere Leinwand, auf der Sie Absätze, Tabellen oder in diesem Fall einen OLE‑Befehl‑Button hinzufügen können.

## Schritt 3: DocumentBuilder initialisieren

`DocumentBuilder` ist das Hilfsmittel, mit dem Sie Inhalte in das Dokument einfügen können. Sie müssen es an das Dokument anhängen, das Sie gerade erstellt haben.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder behält die aktuelle Cursor‑Position bei, sodass jede nachfolgende Einfügung genau dort erfolgt, wo Sie es wünschen.

## Schritt 4: Command‑Button einfügen

Jetzt **insert command button** (ein OLE `Forms2OleControl`) in das Dokument. Die Methode `InsertForms2OleControl` benötigt drei Argumente:

1. Die ProgID des OLE‑Steuerelements – `"CommandButton"` für einen Standard‑Button.
2. Ein `Rectangle`, das die **set button size** und Position definiert.
3. Die Beschriftung, die auf dem Button angezeigt wird.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Wenn das Dokument in Word geöffnet wird, verhält sich der Button wie jedes native Formularsteuerelement – Sie können ihn anklicken, und Word führt das zugehörige Makro aus (falls vorhanden). Das erfüllt die Anforderung **add clickable button**.

### Warum Forms2OleControl verwenden?

`Forms2OleControl` bettet ein OLE‑Objekt direkt in die DOCX‑Datei ein und bewahrt die Eigenschaften des Steuerelements, ohne dass die Word‑Interop‑Assembly benötigt wird. Es ist der zuverlässigste Weg, um **create command button** zu erstellen, das über verschiedene Word‑Versionen hinweg funktioniert.

## Schritt 5: Button anpassen (optional)

Vielleicht möchten Sie **set button size** genauer festlegen oder zusätzliche Eigenschaften wie Schriftart oder Hintergrundfarbe ändern. Aspose.Words gibt Zugriff auf das zugrunde liegende OLE‑Objekt, sodass weitere Anpassungen möglich sind.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Falls Sie eine andere Größe benötigen, passen Sie einfach die `Rectangle`‑Werte in Schritt 4 an. Die Koordinaten werden in Punkten gemessen (1 pt = 1/72 Zoll), sodass `120` etwa 1,67 Zoll Breite entspricht.

## Schritt 6: Dokument speichern

Abschließend schreiben Sie das Dokument auf die Festplatte. Die resultierende Datei enthält ein **blank word document** mit einem voll funktionsfähigen Command‑Button.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Wenn Sie `CommandButtonDemo.docx` in Microsoft Word öffnen, sehen Sie einen Button mit der Aufschrift „Click Me“. Ein Klick auf den Button zeigt den Standard‑Makro‑Dialog an, sofern Sie kein benutzerdefiniertes Makro anhängen.

## Vollständiger Quellcode

Unten finden Sie das vollständige Programm, das Sie in `Program.cs` kopieren können. Es enthält alle oben beschriebenen Schritte und lässt sich ohne Änderungen kompilieren.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Erwartetes Ergebnis

Das Ausführen des Programms erzeugt `CommandButtonDemo.docx`. Das Öffnen der Datei in Word zeigt:

* Eine einzelne Seite, die einen Button mit der Beschriftung **Click Me** enthält.
* Der Button respektiert die **set button size** (120 × 30 Punkte).
* Ein Klick auf den Button löst das Standard‑Command‑Button‑Verhalten von Word aus und bestätigt, dass die **add clickable button**‑Operation erfolgreich war.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Funktioniert das mit .doc‑Dateien?** | Ja. Ändern Sie die Dateierweiterung in `doc.Save("file.doc")`. Das OLE‑Steuerelement wird ebenfalls im alten Binärformat gespeichert. |
| **Was, wenn ich mehrere Buttons benötige?** | Rufen Sie `InsertForms2OleControl` mehrfach auf und passen Sie das `Rectangle` für jeden neuen Button an, um Überlappungen zu vermeiden. |
| **Kann ich dem Button ein Makro zuweisen?** | Der Button selbst enthält keinen Makro‑Code. Sie müssen ein VBA‑Makro manuell oder über die `Modules`‑Sammlung des `Document`‑Objekts zum Dokument hinzufügen. |
| **Ist der Button im PDF‑Export sichtbar?** | Wenn Sie das DOCX mit Aspose.Words nach PDF exportieren, wird der Button als statisches Bild gerendert, nicht als interaktives Steuerelement. |
| **Welche Word‑Versionen werden unterstützt?** | Der OLE‑Command‑Button funktioniert in Word 2007 und später, da er der standardmäßigen Forms2.0‑Spezifikation folgt. |

## Fazit

Sie wissen jetzt, wie Sie mit Aspose.Words für .NET ein **blank word document** **insert command button**, **add clickable button** und **set button size** erstellen. Das vollständige Beispiel demonstriert den **create command button**‑Workflow von Anfang bis Ende und liefert Ihnen eine solide Grundlage für weiterführende Word‑Automatisierungsaufgaben.

## Nächste Schritte

* Erkunden Sie weitere OLE‑Steuerelemente (z. B. `CheckBox`, `ListBox`), indem Sie die ProgID in `InsertForms2OleControl` ändern.
* Kombinieren Sie den Button mit einem VBA‑Makro, um benutzerdefinierte Aktionen auszuführen, wenn der Benutzer darauf klickt.
* Verwenden Sie Aspose.Words’ `DocumentBuilder`, um zusätzlichen Inhalt wie Tabellen, Bilder oder Fußnoten hinzuzufügen, bevor Sie den Button einfügen.
* Experimentieren Sie mit **set button size**‑Werten, um sie an die Layout‑Anforderungen Ihres Dokuments anzupassen.

Viel Spaß beim Coden und beim Erstellen umfangreicherer Word‑Dokumente mit interaktiven Steuerelementen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierungsform in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeres Word-Dokument mit schattierter Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}