---
category: general
date: 2025-12-29
description: Aspose Load Options ermöglichen das Laden von DOCX‑Dateien, wobei Sie
  die Schriftarteinstellungen anpassen und fehlende Schriften erkennen können. Erfahren
  Sie, wie Sie DOCX mit voller Kontrolle laden.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: de
og_description: Aspose Load Options ermöglichen das Laden von DOCX-Dateien, wobei
  Sie die Schriftarteinstellungen anpassen und fehlende Schriften erkennen können.
  Erfahren Sie, wie Sie DOCX mit voller Kontrolle laden.
og_title: Aspose-Ladeoptionen – DOCX mit benutzerdefinierten Schriftarteinstellungen
  laden
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose‑Ladeoptionen – DOCX mit benutzerdefinierten Schriftarteinstellungen
  laden
url: /de/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – DOCX mit benutzerdefinierten Schriftarteinstellungen laden

Haben Sie sich jemals gefragt, wie man eine DOCX-Datei in C# lädt, ohne über fehlende Schriftarten zu stolpern? Sie sind nicht allein. **Aspose Load Options** geben Ihnen die Möglichkeit, genau zu steuern, wie ein Word-Dokument geöffnet wird, sodass Sie benutzerdefinierte Schriftarteinstellungen festlegen und sogar fehlende Schriftarten erkennen können, bevor sie zum Problem werden.

In diesem Tutorial führen wir Sie durch den gesamten Prozess, ein DOCX mit Aspose.Words zu laden, **custom font settings** zu konfigurieren und einen Warn‑Callback einzurichten, der Ihnen mitteilt, welche Schriftarten fehlen. Am Ende können Sie **load word document** Dateien sicher laden, egal welche Schriftarten der ursprüngliche Autor verwendet hat.

> **Voraussetzung** – Sie benötigen Aspose.Words für .NET (neueste Version) in Ihrem Projekt referenziert und grundlegende Kenntnisse in C#. Keine weiteren Bibliotheken sind erforderlich.

## Was Sie lernen werden

- Wie man ein `LoadOptions`‑Objekt erstellt und einen Warn‑Callback anhängt.  
- Wie man `FontSettings` für **custom font settings** einrichtet.  
- Wie man tatsächlich **load docx** ausführt und überprüft, dass fehlende Schriftarten gemeldet werden.  
- Tipps zum Umgang mit Randfällen wie eingebetteten Schriftarten oder netzwerkbasierten Schriftordnern.

## Schritt 1: Aspose.Words installieren und das Projekt vorbereiten

Zuerst stellen Sie sicher, dass Aspose.Words installiert ist. Der einfachste Weg ist über NuGet:

```bash
dotnet add package Aspose.Words
```

Sobald das Paket hinzugefügt wurde, erstellen Sie ein neues C#‑Konsolenprojekt (oder fügen Sie den Code in eine bestehende Anwendung ein). Der Code, den wir schreiben, funktioniert mit .NET 6+ und .NET Framework 4.7.2+, sodass Sie in beiden Fällen abgedeckt sind.

> **Pro‑Tipp:** Wenn Sie .NET Core anvisieren, fügen Sie `using System;` am Anfang der Datei hinzu; die IDE fügt es normalerweise automatisch ein.

## Schritt 2: Aspose Load Options mit einem Warn‑Callback konfigurieren

Jetzt kommen wir zum Kern der Sache—**aspose load options**. Die Klasse `LoadOptions` ermöglicht es Ihnen, die Art und Weise, wie ein Dokument geparst wird, anzupassen. Wir werden sie verwenden, um:

1. Einen Callback anzuhängen, der ausgelöst wird, sobald der Loader eine angeforderte Schriftart nicht finden kann.  
2. Eine `FontSettings`‑Instanz zuzuweisen, die später für **custom font settings** angepasst werden kann.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Warum das wichtig ist:** Ohne einen Warn‑Callback ersetzt Aspose fehlende Schriftarten stillschweigend, was später zu Layout‑Überraschungen führen kann. Durch das Einbinden des Callbacks können Sie **fehlende Schriftarten** frühzeitig **erkennen** und entscheiden, ob Sie eine Ersatzschrift einbetten oder den Benutzer auffordern, die fehlende Schriftart zu installieren.

## Schritt 3: Das DOCX mit den konfigurierten Optionen laden

