---
category: general
date: 2026-04-10
description: Wie man LoadOptions in Aspose.Words verwendet, um Schriftart‑Ersetzungshinweise
  beim Laden von Dokumenten zu erfassen. Lernen Sie eine Schritt‑für‑Schritt‑C#‑Lösung
  mit einem vollständigen Codebeispiel.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: de
og_description: Wie man LoadOptions in Aspose.Words verwendet, um Schriftart‑Ersetzungshinweise
  beim Laden von Dokumenten zu erfassen. Dieser Leitfaden führt Sie durch eine vollständige
  C#‑Implementierung.
og_title: Wie man LoadOptions in Aspose.Words verwendet – Vollständiger C#‑Leitfaden
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Wie man LoadOptions in Aspose.Words verwendet – Vollständiger C#‑Leitfaden
url: /de/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man LoadOptions in Aspose.Words verwendet – Vollständiger C#‑Leitfaden

Wie man LoadOptions in Aspose.Words verwendet, ist ein häufiges Hindernis, wenn Sie eine enge Kontrolle über das Laden von Dokumenten benötigen. In diesem Tutorial zeigen wir Ihnen genau **wie man LoadOptions verwendet**, um Warnungen bei Schriftart‑Ersetzungen abzufangen und darauf in C# zu reagieren.  

Wenn Sie jemals ein DOCX geöffnet haben, das auf eine fehlende Schriftart verweist, und sich gefragt haben, warum das Ergebnis seltsam aussieht, sind Sie hier richtig. Wir gehen den gesamten Prozess durch, vom Erstellen einer `LoadOptions`‑Instanz bis zum Ausgeben von Warnungsdetails auf der Konsole. Am Ende haben Sie ein einsatzbereites Snippet, das Sie in jedes .NET‑Projekt einbinden können.

## Was Sie lernen werden

- Warum `LoadOptions` für zuverlässige Dokumentimporte wichtig ist.  
- Wie man einen **WarningCallback** einbaut, der speziell nach **Schriftart‑Ersetzungswarnungen** Ausschau hält.  
- Der genaue Code, der nötig ist, um eine Word‑Datei mit aktivierten Optionen zu laden.  
- Tipps zum Umgang mit Sonderfällen, z. B. Dokumenten, die mehrere fehlende Schriftarten enthalten.  

Keine externe Dokumentation nötig – alles, was Sie brauchen, finden Sie hier.

## Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| .NET 6.0 oder höher | Stellt die Laufzeit für die in den Beispielen verwendete C# 10‑Syntax bereit. |
| Aspose.Words für .NET (neueste Version) | Die Bibliothek, die `LoadOptions` und die Warnungsinfrastruktur bereitstellt. |
| Eine DOCX‑Datei, die möglicherweise auf nicht installierte Schriftarten verweist | Um den Warn‑Callback in Aktion zu sehen. |
| Visual Studio 2022 (oder ein beliebiges IDE Ihrer Wahl) | Macht Debugging und Testen unkompliziert. |

Wenn Sie das bereits haben, großartig – lassen Sie uns loslegen.

## Schritt 1 – Erstellen eines LoadOptions‑Objekts und Einbinden des WarningCallback

Das Erste, was Sie tun, wenn Sie **wie man LoadOptions verwendet**, ist, es zu instanziieren. Der entscheidende Teil ist das Zuweisen eines Delegaten zu `WarningCallback`. Dieser Delegat wird jedes Mal ausgelöst, wenn Aspose.Words auf eine Situation stößt, über die Sie informiert werden sollten – insbesondere bei einer fehlenden Schriftart.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Warum das wichtig ist:** Ohne den Callback tauscht Aspose.Words fehlende Schriftarten stillschweigend gegen Standardschriftarten aus, und Sie bemerken die visuelle Verschiebung möglicherweise nie. Durch das Registrieren eines `WarningCallback` erhalten Sie ein Echtzeit‑Log jeder Ersetzung, was für qualitätsgesicherte Dokument‑Pipelines unverzichtbar ist.

## Schritt 2 – Nur auf Schriftart‑Ersetzungswarnungen reagieren

Sie fragen sich vielleicht, ob der Callback Sie mit irrelevanten Warnungen (wie veralteten Features) überflutet. Die Antwort ist *ja* – aber wir können sie filtern. Im obigen Snippet prüfen wir bereits `args.WarningType == WarningType.FontSubstitution`. Diese Zeile ist die **Schriftart‑Ersetzungs‑Warnungs‑Abfrage**, ein sekundäres Schlüsselwort, das die Ausgabe fokussiert.

Falls Sie andere Warnungstypen behandeln wollen, erweitern Sie einfach den `if`‑Block:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Dieses Muster zeigt, wie flexibel der **warningcallback**‑Mechanismus ist und Ihnen ermöglicht, Antworten exakt an die Szenarien anzupassen, die Sie interessieren.

## Schritt 3 – Laden Ihres Dokuments mit den konfigurierten LoadOptions

