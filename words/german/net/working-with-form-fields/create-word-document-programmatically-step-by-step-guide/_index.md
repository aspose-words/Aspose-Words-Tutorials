---
category: general
date: 2026-08-04
description: Erstellen Sie ein Word‑Dokument programmgesteuert mit C#. Erfahren Sie,
  wie Sie programmgesteuert einen Befehlsbutton mit Aspose.Words in nur wenigen Schritten
  hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: de
lastmod: 2026-08-04
og_description: Erstellen Sie ein Word‑Dokument programmgesteuert mit Aspose.Words.
  Dieser Leitfaden zeigt, wie Sie programmgesteuert eine Schaltfläche hinzufügen,
  sie konfigurieren und die Datei speichern.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Word-Dokument programmgesteuert erstellen – vollständiges C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word‑Dokument programmgesteuert erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert erstellen – vollständiges C#‑Tutorial

Wenn Sie **Word-Dokumente programmgesteuert erstellen** möchten, zeigt Ihnen dieses Handbuch genau, wie Sie das mit Aspose.Words für .NET erledigen. Mit nur wenigen Zeilen C# können Sie eine leere `.docx`‑Datei erzeugen, **programmgesteuert Command‑Button**‑Steuerelemente hinzufügen, deren Eigenschaften festlegen und das Ergebnis speichern.  

Die nachfolgenden Schritte decken alles ab – von der Projektkonfiguration bis hin zur Behandlung von Randfällen – sodass Sie den Code in Ihre eigene Anwendung übernehmen und ohne Änderungen ausführen können.

## Was Sie erreichen werden

* Ein neues Word‑Dokument vollständig im Speicher initialisieren.  
* **Programmgesteuert Command‑Button**‑OLE‑Steuerelemente an beliebiger Position und Größe einfügen.  
* Die Beschriftung, den internen Namen und weitere OLE‑Eigenschaften des Buttons konfigurieren.  
* Das erzeugte Dokument auf Festplatte oder in einen Stream speichern für weitere Verarbeitung.

### Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder eine kostenlose Evaluierung).  
* Grundlegende Kenntnisse in C# und Visual Studio (oder einer IDE Ihrer Wahl).  

> **Pro Tipp:** Wenn Sie das Beispiel ohne Lizenz ausführen, fügt Aspose.Words ein kleines Evaluierungs‑Wasserzeichen zur ersten Seite hinzu.

## Schritt 1: Projekt einrichten und erforderliche Namespaces importieren

Erstellen Sie eine neue Konsolen‑App (oder integrieren Sie sie in einen bestehenden Service) und fügen Sie das Aspose.Words‑NuGet‑Paket hinzu:

```bash
dotnet add package Aspose.Words
```

Fügen Sie anschließend die erforderlichen Namespaces am Anfang Ihrer `.cs`‑Datei ein:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Durch diese Importe erhalten Sie Zugriff auf `Document`, `DocumentBuilder`, `Forms2OleControl` und die Struktur `RectangleF`, die für die Positionierung verwendet wird.

## Schritt 2: Neues Word‑Dokument initialisieren

Der erste Vorgang in jedem **Word‑Dokument programmgesteuert erstellen**‑Workflow besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt existiert nur im Speicher, bis Sie es explizit speichern.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fungiert wie ein Cursor, der verfolgt, wo das nächste Element eingefügt wird. Die Verwendung hält den Code kompakt und spiegelt die Art und Weise wider, wie Sie direkt in Word tippen würden.

## Schritt 3: Command‑Button‑OLE‑Steuerelement einfügen

Aspose.Words stellt die Methode `InsertForms2OleControl` bereit, um OLE‑Objekte wie Command‑Buttons, Kontrollkästchen oder Kombinationsfelder einzubetten. Die Methode benötigt drei Argumente:

1. Den `ControlType`‑Enum‑Wert (hier `CommandButton`).  
2. Ein `RectangleF`, das die X‑Y‑Position sowie Breite‑Höhe des Steuerelements definiert (gemessen in Punkten, wobei 72 pt = 1 inch).  
3. Optional zusätzliche OLE‑Eigenschaften (für den Basis‑Button nicht erforderlich).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Warum das funktioniert:** `InsertForms2OleControl` erstellt einen OLE‑Container im Dokument und gibt ein `Forms2OleControl`‑Wrapper‑Objekt zurück. Der Wrapper ermöglicht es Ihnen, das zugrunde liegende OLE‑Objekt (den eigentlichen Button) zu manipulieren, ohne sich mit Low‑Level‑COM‑Interop befassen zu müssen.

## Schritt 4: Beschriftung und internen Namen des Buttons konfigurieren

