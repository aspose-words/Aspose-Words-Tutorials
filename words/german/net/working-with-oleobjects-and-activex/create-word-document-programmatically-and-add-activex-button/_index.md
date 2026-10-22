---
category: general
date: 2026-08-10
description: Erstellen Sie ein Word‑Dokument programmgesteuert mit Aspose.Words und
  fügen Sie anschließend eine ActiveX‑Steuerung, einen Word‑Button, hinzu. Fügen Sie
  in wenigen Minuten eine ActiveX‑Befehlsschaltfläche ein.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: de
lastmod: 2026-08-10
og_description: Erstellen Sie ein Word‑Dokument programmgesteuert mit Aspose.Words
  und fügen Sie anschließend einen ActiveX‑Steuerungs‑Button hinzu. Erfahren Sie,
  wie Sie einen ActiveX‑Befehlsschaltfläche schnell einfügen.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Word‑Dokument programmgesteuert erstellen – einen ActiveX‑Button in C# hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Word‑Dokument programmgesteuert erstellen und ActiveX‑Schaltfläche hinzufügen
url: /de/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein Word-Dokument programmgesteuert und fügen Sie eine ActiveX-Schaltfläche hinzu

Wenn Sie **ein Word-Dokument programmgesteuert erstellen** müssen, führt Sie diese Anleitung durch den gesamten Prozess mit Aspose.Words für .NET. Sie lernen außerdem, wie Sie **ActiveX-Steuerelemente für Word** hinzufügen und **ActiveX-CommandButton**-Objekte in einem einzigen, eigenständigen Beispiel einfügen.

Das Erzeugen von Word-Dateien aus Code entfernt den manuellen Schritt, Microsoft Word zu öffnen, und ermöglicht es Ihnen, Berichte, Rechnungen oder datenbasierte Verträge automatisch zu erstellen. Am Ende dieses Tutorials verfügen Sie über eine einsatzbereite C#-Konsolenanwendung, die eine `.docx`‑Datei mit einem interaktiven ActiveX‑CommandButton erzeugt.

## Voraussetzungen

* .NET 6.0 SDK oder neuer (der Code funktioniert auch mit .NET Framework 4.6+)
* Visual Studio 2022 oder jede IDE, die .NET-Entwicklung unterstützt
* Eine gültige Aspose.Words für .NET Lizenz (Sie können den kostenlosen Evaluierungsschlüssel zum Testen verwenden)
* Grundlegende Kenntnisse der C#-Syntax und des Konzepts von COM/ActiveX-Steuerelementen

> **Profi‑Tipp:** Wenn Sie planen, das erzeugte Dokument an Benutzer zu verteilen, die Word nicht installiert haben, betten Sie die Laufzeitdateien des ActiveX-Steuerelements zusammen mit der `.docx` ein oder stellen Sie eine makrofähige Vorlage bereit.

## Word-Dokument programmgesteuert erstellen – Erste Einrichtung

Zuerst fügen Sie das Aspose.Words NuGet‑Paket zu Ihrem Projekt hinzu:

```bash
dotnet add package Aspose.Words
```

Erstellen Sie dann ein neues Konsolenprojekt (falls Sie noch keines haben):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Öffnen Sie die erzeugte `Program.cs`‑Datei – wir werden deren Inhalt durch die vollständige Lösung unten ersetzen.

## Schritt 1: Namespaces importieren und Lizenz konfigurieren

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Warum das wichtig ist*: Durch das Importieren von `Aspose.Words.Drawing` erhalten Sie Zugriff auf `Forms2OleControl`, die Klasse, die ein ActiveX‑Steuerelement in einem Word‑Dokument repräsentiert. Das frühe Setzen einer Lizenz verhindert Laufzeitwarnungen in der Produktion.

## Schritt 2: Ein leeres Dokument und einen DocumentBuilder erstellen

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Das `Document`‑Objekt ist die In‑Memory‑Darstellung einer `.docx`‑Datei. `DocumentBuilder` funktioniert wie ein Cursor, den Sie im Dokument bewegen, um Elemente einzufügen.

## Schritt 3: Ein ActiveX‑CommandButton‑Steuerelement einfügen

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` erstellt ein OLE‑Objekt, das Word als ActiveX‑Steuerelement behandelt. Das Koordinatensystem verwendet Punkte (1 Punkt = 1/72 Zoll), was dem Layout‑Engine von Word entspricht.

## Schritt 4: Die Beschriftung und optionale Eigenschaften der Schaltfläche festlegen

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Das Setzen der `Caption`‑Eigenschaft ist die gängigste Methode, die Schaltfläche zu beschriften. Wenn die Schaltfläche ein VBA‑Makro ausführen soll, weisen Sie den Makronamen `OnAction` zu. Dieses Tutorial konzentriert sich auf den visuellen Teil; die Makro‑Integration wird im Abschnitt „Nächste Schritte“ behandelt.

## Schritt 5: Das Dokument speichern

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Wenn Sie das Programm ausführen, sehen Sie eine Konsolennachricht, die bestätigt, dass `ActiveX_CommandButton.docx` auf die Festplatte geschrieben wurde.

### Vollständiger Quellcode (zum Kopieren und Einfügen bereit)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Das Ausführen des Snippets erzeugt eine Word‑Datei, die einen anklickbaren **ActiveX‑CommandButton** enthält. Öffnen Sie die Datei in Microsoft Word, wechseln Sie in den **Entwurfsmodus** (Registerkarte Entwickler → Entwurfsmodus), und Sie sehen die Schaltfläche genau an der Stelle, an der Sie sie platziert haben.

## Schritt 6: Ergebnis überprüfen

1. Öffnen Sie `ActiveX_CommandButton.docx` in Microsoft Word.  
2. Aktivieren Sie die **Entwickler**‑Registerkarte, falls sie nicht sichtbar ist (`Datei → Optionen → Menüband anpassen → Entwickler aktivieren`).  
3. Klicken Sie auf **Entwurfsmodus**. Die Schaltfläche sollte mit der Beschriftung „Submit“ erscheinen.  
4. Wenn Sie ein `OnAction`‑Makro hinzugefügt haben, klicken Sie die Schaltfläche, während der Entwurfsmodus deaktiviert ist, um das Makro auszulösen.

Falls die Schaltfläche nicht angezeigt wird, stellen Sie sicher, dass die Sicherheitseinstellungen von Word ActiveX‑Steuerelemente zulassen (`Datei → Optionen → Trust Center → Einstellungen des Trust Centers → ActiveX‑Einstellungen`).

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich andere ActiveX‑Typen einfügen?** | Ja. Das `Forms2OleControlType`‑Enum enthält `CheckBox`, `OptionButton`, `ComboBox` usw. Ersetzen Sie `CommandButton` durch den gewünschten Enum‑Wert |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Erstellen einer Gruppierung in einem Word-Dokument mit Aspose.Words für .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Erstellen eines Word-Dokuments mit Kopf‑ und Fußzeile mit Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Einfügen eines Inline‑Bildes in ein Word-Dokument mit Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}