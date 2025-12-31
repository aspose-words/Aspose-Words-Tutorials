---
category: general
date: 2025-12-31
description: Erfassen Sie Schriftartwarnungen in Aspose.Words, um fehlende Schriftarten
  zu erkennen, und listen Sie fehlende Schriftarten in Ihrer .NET‑Anwendung auf. Lernen
  Sie eine Schritt‑für‑Schritt‑C#‑Lösung kennen.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: de
og_description: Erfassen Sie Schriftartwarnungen in Aspose.Words, um fehlende Schriftarten
  zu erkennen und aufzulisten. Vollständige C#‑Anleitung mit Code und Tipps.
og_title: Schriftwarnungen erfassen – Fehlende Schriften erkennen und auflisten
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Schriftartwarnungen erfassen – Fehlende Schriften erkennen und auflisten
url: /de/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font‑Warnungen erfassen – Fehlende Schriften erkennen & auflisten

Haben Sie schon einmal **Font‑Warnungen** erfassen wollen, wenn ein Word‑Dokument geladen wird, wussten aber nicht, wie Sie die fehlenden Schriften sichtbar machen können? Sie sind nicht allein. In vielen realen Projekten führen fehlende Schriften zu Layout‑Fehlern, und ohne entsprechende Warnungen jagt man Phantom‑Bugs.

In diesem Tutorial zeigen wir Ihnen, wie Sie **fehlende Schriften erkennen** und **fehlende Schriften auflisten** mit Aspose.Words für .NET. Am Ende haben Sie ein sofort ausführbares C#‑Snippet, das jede Ersetzungs‑Warnung ausgibt, sodass Sie protokollieren, alarmieren oder sogar Schriften automatisch ersetzen können.

---

## Warum das Erfassen von Font‑Warnungen wichtig ist

Wenn Aspose.Words ein DOCX öffnet, das auf eine Schrift verweist, die auf dem Server nicht installiert ist, wird stillschweigend ein Fallback verwendet. Das Dokument sieht zwar gut aus, aber die visuelle Treue ist beeinträchtigt – denken Sie an ein Firmenlogo, das in der falschen Schriftart dargestellt wird.

Das Erfassen dieser Warnungen ermöglicht Ihnen:

* **Markenkonsistenz wahren** – Sie wissen genau, welche Schriften fehlen.
* **Automatisierte Behebung** – fehlende Schriften programmgesteuert ersetzen.
* **Compliance‑Audit** – Berichte für rechtliche oder gestalterische Prüfungen erstellen.

Kurz gesagt, **Font‑Warnungen erfassen** ist die erste Verteidigungslinie gegen stilles Ersetzen von Schriften.

---

## LoadOptions einrichten, um fehlende Schriften zu erkennen

Der Schlüssel, um Warnungen sichtbar zu machen, ist die Eigenschaft `LoadOptions.FontSubstitutionWarning`. Standardmäßig ist sie auf `None` gesetzt, wodurch Aspose.Words die Meldungen verwirft. Auf `All` zu setzen veranlasst die Bibliothek, jedes Ersetzungs‑Ereignis zu protokollieren.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Pro‑Tipp:** Wenn Sie bereits einen eigenen Schriftordner haben, weisen Sie ihn mit `FontSettings.SetFontsFolder("path")` zu, bevor Sie das Dokument laden. So können Sie **fehlende Schriften erkennen**, die nicht im Systemverzeichnis liegen.

---

## Das Dokument laden und fehlende Schriften auflisten

Jetzt, wo die `LoadOptions` bereit sind, ist der nächste Schritt, die Word‑Datei zu laden. Der Konstruktor akzeptiert das Options‑Objekt, und jede Ersetzung wird in der `WarningInfoCollection` des Dokuments festgehalten.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Wenn die Datei Schriften referenziert, die nicht verfügbar sind, erzeugt jede fehlende Schrift einen `WarningInfo`‑Eintrag. Sie können **fehlende Schriften auflisten**, indem Sie über diese Sammlung iterieren.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Typische Ausgabe sieht so aus:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Jede Zeile sagt Ihnen exakt, welche Schrift fehlte, und erfüllt damit die Anforderung **fehlende Schriften auflisten**.

---

## Die WarningInfoCollection lesen und interpretieren

