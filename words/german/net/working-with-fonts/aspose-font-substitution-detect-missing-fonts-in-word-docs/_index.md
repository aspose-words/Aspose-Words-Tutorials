---
category: general
date: 2026-05-04
description: Erfahren Sie, wie Sie die Aspose‑Schriftart‑Substitution verwenden, um
  fehlende Schriftarten zu erkennen, wenn Sie ein Word‑Dokument laden, und fehlende
  Schriftartdetails abrufen – Schritt‑für‑Schritt‑Anleitung.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: de
og_description: Meistern Sie die Aspose-Schriftart-Substitution, um fehlende Schriftarten
  beim Laden eines Word‑Dokuments zu erkennen und fehlende Schriftartinformationen
  mit vollständigem C#‑Code abzurufen.
og_title: Aspose Schriftart-Substitution – Fehlende Schriftarten in Word-Dokumenten
  erkennen
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose-Schriftart-Substitution: Fehlende Schriftarten in Word‑Dokumenten erkennen'
url: /de/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Fehlende Schriften in Word-Dokumenten erkennen

Haben Sie sich jemals gefragt, warum ein Word-Dokument auf einem anderen Rechner falsch aussieht? Oft ist die Ursache eine fehlende Schrift, und **Aspose Font Substitution** ist das Werkzeug, das Ihnen ermöglicht, diese Lücken zu erkennen, bevor sie zu einer visuellen Katastrophe werden. In diesem Tutorial zeigen wir Ihnen, wie Sie **fehlende Schriften** sofort beim **Laden eines Word-Dokuments** **erkennen** und anschließend **Details zu fehlenden Schriften** abrufen können, um sie zu beheben oder zu ersetzen.

Wir behandeln alles, von der Einrichtung des Warn‑Callbacks bis zum Abrufen einer sauberen Liste fehlender Schriften. Am Ende haben Sie ein sofort einsatzbereites C#‑Snippet, das Ihnen genau anzeigt, welche Schriften nicht gefunden wurden, und Sie verstehen, warum das für die Dokumententreue wichtig ist.

---

## Voraussetzungen – Was Sie vor dem Start benötigen

- **Aspose.Words for .NET** (v23.12 oder höher empfohlen).  
- Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder die `dotnet`‑CLI).  
- Ein Beispiel‑DOCX, das absichtlich eine Schrift verwendet, die nicht installiert ist – nennen wir es `DocumentWithMissingFont.docx`.  
- Grundkenntnisse in C# – nichts Aufwändiges, nur die Fähigkeit, eine Konsolen‑App auszuführen.

Falls Ihnen etwas davon unbekannt ist, halten Sie kurz inne und installieren Sie das NuGet‑Paket:

```bash
dotnet add package Aspose.Words
```

Das war’s. Keine zusätzlichen Schriften, keine externen Dienste.

## Schritt 1: Word-Dokument laden (und Schriftprüfungen auslösen)

Das allererste, was Sie tun, ist ein **Word‑Dokument laden**. Aspose.Words analysiert die Datei und wenn es eine referenzierte Schrift nicht finden kann, wird eine *FontSubstitution*‑Warnung in die Warteschlange gestellt. Hier ist der Code, der das Laden übernimmt:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Warum das wichtig ist:** Durch das frühe Laden des Dokuments erhält Aspose die Möglichkeit, jeden Textlauf, Stil und eingebettetes Objekt zu prüfen. Wenn eine Schrift nicht im System oder im benutzerdefinierten Schriftordner gefunden wird, erhalten Sie später eine Warnung.

## Schritt 2: Einen Warn‑Callback anhängen, um Substitutions‑Ereignisse zu erfassen

Aspose.Words verwendet einen Callback‑Mechanismus, um Sie über Probleme wie fehlende Schriften zu informieren. Durch das Zuweisen einer Implementierung von `IWarningCallback` zu `doc.WarningCallback` können Sie jede Warnung in Echtzeit abfangen.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Pro‑Tipp:** Sie können mehrere Callbacks (z. B. Logging, UI‑Updates) anhängen, indem Sie sie in einem Composite‑Pattern bündeln, aber für dieses Tutorial sorgt ein einzelner Callback für Klarheit.

## Schritt 3: Das Font‑Substitution‑Warn‑Callback implementieren

Jetzt definieren wir die Klasse, die die eigentliche Arbeit übernimmt. Der Callback erhält ein `WarningInfo`‑Objekt; wir filtern nach `WarningType.FontSubstitution` und speichern die Beschreibung für die spätere Verwendung.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Was passiert:** Wenn Aspose auf eine fehlende Schrift stößt, erzeugt es eine Warnung wie „Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.“ Unser Callback gibt diese Zeile aus und speichert sie.

## Schritt 4: Dokument verarbeiten (optional) und fehlende Schriften sammeln

