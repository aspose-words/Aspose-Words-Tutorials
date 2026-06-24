---
category: general
date: 2026-05-23
description: Setzen Sie den Aspose-Warnungs‑Callback, um Schriftart‑Ersetzungshinweise
  in Aspose.Words zu erfassen. Lernen Sie LoadOptions, FontSettings und die Implementierung
  von IWarningCallback kennen.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: de
og_description: Setzen Sie den Warnungs-Callback von Aspose, um die Schriftart-Substitution
  in Aspose.Words zu überwachen. Dieses Tutorial zeigt die Implementierung von LoadOptions,
  FontSettings und dem Warnungs-Handler.
og_title: Warnungs‑Callback festlegen Aspose – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Warnungs‑Callback festlegen Aspose – Vollständige Anleitung zum Laden von Word‑Dokumenten
url: /de/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Komplettanleitung zum Laden von Word-Dokumenten

Haben Sie sich jemals gefragt, wie man **set warning callback aspose** einstellt, damit Sie nie wieder eine Schriftart‑Ersetzungsmeldung verpassen? Sie sind nicht allein. Wenn ein DOCX eine Schriftart referenziert, die nicht installiert ist, ersetzt Aspose.Words sie stillschweigend, und ohne einen geeigneten Callback erfahren Sie möglicherweise nie, dass sich etwas geändert hat.

In diesem Tutorial führen wir Sie durch ein vollständiges, ausführbares Beispiel, das genau zeigt, wie man diese Warnungen erfasst. Am Ende verstehen Sie **Aspose.Words LoadOptions**, wie man **FontSettings** konfiguriert und warum die Implementierung von **IWarningCallback** der sauberste Weg ist, um auf dem Laufenden zu bleiben. Kein Schnickschnack – nur der Code, den Sie noch heute in ein .NET‑Projekt einbinden können.

## Was Sie lernen werden

- Wie man **set warning callback aspose** auf einer `LoadOptions`‑Instanz einstellt.  
- Die Rolle von **Aspose.Words LoadOptions** beim Öffnen eines Dokuments.  
- Konfiguration der **Aspose fonts substitution**‑Verarbeitung mit `FontSettings`.  
- Schreiben einer benutzerdefinierten **IWarningCallback‑Implementierung**, um Schriftart‑Probleme zu protokollieren.  
- Sicheres Laden eines Dokuments mit bewährten Methoden für **Aspose document loading**.

### Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.5+).  
- Eine gültige Aspose.Words‑für‑.NET‑Lizenz oder ein Testschlüssel.  
- Visual Studio, Rider oder ein beliebiger C#‑Editor Ihrer Wahl.  
- Ein Beispiel‑DOCX (`fontTest.docx`), das eine fehlende Schriftart referenziert (optional, aber hilfreich).

> **Pro‑Tipp:** Wenn Sie kein DOCX mit fehlender Schriftart haben, benennen Sie einfach eine Schriftart im Dokumentstil um und beobachten Sie, wie die Warnung ausgelöst wird.

---

## Wie man set warning callback aspose für das Laden von Dokumenten einstellt

Unten finden Sie das vollständige, eigenständige Programm. Speichern Sie es als `Program.cs`, stellen Sie die NuGet‑Pakete wieder her und führen Sie es aus. Die Konsole gibt jede Schriftart‑Ersetzungswarnung aus, die Aspose.Words beim Laden der Datei erzeugt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Erwartete Konsolenausgabe

Wenn `fontTest.docx` eine Schriftart referenziert, die nicht installiert ist, sehen Sie etwa Folgendes:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Wenn alle Schriftarten vorhanden sind, wird nur die Zeile *Document loaded successfully* ausgegeben – keine Warnungen, kein Rauschen.

![Beispiel für set warning callback aspose](image.png "Beispiel für set warning callback aspose")

---

## Verständnis von LoadOptions in Aspose.Words

`LoadOptions` ist das Tor zu allen Anpassungen, die Sie beim **aspose document loading** vornehmen können. Es ermöglicht Ihnen:

1. **Ein benutzerdefiniertes `FontSettings` angeben** – nützlich, wenn Ihre Anwendung eigene Schriftarten mitliefert.  
2. **Einen Warn‑Callback anhängen** – genau das, was wir getan haben, um Schriftart‑Ersetzungen abzufangen.  
3. Die Erkennung des Dokumentformats, die Passwortbehandlung und mehr steuern.

Da `LoadOptions` an den `Document`‑Konstruktor übergeben wird, werden die Einstellungen **einmalig** angewendet, genau in dem Moment, in dem die Datei geparst wird. Deshalb können wir garantieren, dass unser Warn‑Handler jede Ersetzung sieht, bevor das Dokument überhaupt im Speicher aufgebaut wird.

### Wann man benutzerdefinierte LoadOptions verwendet

