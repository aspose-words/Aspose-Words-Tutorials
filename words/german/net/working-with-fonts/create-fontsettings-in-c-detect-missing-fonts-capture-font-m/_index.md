---
category: general
date: 2026-03-01
description: Erstellen Sie FontSettings in C#, um fehlende Schriftarten zu erkennen,
  Schriftartmeldungen zu erfassen und fehlende Schriftarten mit Aspose.Words zu behandeln.
  Schritt‑für‑Schritt‑Anleitung für Entwickler.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: de
og_description: Erstellen Sie FontSettings in C#, um fehlende Schriftarten zu erkennen,
  Schriftartnachrichten zu erfassen und fehlende Schriftarten mit Aspose.Words zu
  behandeln. Vollständiges Tutorial mit Code.
og_title: FontSettings in C# erstellen – Fehlende Schriften erkennen & Schriftmeldungen
  erfassen
tags:
- Aspose.Words
- C#
- Font Management
title: FontSettings in C# erstellen – Fehlende Schriftarten erkennen und Schriftmeldungen
  erfassen
url: /de/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen von FontSettings in C# – Fehlende Schriftarten erkennen & Schriftmeldungen erfassen

Haben Sie jemals **FontSettings erstellen** in einem .NET‑Projekt müssen, waren sich aber nicht sicher, wie Sie Schriftarten erkennen können, die auf dem Zielrechner nicht installiert sind? Sie sind nicht allein. In vielen realen Anwendungen – denken Sie an automatisierte Berichtsgeneratoren oder Dokumentenkonverter – können fehlende Schriftarten stillschweigend das Layout zerstören, und Sie merken es erst, wenn das PDF seltsam aussieht.  

Was wäre, wenn Sie **fehlende Schriftarten erkennen**, **Schriftartmeldungen erfassen** und **fehlende Schriftarten behandeln** könnten, bevor sie Ihre Ausgabe ruinieren? Die gute Nachricht ist, dass Aspose.Words das zum Kinderspiel macht. In diesem Tutorial führen wir Sie durch den gesamten Prozess, vom Einrichten des `FontSettings`‑Objekts bis zum Anschließen eines Warn‑Callbacks, das Ihnen genau sagt, welche Glyphen ersetzt wurden.

> **TL;DR:** Am Ende haben Sie eine sofort einsatzbereite C#‑Konsolenanwendung, die jede Schriftartsubstitution protokolliert, sodass Sie entscheiden können, ob Sie einen Ersatz einbetten oder den Benutzer benachrichtigen.

## Voraussetzungen

- .NET 6 SDK (oder eine aktuelle .NET‑Version)  
- Visual Studio 2022 oder VS Code mit C#‑Erweiterungen  
- Eine Aspose.Words für .NET‑Lizenz (die kostenlose Testversion funktioniert für diese Demo)  
- Eine Beispiel‑DOCX, die eine Schriftart referenziert, die nicht installiert ist (z. B. *Comic Sans MS* auf einer Linux‑Box)  

Keine speziellen NuGet‑Pakete über `Aspose.Words` hinaus werden benötigt.

## Schritt 1 – Aspose.Words installieren und das Projekt einrichten

Zuerst erstellen Sie ein neues Konsolenprojekt und binden die Aspose.Words‑Bibliothek ein.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro‑Tipp:** Wenn Sie bereits eine Lösung haben, fügen Sie das Paket einfach über die NuGet‑Package‑Manager‑UI hinzu – das erleichtert die Versionsverfolgung.

## Schritt 2 – FontSettings erstellen (Haupt‑Schlüsselwort erscheint hier)

Der **create FontSettings**‑Schritt ist das Fundament jedes schriftbezogenen Workflows. `FontSettings` teilt Aspose.Words mit, wo nach Schriftarten gesucht werden soll, ob Systemordner verwendet werden und wie im Falle eines Fehlens ausweichend vorgegangen wird.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Warum ist das wichtig? Ohne korrekt konfigurierte `FontSettings` ersetzt die Engine fehlende Glyphen stillschweigend durch die Standardsystemschriftart, und Sie erhalten nie eine Warnung.

## Schritt 3 – LoadOptions mit den FontSettings verbinden

`LoadOptions` ermöglicht es Ihnen, die `FontSettings` an den Dokument‑Lader zu übergeben. Dies ist die Brücke, die der Engine erlaubt, **fehlende Schriftarten** während der `Document`‑Konstruktionsphase zu **erkennen**.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Jetzt wird jedes Mal, wenn Sie ein DOCX mit `loadOptions` laden, Aspose.Words die zuvor eingerichteten `FontSettings` konsultieren.

## Schritt 4 – Einen Warn‑Callback anhängen, um **Schriftartmeldungen zu erfassen**

Aspose.Words gibt Warnungen für verschiedene Bedingungen aus – die Schriftartsubstitution ist eine häufige. Durch Bereitstellung einer Implementierung von `IWarningCallback` können Sie **Schriftartmeldungen** in Echtzeit **erfassen**.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Die Warn‑Handler‑Klasse

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Das Feld `info.Description` enthält eine menschenlesbare Meldung wie *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.“* Das ist genau die Art von Ausgabe, die Sie benötigen, um **fehlende Schriftarten** elegant zu **handhaben**.

