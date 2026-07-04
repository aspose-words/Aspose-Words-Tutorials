---
category: general
date: 2026-04-21
description: Erfahren Sie, wie Sie Schriftarten erkennen, Warnungen erfassen, Rückrufe
  konfigurieren und Warnungen mit Aspose.Words in C# auflisten. Schritt‑für‑Schritt‑Anleitung
  für zuverlässige Schriftartenverwaltung.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: de
og_description: Wie erkennt man Schriftarten in Aspose.Words? Dieses Tutorial zeigt,
  wie man Warnungen erfasst, einen Callback konfiguriert und Warnungen in C# aufzählt.
og_title: Wie man Schriftarten in Aspose.Words erkennt – Vollständiger Leitfaden
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man Schriftarten in Aspose.Words erkennt – Vollständiger Leitfaden
url: /de/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Schriftarten in Aspose.Words erkennt – Vollständiger Leitfaden

Haben Sie sich jemals gefragt, **wie man Schriftarten** erkennt, die beim Laden eines Word‑Dokuments fehlen? Es ist ein Szenario, das häufiger auftritt, als man möchte, besonders beim Umgang mit Legacy‑Dateien oder plattformübergreifenden Deployments. In diesem Tutorial führen wir Sie durch ein vollständiges, ausführbares Beispiel, das **Warnungen erfasst**, **einen Callback konfiguriert** und **Warnungen aufzählt**, sodass Sie stets wissen, welche Schriftarten ersetzt wurden.

Wir verwenden Aspose.Words für .NET (v24.9 zum Zeitpunkt des Schreibens) und reines C#. Keine externen Dienste, keine Magie – nur die API und ein paar Code‑Zeilen. Am Ende können Sie jede Schriftarten‑Ersetzung erkennen, protokollieren und sogar entscheiden, ob das Laden abgebrochen werden soll, wenn eine kritische Schriftart fehlt.  

