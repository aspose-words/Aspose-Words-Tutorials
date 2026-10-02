---
category: general
date: 2026-02-21
description: Erfahren Sie, wie Sie Warnungen aktivieren, fehlende Schriftarten erkennen
  und DOCX-Dateien sicher mit Aspose.Words in C# laden. Folgen Sie der Schritt‑für‑Schritt‑Anleitung.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: de
og_description: Wie man Warnungen aktiviert, fehlende Schriftarten erkennt und docx‑Dateien
  mit Aspose.Words korrekt lädt. Vollständiges Codebeispiel enthalten.
og_title: Wie man Warnungen aktiviert und fehlende Schriftarten beim Laden von DOCX
  erkennt
tags:
- C#
- Aspose.Words
- Document processing
title: Wie man Warnungen aktiviert und fehlende Schriftarten beim Laden von DOCX‑Dateien
  erkennt
url: /de/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen aktiviert und fehlende Schriftarten beim Laden von DOCX‑Dateien erkennt

Haben Sie sich schon einmal gefragt, **wie man Warnungen** für fehlende Schriftarten aktiviert, bevor sie stillschweigend die Dokumentdarstellung beeinträchtigen? Sie sind nicht allein – die meisten Entwickler gehen davon aus, die Bibliothek erledige das „richtige“, nur um später festzustellen, dass eine Schriftart ausgetauscht wurde, ohne dass ein Hinweis darauf erschien.  

In diesem Tutorial zeigen wir Ihnen genau **wie man Warnungen aktiviert**, **wie man fehlende Schriftarten erkennt** und den richtigen Weg, **wie man docx lädt** mit Aspose.Words für .NET. Am Ende haben Sie ein sofort ausführbares Beispiel, das jede Schriftart‑Ersetzungswarnung in die Konsole ausgibt, sodass Sie nie wieder raten müssen, was im Dokument passiert ist.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)  
- Visual Studio 2022 oder jede andere C#‑IDE Ihrer Wahl  
- Das **Aspose.Words** NuGet‑Paket (`Install-Package Aspose.Words`)  
- Eine DOCX‑Datei, die Schriftarten enthalten kann, die nicht auf Ihrem Rechner installiert sind (wir nennen sie `input.docx`)

> **Pro‑Tipp:** Wenn Sie keine Testdatei haben, öffnen Sie einfach ein Word‑Dokument, das eine benutzerdefinierte Unternehmensschriftart verwendet, und speichern Sie es als `input.docx`. Das löst die Warnung aus, die wir erfassen wollen.

## Überblick über die Lösung

1. **Erstellen** Sie ein `LoadOptions`‑Objekt mit aktivierten `FontSubstitutionWarnings`.  
2. **Laden** Sie die DOCX‑Datei mit diesen Optionen.  
3. **Untersuchen** Sie die `WarningCallback`‑Sammlung auf Einträge vom Typ `FontSubstitution`.  
4. **Reagieren** – Sie können protokollieren, anzeigen oder die fehlende Schriftart programmgesteuert ersetzen.

Im Folgenden zerlegen wir jeden Schritt, erklären *warum* er wichtig ist und geben Ihnen ein vollständiges, ausführbares Code‑Snippet.

---

## Schritt 1: Aspose.Words installieren und das Projekt einrichten

Bevor wir **wie man Warnungen aktiviert**, benötigen wir die Bibliothek, die das überhaupt unterstützt.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Oder in der Visual‑Studio‑Package‑Manager‑Konsole:

```powershell
Install-Package Aspose.Words
```

> **Warum dieser Schritt?**  
> Ohne das Paket existieren `LoadOptions`, `Document` und die Warnungs‑Infrastruktur einfach nicht. Das Hinzufügen der NuGet‑Referenz stellt sicher, dass Sie die neueste stabile Version verwenden (zum Zeitpunkt dieses Schreibens 24.5).

---

## Schritt 2: Ladeoptionen erstellen, die Schriftart‑Ersetzungs‑Warnungen aktivieren

Das Herzstück von **wie man Warnungen aktiviert** steckt in der Klasse `LoadOptions`. Das Setzen von `FontSubstitutionWarnings` auf `true` weist die Engine an, jedes Mal zu protokollieren, wenn sie eine fehlende Schriftart ersetzen muss.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Warum dieses Flag aktivieren?**  
> Standardmäßig tauscht Aspose.Words fehlende Schriftarten stillschweigend gegen eine Ersatzschrift (meist Arial) aus. Das kann zu Layout‑Verschiebungen, unsichtbaren Zeichen oder Marken‑Verstößen führen. Durch das Aktivieren des Flags erhalten Sie vollständige Transparenz.