Die `WarningInfoCollection` kann verschiedene Warnungstypen enthalten (z. B. `DocumentStructure`, `ImageLoading`). Um sich ausschließlich auf Schrift‑Probleme zu konzentrieren, filtern Sie nach `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Warum filtern? Weil ein großes Dokument auch Warnungen zu beschädigten Bildern oder nicht unterstützten Features erzeugen kann. Durch das Eingrenzen der Sammlung vermeiden Sie Rauschen und halten die Ausgabe von **Font‑Warnungen erfassen** sauber.

---

## Vollständiges Beispiel – Font‑Warnungen in Aktion

Unten finden Sie das komplette, eigenständige Programm, das Sie in jedes .NET‑Konsolenprojekt einbinden können. Es demonstriert jeden Schritt von der Konfiguration der `LoadOptions` bis zum Ausgeben einer übersichtlichen Liste fehlender Schriften.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Erwartete Konsolenausgabe**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Enthält das Dokument keine fehlenden Schriften, sehen Sie:

```
All referenced fonts are available – no warnings captured.
```

---

## Häufige Randfälle & deren Behandlung

| Situation | Warum es passiert | Empfohlene Lösung |
|-----------|-------------------|-------------------|
| **Dokument verwendet eine eingebettete OpenType‑Schrift** | Aspose.Words kann eingebettete Schriften lesen, aber nur, wenn die Datei nicht beschädigt ist. | Öffnen Sie das DOCX zuerst in Word; betten Sie die Schrift bei Bedarf erneut ein. |
| **Viele Warnungen** (z. B. 200+ fehlende Schriften) | Bulk‑Importe aus Altsystemen referenzieren häufig ein breites Schrift‑Portfolio. | Warnungen stapelweise verarbeiten: in einer Datenbank speichern und anschließend ein Schrift‑Installations‑Script ausführen. |
| **WarningInfoCollection ist leer** | Entweder hat das Dokument alle Schriften, oder `FontSubstitutionWarning` blieb auf `None`. | Überprüfen Sie Ihre `LoadOptions`‑Konfiguration und stellen Sie sicher, dass der korrekte Dateipfad geladen wird. |
| **Benutzerdefinierte Schriften auf einem Netzwerk‑Share** | Netzwerklatenz kann bei der Schrift‑Suche zu Timeouts führen. | Laden Sie die Schriften vorab mit `FontSettings.SetFontsFolder` und setzen Sie `CacheFontData = true`. |

Diese Tipps helfen Ihnen, **fehlende Schriften zuverlässig zu erkennen**, selbst in komplexen Umgebungen.

---

## Bildliche Darstellung

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*Der Screenshot zeigt einen Konsolendurchlauf, bei dem zwei fehlende Schriften gemeldet werden.*

---

## Nächste Schritte – Mehr als nur Berichten

Jetzt, wo Sie **Font‑Warnungen erfassen** können, überlegen Sie, die Behebung zu automatisieren:

1. **Automatischer Schrift‑Fallback** – Ersetzen Sie fehlende Schriften durch einen firmeneigenen Ersatz, indem Sie `FontSettings.SubstitutionSettings` anpassen.
2. **Logging in ein Monitoring‑System** – Leiten Sie die Warnmeldungen an Serilog, ELK oder Azure Application Insights weiter.
3. **Benutzer‑Reports** – Generieren Sie eine HTML‑ oder PDF‑Zusammenfassung, damit Designer sehen, welche Schriften installiert werden müssen.

All diese Erweiterungen bauen auf derselben Basis auf, die wir behandelt haben: `LoadOptions` konfigurieren, das Dokument laden und die `WarningInfoCollection` auswerten.

---

## Fazit

Sie haben gerade gelernt, wie Sie **Font‑Warnungen erfassen** in Aspose.Words, **fehlende Schriften erkennen** und **fehlende Schriften auflisten** mit einer sauberen, konsolenfreundlichen Ausgabe. Der Ansatz ist unkompliziert, erfordert nur wenige Zeilen C# und funktioniert mit jeder .NET‑Version, die Aspose.Words 23.x oder höher unterstützt.

Probieren Sie es mit einem Beispiel‑DOCX aus, das bewusst auf eine nicht installierte Schrift verweist – Sie werden die Warnungen sofort sehen. Anschließend können Sie entscheiden, ob Sie die fehlenden Schriftarten installieren, programmgesteuert ersetzen oder die Meldungen einfach für später protokollieren.

Viel Spaß beim Coden und mögen Ihre Dokumente stets mit den richtigen Schriften dargestellt werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}