---
category: general
date: 2026-06-17
description: Verwalten Sie die Schriftart‑Substitution in Aspose.Words und erkennen
  Sie fehlende Schriftarten schnell mit diesem Schritt‑für‑Schritt‑Tutorial für .NET‑Entwickler.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: de
og_description: Verwalten Sie die Schriftart-Substitution in Aspose.Words und lernen
  Sie, fehlende Schriftarten in Ihren Dokumenten mit klaren Codebeispielen zu erkennen.
og_title: Umgang mit Schriftart-Substitution in Aspose.Words – Vollständiger Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Umgang mit Schriftart‑Ersetzung in Aspose.Words – Vollständiger Programmierleitfaden
url: /de/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schriftersetzung in Aspose.Words behandeln – Vollständiger Programmierleitfaden

Haben Sie sich jemals gefragt, wie man **Schriftersetzung** handhabt, wenn ein Word‑Dokument auf eine Schriftart verweist, die auf dem Server nicht installiert ist? Sie sind nicht allein. In vielen realen Anwendungen – denken Sie an Rechnungsgeneratoren oder automatisierte Berichtsdienste – führen fehlende Schriften zu stillen Ausweichungen, die das Layout ruinieren.  

Die gute Nachricht ist, dass Aspose.Words Ihnen ein integriertes Warnsystem bietet, mit dem Sie **fehlende Schriften erkennen** und nach Belieben reagieren können. In diesem Tutorial führen wir Sie durch das Registrieren eines Warn‑Handlers, das Laden eines Dokuments und das Extrahieren der genauen Schriftersetzungs‑Ereignisse, die Sie kennen müssen. Am Ende sehen Sie außerdem, wie Sie die klassische Frage „**wie erkennt man fehlende Schriften?**“ mit sauberem, produktionsreifem Code beantworten.

## What This Tutorial Covers

* Einrichtung von Aspose.Words, um Warnungen für jede Schriftersetzung auszulösen.  
* Erfassen dieser Warnungen in einem benutzerdefinierten Handler, um sie zu protokollieren, zu ersetzen oder abzubrechen.  
* Nutzung der erfassten Daten, um **fehlende Schriften** zu erkennen, bevor das Dokument gespeichert oder gerendert wird.  
* Tipps zur Fehlersuche bei Randfällen – z. B. wenn eine Ausweichschrift stillschweigend gewählt wird.  
* Ein vollständiges, ausführbares Beispiel, das Sie in jede .NET‑Konsolen‑App einbinden können.

> **Prerequisites** – Sie benötigen ein aktuelles .NET‑SDK (6.0+ funktioniert einwandfrei), eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder einen temporären Evaluierungsschlüssel) und ein Beispiel‑DOCX, das absichtlich auf eine Schrift verweist, die nicht installiert ist. Weitere Drittanbieter‑Bibliotheken sind nicht erforderlich.

---

## ## Handle Font Substitution with a Custom Warning Handler

Aspose.Words erzeugt jedes Mal ein `WarningInfo`‑Objekt, wenn es die angeforderte Schrift nicht finden kann. Standardmäßig werden diese Warnungen ignoriert, weshalb Sie oft nie von einer Ersetzung erfahren. Um **Schriftersetzung zu handhaben**, ersetzen Sie den Standard‑Warning‑Handler durch einen, der tatsächlich etwas tut.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Why This Works

* `FontSettings.DefaultWarningHandler` ist eine globale statische Eigenschaft – sobald Sie sie setzen, verwendet **jede** Aspose.Words‑Operation im aktuellen AppDomain Ihren Delegaten.  
* Der `WarningInfoCollectionHandler` erhält ein `WarningInfo`‑Objekt, das `WarningType` und eine menschenlesbare `Description` enthält. Das Filtern nach `WarningType.FontSubstitution` stellt sicher, dass Sie nur die Ereignisse sehen, die Sie interessieren.  
* Der Aufruf von `doc.Save` zwingt die Bibliothek, alle Schriften aufzulösen, was der Moment ist, in dem die Warnungen ausgelöst werden. Wenn Sie das Dokument nur prüfen wollen, ohne zu speichern, können Sie stattdessen `doc.UpdatePageLayout()` aufrufen.

