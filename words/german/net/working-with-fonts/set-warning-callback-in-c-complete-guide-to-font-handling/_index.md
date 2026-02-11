---
category: general
date: 2026-02-10
description: Setzen Sie einen Warnungs‑Callback, um Schriftartänderungen zu überwachen,
  während Sie die Standardschriftart konfigurieren und die Standardschriftart für
  den Import in Aspose.Words festlegen. Erfahren Sie die vollständige Schritt‑für‑Schritt‑Lösung.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: de
og_description: Setzen Sie den Warnungs‑Callback, um Schriftartänderungen zu überwachen,
  während Sie die Standardschriftart konfigurieren und die Standardschriftart für
  den Import festlegen. Folgen Sie dem vollständigen Tutorial für Aspose.Words.
og_title: Warnungs‑Callback in C# festlegen – Vollständige Anleitung
tags:
- Aspose.Words
- C#
- Document Import
title: Warnungs‑Callback in C# festlegen – Kompletter Leitfaden zur Schriftartenverwaltung
url: /de/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Warnungs‑Callback in C# festlegen – Vollständiger Leitfaden zur Schriftartenverarbeitung

Haben Sie jemals **Warnungs‑Callback festlegen** müssen, wenn Sie ein Word‑Dokument laden, und sich gleichzeitig gefragt, wie man *Standard‑Schriftart konfigurieren* kann? Sie sind nicht allein. In vielen realen Projekten – wie automatisierten Berichtsgeneratoren oder Dokumentkonvertierungspipelines – können fehlende Schriftarten stillschweigend das Layout zerstören, und der einzige Weg, diese Probleme zu erkennen, besteht darin, **Schriftartenänderungen zu überwachen** über einen Warnungs‑Callback.

In diesem Tutorial führen wir Sie durch ein praktisches Beispiel, das zeigt, wie Sie **Warnungs‑Callback festlegen**, **Standard‑Schriftart konfigurieren** und sogar **Standard‑Import‑Schriftart festlegen** mit Aspose.Words für .NET. Am Ende haben Sie ein sofort ausführbares Snippet, verstehen, warum jedes Element wichtig ist, und wissen, wie Sie es für Sonderfälle wie benutzerdefinierte Schriftordner oder stille Ersetzungen anpassen können.

---

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)  
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)  
- Ein Ordner, der die Ersatzschriftart enthält, die Sie verwenden möchten (z. B. `fonts/Arial.ttf`)  
- Grundlegende Kenntnisse von C#‑Konsolen‑Apps  

Es werden keine zusätzlichen Bibliotheken benötigt.

---

## Schritt 1: LoadOptions erstellen und **Standard‑Schriftart konfigurieren**

Das Erste, was Sie tun, wenn Sie die Schriftartenverarbeitung steuern möchten, ist eine `LoadOptions`‑Instanz zu erstellen. Dieses Objekt teilt Aspose.Words mit, wie fehlende Schriftarten beim Import behandelt werden sollen.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Warum das wichtig ist:**  
Wenn das Quell‑Dokument eine Schriftart referenziert, die nicht auf dem Server installiert ist, schaut Aspose.Words in den von Ihnen angegebenen Ordner. Das ist das Kernprinzip von **Standard‑Import‑Schriftart festlegen** – Sie teilen der Bibliothek explizit mit, wo ein Ersatz gefunden werden kann, bevor überhaupt Warnungen ausgegeben werden.

---

## Schritt 2: **Warnungs‑Callback festlegen** um **Schriftartenänderungen zu überwachen**

Aspose.Words erzeugt eine `WarningInfoCollection`, wann immer es eine Schriftart ersetzen muss, unter anderem. Durch das Anhängen eines Handlers können Sie jede Ersetzung protokollieren oder darauf reagieren.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Warum das wichtig ist:**  
Einfach **Standard‑Schriftart konfigurieren** reicht nicht aus, wenn Sie prüfen müssen, welche Schriftarten tatsächlich ausgetauscht wurden. Der Callback liefert ein Echtzeit‑Log, erfüllt die Anforderung **Schriftartenänderungen zu überwachen** und hilft, unerwartete Ersatzschriften frühzeitig in einer CI‑Pipeline zu erkennen.

---

## Schritt 3: Dokument mit den vorbereiteten Optionen laden

Da die Ladeoptionen nun vollständig vorbereitet sind, können Sie jede `.docx`‑Datei sicher laden. Der Callback wird automatisch ausgelöst, wenn eine Ersetzung stattfindet.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Was Sie sehen werden:**  
Wenn das Quell‑Dokument eine nicht vorhandene Schriftart verwendet, gibt die Konsole etwas Ähnliches aus:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Diese Ausgabe bestätigt, dass Sie erfolgreich **Warnungs‑Callback festgelegt** haben und dass die **Standard‑Import‑Schriftart** wirksam wurde.

---

