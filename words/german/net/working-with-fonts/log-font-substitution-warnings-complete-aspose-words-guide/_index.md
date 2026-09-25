---
category: general
date: 2026-01-14
description: Protokollieren Sie Warnungen zur Schriftartsubstitution beim Laden von
  Word‑Dokumenten mit Aspose.Words. Erfahren Sie, wie Sie fehlende Schriftarten erkennen
  und in C# erfassen können.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: de
og_description: Protokollieren Sie Schriftart‑Substitutionswarnungen beim Laden von
  Word‑Dokumenten mit Aspose.Words. Erfahren Sie, wie Sie fehlende Schriftarten erkennen
  und fehlende Schriftarten in C# erfassen.
og_title: Protokollieren von Schriftart-Substitutionswarnungen – Vollständiger Aspose.Words‑Leitfaden
tags:
- Aspose.Words
- C#
- Document Processing
title: Protokollierung von Warnungen zur Schriftart‑Ersetzung – Vollständiger Aspose.Words‑Leitfaden
url: /de/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Protokollieren von Schriftart‑Ersetzungshinweisen – Vollständiger Aspose.Words‑Leitfaden

Das Protokollieren von Schriftart‑Ersetzungshinweisen ist entscheidend, wenn Sie sicherstellen müssen, dass ein Word‑Dokument nach dem Laden mit Aspose.Words exakt gleich aussieht. Wenn Sie sich jemals gefragt haben, **wie man fehlende Schriftarten erkennt** oder wissen wollen, **wie man fehlende Schriftarten erfasst**, sind Sie hier genau richtig.  

In diesem Tutorial gehen wir Schritt für Schritt durch ein praxisnahes Szenario, zeigen Ihnen den vollständigen C#‑Code und erklären, warum jede Zeile wichtig ist. Am Ende können Sie jedes Schriftart‑Ersetzungsereignis protokollieren und darauf reagieren – keine mysteriösen Warnungen mehr.

![Beispiel für das Protokollieren von Schriftart‑Ersetzungshinweisen](/images/font-warnings.png "Screenshot, der die Konsolenausgabe des Protokollierens von Schriftart‑Ersetzungshinweisen zeigt")

## Was Sie lernen werden

- Wie Sie `LoadOptions` so konfigurieren, dass Aspose.Words typisierte Warnungen für Schriftart‑Ersetzungen ausgibt.  
- Die genauen Schritte, um **fehlende Schriftarten zu erkennen** während des Ladens eines Dokuments.  
- Eine saubere Methode, **fehlende Schriftarten zu erfassen** und in Ihr eigenes Protokoll oder Überwachungssystem zu schreiben.  
- Umgang mit Sonderfällen (z. B. wenn ein Dokument eine Schriftart verwendet, die auf dem Server nicht installiert ist).  

### Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
- Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder die kostenlose Testversion).  
- Grundkenntnisse in C# und Konsolenanwendungen.  

Wenn Sie das bereits haben, legen wir los.

## Schritt 1 – LoadOptions einrichten, um typisierte Warnungen auszulösen

Der Kern der Lösung liegt in `LoadOptions.FontSubstitutionWarning`. Indem Sie es auf `RaiseTypedWarnings` setzen, teilen Sie Aspose.Words mit, bei jeder nicht gefundenen Schriftart ein Ereignis **auszulösen**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Warum das wichtig ist:**  
> Das Standardverhalten ersetzt eine fehlende Schriftart stillschweigend durch die am besten passende, was zu Layout‑Fehlern führen kann, die Sie nicht bemerken. Das Auslösen typisierter Warnungen gibt Ihnen volle Transparenz.

## Schritt 2 – Das Warn‑Ereignis abonnieren

Jetzt binden wir uns an `loadOptions.FontSubstitutionWarning`. Das Lambda erhält ein `e`‑Objekt, das genau angibt, welche Schriftart fehlte und welche stattdessen verwendet wurde.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro‑Tipp:** Wenn Sie das auf einem Web‑Server ausführen, ersetzen Sie `Console.WriteLine` durch einen strukturierten Logger (Serilog, NLog usw.), damit Sie die Daten später abfragen können.

## Schritt 3 – Das Dokument mit den konfigurierten Optionen laden

Mit dem Warn‑Mechanismus können Sie das Dokument wie gewohnt laden. Das Ereignis wird automatisch für jede fehlende Schriftart ausgelöst.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Erwartete Konsolenausgabe