## Schritt 5 – Das Dokument laden und den Callback seine Arbeit tun lassen

Mit allem verkabelt ist das Laden des Dokuments unkompliziert. Wenn die Quelldatei eine Schriftart referenziert, die im System fehlt, wird unser Warn‑Handler ausgelöst.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Wenn Sie das Programm ausführen, sehen Sie eine Konsolenausgabe ähnlich wie:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Diese Ausgabe ist der **capture font messages**‑Teil unseres Workflows. Sie können den Handler erweitern, um in eine Datei zu protokollieren, Telemetrie zu senden oder sogar die Konvertierung abzubrechen, wenn kritische Schriftarten fehlen.

## Schritt 6 – Vollständiges funktionierendes Beispiel (Alle Teile zusammen)

Unten finden Sie ein vollständiges, sofort kopier‑fertiges Programm. Fügen Sie es in `Program.cs` ein, passen Sie die Dateipfade an und führen Sie `dotnet run` aus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Erwartete Ausgabe

Wenn Sie das Programm auf einem Rechner ausführen, dem *Comic Sans MS* fehlt, wird etwas Ähnliches ausgegeben:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Sie erhalten außerdem `Result.pdf`, das die ersetzten Schriftarten verwendet und sicherstellt, dass die Konvertierung nie abstürzt.

## Häufige Fragen & Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Was ist, wenn ich möchte, dass die Konvertierung fehlschlägt anstatt zu substituieren?** | Innerhalb von `FontSubstitutionWarningHandler` werfen Sie eine Ausnahme, wenn `info.Description` einen kritischen Schriftartnamen enthält. |
| **Kann ich automatisch eine Ersatzschriftart einbetten?** | Ja. Nachdem Sie eine fehlende Schriftart erkannt haben, können Sie ein Fallback-`FontInfo` von einem bekannten Pfad laden und es über `fontSettings.SetFontsFolder` zu `fontSettings` hinzufügen. |
| **Funktioniert das unter Linux/macOS?** | Absolut. `FontSettings` funktioniert plattformübergreifend; stellen Sie lediglich sicher, dass der Fallback‑Ordner die entsprechenden `.ttf`‑ oder `.otf`‑Dateien enthält. |
| **Ist der Warn‑Callback thread‑sicher?** | Der Callback läuft im selben Thread, der das Dokument lädt, sodass Sie für die Konsolenprotokollierung keine zusätzliche Synchronisation benötigen. Für Multi‑Thread‑Szenarien sollten Sie gemeinsam genutzte Ressourcen schützen. |
| **Wie protokolliere ich Warnungen in eine Datei?** | Ersetzen Sie `Console.WriteLine` durch `File.AppendAllText("font_warnings.log", ...)` oder verwenden Sie ein beliebiges Logging‑Framework (Serilog, NLog). |

## Pro‑Tipps für produktionsreife Schriftarten‑Handhabung

1. **Font‑Lookups zwischenspeichern** – Die Wiederverwendung derselben `FontSettings`‑Instanz über mehrere Dokumentladungen hinweg vermeidet wiederholte Dateisystem‑Scans.  
2. **Whitelist kritischer Schriftarten** – Wenn Ihre Marke eine bestimmte Schriftart erfordert, prüfen Sie deren Vorhandensein frühzeitig und brechen Sie mit einer klaren Fehlermeldung ab.  
3. **`SetFontFolder` rekursiv verwenden** – Das Setzen von `recursive: true` sorgt dafür, dass Unterordner durchsucht werden, was praktisch ist, wenn Sie eine komplette Schriftartensammlung mitliefern.  
4. **Mit `FontSubstitutionSettings` kombinieren** – Sie können Substitutionsregeln feinjustieren (z. B. bevorzugen Sie Schriftarten mit demselben Familiennamen).  

## Fazit

Wir haben gerade **FontSettings erstellt**, `LoadOptions` konfiguriert, um **fehlende Schriftarten zu erkennen**, einen Callback angehängt, der **Schriftartmeldungen erfasst**, und gezeigt, wie man **fehlende Schriftarten** sauber und produktionsreif handhabt. Der gesamte Ablauf passt in ein paar Dutzend Zeilen C#, bietet Ihnen jedoch vollständige Sichtbarkeit über die Schriftlandschaft jedes zu verarbeitenden DOCX.

Als Nächstes könnten Sie erkunden:

- **Fallback‑Schriftarten einbetten** direkt in das Ausgabe‑PDF (`PdfSaveOptions.FontEmbeddingMode`).  
- **Schriftarten programmgesteuert substituieren** basierend auf Unternehmens‑Branding‑Regeln.  
- **Integration in eine CI‑Pipeline** zur automatischen Kennzeichnung von Dokumenten, die nicht autorisierte Schriftarten verwenden.

Probieren Sie es aus, passen Sie den Warn‑Handler an Ihre Bedürfnisse an und lassen Sie Ihre Dokument‑Pipelines mit Zuversicht laufen – keine mysteriösen Layout‑Fehler mehr, die durch unsichtbare Schriftart‑Ersetzungen verursacht werden.

Viel Spaß beim Coden! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}