Wenn Sie nur **fehlende Schriften erkennen** müssen, reicht der Ladeschritt aus – die Warnungen werden automatisch ausgelöst. Viele Entwickler benötigen jedoch nach bestimmten Vorgängen (z. B. Speichern, Konvertieren) **Informationen zu fehlenden Schriften**. Im Folgenden erzwingen wir eine kleine Operation – das Speichern als PDF – um sicherzustellen, dass alle Warnungen ausgegeben werden, und holen dann die gesammelten Meldungen.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Erwartete Konsolenausgabe** (Beispiel):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Beachten Sie, dass jede Zeile eindeutig die ursprüngliche Schrift und die von Aspose gewählte Ersatzschrift angibt. Das ist das Kernprinzip der **Aspose Font Substitution**‑Berichterstattung.

## Schritt 5: Fortgeschritten – Benutzerdefinierte Schriftquellen verwenden, um Substitutionen zu reduzieren

Manchmal haben Sie die fehlenden Schriften *eigentlich* vorhanden, jedoch nicht im Standard‑Systemordner. Aspose.Words ermöglicht es Ihnen, über `FontSettings` auf ein benutzerdefiniertes Verzeichnis zu verweisen. Dieser Schritt kann die Anzahl der Substitutions‑Warnungen erheblich reduzieren.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Warum das hinzufügen?** Wenn Sie Dokumente auf verschiedene Rechner verteilen, sorgt das Bündeln der benötigten Schriften in einem bekannten Ordner für überall dieselbe optische Darstellung. Außerdem wird Ihre **fehlende Schriften erkennen**‑Routine genauer, da Aspose diesen Ordner prüft, bevor es auf eine Ersatzschrift zurückgreift.

## Vollständiges funktionierendes Beispiel

Alles zusammengeführt, hier ein einzelnes, kopier‑und‑einfüge‑fertiges Konsolenprogramm. Speichern Sie es als `Program.cs` und führen Sie es mit `dotnet run` aus.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Was Sie sehen sollten:** Wenn das Quell‑DOCX Schriften referenziert, die Sie nicht besitzen, gibt die Konsole jede Substitutionszeile gefolgt von einer kurzen Zusammenfassung aus. Sind alle Schriften vorhanden, erhalten Sie die Meldung „No missing fonts were detected.“  

## Häufige Fallstricke & wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|-------|----------------|-----|
| **Keine Warnungen erscheinen** | Das Dokument verwendet nur Systemschriften oder Sie haben bereits einen benutzerdefinierten Ordner mit den fehlenden Schriften hinzugefügt. | Überprüfen Sie, ob das DOCX tatsächlich eine nicht verfügbare Schrift referenziert. Öffnen Sie es in Word und ändern Sie einen Absatz zu einer seltenen Schrift (z. B. „Papyrus“). |
| **Doppelte Meldungen** | Die gleiche Schrift wird in mehreren Runs verwendet, was zu mehreren Warnungen führt. | Entfernen Sie Duplikate aus der Liste mit `Distinct()`, wenn Sie nur ein eindeutiges Set benötigen. |
| **Leistungsprobleme bei großen Dokumenten** | Jede Warnung wird im UI‑Thread verarbeitet. | Laden Sie das Dokument in einem Hintergrund‑Task oder verwenden Sie `Parallel.ForEach` für die Nachbearbeitung. |
| **Falsche Ersatzschrift** | Asposes Standard‑Ersatzschrift entspricht möglicherweise nicht Ihrem Branding. | Setzen Sie `FontSettings.SubstitutionSettings.DefaultFontName` auf eine bevorzugte Ersatzschrift (z. B. „Calibri“). |

## Erweiterung der Lösung – Fehlende Schriften nach JSON exportieren

Wenn Sie einen Web‑Service erstellen, der fehlende Schriften an einen Client melden muss, ist das Serialisieren der Liste trivial:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Jetzt kann Ihre API ein sauberes JSON‑Payload zurückgeben, das ein anderes System verarbeiten kann.

## Fazit

In diesem Leitfaden haben wir **Aspose Font Substitution** von Anfang bis Ende demonstriert: ein Word‑Dokument laden, einen Warn‑Callback anhängen, jedes *fehlende Schrift erkennen*‑Ereignis erfassen und schließlich **Informationen zu fehlenden Schriften** für Berichte oder Korrekturen abrufen. Durch das Hinzufügen optionaler benutzerdefinierter Schriftordner können Sie die Liste der Substitutionen verkleinern, und mit ein paar zusätzlichen Zeilen können Sie die Ergebnisse sogar als JSON exportieren.

Denken Sie daran, dass die visuelle Integrität Ihrer Dokumente von den verwendeten Schriften abhängt. Mit der hier gezeigten Technik werden Sie nie wieder von einer unerwarteten Ersatzschrift überrascht.  

Bereit für den nächsten Schritt? Versuchen Sie, diese Logik in eine größere Dokument‑Verarbeitungspipeline zu integrieren, oder erkunden Sie weitere Funktionen von Aspose.Words wie das Einbetten von Schriften (`doc.FontSettings.EmbeddedFonts`). Die Möglichkeiten sind endlos, und Ihre Nutzer werden Ihnen für das hochwertige Ergebnis danken.

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}