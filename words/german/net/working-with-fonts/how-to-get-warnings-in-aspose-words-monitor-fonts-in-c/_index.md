---
category: general
date: 2026-01-06
description: Erfahren Sie, wie Sie beim Laden von Dokumenten Warnungen erhalten und
  wie Sie Schriftarten mit Aspose.Words überwachen können. Dieser Leitfaden behandelt
  Warnungs‑Callbacks und die Verfolgung von Schriftart‑Substitutionen.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: de
og_description: Wie erhält man Warnungen in Aspose.Words? Folgen Sie diesem Schritt‑für‑Schritt‑Tutorial,
  um Schriftarten zu überwachen und Ersetzungsnachrichten beim Laden von Dokumenten
  zu erfassen.
og_title: Wie man Warnungen in Aspose.Words erhält – Schriftarten überwachen
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Wie man Warnungen in Aspose.Words erhält – Schriftarten in C# überwachen
url: /de/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen in Aspose.Words erhält – Schriftarten in C# überwachen

Haben Sie sich jemals gefragt, **wie man Warnungen** erhält, wenn ein Word-Dokument Schriftarten enthält, die Sie nicht installiert haben? Das ist ein häufiges Problem – Ihre Anwendung tauscht fehlende Schriftarten stillschweigend aus, und Sie wissen nie, was sich geändert hat. Die gute Nachricht ist, dass Sie sich in das Warnsystem von Aspose.Words einklinken und **Schriftarten** in Echtzeit **überwachen** können.

> **Pro Tipp:** Wenn Sie eine Dokumentkonvertierungspipeline erstellen, spart das frühzeitige Protokollieren fehlender Schriftarten Ihnen später unangenehme Layout‑Überraschungen.

---

## Was Sie benötigen

