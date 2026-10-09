---
category: general
date: 2026-03-19
description: Erfahren Sie, wie Sie Warnungen in Aspose.Words erfassen, Standardeinstellungen
  für Schriftarten festlegen und fehlende Schriftarten beim Laden eines Word-Dokuments
  erkennen.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: de
og_description: Wie man Warnungen in Aspose.Words erfasst, Standardeinstellungen für
  Schriftarten festlegt und fehlende Schriftarten beim Laden eines Word-Dokuments
  erkennt.
og_title: Wie man Warnungen erfasst – Standard‑Schrifteinstellungen festlegen
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man Warnungen erfasst – Standard‑Schrifteinstellungen festlegen
url: /de/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen erfasst – Standard‑Schrifteinstellungen festlegen

**Warnungen erfassen** ist ein häufiges Bedürfnis, wenn Sie mit Aspose.Words arbeiten, besonders wenn Ihre Dokumente auf bestimmte Schriftarten angewiesen sind, die auf dem Zielrechner möglicherweise nicht vorhanden sind. Haben Sie jemals ein DOCX geöffnet und sich gefragt, warum das Layout falsch aussah? Die Antwort steckt oft in einer Warnung über eine fehlende Schriftart.  

In diesem Leitfaden gehen wir Schritt für Schritt darauf ein, **how to capture warnings**, während Sie **load word document** laden, **set default font settings** konfigurieren und schließlich **detect missing fonts** erkennen, damit Sie programmgesteuert reagieren können. Kein Schnickschnack – nur ein vollständiges, ausführbares Beispiel und die Begründung zu jeder Zeile.

> *Pro Tipp:* Das frühe Erfassen von Warnungen bewahrt Sie davor, später mysteriöse Layout‑Fehler zu debuggen.

---

## Was Sie benötigen

- **Aspose.Words for .NET** (neueste Version ab 2026).  
- Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code).  
- Ein Beispiel‑DOCX, das eine Schriftart referenziert, die Sie *nicht* installiert haben (z. B. *Comic Sans MS* auf einer Linux‑Box).  

Das ist alles. Keine zusätzlichen NuGet‑Pakete sind über Aspose.Words hinaus erforderlich.

---

## Schritt 1 – Verstehen, warum Sie Warnungen erfassen müssen

Wenn Aspose.Words ein Dokument analysiert, kann es auf Schriftarten stoßen, die auf dem Host nicht verfügbar sind. Standardmäßig ersetzt die Bibliothek stillschweigend eine Ersatzschriftart, was Zeilenumbrüche, Abstände und sogar das Verschwinden von Text verändern kann.  

Die Verwendung des **WarningCallback** zusammen mit einem **FontSettings**‑Objekt liefert Ihnen zwei Dinge:

1. **Sichtbarkeit** – Sie erhalten für jede Substitution einen `WarningInfo`‑Eintrag.  
2. **Kontrolle** – Sie können eine Standard‑Schriftart vorkonfigurieren, um visuelle Überraschungen zu minimieren.

Stellen Sie sich das vor wie einen „Watchdog“, der jedes Mal laut ruft, wenn der Motor ein Teil unter der Haube austauscht.

---

## Schritt 2 – Standard‑Schrifteinstellungen festlegen

Das erste sekundäre Schlüsselwort, **set default font settings**, erscheint genau hier. Sie erstellen eine `FontSettings`‑Instanz und geben optional einen Ordner an, der Ihre Ersatz‑Schriftarten enthält.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Warum?**  
> Wenn Sie keinen Ersatz angeben, wählt Aspose.Words die erste Systemschriftart, die zum Stil passt, was stark abweichen kann. Durch das Festlegen einer bekannten Vorgabe gewährleisten Sie ein konsistentes Rendering auf allen Maschinen.

---

## Schritt 3 – Einen Warning‑Callback vorbereiten, um Warnungen zu erfassen

Jetzt zeigen wir **how to capture warnings**, indem wir eine `WarningInfoCollection` zu den Ladeoptionen hinzufügen. Diese Sammlung speichert jede während des Ladevorgangs ausgegebene Warnung.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

Die `WarningInfoCollection` implementiert `IWarningCallback`, sodass Aspose.Words jede Warnung automatisch in `warningInfos` einfügt. Kein Polling nötig.

---

## Schritt 4 – Word‑Dokument mit den konfigurierten Optionen laden

Hier kommt das zweite sekundäre Schlüsselwort, **load word document**, zum Einsatz. Wir übergeben sowohl die `FontSettings` als auch den `WarningCallback` über eine `LoadOptions`‑Instanz.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Wenn das Dokument eine Schriftart referenziert, die nicht installiert ist, wird der Warn‑Callback einen Eintrag vom Typ `WarningType.FontSubstitution` erfassen.

---

## Schritt 5 – Fehlende Schriftarten aus gesammelten Warnungen erkennen

Abschließend beantworten wir das dritte sekundäre Schlüsselwort, **detect missing fonts**, indem wir die gesammelten Warnungen durchlaufen.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Typische Ausgabe sieht so aus:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Diese Zeile sagt Ihnen genau, welche Schriftart fehlt und welche Ersatzschrift verwendet wurde – Informationen, die Sie protokollieren, dem Benutzer anzeigen oder sogar eine benutzerdefinierte Schrift‑Installations‑Routine auslösen können.

---

## Vollständiges ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es demonstriert **how to capture warnings**, **set default font settings**, **load word document** und **detect missing fonts** in einem Durchgang.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Erwartetes Ergebnis:** Wenn das angegebene DOCX eine nicht installierte Schriftart referenziert, gibt die Konsole für jede Substitution eine Warnung aus. Sind alle Schriftarten vorhanden, erzeugt die Schleife keine Ausgabe.

---

## Häufige Stolperfallen & Randfälle

| Situation | Warum es passiert | Wie man es behebt |
|-----------|-------------------|-------------------|
| **No warnings appear** even though the layout looks wrong | The document may be using *embedded* fonts, which Aspose.Words renders without substitution. | Check `Document.HasEmbeddedFonts` and consider extracting the embedded fonts if you need them on another machine. |
| **Multiple warnings for the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}