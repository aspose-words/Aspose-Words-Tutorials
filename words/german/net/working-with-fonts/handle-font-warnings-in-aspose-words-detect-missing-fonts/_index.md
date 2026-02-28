---
category: general
date: 2026-02-28
description: Erfahren Sie, wie Sie Schriftartwarnungen behandeln und fehlende Schriftarten
  in Aspose.Words mit C# erkennen. Vollständige Schritt‑für‑Schritt‑Anleitung mit
  vollständigem Code.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: de
og_description: Behandeln Sie Schriftartwarnungen in Aspose.Words und erkennen Sie
  fehlende Schriftarten mit einem sofort einsatzbereiten C#‑Beispiel. Folgen Sie den
  Schritten und sehen Sie das Ergebnis.
og_title: Schriftartwarnungen in Aspose.Words behandeln – Vollständiger Leitfaden
tags:
- Aspose.Words
- C#
- Document Loading
title: Schriftwarnungen in Aspose.Words behandeln – Fehlende Schriftarten erkennen
url: /de/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font‑Warnungen in Aspose.Words behandeln – Fehlende Schriften erkennen

Haben Sie schon einmal **Font‑Warnungen** beim Laden eines Word‑Dokuments behandeln müssen und sich gefragt, warum ein Teil des Textes seltsam aussieht? Sie sind nicht allein. Fehlende Schriften lösen Ersetzungs‑Warnungen aus, die das Layout stillschweigend verfälschen können, und wenn Sie **fehlende Schriften nicht erkennen**, wissen Sie nie, was schiefgelaufen ist.

In diesem Tutorial zeigen wir Ihnen eine praktische Methode, **Font‑Warnungen** mit Aspose.Words’ `IWarningCallback` zu **behandeln**. Am Ende der Anleitung können Sie jedes Font‑Substitutions‑Ereignis erkennen, protokollieren und sogar entscheiden, ob der Ladevorgang abgebrochen werden soll. Keine externen Dokumente, nur ein einzelnes, copy‑paste‑fertiges Beispiel.

## Was Sie lernen werden

- Einen benutzerdefinierten Warn‑Handler einrichten, der nur auf Font‑Substitutions‑Alarme reagiert.  
- Den Handler an `LoadOptions` anhängen, sodass jeder Dokument‑Ladevorgang darüber läuft.  
- Die Ausgabe in der Konsole überprüfen und verstehen, was jede Warnung bedeutet.  

**Voraussetzungen**

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
- Aspose.Words für .NET über NuGet installiert (`Install-Package Aspose.Words`).  
- Eine Word‑Datei, die eine Schriftart referenziert, die nicht auf Ihrem Rechner installiert ist (z. B. eine firmeneigene Schrift).  

Falls Ihnen etwas davon fehlt, holen Sie es jetzt – ansonsten legen wir los.

## So behandeln Sie Font‑Warnungen in Aspose.Words

Unten finden Sie das vollständige, ausführbare Programm. Es enthält alles von den `using`‑Anweisungen bis zur `Main`‑Methode, sodass Sie es in eine Konsolen‑App einfügen und **F5** drücken können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Erwartete Konsolenausgabe** (unter der Annahme, dass das Dokument eine Schrift verwendet, die Sie nicht installiert haben):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Wenn das Dokument **keine fehlenden Schriften** enthält, erscheint die Warnzeile nie – Sie haben also **fehlende Schriften nur dann erkannt**, wenn es nötig war.

### Warum das funktioniert

Aspose.Words wirft für jedes nicht‑kritische Problem, das beim Parsen einer Datei auftritt, ein `WarningInfo`. Durch die Implementierung von `IWarningCallback` erhalten Sie einen Hook in diese Pipeline. Das Flag `WarningType.FontSubstitution` sagt Ihnen exakt, wann die Bibliothek eine angeforderte Schrift durch eine Ersatzschrift ersetzen musste. Das ist der zuverlässigste Weg, **Font‑Warnungen zu behandeln**, weil er *während* des Ladens läuft, bevor Sie überhaupt das Document‑Objektmodell berühren.