---

## Schritt 3: Die DOCX‑Datei mit den konfigurierten Optionen laden

Jetzt, wo wir **wie man docx lädt** mit aktivierten Warnungen kennen, führen wir den Ladevorgang tatsächlich aus.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Was passiert im Hintergrund?**  
> Beim Parsen der DOCX prüft Aspose.Words jedes `<w:rFonts>`‑Element. Ist die angegebene Schriftart nicht installiert, wird eine `FontSubstitution`‑Warnung erzeugt und auf eine Standardschriftart zurückgegriffen. Da wir Warnungen aktiviert haben, landen diese Einträge in `document.WarningCallback.Warnings`.

---

## Schritt 4: Schriftart‑Ersetzungs‑Warnungen abrufen und anzeigen

Die Eigenschaft `WarningCallback` enthält eine `WarningInfoCollection`. Durchlaufen Sie diese, filtern Sie nach `WarningType.FontSubstitution` und geben Sie die Meldungen aus.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Erwartete Ausgabe** (Beispiel):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Was tun mit diesen Meldungen?**  
> Sie können sie in eine Datei protokollieren, in einer UI anzeigen oder sogar eine benutzerdefinierte Schrift‑Fallback‑Routine auslösen. Der entscheidende Punkt ist, dass Sie jetzt *fehlende Schriftarten erkennen* statt später zu raten.

---

## Schritt 5: (Optional) Fehlende Schriftarten durch einen bestimmten Ersatz ersetzen

Wenn Sie eine Unternehmensschriftart durchsetzen möchten, können Sie die Warnungen verarbeiten und sie on‑the‑fly ersetzen.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Warum das in Betracht ziehen?**  
> Es garantiert visuelle Konsistenz über alle erzeugten Dokumente hinweg, was für die Marken‑Einheitlichkeit entscheidend ist.

---

## Vollständiges, ausführbares Beispiel

Unten finden Sie eine einzelne C#‑Datei, die Sie in eine Konsolen‑App kopieren können. Sie deckt alles ab – vom Installieren des Pakets bis zum Ausgeben der Warnungen.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Ausführen:** `dotnet run` im Projektordner. Wenn Schriftarten fehlen, sehen Sie die Warnungen in der Konsole, und die optionale Ersetzung wird angewendet, bevor die Datei gespeichert wird.

---

## Häufig gestellte Fragen

### Funktioniert das auch bei der PDF‑Konvertierung?

Ja. Nachdem Sie die Warnungen verarbeitet haben, können Sie `doc.Save("output.pdf")` aufrufen und die ersetzten Schriftarten erscheinen im PDF genauso wie in der DOCX.

### Was, wenn ich Warnungen für eine bestimmte Schriftart unterdrücken möchte?

Sie können sie in der Schleife herausfiltern – einfach das `WarningInfo`‑Objekt überspringen, dessen `Message` den Namen der zu ignorierenden Schriftart enthält.

### Ist `FontSubstitutionWarnings` in älteren Aspose.Words‑Versionen verfügbar?

Es wurde in Version 20.5 eingeführt. Wenn Sie eine ältere Version verwenden, aktualisieren Sie über NuGet; die API‑Änderung ist rückwärtskompatibel.

---

## Fazit

Wir haben gezeigt, **wie man Warnungen aktiviert**, **wie man fehlende Schriftarten erkennt** und den korrekten Weg, **wie man docx lädt** mit Aspose.Words, während man volle Transparenz über Schriftart‑Ersetzungen behält. Durch das Untersuchen von `document.WarningCallback.Warnings` erhalten Sie ein zuverlässiges Audit‑Protokoll – keine stillen Fallbacks mehr.

Nächste Schritte? Binden Sie die Warnungs‑Logik in ein Logging‑Framework wie Serilog ein oder bauen Sie eine UI, die fehlende Schriftarten vor dem Versand des Dokuments hervorhebt. Sie können zudem die Klasse `FontSettings` für eine noch feinere Steuerung der Schriftart‑Ersetzungs‑Richtlinien erkunden.

Viel Spaß beim Coden, und mögen Ihre Dokumente immer exakt so gerendert werden, wie Sie es beabsichtigen! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}