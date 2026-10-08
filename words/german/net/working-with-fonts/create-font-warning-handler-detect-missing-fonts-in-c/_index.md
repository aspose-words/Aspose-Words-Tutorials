---
category: general
date: 2026-02-12
description: Erstellen Sie einen Schriftart‑Warnungs‑Handler, um fehlende Schriftarten
  zu erkennen und fehlende Schriftarten in Aspose.Words zu verfolgen. Erfahren Sie,
  wie Sie Warnungen effizient protokollieren.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: de
og_description: Erstellen Sie einen Schriftart‑Warnungs‑Handler in C#, um fehlende
  Schriftarten zu erkennen, und erfahren Sie, wie Sie Warnungen protokollieren, wenn
  Aspose.Words Schriftarten ersetzt.
og_title: Erstelle Schriftart-Warnungs-Handler – Fehlende Schriftarten erkennen
tags:
- Aspose.Words
- C#
- Document Processing
title: Erstelle Schriftart‑Warnungs‑Handler – Erkenne fehlende Schriftarten in C#
url: /de/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstelle Font‑Warnungs‑Handler – Fehlende Schriftarten in C# erkennen

Haben Sie schon einmal einen **Font‑Warning‑Handler** erstellen müssen, weil ein Word‑Dokument stillschweigend eine Schriftart ausgetauscht hat, die Sie nicht erwartet haben? Sie sind nicht allein. Wenn Aspose.Words ein DOCX lädt, das eine Schriftart referenziert, die auf dem Server nicht vorhanden ist, greift es stillschweigend auf eine Standardschrift zurück – wodurch Ihr Layout subtil beschädigt wird.  

In diesem Tutorial zeigen wir Ihnen genau, wie Sie **fehlende Schriftarten erkennen**, **fehlende Schriftarten verfolgen** und **Warnungen protokollieren**, sodass Sie diese Ersetzungen rechtzeitig bemerken. Am Ende haben Sie einen wiederverwendbaren Warnungs‑Handler, der jedes Schriftart‑Ersetzungs‑Ereignis in die Konsole (oder einen beliebigen Logger Ihrer Wahl) ausgibt. Keine Geheimnisse, nur klarer, umsetzbarer Code.

## Voraussetzungen

- .NET 6.0 oder höher (die API ist dieselbe für .NET Framework 4.6+)
- Aspose.Words für .NET installiert (`dotnet add package Aspose.Words`)
- Eine Word‑Datei, die eine Schriftart referenziert, die nicht auf Ihrem Rechner installiert ist (z. B. `MissingFont.docx`)

Wenn Sie das bereits haben, super – lassen Sie uns loslegen.

## Schritt 1: LoadOptions mit einem Warn‑Callback einrichten  

Das Erste, was Sie tun, wenn Sie einen **Font‑Warning‑Handler erstellen** möchten, ist Aspose.Words mitzuteilen, dass bei einem Problem ein Callback ausgelöst werden soll. `LoadOptions` ist der Behälter für diese Konfiguration.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Warum das wichtig ist:**  
`LoadOptions` ist der einzige Ort, an dem Sie ein `IWarningCallback` einbinden können. Ohne diesen Callback protokolliert Aspose.Words Warnungen intern, Sie sehen sie jedoch nie. Durch das Zuweisen von `FontWarningHandler` erhalten Sie die volle Kontrolle darüber, was passiert, wenn eine fehlende Schriftart substituiert wird.

## Schritt 2: Die Klasse FontWarningHandler implementieren  

Jetzt schreiben wir tatsächlich den Code für den **Font‑Warning‑Handler**. Die Klasse implementiert `IWarningCallback` und erhält für jede von Aspose.Words ausgelöste Warnung ein `WarningInfo`‑Objekt.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Erläuterung:**  
- `info.Type` gibt die Kategorie der Warnung an. Wir interessieren uns für `WarningType.FontSubstitution`, weil dies anzeigt, dass eine Schriftart fehlt.  
- `info.Description` enthält eine menschenlesbare Meldung wie *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.“*  
- Durch das Schreiben in `Console.WriteLine` **protokollieren wir Warnungen** sofort. In einer realen Anwendung ersetzen Sie das möglicherweise durch `ILogger`, einen Dateischreiber oder einen Telemetrie‑Dienst.

> **Pro‑Tipp:** Wenn Sie alle fehlenden Schriftarten später berichten möchten, speichern Sie `info.Description` in einer `List<string>` statt sie sofort auszugeben.

## Schritt 3: Das Dokument mit den konfigurierten LoadOptions laden  