## Fehlende Schriften erkennen, ohne Ihre App zu brechen

Manchmal möchten Sie eine fehlende Schrift als fatalen Fehler behandeln – vielleicht verbieten Ihre Markenrichtlinien jede Substitution. Sie können den Handler so ändern, dass er eine Ausnahme wirft, anstatt nur zu protokollieren:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Jetzt fängt der `try…catch`‑Block um `new Document(...)` das Problem ab, sodass Sie entscheiden können, ob Sie abbrechen, eine Alternative verwenden oder den Benutzer auffordern möchten.

## Bonus: Warnungen in einer UI‑Anwendung visualisieren

Wenn Sie eine WinForms‑ oder WPF‑App bauen, ersetzen Sie `Console.WriteLine` durch einen UI‑freundlichen Aufruf:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

So sehen End‑User die Warnung sofort, und Sie **behandeln Font‑Warnungen** weiterhin konsistent über alle Plattformen hinweg.

## Häufige Stolperfallen & Pro‑Tipps

- **Stolperfalle:** Vergessen, `WarningCallback` zu setzen. Das Standardverhalten ist, Font‑Warnungen zu ignorieren, sodass Sie sie nie sehen.  
  **Pro‑Tipp:** Erstellen Sie immer eine `LoadOptions`‑Instanz, selbst wenn Sie nur den Warn‑Handler benötigen. Das ist günstig und explizit.  

- **Stolperfalle:** Den falschen Pfad‑Separator auf Nicht‑Windows‑OS verwenden.  
  **Pro‑Tipp:** Nutzen Sie `Path.Combine` oder ein rohes String‑Literal (`@"C:\Docs\MissingFont.docx"` funktioniert unter Windows; unter Linux verwenden Sie `"/home/user/docs/MissingFont.docx"`).  

- **Stolperfalle:** Annehmen, dass die Warnung bei eingebetteten Schriften ausgelöst wird.  
  **Pro‑Tipp:** Eingebettete Schriften gelten als vorhanden, daher erscheint keine Substitutions‑Warnung. Testen Sie mit wirklich *fehlenden* Schriften, um den Handler in Aktion zu sehen.  

- **Stolperfalle:** Jede Warnungsart über‑protokollieren.  
  **Pro‑Tipp:** Filtern Sie nach `WarningType.FontSubstitution` wie gezeigt – das hält die Konsole sauber und fokussiert auf das **Erkennen fehlender Schriften**‑Szenario.

## Vollständiges funktionierendes Beispiel – Zusammenfassung

Hier ist das gesamte Programm noch einmal, diesmal ohne Kommentare für alle, die eine saubere Ansicht bevorzugen:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Kopieren, einfügen, ausführen – Ihre Konsole wird nun **Font‑Warnungen** und **fehlende Schriften** automatisch **behandeln** und **erkennen**.

## Nächste Schritte

- **In eine Datei protokollieren:** Ersetzen Sie `Console.WriteLine` durch einen Logger (z. B. NLog) für produktionsreifes Tracing.  
- **Batch‑Verarbeitung:** Durchlaufen Sie einen Ordner mit Dokumenten und sammeln Sie alle Font‑Substitutions‑Ereignisse in einem CSV‑Report.  
- **Automatische Schriftinstallation:** Binden Sie den Warn‑Handler ein, um fehlende Schriften aus einem Unternehmens‑Repository herunterzuladen, bevor das Laden fortgesetzt wird.  

Jede dieser Erweiterungen baut auf der Kernidee des **Behandelns von Font‑Warnungen** in einer sauberen, wiederverwendbaren Weise auf.

---

*Viel Spaß beim Coden! Wenn Sie beim **Erkennen fehlender Schriften** auf Eigenheiten stoßen, hinterlassen Sie unten einen Kommentar. Ich helfe Ihnen gern beim Troubleshooting.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}