### Was Sie benötigen
- **Aspose.Words for .NET** (Installation via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 oder höher (der Code funktioniert auch unter .NET Framework)
- Eine Beispiel‑DOCX, die auf eine Schriftart verweist, die auf dem Rechner nicht vorhanden ist (z. B. „MyCustomFont.ttf“)
- Visual Studio, Rider oder ein beliebiger C#‑Editor Ihrer Wahl

> **Pro‑Tipp:** Wenn Sie kein Dokument mit fehlenden Schriftarten haben, benennen Sie einfach eine Schriftartdatei auf Ihrem System um oder bearbeiten Sie das DOCX‑XML, um auf eine nicht vorhandene Schriftfamilie zu verweisen.

---

## Wie man Schriftarten mit Aspose.Words erkennt

Die Kernidee besteht darin, sich in das Warnsystem von Aspose.Words einzuklinken. Wenn die Bibliothek eine angeforderte Schriftart nicht finden kann, erzeugt sie eine `WarningType.FontSubstitution`‑Warnung. Durch Bereitstellung einer eigenen `IWarningCallback`‑Implementierung können Sie **Schriftarten** erkennen, die während des Ladevorgangs ausgetauscht wurden.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Warum das funktioniert:** Aspose.Words ruft die `Warning`‑Methode für jedes nicht kritische Problem auf. Durch das Speichern der `WarningInfo`‑Objekte erhalten Sie vollen Zugriff auf Typ, Nachricht und Kontext – genau das, was Sie benötigen, um **Schriftarten** zu erkennen, die ersetzt wurden.

---

## Wie man Warnungen beim Laden eines Dokuments erfasst

Jetzt, wo wir einen Sammler haben, müssen wir den `LoadOptions` mitteilen, ihn zu verwenden. Das ist der **Wie‑man‑Warnungen‑erfasst**‑Teil des Puzzles.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Randfall:** Wenn Sie ein Dokument aus einem Stream laden (`new Document(stream, loadOptions)`), funktioniert derselbe Callback – übergeben Sie einfach den Stream anstelle eines Dateipfads.

An diesem Punkt ist das Dokument vollständig geladen, aber alle Schriftarten‑Ersetzungs‑Warnungen sind sicher in `warningCollector.Warnings` gespeichert.

---

## Wie man Warnungen aufzählt und Schriftart‑Ersetzungen meldet

Schließlich gehen wir die gesammelten Warnungen durch und **zählen Warnungen** auf, die speziell die Schriftarten‑Ersetzung betreffen. Dieser Schritt verwandelt Rohdaten in einen lesbaren Bericht.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Erwartete Ausgabe** (Beispiel):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Enthält das Dokument keine fehlenden Schriftarten, erzeugt die Schleife einfach keine Ausgabe – nichts, worüber man sich Sorgen machen müsste.

---

## Vollständiges funktionierendes Beispiel (Alle Schritte in einer Datei)

Unten finden Sie das komplette Programm, das Sie in ein Konsolen‑Projekt kopieren‑und‑einfügen können. Es verbindet **wie man Schriftarten erkennt**, **wie man Warnungen erfasst**, **wie man den Callback konfiguriert** und **wie man Warnungen aufzählt** in einem einzigen, zusammenhängenden Ablauf.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Wenn Sie dieses Programm ausführen**, wird jede Schriftart ausgegeben, die Aspose.Words ersetzen musste. Sie können die Ausgabe in eine Log‑Datei umleiten, einen Alarm auslösen oder das Laden sogar abbrechen, wenn eine kritische Schriftart fehlt.

---

## Häufige Fragen & Stolperfallen

### Was tun, wenn das Laden bei einer fehlenden erforderlichen Schriftart gestoppt werden soll?
Sie können die `WarningInfo`‑Objekte im Callback inspizieren und eine Ausnahme werfen, sobald ein bestimmter Schriftartname auftaucht. Die Ausnahme bricht das Laden ab und gibt Ihnen die volle Kontrolle.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Funktioniert das mit PDFs oder anderen Formaten?
Ja. Aspose.Words verwendet dieselbe Warnungs‑Infrastruktur für PDFs, RTF und HTML. Ersetzen Sie einfach die Dateierweiterung, und der Rest des Codes bleibt unverändert.

### Wie kann ich Warnungen in eine Datei statt in die Konsole protokollieren?
Ersetzen Sie `Console.WriteLine` durch ein beliebiges Logging‑Framework Ihrer Wahl (`Serilog`, `NLog` usw.). Die `WarningInfo`‑Klasse stellt `Message`, `Source` und `Exception` für detaillierte Logs bereit.

### Wird dies die Leistung beeinträchtigen?
Der Overhead ist vernachlässigbar – Aspose.Words erzeugt die Warnungen bereits intern. Das Hinzufügen eines Callbacks speichert sie lediglich in einer Liste, was O(n) in der Anzahl der Warnungen bedeutet. Bei typischen Dokumenten liegt der Einfluss weit unter 1 % der gesamten Ladezeit.

---

## Visuelle Zusammenfassung

![Wie man Schriftarten in Aspose.Words erkennt – Warnungsablaufdiagramm](https://example.com/images/font-detection-diagram.png "wie man schriftarten erkennt")

*Alt‑Text:* **wie man schriftarten erkennt** – Diagramm, das den Warnungs‑Callback, die Sammlung und die Aufzählungsschritte zeigt.

---

## Fazit

Wir haben gezeigt, **wie man Schriftarten** in Aspose.Words erkennt, indem wir **Warnungen erfasst**, **einen Callback konfiguriert** und **Warnungen aufzählt**. Das vollständige Code‑Beispiel demonstriert ein produktionsreifes Muster, das Sie in jede .NET‑Anwendung einbinden können.  

Als Nächstes möchten Sie vielleicht erkunden:

- **Wie man Warnungen erfasst** für andere Probleme (z. B. Bildkonvertierungs‑Probleme)
- **Wie man den Callback konfiguriert** für benutzerdefinierte Logging‑Frameworks
- **Wie man Warnungen aufzählt** über mehrere Dokumente hinweg in einem Batch‑Job
- Verwendung von **Aspose.Words.Fonts.FontSettings**, um Ersatz‑Schriftordner bereitzustellen, was die Anzahl der Ersetzungen von vornherein reduzieren kann.

Probieren Sie es aus, passen Sie den Sammler an Ihren Logging‑Stil an, und Sie werden nie wieder von einer unerwarteten Schriftarten‑Ersetzung überrascht. Wenn Sie auf irgendwelche Eigenheiten stoßen, hinterlassen Sie unten einen Kommentar – happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}