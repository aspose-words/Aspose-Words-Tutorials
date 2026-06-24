---
category: general
date: 2026-06-20
description: Aktivieren Sie Schriftart‑Substitutionswarnungen in C# mit Aspose.Words.
  Erfahren Sie, wie Sie LoadOptions konfigurieren, Warnungen erfassen und fehlende
  Schriftarten effizient behandeln.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: de
og_description: Aktivieren Sie Warnungen für Schriftartsubstitutionen in C# mit Aspose.Words.
  Dieser Leitfaden zeigt Ihnen, wie Sie LoadOptions einrichten, WarningInfo auslesen
  und Meldungen über fehlende Schriftarten anzeigen.
og_title: Warnungen bei Schriftart-Substitution in C# aktivieren – Komplettanleitung
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Warnungen zur Schriftart-Substitution in C# mit Aspose.Words aktivieren
url: /de/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font‑Substitutionswarnungen in C# mit Aspose.Words aktivieren

Haben Sie sich jemals gefragt, wie man **Font-Substitutionswarnungen** aktiviert, wenn ein Word‑Dokument eine Schriftart referenziert, die auf dem Server nicht installiert ist? Sie sind nicht allein. Fehlende Schriftarten können stillschweigend das Layout von erzeugten PDFs oder Bildern beschädigen, und der einzige Weg, das frühzeitig zu erkennen, besteht darin, die von Aspose.Words ausgegebenen Warnungen zu beobachten.

In diesem Tutorial führen wir Sie durch ein praktisches Beispiel, das genau zeigt, wie Sie diese Warnungen aktivieren, sie aus der `WarningInfo`‑Sammlung extrahieren und aussagekräftige Meldungen in der Konsole ausgeben. Am Ende wissen Sie, wie Sie **Aspose.Words LoadOptions** konfigurieren, **C#‑Font‑Substitutionswarnungen** behandeln und Ihre Dokumentverarbeitungspipeline robust halten.

Wir gehen auch auf einige Randfälle ein – was passiert, wenn Sie Warnungen unterdrücken oder sie statt der Ausgabe protokollieren müssen – und geben Ihnen ein vollständiges, sofort einsatzbereites Code‑Beispiel, das mit der neuesten Aspose.Words‑Version für .NET (Stand Version 24.10) funktioniert.

## Was Sie benötigen

- .NET 6.0 oder höher (der Code funktioniert auch unter .NET Framework 4.7+)
- Ein NuGet‑Verweis auf `Aspose.Words` (Installation über `dotnet add package Aspose.Words`)
- Eine Word‑Datei, die eine Schriftart referenziert, die Sie **nicht** installiert haben (z. B. `DocumentWithMissingFont.docx`)
- Eine geeignete IDE (Visual Studio, Rider oder VS Code)

Das war’s – keine zusätzlichen Dienste, keine proprietären Werkzeuge. Bereit? Dann legen wir los.

## Schritt 1: Font‑Substitutionswarnungen aktivieren

Das Erste, was Sie tun müssen, ist Aspose.Words mitzuteilen, dass Sie benachrichtigt werden möchten, wenn eine fehlende Schriftart substituiert wird. Dies geschieht über die `FontSettings`‑Eigenschaft eines `LoadOptions`‑Objekts. Standardmäßig sind Warnungen **deaktiviert**, um die API ruhig zu halten, daher müssen wir den Schalter selbst umlegen.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Warum das funktioniert:** Wenn `FontSettings` nicht `null` ist, füllt die Bibliothek automatisch `Document.WarningInfo` mit allen `WarningType.FontSubstitution`‑Einträgen, die beim Laden eines Dokuments auftreten. Betrachten Sie es als Aktivierung eines „Debug‑Modus“ für Schriftarten.

## Schritt 2: Dokument mit konfigurierten Optionen laden

Da die Warnungssammlung nun aktiv ist, laden Sie Ihr Dokument mit den gerade erstellten `LoadOptions`. Enthält das Dokument eine fehlende Schriftart, substituiert Aspose.Words eine Ersatzschrift und fügt eine Warnung zur `WarningInfo`‑Liste hinzu.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro‑Tipp:** Wenn Sie viele Dateien in einer Schleife verarbeiten, verwenden Sie dieselbe `LoadOptions`‑Instanz wieder – das einmalige Erstellen spart pro Durchlauf ein paar Millisekunden.

## Schritt 3: Durch `WarningInfo` iterieren und Font‑Substitutionsmeldungen anzeigen