**Expected console output** (assuming the missing font is “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Diese Zeile ist Ihr Beweis, dass die Bibliothek **fehlende Schriften erkannt** und eine Ausweichschrift gewählt hat.

---

## ## Detect Missing Fonts Before Rendering

Manchmal möchten Sie den Vorgang komplett abbrechen, wenn eine benötigte Schrift fehlt – etwa weil Markenrichtlinien eine exakte Typografie verlangen. Der Warn‑Handler kann erweitert werden, um alle fehlenden‑Schrift‑Nachrichten in einer Liste zu sammeln, woraufhin Sie eine Entscheidung treffen können.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### How This Answers “how to detect missing fonts”

* Die Liste `missingFonts` fungiert als Register jedes Ersetzungs‑Ereignisses.  
* Nach `UpdatePageLayout` können Sie die Liste prüfen und entscheiden, ob Sie fortfahren, protokollieren oder eine Ausnahme auslösen wollen.  
* Dieses Muster funktioniert für jedes Ausgabformat (PDF, HTML, Bilder), da das Warnsystem formatunabhängig ist.

---

## ## Advanced Tip: Replace Missing Fonts with a Specific Substitute

Wenn Sie eine Unternehmensschrift haben, die zwingend verwendet werden muss, können Sie Aspose.Words anweisen, jede fehlende Schrift automatisch durch Ihre Ausweichschrift zu ersetzen. Das ist praktisch, wenn das Dokument *trotzdem* akzeptabel aussehen soll, ohne manuelle Nachbearbeitung.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Platzieren Sie das obige Snippet **vor** dem Laden des Dokuments. Jetzt wird jede fehlende Schrift – egal wie ihr ursprünglicher Name lautet – durch „Calibri“ (oder „Arial“, falls Calibri nicht vorhanden ist) ersetzt. Sie erhalten weiterhin die Warnung, aber das Dokument wird mit der von Ihnen gesteuerten Schrift gerendert.

---

## ## Common Pitfalls & How to Avoid Them

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **Warnings disappear after the first call** | The static `DefaultWarningHandler` is overwritten later in the app. | Set the handler **once** at application start, or store a reference and re‑assign if you change it. |
| **Only the first missing font is reported** | Some APIs batch warnings; you need to call `UpdatePageLayout` or `Save` to flush the queue. | Force a layout update or save in the format you intend to generate. |
| **Substitution still occurs even after aborting** | The warning handler runs *after* the substitution has already happened. | Use the handler to **log** and then throw an exception to stop further processing. |
| **Missing fonts on Linux containers** | Linux often lacks the Windows font catalog, leading to many substitutions. | Mount required fonts into the container or use `FontSettings.SetFontsFolder` to point to a custom font directory. |

---

## ## Detect Font Substitution in a Web API Scenario

Wenn Sie Dokumente über ASP.NET Core bereitstellen, wollen Sie wahrscheinlich keine Konsolenausgaben. Stattdessen sammeln Sie Warnungen und geben sie als Teil der HTTP‑Antwort zurück.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Jetzt erkennt die API **fehlende Schriften** und liefert ein klares JSON‑Payload, bevor irgendein PDF erzeugt wird. Dies ist eine praktische Illustration von „wie erkennt man fehlende Schriften“ in einem produktionsreifen Service.

---

## ## Testing Your Implementation

1. **Create a test DOCX** that references a font you know isn’t on the machine (e.g., “Comic Sans MS” on a minimal Docker image).  
2. Run the console app or API endpoint.  
3. Verify that the console (or HTTP response) lists the substitution warning.  
4. Optionally, open the resulting PDF and check the font properties—Aspose.Words should show the fallback font you configured.

If you see the warning but the PDF still uses an unexpected font, double‑check the `SubstitutionSettings` order; the first match wins.

---

## ## Conclusion

Wir haben alles behandelt, was Sie benötigen, um **Schriftersetzung** in Aspose.Words zu **handhaben**, vom Registrieren eines Warn‑Handlers bis zum programmgesteuerten **Erkennen fehlender Schriften** und sogar dem Ersetzen durch eine Unternehmensschrift. Durch die Nutzung des integrierten Warnsystems erhalten Sie volle Sichtbarkeit über jedes „Schrift nicht gefunden“-Ereignis, was die Frage „**wie erkennt man fehlende Schriften?**“ eindeutig beantwortet, die jeder Entwickler bei der automatischen Dokumentenerstellung stellt.

Was kommt als Nächstes? Kombinieren Sie diese Logik mit **dynamic font loading** (`FontSettings.SetFontsFolder`), um benutzer‑hochgeladene Schriften on the fly zu unterstützen, oder erweitern Sie den Warn‑Handler, um Einträge in einen zentralen Logging‑Service wie Serilog zu schreiben. Je mehr Sie die Schriftverarbeitung instrumentieren, desto zuverlässiger wird Ihre Dokument‑Pipeline.

Haben Sie ein kniffliges Schrift‑Ersatz‑Szenario, das Sie beschäftigt? Hinterlassen Sie einen Kommentar unten, und wir lösen das Problem gemeinsam. Happy coding!

## What Should You Learn Next?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Wie man Schriften in Aspose.Words erkennt – Warnungen & Einstellungen handhaben](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Warnungen für Schriftersetzung in Aspose.Words aktivieren – Vollständiger Leitfaden](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Wie man DOCX lädt und fehlende Schriften erkennt – Vollständiger C#‑Leitfaden](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}