## Schritt 4: (Optional) Verhalten der Schriftart‑Ersetzung feinabstimmen

Manchmal möchten Sie *alle* fehlenden Schriftarten durch eine einzige Familie ersetzen, unabhängig von der ursprünglichen Anforderung. Aspose.Words ermöglicht das globale Setzen einer *Ersatzschriftart*.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Wann das zu verwenden ist:**  
Wenn Sie PDFs für eine Marke erstellen, die nur einen begrenzten Satz von Schriftarten zulässt, sorgt dies für Konsistenz in jedem Dokument, selbst wenn das Quell‑Dokument etwas Exotisches verwenden möchte.

---

## Schritt 5: Dokument speichern oder weiterverarbeiten

Nach dem Laden können Sie jede gewünschte Verarbeitung fortsetzen – Bearbeiten, in PDF konvertieren, Text extrahieren usw. Hier ein kurzes Beispiel, wie das Dokument als PDF gespeichert wird, wobei die ersetzten Schriftarten erhalten bleiben.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Das resultierende PDF zeigt die Ersatzschriftart überall dort, wo eine Ersetzung stattfand, und liefert eine visuelle Bestätigung, dass der **Warnungs‑Callback festgelegt** wie erwartet funktioniert hat.

---

## Häufige Fallstricke & Pro‑Tipps

| Fallstrick | Warum es passiert | Lösung |
|------------|-------------------|--------|
| **Callback never fires** | `LoadOptions.WarningCallback` wurde *nicht* vor dem Laden des Dokuments zugewiesen. | Hängen Sie den Callback immer **vor** dem Aufruf von `new Document(...)` an. |
| **Wrong font folder** | Pfad‑Tippfehler oder fehlende Leseberechtigungen. | Stellen Sie sicher, dass der Ordner existiert und die Anwendung Lese‑Zugriff hat. Verwenden Sie absolute Pfade für Zuverlässigkeit. |
| **Multiple substitutions, noisy output** | Große Dokumente mit vielen fehlenden Schriftarten. | Filtern Sie Warnungen nach `WarningType.FontSubstitution` (wie gezeigt) oder schreiben Sie sie in eine Log‑Datei statt in die Konsole. |
| **Fallback font not applied** | Die Ersatzschriftart ist nicht auf dem Rechner installiert. | Legen Sie die `.ttf`/`.otf`‑Datei in den Ordner, den Sie `SetFontsFolder` übergeben haben. Aspose.Words lädt sie direkt, eine OS‑Installation ist nicht nötig. |

**Pro‑Tipp:** Wenn Sie dies in einer CI/CD‑Pipeline ausführen, leiten Sie die Konsolenausgabe zu einem Build‑Artefakt um. So haben Sie einen Prüfpfad für jede Schriftart‑Ersetzung, die während des Builds stattgefunden hat.

---

## Vollständiges funktionierendes Beispiel (Kopieren‑und‑Einfügen bereit)

Unten finden Sie das komplette Programm, das Sie in ein neues Konsolen‑App‑Projekt einfügen können. Es enthält alle Schritte, using‑Anweisungen und Kommentare, die Sie benötigen.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Erwartete Konsolenausgabe** (unter der Annahme, dass `Times New Roman` fehlt):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Führen Sie das Programm aus, öffnen Sie `output.pdf`, und Sie werden das Dokument sehen, das überall dort mit der Ersatzschriftart gerendert wird, wo es nötig ist.

---

## Fazit

Sie haben nun ein solides, produktionsreifes Muster, wie Sie **Warnungs‑Callback festlegen** in C#, **Standard‑Schriftart konfigurieren**, **Schriftartenänderungen überwachen** und **Standard‑Import‑Schriftart festlegen** bei der Arbeit mit Aspose.Words. Indem Sie einen Warnungssammler vor dem Laden anhängen, `FontSettings` auf einen zuverlässigen Schriftordner verweisen und optional einen globalen Ersatz erzwingen, erhalten Sie vollständige Sichtbarkeit und Kontrolle über Schriftart‑Ersetzungen – genau das, was jede robuste Dokument‑Verarbeitungspipeline benötigt.

Bereit für die nächste Stufe? Versuchen Sie, diesen Ansatz zu kombinieren mit:

- **Dynamisches Laden von Schriftarten** aus einer Datenbank (verwenden Sie `FontSettings.SetFontsFolder` zur Laufzeit).  
- **Benutzerdefinierte Warnungs‑Handler**, die in ein strukturiertes Log (JSON oder CSV) für Analysen schreiben.  
- **Parallele Dokumentenverarbeitung**, bei der jeder Thread seine eigenen `LoadOptions` erhält, um Überschneidungen zu vermeiden.  

Fühlen Sie sich frei zu experimentieren, den Code an Ihre eigene Architektur anzupassen und Ihre Entdeckungen in den Kommentaren zu teilen. Viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}