Nachdem das Dokument geladen ist, enthält die `WarningInfo`‑Sammlung jede während des Ladevorgangs aufgetretene Warnung. Wir interessieren uns nur für `WarningType.FontSubstitution` und filtern dementsprechend.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Das Ausführen des obigen Snippets mit einem Dokument, das die fehlende Schriftart „Papyrus“ referenziert, könnte eine Ausgabe wie folgt erzeugen:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Das sind die **Font‑Substitutionsmeldungen**, nach denen Sie gesucht haben – klar, umsetzbar und bereit, protokolliert oder an ein Alarmsystem gesendet zu werden.

## Vollständiges funktionierendes Beispiel

Unten finden Sie ein eigenständiges Konsolenprogramm, das alles zusammenführt. Kopieren Sie es in ein neues `.csproj` und klicken Sie auf **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Erwartete Ausgabe

Wenn das Dokument Schriftarten referenziert, die nicht installiert sind, sehen Sie etwas Ähnliches wie:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Wenn alle Schriftarten auf dem Rechner vorhanden sind, gibt das Programm einfach aus:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Häufige Fallstricke & Pro‑Tipps

| Problem | Warum es passiert | Wie zu beheben / vermeiden |
|---------|-------------------|----------------------------|
| **Warnungen verschwinden** | Sie haben `FontSettings` gelöscht oder ein `LoadOptions` ohne diese verwendet. | Instanziieren Sie immer `FontSettings`, selbst wenn Sie keine Eigenschaften ändern. |
| **Zu viele Warnungen** | Das Dokument verwendet viele exotische Schriftarten. | Erwägen Sie, einen benutzerdefinierten Schriftordner zu `FontSettings` über `SetFontsFolder` hinzuzufügen, um Substitutionen zu reduzieren. |
| **Leistungsverlust in einer engen Schleife** | Das erneute Erstellen von `LoadOptions` in jeder Iteration verursacht Overhead. | Verwenden Sie eine einzelne `LoadOptions`‑Instanz für alle Dokumente wieder. |
| **Fehlende Konsolenausgabe** | Ausführung in einer GUI‑App, in der `Console.WriteLine` ignoriert wird. | Leiten Sie Warnungen an einen Logger (`ILogger`) weiter oder schreiben Sie sie in eine Datei. |

### Umgang mit Warnungen in einem realen Service

In einer Web‑API möchten Sie wahrscheinlich nicht in die Konsole schreiben. Stattdessen leiten Sie die Warnungen in ein strukturiertes Log weiter:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Auf diese Weise behalten Sie die **Dokumentwarnungsbehandlung** bei und halten Ihren Service sauber.

## Erweiterung des Beispiels

- **Andere Warnungstypen erfassen** (z. B. `WarningType.UnknownFileFormat`) indem Sie den `if`‑Filter entfernen.
- **Einen Bericht** aller Warnungen als JSON für nachgelagerte Analysen speichern.
- **Eine bestimmte Ersatzschriftart erzwingen** durch Setzen von `FontSettings.SubstitutionSettings.DefaultFontName`.

All dies sind natürliche Erweiterungen, sobald Sie **Font‑Substitutionswarnungen aktivieren** beherrschen.

## Fazit

Wir haben Ihnen gezeigt, wie Sie **Font‑Substitutionswarnungen** in C# mit Aspose.Words aktivieren, von der Konfiguration von `LoadOptions` über das Durchlaufen von `WarningInfo` bis hin zum Ausgeben freundlicher Meldungen. Wenn Sie die obigen Schritte befolgen, können Sie Ihre Dokumentverarbeitungspipelines vor stillen Layoutänderungen durch fehlende Schriftarten schützen.

Als Nächstes können Sie einen benutzerdefinierten Schriftordner hinzufügen, die Warnungen in eine Datei protokollieren oder sogar an ein Monitoring‑Dashboard senden. Das gleiche Muster funktioniert für jedes **Dokumentwarnungs‑Handling**‑Szenario, egal ob Sie zu PDF konvertieren, Bilder rendern oder einen Seriendruck durchführen.

Haben Sie Fragen zu **C#‑Font‑Substitutionswarnungen** oder möchten Sie einen cleveren Workaround teilen? Hinterlassen Sie unten einen Kommentar – happy coding!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren Projekten zu erkunden.

- [Font‑Substitutionswarnungen in Aspose.Words aktivieren – Komplett‑Leitfaden](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Wie man Schriftarten in Aspose.Words erkennt – Warnungen & Einstellungen behandeln](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Font‑Substitutionswarnungen in Java mit Aspose.Words erfassen – Komplett‑Leitfaden](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}