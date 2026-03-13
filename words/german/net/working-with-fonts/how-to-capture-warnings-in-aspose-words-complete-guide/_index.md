---
category: general
date: 2026-03-13
description: Wie man Warnungen beim Laden von Dokumenten mit Aspose.Words erfasst,
  sowie Tipps zum Umgang mit fehlenden Schriftarten und zum Festlegen benutzerdefinierter
  Schriftarteinstellungen. Erfahren Sie eine vollständige C#‑Lösung.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: de
og_description: Wie man Warnungen beim Laden von Word‑Dateien mit Aspose.Words erfasst,
  sowie praktische Methoden zum Umgang mit fehlenden Schriftarten und zum Festlegen
  benutzerdefinierter Schriftarteinstellungen.
og_title: Wie man Warnungen in Aspose.Words erfasst – Vollständiger Leitfaden
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man Warnungen in Aspose.Words erfasst – Vollständiger Leitfaden
url: /de/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

placeholders. So fine.

Make sure to keep all shortcodes exactly.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen in Aspose.Words erfasst – Vollständige Anleitung

Haben Sie sich jemals gefragt, **wie man Warnungen** erfasst, die erscheinen, wenn Aspose.Words ein Dokument lädt? In vielen realen Projekten sehen Sie Schriftart‑Ersetzungs‑Hinweise, Hinweise zu veralteten Funktionen oder sogar sicherheitsbezogene Meldungen. Sie zu ignorieren ist wie mit einer gesprungenen Windschutzscheibe zu fahren – Sie kommen vielleicht ans Ziel, aber Sie wissen nie, wann etwas kaputt geht.

Die gute Nachricht ist, dass Aspose.Words Ihnen eine saubere, Callback‑basierte Methode bietet, um diese Meldungen abzufangen. In diesem Tutorial führen wir Sie durch ein **vollständiges C#‑Beispiel**, das nicht nur Warnungen erfasst, sondern Ihnen auch zeigt, wie man **fehlende Schriftarten behandelt** und **benutzerdefinierte Schriftarteinstellungen festlegt**, sodass Ihre Dokumente genau wie erwartet gerendert werden.

---

## Was Sie lernen werden

- Konfigurieren Sie `LoadOptions`, um ein benutzerdefiniertes `FontSettings`‑Objekt einzubinden.  
- Registrieren Sie einen Warn‑Callback, der nach `FontSubstitution`‑Ereignissen filtert.  
- Geben Sie Warnungsdetails in der Konsole aus (oder in einem beliebigen Logger Ihrer Wahl).  
- Erweitern Sie die Lösung, um fehlende Schriftarten auf verschiedenen Plattformen elegant zu behandeln.  

Am Ende dieses Leitfadens haben Sie ein sofort einsatzbereites Snippet, das Sie in jedes .NET‑Projekt einfügen können, sowie eine Handvoll praktischer Tipps, um häufige Fallstricke zu vermeiden.

---

## Voraussetzungen

| Anforderung | Warum es wichtig ist |
|-------------|----------------------|
| **Aspose.Words for .NET** (v23.12 oder später) | Die API, die wir verwenden (`LoadOptions`, `IWarningCallback`), befindet sich hier. |
| **.NET 6+** (oder .NET Framework 4.7.2+) | Moderne Sprachfeatures machen den Code sauberer. |
| **Ein Beispiel‑DOCX** (namens `input.docx`) in einem bekannten Ordner | Wir benötigen etwas zum Laden, das eine Warnung auslöst. |
| **Ein Konsolen‑ oder Logging‑Framework** (optional) | Um die erfassten Warnungen in Aktion zu sehen. |

Zusätzliche NuGet‑Pakete sind über Aspose.Words hinaus nicht erforderlich.

---

## Schritt 1: Benutzerdefinierte Schriftarteinstellungen einrichten  

Bevor Sie ein Dokument laden, können Sie Aspose.Words mitteilen, wo nach Schriftarten gesucht werden soll. Dies ist der **Teil zum Festlegen benutzerdefinierter Schriftarteinstellungen** des Puzzles.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Warum das wichtig ist:**  
Wenn ein DOCX eine Schriftart referenziert, die nicht auf dem Rechner installiert ist, wird Aspose.Words stillschweigend eine Ersatzschriftart verwenden *es sei denn*, Sie haben einen Ordner mit den benötigten Schriftarten konfiguriert. Durch das Festlegen eines benutzerdefinierten Ordners verringern Sie die Wahrscheinlichkeit von „Schriftart‑Ersetzungs‑Warnungen“ von vornherein.

> **Pro Tipp:** Unter Linux müssen Sie möglicherweise das Paket `fonts-dejavu-core` oder eine beliebige TrueType‑Sammlung, von der Ihre Dokumente abhängen, hinzufügen.