Mit dem Callback an Ort und Stelle wird das Laden eines Dokuments automatisch unseren Handler auslösen, sobald eine Schriftart fehlt.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Was Sie sehen werden:**  
Beim Ausführen des Programms erscheint etwa Folgendes:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Diese Zeile bestätigt, dass Sie **fehlende Schriftarten erfolgreich erkannt** und nun **fehlende Schriftarten in Echtzeit verfolgen**.

## Schritt 4: Den Handler mit verschiedenen Szenarien verifizieren  

Es ist leicht anzunehmen, der Handler funktioniere nur für DOCX‑Dateien, aber Aspose.Words unterstützt viele Formate. Versuchen Sie, ein PDF zu laden, das eine eingebettete Schriftart referenziert, oder eine ältere `.doc`‑Datei. Der gleiche Callback wird für jedes Format ausgelöst, das den Schrift‑Auflösungs‑Pipeline durchläuft.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Wenn das PDF eine Schriftart referenziert, die nicht installiert ist, erhalten Sie dieselbe Konsolenausgabe. Das zeigt, dass Ihre **Font‑Warning‑Handler**‑Lösung formatunabhängig ist.

## Schritt 5: Den Handler erweitern – Protokollierung in eine Datei  

Konsolenausgabe ist für Demos praktisch, aber Produktionscode schreibt meist in eine Log‑Datei. Hier ein schneller Patch.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Jetzt wird bei jeder Schriftart‑Substitution die Meldung an `font-warnings.log` angehängt. Das erfüllt den **how to log warnings**‑Teil der Aufgabenstellung und liefert ein dauerhaftes Audit‑Trail.

## Schritt 6: Alles zusammen – Vollständiges, ausführbares Beispiel  

Unten finden Sie das komplette Programm, das Sie in eine Konsolen‑App kopieren‑und‑einfügen können. Es fehlen keine Teile; ersetzen Sie lediglich den Dateipfad durch Ihr eigenes Dokument.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Erwartetes Ergebnis:**  

- Die Konsole gibt jede Substitutionszeile aus.  
- `font-warnings.log` enthält nun einen zeitgestempelten Eintrag jedes fehlenden‑Schriftart‑Ereignisses.  
- Die Datei `output.pdf` wird mit den substituierten Schriftarten erstellt, sodass die Konvertierung auch dann gelingt, wenn die Original‑Schriftarten nicht verfügbar sind.

## Häufige Fragen & Sonderfälle  

| Frage | Antwort |
|----------|--------|
| *Was, wenn ich bestimmte Schriftarten ignorieren möchte?* | Prüfen Sie im `Warning`‑Handler `info.Description` auf den Schriftartnamen und `return;` frühzeitig für Schriftarten, die Sie akzeptieren. |
| *Wird der Handler bei eingebetteten Schriftarten ausgelöst?* | Nein – eingebettete Schriftarten stehen dem Dokument immer zur Verfügung, daher gibt es keine Substitutions‑Warnung. |
| *Kann ich andere Warnungstypen erfassen (z. B. Bild‑Auflösungs‑Probleme)?* | Absolut. Entfernen Sie die Bedingung `if (info.Type == WarningType.FontSubstitution)` oder fügen Sie zusätzliche `if`‑Blöcke für `WarningType.ImageResolution` hinzu. |
| *Ist der Handler thread‑sicher?* | Die gezeigte Standard‑Implementierung schreibt ohne Synchronisation in eine Datei. Für Multithread‑Szenarien sollten Dateischreibvorgänge in einem Lock gekapselt oder ein konkurrierender Logger verwendet werden. |

## Nächste Schritte  

Jetzt, wo Sie **wie man Warnungen für fehlende Schriftarten protokolliert** kennen, könnten Sie:

- **Fehlende Schriftarten** während eines Batch‑Import‑Prozesses erkennen und einen Zusammenfassungs‑Report erstellen.  
- **Fehlende Schriftarten** über mehrere Dokumente hinweg verfolgen und eine E‑Mail‑Benachrichtigung senden, wenn eine bestimmte Schriftart häufig vorkommt.  
- **In ein Monitoring‑System** (z. B. Azure Application Insights) integrieren, um Trends bei Schriftart‑Substitutionen im Zeitverlauf sichtbar zu machen.  

All diese Erweiterungen bauen auf derselben `IWarningCallback`‑Grundlage auf, die wir erstellt haben.

---

*Viel Spaß beim Coden! Wenn Sie auf Eigenheiten stoßen – etwa einen benutzerdefinierten Schriftarten‑Ordner oder ein Netzwerk‑Share – hinterlassen Sie einen Kommentar unten. Die Community (und ich) helfen Ihnen gern, Ihre Font‑Warning‑Strategie zu verfeinern.* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}