Jetzt, wo der Listener bereit ist, ist das letzte Stück, die `LoadOptions`‑Instanz an den `Document`‑Konstruktor zu übergeben. Das ist der Moment, in dem das **Aspose.Words LoadOptions Beispiel** wirklich glänzt.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Was Sie sehen werden:** Wenn das DOCX auf eine Schriftart verweist, die nicht auf dem Rechner installiert ist, gibt die Konsole eine Zeile aus wie:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Diese Ausgabe bestätigt, dass Sie **wie man LoadOptions verwendet** erfolgreich implementiert haben, um Schriftart‑Probleme zu überwachen.

## Vollständiges funktionierendes Beispiel (Copy‑Paste‑bereit)

Unten finden Sie das komplette Programm, das Sie sofort kompilieren und ausführen können. Es fasst alle drei Schritte zusammen, fügt ein paar nette Extras (wie ein freundliches Banner) hinzu und demonstriert die Fehlerbehandlung.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Erwartete Ausgabe

Das Ausführen des Programms auf einem Rechner, dem die im `input.docx` referenzierte Schriftart fehlt, liefert etwa Folgendes:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Sind alle Schriftarten vorhanden, sehen Sie nur die Erfolgsmeldungen – es erscheinen keine Warnzeilen.

## Häufige Stolperfallen & Pro‑Tipps

- **Stolperfalle:** Vergessen, `WarningCallback` zu setzen. Der Code lädt weiterhin, aber Sie verpassen die Ersetzungsdetails.  
  **Pro‑Tipp:** Weisen Sie den Callback sofort nach dem Erzeugen von `LoadOptions` zu; das kostet kaum etwas und zahlt sich später aus.

- **Stolperfalle:** Einen relativen Pfad verwenden, der auf den falschen Ordner zeigt.  
  **Pro‑Tipp:** Nutzen Sie `Path.Combine(Environment.CurrentDirectory, "input.docx")` für eine robustere Dateisuche.

- **Stolperfalle:** Annehmen, die Warnung würde das Laden stoppen.  
  **Pro‑Tipp:** Schriftart‑Ersetzungswarnungen sind *informativ*; sie brechen den Ladevorgang nicht ab. Wenn Sie strengere Validierung benötigen, werfen Sie im Callback eine Ausnahme, sobald eine Ersetzung auftritt.

- **Stolperfalle:** Auf einem Server ohne installierte Schriftarten laufen (z. B. ein Minimal‑Docker‑Image).  
  **Pro‑Tipp:** Installieren Sie die benötigten Schriftarten vorab oder bündeln Sie sie mit Ihrer Anwendung und prüfen Sie dann mit dem Callback, dass in der Produktion keine Ersetzungen stattfinden.

## LoadOptions vs. Nach‑Lade‑Inspektion

Sie könnten fragen: „Warum nicht das Dokument nach dem Laden inspizieren?“ Die Antwort liegt in Performance und Korrektheit. Durch das Behandeln von Warnungen **während** des Ladens fangen Sie Probleme früh ab – bevor Layout‑Berechnungen oder PDF‑Konvertierungen stattfinden. Das ist besonders wertvoll in Batch‑Verarbeitungspipelines, wo jeder zusätzliche Schritt Zeit kostet.

## Beispiel erweitern: Bericht über alle ersetzten Schriftarten speichern

Falls Sie einen dauerhaften Nachweis benötigen (z. B. für Compliance), ändern Sie den Callback, sodass er Nachrichten in einer Liste sammelt und nach dem Laden in eine Datei schreibt:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Jetzt haben Sie sowohl Konsolen‑Feedback als auch ein beständiges Log.

## Verwandte Themen, die Sie als Nächstes erkunden könnten

- **Wie man benutzerdefinierte Schriftarten in Aspose.Words einbettet** – eliminiert Ersetzungen vollständig.  
- **LoadOptions verwenden, um die Dokumentgröße zu begrenzen** – schützt vor bösartig großen Dateien.  
- **Word nach PDF konvertieren mit erhaltenen Typografie‑Einstellungen** – passt gut zum Warning‑Callback‑Ansatz.  

Jedes dieser Themen baut auf dem Fundament auf, das Sie gerade mit `LoadOptions` geschaffen haben.

## Fazit

Wir haben **wie man LoadOptions in Aspose.Words** von Anfang bis Ende behandelt: Optionen erstellen, einen `WarningCallback` einbinden, der gezielt **Schriftart‑Ersetzungswarnungen** abfängt, und ein Dokument mit Zuversicht laden. Das vollständige Beispiel läuft sofort, und die zusätzlichen Tipps helfen Ihnen, gängige Fallstricke zu vermeiden.  

Experimentieren Sie gern – tauschen Sie den Callback gegen andere Warnungstypen aus, loggen Sie in eine Datenbank oder integrieren Sie die Logik in einen Web‑Service, der hochgeladene Word‑Dateien validiert. Das Muster ist flexibel, zuverlässig und gibt Ihnen vor allem Sichtbarkeit in den verborgenen Schriftart‑Ersetzungs‑Prozess, der sonst Ihre Dokumentdarstellung verderben könnte.

Viel Spaß beim Coden, und mögen Ihre Dokumente stets exakt wie beabsichtigt gerendert werden! 

![Diagram showing the flow of using LoadOptions with a warning callback in Aspose.Words](https://example.com/images/loadoptions-flow.png "How to use LoadOptions diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}