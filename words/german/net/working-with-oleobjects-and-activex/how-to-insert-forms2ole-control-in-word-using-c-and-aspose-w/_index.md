---
category: general
date: 2026-11-22
description: Lernen Sie, ein Forms2Ole‑Steuerelement in Word mit C# einzufügen. Diese
  Schritt‑für‑Schritt‑Anleitung behandelt DocumentBuilder, das Platzieren von Befehls‑Buttons
  und das Speichern der .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: de
lastmod: 2026-11-22
og_description: Fügen Sie das Forms2Ole‑Steuerelement in Word mit C# ein. Befolgen
  Sie diese Anleitung, um eine Schaltfläche mit Aspose.Words und DocumentBuilder hinzuzufügen.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Forms2Ole‑Steuerelement in Word mit C# einfügen – vollständige Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man das Forms2Ole‑Steuerelement in Word mit C# und Aspose.Words einfügt
url: /de/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man das Forms2Ole‑Steuerelement in Word mit C# und Aspose.Words einfügt

Wenn Sie **ein Forms2Ole‑Steuerelement in Word einfügen** müssen, zeigt Ihnen dieses Tutorial genau, wie Sie dies mit C# erledigen. Egal, ob Sie eine ausfüllbare Vorlage erstellen oder die Formularerstellung automatisieren, die nachstehende Lösung ermöglicht es Ihnen, programmgesteuert eine Schaltfläche hinzuzufügen.

Sie lernen, wie Sie ein leeres Dokument erstellen, `DocumentBuilder` verwenden, um das Steuerelement zu platzieren, und das Ergebnis als `.docx` speichern. Der Leitfaden behandelt außerdem häufige Stolperfallen, wie Koordinatensysteme und die Kompatibilität mit älteren Word‑Versionen.

## Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
* Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`)
* Grundlegende Kenntnisse in C# und dem Word‑Objektmodell
* Eine IDE wie Visual Studio oder VS Code

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie eine neue Konsolenanwendung und fügen Sie das Aspose.Words‑Paket hinzu:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

In `Program.cs` importieren Sie die erforderlichen Namespaces:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Profi‑Tipp:** Verwenden Sie die neueste Aspose.Words‑Version, um vollständige Unterstützung für die `Forms2OleControl`‑API zu erhalten.

## Schritt 2: Leeres Dokument erstellen und DocumentBuilder initialisieren

Die Klasse `Document` repräsentiert die Word‑Datei, während `DocumentBuilder` Methoden zum Einfügen von Inhalten bereitstellt.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funktioniert wie ein Cursor; nach dieser Zeile können Sie Elemente überall im Dokument platzieren.

## Schritt 3: Position und Größe der Schaltfläche festlegen

Word misst Koordinaten in Punkten (1 pt ≈ 1/72 in). Die Struktur `Rectangle` aus `System.Drawing` beschreibt die Begrenzungen des Steuerelements.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` positioniert das Steuerelement in der oberen linken Ecke der aktuellen Seite.
* Passen Sie `x` und `y` an, um die Schaltfläche an anderer Stelle zu platzieren (z. B. `new Rectangle(150, 200, 100, 30)`).

## Schritt 4: Das Forms2Ole‑Befehlsschaltfeld einfügen

Verwenden Sie nun `InsertForms2OleControl`, um das Steuerelement hinzuzufügen. Die Methode benötigt den Steuerelementtyp, einen Namen und die oben definierten Begrenzungen.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Das zurückgegebene `Forms2OleControl`‑Objekt ermöglicht das Ändern von Eigenschaften wie `Enabled`, `Visible` oder das spätere Anhängen eines Makronamens.

### Warum Forms2Ole verwenden?

* **Legacy‑Kompatibilität** – Forms2Ole‑Steuerelemente funktionieren in Word 97‑2003 (`.doc`) und neueren `.docx`‑Dateien.
* **Makro‑Unterstützung** – Sie können VBA‑Makros auslösen, was sie ideal für interaktive Vorlagen macht.
* **Präzise Platzierung** – Im Gegensatz zu Inhaltssteuerelementen steuern Sie exakte Koordinaten.

## Schritt 5: Dokument speichern

Schreiben Sie schließlich die Datei auf die Festplatte. Wählen Sie einen Ordner, in den Sie Schreibrechte haben.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Öffnen Sie `output.docx` in Microsoft Word. Sie sehen eine Schaltfläche mit der Beschriftung **ClickMe** in der oberen linken Ecke der ersten Seite. Ein Klick in Word bewirkt nichts, bis Sie ein Makro zuweisen, aber das Steuerelement ist voll funktionsfähig.

## Umgang mit häufigen Sonderfällen

| Situation | Vorgehensweise |
|-----------|----------------|
| **Schaltfläche erscheint außerhalb der Seite** | Stellen Sie sicher, dass die `Rectangle`‑Koordinaten innerhalb der Seitenränder liegen. Verwenden Sie `builder.PageSetup.PageWidth` und `PageHeight`, um sichere Grenzen zu berechnen. |
| **Steuerelement in älteren Word‑Versionen nicht sichtbar** | Speichern Sie das Dokument als `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`), um die Forms2Ole‑Kompatibilität mit Word 97‑2003 zu gewährleisten. |
| **Beschriftung ändern** | Nach dem Einfügen setzen Sie `commandButton.Caption = "Submit";`. |
| **Ein Makro zuweisen** | Setzen Sie `commandButton.MacroName = "MyMacro"`; das Makro muss im VBA‑Projekt des Dokuments vorhanden sein. |
| **Mehrere Schaltflächen** | Wiederholen Sie Schritt 4 mit unterschiedlichen `Rectangle`‑Werten und eindeutigen Namen. |

## Vollständiges, ausführbares Beispiel

Alles zusammengeführt, hier ein eigenständiges Programm, das Sie kopieren, einfügen und ausführen können:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartete Ausgabe:** Nach dem Ausführen des Programms öffnet sich `output.docx` in Word mit einer anklickbaren Schaltfläche mit der Aufschrift *Click Me!* in der oberen linken Ecke der ersten Seite.

## Fazit

Sie wissen jetzt, wie Sie **ein Forms2Ole‑Steuerelement in Word** mit C# und Aspose.Words einfügen. Der Vorgang besteht darin, ein `Document` zu erstellen, ein `Rectangle` zu positionieren und `InsertForms2OleControl` über `DocumentBuilder` aufzurufen. Mit dem vollständigen Codebeispiel und den Hinweisen zu Sonderfällen können Sie Befehls‑schaltflächen in jede automatisierte Word‑Arbeitsablauf integrieren.

### Nächste Schritte

* Weitere `ControlType`‑Werte wie `CheckBox` oder `OptionButton` erkunden.
* Forms2Ole‑Steuerelemente mit VBA‑Makros für interaktive Formulare kombinieren.
* `DocumentBuilder.MoveTo` verwenden, um Schaltflächen an bestimmten Absätzen oder Tabellen zu platzieren.
* Die **Forms2Ole**‑Dokumentation von Aspose.Words für erweiterte Eigenschaftseinstellungen prüfen.

Viel Spaß beim Programmieren und beim Erstellen umfangreicherer Word‑Dokumente mit C# und Aspose.Words!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man eine OLE‑Befehlsschaltfläche in ein Word‑Dokument mit C# einfügt](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Wie man ein ActiveX‑Steuerelement in Word mit Aspose.Words hinzufügt – Schritt‑für‑Schritt‑Anleitung](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Befehlsschaltfläche zu Word‑Dokument mit Aspose.Words hinzufügen – Komplett‑Leitfaden](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}