- **Batch‑Verarbeitung** vieler Dateien, bei der Sie eine einheitliche Protokollierungsstrategie wünschen.  
- **Cloud‑Dienste**, die fehlende Schriftarten an den Aufrufer melden müssen.  
- **Test‑Pipelines**, die überprüfen, ob Dokumente einer unternehmensinternen Schriftart‑Richtlinie entsprechen.

---

## Konfiguration von FontSettings für Aspose‑Schriftart‑Ersetzungen

Das Objekt `FontSettings` steuert, wie Aspose.Words Schriftarten auflöst. Standardmäßig durchsucht es die Schriftordner des Systems und greift dann auf integrierte Ersatzschriftarten zurück. Sie können dieses Verhalten feinjustieren:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Diese Zeilen sind für das grundlegende „set warning callback aspose“-Szenario optional, aber sie zeigen, wie Sie die Anzahl der Ersetzungswarnungen **reduzieren** können, indem Sie die richtigen Schriftarten im Voraus bereitstellen.

---

## Implementierung von IWarningCallback für Schriftart‑Ersetzungswarnungen

Das Interface `IWarningCallback` ist winzig – es enthält nur eine einzelne `Warning`‑Methode. Dennoch gibt es Ihnen **volle Kontrolle** darüber, wie Warnungen behandelt werden:

- **In eine Datei protokollieren** statt in die Konsole.  
- **Warnungen sammeln** in einer Liste für spätere Analysen.  
- **Ausnahmen werfen** bei kritischen Warnungen (z. B. wenn eine erforderliche Schriftart fehlt).

Hier ein kurzes Beispiel, das Warnungen in einer `List<string>` speichert:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Sie könnten anschließend `handler.Messages` nach dem Laden des Dokuments prüfen, um zu entscheiden, ob die Verarbeitung abgebrochen werden soll.

---

## Laden eines Dokuments mit benutzerdefinierter Warnbehandlung (vollständiger Workflow)

Wenn wir alles zusammenführen, sieht das endgültige Muster, das Sie wahrscheinlich wiederverwenden werden, folgendermaßen aus:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Dieses Snippet demonstriert den **aspose document loading**‑Ablauf, den Sie in der Produktion verwenden werden: konfigurieren, laden und dann reagieren. Das Muster skaliert gut, egal ob Sie eine einzelne Datei verarbeiten oder über Tausende iterieren.

---

## Häufige Fragen & Sonderfälle

**Was ist, wenn das Dokument passwortgeschützt ist?**  
Fügen Sie `Password = "secret"` zum Initialisierer von `LoadOptions` hinzu. Der Warn‑Callback funktioniert weiterhin, sobald die Datei entschlüsselt ist.

**Wird der Callback für andere Warnungstypen ausgelöst?**  
Ja – `WarningInfo.Type` kann `DocumentStructure`, `UnsupportedFileFormat` usw. sein. In unserem Beispiel filtern wir nach `FontSubstitution`, aber Sie können alles protokollieren, indem Sie die `if`‑Prüfung entfernen.

**Beeinflusst das die Leistung?**  
Vernachlässigbar. Der Callback wird nur bei Auftreten einer Warnung aufgerufen, was weitaus seltener ist als die normalen Parsing‑Schritte.

**Kann ich die Schriftart‑Ersetzung komplett deaktivieren?**  
Sie können `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` setzen, dann wirft Aspose.Words jedoch eine Ausnahme für fehlende Schriftarten, anstatt sie zu ersetzen.

---

## Fazit

Sie wissen jetzt genau, wie Sie **set warning callback aspose** einsetzen, um Schriftart‑Ersetzungsereignisse während der Verarbeitung mit **Aspose.Words LoadOptions** zu überwachen. Durch die Konfiguration von `FontSettings`, die Implementierung eines leichten `IWarningCallback` und das Laden des Dokuments mit diesen Optionen erhalten Sie vollständige Transparenz über alle von Aspose im Hintergrund vorgenommenen Schriftartänderungen.  

Ab hier könnten Sie:

- Den Warn‑Handler erweitern, um in einen zentralen Protokollierungsdienst zu schreiben.  
- Den Callback mit einer benutzerdefinierten Schriftart‑Fallback‑Strategie kombinieren.  
- Das Muster verwenden, wenn Sie eine Cloud‑API bauen, die von Clients hochgeladene Dokumente validiert.

Probieren Sie es mit Ihren eigenen DOCX‑Dateien aus, passen Sie die `FontSettings` an und beobachten Sie, wie die Konsole Ihnen genau sagt, welche Schriftarten ausgetauscht wurden. Viel Spaß beim Coden und möge Ihre Dokumente stets wie beabsichtigt dargestellt werden!

## Verwandte Tutorials

- [Erfassung von Schriftart‑Ersetzungswarnungen in Java mit Aspose.Words – Komplettanleitung](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Aktivieren von Schriftart‑Ersetzungswarnungen in Aspose.Words – Komplettanleitung](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Wie man LoadOptions in Aspose.Words für Java festlegt](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}