---

## Schritt 2: Einen Warn‑Callback registrieren  

Aspose.Words implementiert `IWarningCallback`. Wir erstellen einen kleinen Handler, der nur die Warnungen ausgibt, die uns interessieren: fehlende oder ersetzte Schriftarten.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Warum das wichtig ist:**  
Das Szenario **fehlende Schriftarten behandeln** ist jetzt für Sie sichtbar. Anstatt zu raten, welche Schriftart ausgetauscht wurde, erhalten Sie eine klare Beschreibung wie „Font 'Calibri' was substituted with 'Arial'“. Das ist unbezahlbar beim Debuggen von Layout‑Problemen in generierten PDFs oder gedruckten Berichten.

---

## Schritt 3: Das Dokument mit den konfigurierten Optionen laden  

Jetzt laden wir das Dokument endlich in den Speicher, indem wir die zuvor vorbereiteten `LoadOptions` verwenden.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Wenn die Quelldatei eine Schriftart verwendet, die nicht in `C:\MyFonts` vorhanden ist, sehen Sie eine Ausgabe ähnlich wie:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Diese Zeile ist das **Ergebnis zum Erfassen von Warnungen**, das Sie gesucht haben.

---

## Schritt 4: Vollständiges funktionierendes Beispiel (Kopieren‑Einfügen bereit)

Unten finden Sie das gesamte Programm, bereit zum Kompilieren. Fügen Sie es in ein neues Konsolenprojekt ein und führen Sie es aus – stellen Sie nur sicher, dass die Pfade auf reale Orte auf Ihrem Rechner verweisen.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Erwartete Ausgabe:**  

- Wenn alle Schriftarten verfügbar sind:  
  `Document processed. Check console for any warning messages.`  

- Wenn eine Schriftart fehlt:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Schritt 5: Häufige Variationen & Randfälle  

| Situation | Was anzupassen ist |
|-----------|--------------------|
| **Multiple font folders** | Rufen Sie `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` für jeden zusätzlichen Ort auf. |
| **Suppress all warnings** | Implementieren Sie `Warn`, lassen Sie den Körper leer, oder setzen Sie `loadOptions.WarningCallback = null;`. |
| **Capture other warning types** | Prüfen Sie `info.WarningType` gegen `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` usw. |
| **Running on Linux/macOS** | Stellen Sie sicher, dass der Schriftarten‑Ordner Linux‑kompatible `.ttf`/`.otf`‑Dateien enthält; Sie müssen möglicherweise `libfontconfig` installieren. |
| **Large documents** | Erwägen Sie das Streaming des Dokuments (`LoadOptions.LoadFormat = LoadFormat.Docx;`), um den Speicherverbrauch zu reduzieren. |

Wenn Sie diese Szenarien antizipieren, vermeiden Sie Überraschungen beim Wechsel von einer Entwicklungsumgebung zu einer CI‑Pipeline oder einer Cloud‑VM.

---

## Schritt 6: Visuelle Bestätigung (optional)

Wenn Sie einen schnellen visuellen Hinweis bevorzugen, können Sie die erfassten Warnungen in einen kleinen HTML‑Report ausgeben. Hier ist ein winziger Ausschnitt, der die Meldungen in `warnings.html` schreibt:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Nachdem das Dokument geladen wurde, rufen Sie `handler.WriteReport(@"C:\Docs\warnings.html");` auf und öffnen Sie die Datei im Browser. Das Bild unten zeigt, wie der Report aussehen könnte:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt-Text:* **how to capture warnings** – Screenshot der Konsolenausgabe und des HTML‑Reports.

---

## Fazit  

Wir haben **wie man Warnungen** in Aspose.Words erfasst, eine zuverlässige Methode gezeigt, **fehlende Schriftarten zu behandeln**, und Ihnen gezeigt, wie man **benutzerdefinierte Schriftarteinstellungen festlegt** für deterministisches Rendering. Das vollständige Beispiel kann in jede .NET‑Lösung eingefügt werden, und der modulare `FontWarningHandler` lässt sich erweitern, um Ihrer Logging‑ oder Telemetriestrategie zu entsprechen.

Nächste Schritte? Ersetzen Sie die `Console.WriteLine`‑Aufrufe durch einen strukturierten Logger wie Serilog oder senden Sie die Warnungen an Application Insights für Echtzeit‑Monitoring. Sie können auch das `DocumentVisitor`‑Muster erkunden, falls Sie den Inhalt des Dokuments nach dem Laden inspizieren müssen.

Haben Sie Fragen zu anderen Warnungstypen oder Strategien zum Einbetten von Schriftarten? Hinterlassen Sie unten einen Kommentar – happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}