Nach dem Einfügen möchten Sie dem Button in der Regel eine für den Benutzer sichtbare Beschriftung und einen internen Bezeichner zuweisen, auf den Ihr Makro oder Add‑In später zugreifen kann.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` ist der im Word‑UI auf dem Button angezeigte Text.  
* `Name` ist der programmgesteuerte Bezeichner, der von VBA oder externen Automatisierungsskripten verwendet wird.

### Optional: Makro dem Button zuweisen

Wenn Sie planen, beim Klicken des Buttons ein VBA‑Makro auszuführen, können Sie den Makronamen zuweisen:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Randfall:** Wenn das Ziel‑Dokument auf einem Rechner ohne das Makro geöffnet wird, zeigt Word eine Sicherheitswarnung an. Signieren Sie Ihre Makros immer oder informieren Sie die Benutzer über die erforderlichen Einstellungen.

## Schritt 5: Dokument speichern

Sie können die Datei auf die Festplatte, in einen `MemoryStream` oder direkt in ein Response‑Objekt einer Web‑API schreiben. Der einfachste Ansatz für eine Konsolen‑Demo besteht darin, in einen lokalen Ordner zu speichern:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Das resultierende `.docx` öffnet sich in Microsoft Word mit einem funktionierenden Command‑Button, der „Click Me“ anzeigt. Ein Klick auf den Button löst das zugewiesene Makro aus (falls vorhanden) oder zeigt einfach eine Standardnachricht an.

## Vollständiges funktionierendes Beispiel

Kopieren Sie das folgende Programm in `Program.cs` und führen Sie es aus. Es demonstriert den gesamten **Word‑Dokument programmgesteuert erstellen**‑Ablauf, einschließlich Fehlerbehandlung.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Erwartetes Ergebnis:** Beim Öffnen von `CommandButton.docx` in Word wird ein Button mit der Beschriftung „Click Me“ angezeigt. Wenn Sie mit der Maus über den Button fahren, wird im Eigenschaften‑Paneel der Name `cmdClickMe` angezeigt.

## Häufige Fragen und Fehlersuche

| Frage | Antwort |
|----------|--------|
| *Kann ich den Button zu einem bestehenden Dokument hinzufügen?* | Ja. Laden Sie die Datei mit `new Document("Existing.docx")` und verwenden Sie anschließend denselben Aufruf von `InsertForms2OleControl`. |
| *Welche Einheit verwendet `RectangleF`?* | Punkte (1 inch = 72 pt). Passen Sie die Werte an, um den Button exakt zu positionieren. |
| *Funktioniert der Button in Word für Mac?* | OLE‑Steuerelemente werden nur in Word für Windows unterstützt. Auf dem Mac erscheint der Button als statisches Bild. |
| *Benötige ich eine Lizenz für den Produktionseinsatz?* | Eine kommerzielle Lizenz entfernt Evaluierungs‑Wasserzeichen und schaltet die volle Funktionalität frei. |
| *Wie ändere ich die Größe des Buttons nach dem Einfügen?* | Ändern Sie `commandButton.Width` und `commandButton.Height` oder fügen Sie ihn erneut mit einem neuen `RectangleF` ein. |

## Lösung erweitern

Jetzt, da Sie wissen, wie Sie **programmgesteuert Command‑Button**‑Steuerelemente hinzufügen**, können Sie diese verwandten Themen erkunden:

* **Andere Formularsteuerelemente einfügen** – verwenden Sie `ControlType.CheckBox`, `ControlType.OptionButton` usw. (deckt das sekundäre Stichwort *Aspose.Words InsertForms2OleControl* ab).  
* **Dokument mit dynamischen Daten füllen** – Daten aus einer Datenbank in Tabellen oder Seriendruckfelder einfügen.  
* **Export nach PDF** – nach dem Hinzufügen des Buttons rufen Sie `doc.Save("output.pdf", SaveFormat.Pdf)` auf, um eine PDF‑Version zu erzeugen (relevant für *C# Word automation*).  

## Fazit

Sie verfügen nun über ein vollständiges, produktionsreifes Muster zum **Word‑Dokument programmgesteuert erstellen** und **programmgesteuert Command‑Button**‑Steuerelemente hinzufügen** mit Aspose.Words für .NET. Das Tutorial behandelte die Projektkonfiguration, Dokumentinitialisierung, OLE‑Button‑Einfügung, Eigenschaftskonfiguration und das Speichern der Datei. Passen Sie den Code gerne an, um weitere Formularsteuerelemente einzufügen, Makros zuzuweisen oder die Logik in Web‑Services oder Hintergrundjobs zu integrieren.

Viel Spaß beim Coden und beim Automatisieren von Word‑Dokumenten!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Word‑Dokument mit Tabelle erstellen mit Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Gruppiertes Shape in Word‑Dokument erstellen mit Aspose.Words für .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}