Mit den vorbereiteten `LoadOptions` ist das Laden eines DOCX einzeilig. Der `Document`‑Konstruktor akzeptiert den Pfad zur Datei und die gerade erstellten Optionen.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Wenn die Quelldatei eine Schriftart referenziert, die nicht im System oder im benutzerdefinierten Ordner vorhanden ist, sehen Sie eine Ausgabe wie:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Dieses sofortige Feedback ist unbezahlbar, wenn Sie eine Batch‑Verarbeitungspipeline erstellen, die visuelle Treue garantieren muss.

## Schritt 4: Das geladene Dokument überprüfen (optional aber hilfreich)

Nach dem Laden möchten Sie vielleicht bestätigen, dass der Inhalt des Dokuments zugänglich ist. Für einen schnellen Plausibilitätstest geben wir den Text des ersten Absatzes aus.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Das Ausführen des Programms liefert jetzt:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Schritt 5: Randfälle & erweiterte Tipps

### 5.1 Umgang mit eingebetteten Schriftarten

Einige DOCX‑Dateien betten die erforderlichen Schriftarten direkt ein. Aspose.Words verwendet diese automatisch, sodass Sie dafür keine Warnungen erhalten. Wenn Sie jedoch bewusst **load word document**‑Dateien laden, die eingebettete Schriftarten entfernen (z. B. nach einer Konvertierung), müssen Sie die fehlenden Schriftarten möglicherweise über `SetFontsFolder` bereitstellen, wie oben gezeigt.

### 5.2 Verwendung eines MemoryStream anstelle eines Dateipfads

Wenn Ihr DOCX in einer Datenbank liegt oder von einer HTTP‑Anfrage kommt, können Sie es aus einem `MemoryStream` laden:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Die gleichen **aspose load options** gelten, und der Warn‑Callback funktioniert weiterhin.

### 5.3 Globale Überschreibung der Schriftart‑Substitution

Wenn Sie fehlende Schriftarten lieber durch einen bestimmten Ersatz (z. B. Arial) ersetzen möchten, können Sie eine Substitutionsregel hinzufügen:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Kombinieren Sie dies mit dem Warn‑Callback, um das Substitutionsereignis zu protokollieren und Ihre Ausgabe konsistent zu halten.

## Schritt 6: Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige, sofort kopier‑und einfüg‑bereite Programm, das alle oben genannten Schritte integriert. Speichern Sie es als `Program.cs`, stellen Sie die NuGet‑Pakete wieder her und führen Sie es aus.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Erwartete Ausgabe

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Wenn keine Schriftarten fehlen, erscheinen die Warnzeilen einfach nicht.

## Visuelle Übersicht

![Beispiel für Aspose Load Options](/images/aspose-load-options.png "Diagramm, das den Aspose Load Options‑Ablauf zeigt")

*Das Diagramm veranschaulicht, wie **Aspose Load Options** zwischen Ihrer Dateiquelle und dem `Document`‑Objekt liegen, die Schriftartauflösung und die Erkennung fehlender Schriftarten übernehmen.*

## Fazit

Wir haben eine vollständige Lösung für **aspose load options** durchgegangen und Ihnen genau gezeigt, **wie man docx** lädt, während **custom font settings** angewendet und **fehlende Schriftarten** erkannt werden. Durch das Konfigurieren eines Warn‑Callbacks und optional das Zeigen von Aspose auf einen benutzerdefinierten Schriftordner erhalten Sie vollständige Sichtbarkeit auf Schriftartprobleme, bevor sie das Rendering beeinflussen.  

Ab hier können Sie verwandte Themen erkunden, wie die **load word document**‑Konvertierung zu PDF, das Hinzufügen von Wasserzeichen oder die Batch‑Verarbeitung von Dutzenden Dateien in einem Ordner. Das gleiche Muster – `LoadOptions` erstellen, Callbacks anhängen und `new Document(...)` aufrufen – funktioniert über die gesamte Aspose.Words‑API hinweg.

Haben Sie Fragen zu einem speziellen Randfall, etwa dem Umgang mit Rechts‑zu‑Links‑Sprachen oder verschlüsselten DOCX‑Dateien? Hinterlassen Sie einen Kommentar oder prüfen Sie die Aspose.Words‑Dokumentation für weiterführende Informationen. Viel Spaß beim Programmieren, und möge Ihre Dokumente stets exakt wie beabsichtigt gerendert werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}