Wenn `input.docx` eine Schriftart namens *MyFancyFont* referenziert, die nicht installiert ist, sehen Sie:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Jede Zeile entspricht einem **fehlende Schriftarten erkennen**‑Ereignis und liefert ein vollständiges Prüfprotokoll.

## Schritt 4 – Sonderfälle und erweiterte Szenarien behandeln

### 4.1 Wenn keine Ersetzung stattfindet

Manchmal verwendet ein Dokument nur Systemschriftarten, die bereits vorhanden sind. In diesem Fall wird das Warn‑Ereignis nie ausgelöst und die Konsole bleibt leer. Das ist ein gutes Zeichen – Ihre Umgebung verfügt bereits über alle benötigten Schriftarten.

### 4.2 Warnungen für spätere Analysen erfassen

Wenn Sie die Warnungen für einen nächtlichen Bericht speichern möchten, sammeln Sie sie in einer Liste:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Nach dem Laden können Sie `missingFonts` in JSON serialisieren, in eine Datenbank schreiben oder eine Zusammenfassung per E‑Mail versenden.

### 4.3 Arbeiten mit PDFs oder anderen Formaten

Der gleiche `LoadOptions`‑Ansatz funktioniert für `Load`‑Aufrufe von PDFs, RTF und sogar HTML‑Dateien. Übergeben Sie einfach dieselbe Options‑Instanz, und Aspose.Words gibt Warnungen für jede nicht zuordenbare Schriftart aus.

## Schritt 5 – Das Ergebnis programmgesteuert verifizieren

Wenn Sie lieber einen automatisierten Test statt einer manuellen Konsolenprüfung möchten, prüfen Sie, ob die Liste die erwarteten Einträge enthält:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Dieses Snippet zeigt **wie man fehlende Schriftarten im Code erfasst**, nicht nur im Protokoll.

## Häufige Stolperfallen & wie man sie vermeidet

| Stolperfalle | Warum sie auftritt | Lösung |
|--------------|--------------------|--------|
| Vergessen, `RaiseTypedWarnings` zu setzen | Der Standard ist `DoNotRaise`, sodass keine Ereignisse ausgelöst werden. | Setzen Sie `FontSubstitutionWarning` explizit wie in Schritt 1 gezeigt. |
| Verwendung von `Console.WriteLine` in einer Web‑App | Konsolenausgabe verschwindet unter IIS/ASP.NET Core. | Wechseln Sie zu einem persistenten Logger (z. B. Serilog). |
| Laden eines Dokuments mit relativem Pfad | Das Arbeitsverzeichnis kann zur Laufzeit anders sein. | Verwenden Sie absolute Pfade oder `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorieren von `SubstitutedFontName` | Sie verlieren die Information, welche Ersatzschriftart gewählt wurde. | Protokollieren Sie immer sowohl `FontName` als auch `SubstitutedFontName`. |

## Bonus: Automatisches Installieren von Schriftarten

Wenn Sie die Bereitstellungsumgebung kontrollieren, können Sie fehlende Schriftarten mit einem PowerShell‑Skript vorinstallieren:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Wenn Sie das vor dem Start Ihrer Anwendung ausführen, entfallen die meisten **fehlende Schriftarten erkennen**‑Warnungen.

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **Schriftart‑Ersetzungshinweise zu protokollieren**, wenn Sie Word‑Dokumente mit Aspose.Words laden. Durch das Konfigurieren von `LoadOptions`, das Abonnieren des Warn‑Ereignisses und optionales Persistieren der Ergebnisse können Sie zuverlässig **fehlende Schriftarten erkennen** und verstehen, **wie man fehlende Schriftarten erfasst** für jedes .NET‑Projekt.

Nehmen Sie den Code, passen Sie den Logger an Ihre Infrastruktur an, und Sie werden nie wieder von einem stillen Schriftart‑Austausch überrascht. Nächste Schritte könnten sein:

- Integration der Warnliste in Ihre CI/CD‑Pipeline, um Builds fehlschlagen zu lassen, wenn kritische Schriftarten fehlen.  
- Erweiterung des Ansatzes, um die Schriftart‑Nutzung in einer Dokumentenflotte zu überwachen.  
- Untersuchung der Aspose.Words‑`FontSettings`‑API, um benutzerdefinierte Ersatzschriftarten bereitzustellen.

Haben Sie Fragen oder ein kniffliges Szenario? Hinterlassen Sie einen Kommentar, und wir lösen das gemeinsam. Viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}