- **Aspose.Words for .NET** (neueste Version; die API hat sich seit v23.10 nicht geändert)
- Eine .NET-Entwicklungsumgebung (Visual Studio, Rider oder VS Code mit der C#‑Erweiterung)
- Eine Beispiel‑docx`, die eine Schriftart referenziert, die Sie nicht installiert haben (z. B. **„NonExistentFont“**)

Das war’s – keine zusätzlichen NuGet‑Pakete außer Aspose.Words.

---

## Schritt 1 – Einen Warnungs‑Collector einrichten (Primäres Schlüsselwort in der Überschrift)

Das Erste, was Sie benötigen, ist ein Ort, um Warnungen zu speichern, sobald sie auftreten. Aspose.Words stellt die `WarningCallback`‑Eigenschaft auf `LoadOptions` genau für diesen Zweck bereit.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Warum das wichtig ist:**  
Wenn die Bibliothek auf eine fehlende Schriftart stößt, wirft sie keine Ausnahme; sie erzeugt ein `WarningInfo`‑Objekt. Durch das Anschließen eines Collectors erhalten Sie vollständige Sicht auf jedes Substitutions‑Ereignis, sodass Sie **Schriftarten überwachen können, ohne Ihre Konsole mit irrelevanten Meldungen zu verschmutzen.

---

## Schritt 2 – Das Dokument mit den aktivierten Warnungs‑Optionen laden

Jetzt lesen wir tatsächlich die Datei. Die `LoadOptions`, die wir im vorherigen Schritt vorbereitet haben, stellen sicher, dass alle schriftbezogenen Warnungen erfasst werden.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Was im Hintergrund passiert:**  
Aspose.Words analysiert die Word‑Datei, löst Schriftarten auf und wann immer es eine angeforderte Schriftart nicht finden kann, greift es auf eine Ersatzschriftart zurück (in der Regel Arial). Der Rückgriff löst eine `WarningType.FontSubstitution`‑Warnung aus, die in `warningCollector` landet.

---

## Schritt 3 – Die gesammelten Warnungen prüfen (Primäres Schlüsselwort erscheint erneut)

Nachdem das Dokument geladen ist, iterieren wir überwarningCollector` und geben alle Schriftart‑Substitutions‑Meldungen aus.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Erwartete Ausgabe** (angenommen, die fehlende Schriftart ist *„FancyScript“*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Wenn das Dokument mehrere unbekannte Schriftarten enthält, sehen Sie eine Zeile pro Sub ideal zum Protokollieren oder Benachrichtigen.

---

## Schritt 4 – Optional: Die Warnungsinformationen protokollieren oder speichern

In der Produktion möchten Sie wahrscheinlich mehr als ein `Console.WriteLine`. Hier ein kurzes Beispiel, das die Warnungen in eine JSON‑Datei schreibt, um sie später zu analysieren.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Jetzt haben Sie ein dauerhaftes Protokoll, das Sie in ein Monitoring‑Dashboard einspeisen oder sogar eine automatisierte Anforderung für die fehlenden Schriftdateien auslösen können.

---

## Schritt 5 – Ergebnis überprüfen und aufräumen

Führen Sie das Programm aus. Wenn Sie die Substitutionsmeldungen sehen, haben Sie erfolgreich **Warnungen erhalten** und überwachen jetzt aktiv **Schriftarten**. Wenn nichts erscheint, prüfen Sie erneut, ob das Testdokument tatsächlich eine Schriftart referenziert, die nicht auf dem Rechner installiert ist.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Eine Null‑Anzahl bedeutet normalerweise entweder:

1. Alle Schriftarten wurden aufgelöst (vielleicht ist die Schriftart *lokal* installiert), oder
2. Das Dokument enthielt keine Schriftart‑Referenzen, die eine Substitution erforderten.

---

## Häufige Fallstricke & wie man sie vermeidet

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **Keine Warnungen erscheinen** | Die Schriftart ist tatsächlich auf dem System vorhanden, oder das Dokument verwendet nur eingebaute Schriftarten. | Benennen Sie die Schriftart in der Quelldatei in etwas Unmögliches um (z. B. `XYZ123`) und versuchen Sie es erneut. |
| **Zu viele Warnungen (Rauschen)** | Sie laden viele Dokumente in einer Schleife, ohne den Collector zu leeren. | Instanziieren Sie `WarningInfoCollection` für jedes Dokument neu oder rufen Sie nach der Verarbeitung `warningCollector.Clear()` auf. |
| **Performance‑Auswirkungen** | Exzessives Schreiben auf die Festplatte kann die Batch‑Verarbeitung verlangsamen. | Puffern Sie Warnungen im Speicher und schreiben Sie sie gesammelt, oder verwenden Sie asynchrones Datei‑I/O. |
| **Fehlendes `using Aspose.Words.Loading;`** | Die Klasse `LoadOptions` befindet sich in diesem Namensraum. | Fügen Sie die fehlende `using`‑Direktive hinzu, wie in Schritt 1 gezeigt. |

---

## Erweiterung der Lösung – Überwachung anderer Warnungsarten

Obwohl die Schriftart‑Substitution die sichtbarste ist, kann Aspose.Words Warnungen ausgeben für:

- **Veraltete Funktionen** (`WarningType.Deprecated`),
- **Möglichen Datenverlust** (`WarningType.DataLoss`),
- **Nicht unterstützte Dateiformate** (`WarningType.UnsupportedFileFormat`).

Sie können den Filter in Schritt 3 erweitern, um diese ebenfalls zu erfassen:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Auf diese Weise geht es nicht nur darum, **wie man Schriftarten überwacht**, sondern auch **wie man Warnungen erhält** für jedes Szenario, dem Ihre Anwendung begegnen könnte.

---

## Vollständiges funktionierendes Beispiel (Copy‑Paste‑bereit)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Ausführen:** Bauen Sie das Projekt, führen Sie es aus, und Sie sehen die Warnungen ausgegeben und gespeichert. Das ist die vollständige Antwort auf **wie man Warnungen erhält** und **wie man Schriftarten überwacht** mit Aspose.Words.

---

## Fazit

Sie wissen jetzt, **wie man Warnungen** von Aspose.Words erhält, speziell für Schriftart‑Substitutions‑Szenarien, und Sie haben gelernt, **wie man Schriftarten** während des Dokument‑Ladevorgangs überwacht. Durch das Anhängen eines `WarningCallback`, das Durchlaufen der gesammelten `WarningInfo`‑Objekte und das optionale Persistieren der Daten erhalten Sie vollständige Transparenz über fehlende Schriftart‑Ereignisse – eine wesentliche Fähigkeit für jede Dokument‑Verarbeitungspipeline.

Nächste Schritte? Versuchen Sie, den Warnungsfilter zu erweitern, um Datenverlust‑ oder veraltete‑Funktion‑Warnungen abzudecken, oder integrieren Sie das JSON‑Log in ein Monitoring‑Dashboard wie Grafana. Das gleiche Muster funktioniert für alle Warnungsarten, sodass Sie gut gerüstet sind, jedes Problem im Blick zu behalten, das Aspose.Words Ihnen liefert.

Viel Spaß beim Coden, und möge Ihr Dokument stets genau so gerendert werden, wie Sie es erwarten!

---

<img src="font-warnings.png" alt="wie man Warnungen in Aspose.Words erhält" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}