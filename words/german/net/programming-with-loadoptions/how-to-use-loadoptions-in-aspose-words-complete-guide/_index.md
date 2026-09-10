---
category: general
date: 2026-01-10
description: Erfahren Sie, wie Sie LoadOptions verwenden, um fehlende Schriftarten
  in Aspose.Words zu handhaben. Schritt‑für‑Schritt‑Code, Tipps und bewährte Methoden
  für ein robustes Laden von Dokumenten.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: de
og_description: Wie man LoadOptions verwendet, um fehlende Schriftarten in Aspose.Words
  zu behandeln. Erhalten Sie ein vollständiges, ausführbares Beispiel mit Erklärungen
  und praktischen Tipps.
og_title: Wie man LoadOptions in Aspose.Words verwendet – Vollständiger Leitfaden
tags:
- Aspose.Words
- C#
- .NET
title: Wie man LoadOptions in Aspose.Words verwendet – Komplettanleitung
url: /de/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man LoadOptions in Aspose.Words verwendet – Komplettanleitung

Haben Sie sich jemals gefragt **wie man LoadOptions** verwendet, wenn man ein Word‑Dokument lädt, dem möglicherweise einige Schriftarten fehlen? Sie sind nicht der Einzige, der sich darüber den Kopf zerbricht. In vielen realen Projekten reisen Dokumente zwischen Rechnern, und das Zielsystem hat oft nicht die genauen Schriftarten, die der Autor verwendet hat. Das Ergebnis? Unerwartete Schriftart‑Ersetzungen, die das Layout zerstören, wichtige Zeichen verbergen oder einfach unpassend aussehen.  

Glücklicherweise bietet Aspose.Words eine saubere Methode, um *fehlende Schriftarten zu behandeln*, indem es ein `LoadOptions`‑Objekt mit einem Warn‑Callback bereitstellt. In diesem Tutorial lernen Sie genau **wie man LoadOptions** verwendet, um diese Schriftart‑Ersetzungs‑Warnungen zu erfassen, zu protokollieren und Ihre Verarbeitungspipeline robust zu halten.

Wir behandeln:

* Einrichten der Warn‑Callback‑Klasse  
* Konfigurieren von `LoadOptions` mit diesem Callback  
* Laden eines Dokuments unter Verfolgung fehlender Schriftarten  
* Tipps zur Fehlersuche und Erweiterung der Lösung  

Keine externe Dokumentation nötig – alles, was Sie brauchen, finden Sie hier.

## Was Sie benötigen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* **Aspose.Words for .NET** (neueste Version ab 2026) über NuGet installiert  
* Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code)  
* Ein Beispiel‑DOCX, das eine Schriftart referenziert, die nicht installiert ist (wir nennen es `input.docx`)  

Das war’s – keine zusätzlichen Bibliotheken erforderlich.

## Schritt 1 – Definieren Sie einen Warn‑Callback zum Erfassen von Schriftart‑Ersetzungen

Das erste Puzzleteil ist eine Klasse, die `IWarningCallback` implementiert. Aspose.Words ruft deren `Warning`‑Methode auf, sobald etwas Bemerkenswertes auftritt – zum Beispiel eine fehlende Schriftart.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Warum das wichtig ist:**  
Durch das Filtern nach `WarningType.FontSubstitution` vermeiden wir Unordnung durch nicht relevante Warnungen (z. B. veraltete Features). Der Callback gibt Ihnen die volle Kontrolle – Sie können in eine Datei protokollieren, eine Ausnahme auslösen oder sogar programmatisch versuchen, eine Ersatzschriftart einzubetten.

## Schritt 2 – Konfigurieren Sie LoadOptions mit dem Callback

Jetzt, wo wir einen Handler haben, müssen wir Aspose.Words mitteilen, ihn zu verwenden. Hier kommt **wie man LoadOptions** in der Praxis zum Einsatz.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Tipp:** `LoadOptions` bietet viele weitere Optionen (z. B. `Password`, `LoadFormat`, `Encoding`). Sie können sie verketten, aber für die Behandlung fehlender Schriftarten ist `WarningCallback` das Highlight.

## Schritt 3 – Laden Sie das Dokument mit den konfigurierten Optionen

Mit den vorbereiteten `LoadOptions` ist das Laden des Dokuments einfach. Aspose.Words ruft automatisch den Callback für jede Schriftart auf, die es nicht finden kann.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Erwartete Ausgabe:**  

Wenn `input.docx` eine Schriftart namens *„GothicBold“* verwendet, die nicht installiert ist, sehen Sie etwa Folgendes:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Die Warnzeile erscheint **genau dann, wenn die fehlende Schriftart gefunden wird**, und gibt Ihnen sofortiges Feedback.

## Schritt 4 – (Optional) Weiterverarbeitung des Dokuments

Normalerweise möchten Sie mehr tun, als nur die Datei zu laden. Im Folgenden finden Sie einige gängige Aktionen nach dem Laden, die nahtlos mit unserer Warn‑Einrichtung funktionieren.

### 4.1 Dokument als PDF speichern

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Fehlende Schriftarten durch bekannte Ersatzschriftart ersetzen

Wenn Sie eine bestimmte Ersatzschriftart bevorzugen (z. B. *„Calibri“*), können Sie die `FontSettings` vor dem Speichern anpassen:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Alle Warnungen in eine Datei protokollieren

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Diese Snippets zeigen **wie man LoadOptions** über den Basisfall hinaus verwendet und geben Ihnen Flexibilität für produktionsreife Lösungen.

## Häufige Fallstricke & Wie man **fehlende Schriftarten** elegant behandelt

| Problem | Warum es passiert | Wie man es behebt / mindert |
|---------|-------------------|-----------------------------|
| **Kein Callback angehängt** | Sie vergessen, `WarningCallback` zu setzen. | Erstellen Sie immer eine `LoadOptions`‑Instanz und weisen Sie Ihren Handler vor dem Laden zu. |
| **Callback gibt nur aus, speichert nie** | In einem Web‑Service verschwindet die Konsolenausgabe. | `Console.WriteLine` durch einen Logger (Serilog, NLog) ersetzen oder in einen persistenten Speicher schreiben. |
| **Mehrere fehlende Schriftarten, nur die erste gemeldet** | Ihr Callback wirft bei der ersten Warnung eine Ausnahme. | Halten Sie den Callback leichtgewichtig; vermeiden Sie das Werfen von Ausnahmen, es sei denn, Sie möchten wirklich abbrechen. |
| **Ersetzte Schriftart sieht falsch aus** | Die Standard‑Ersetzung kann eine visuell unähnliche Schriftart wählen. | Verwenden Sie `FontSettings.SubstitutionSettings.FontSubstitutionRules`, um Ihre bevorzugte Ersatzschriftart zu priorisieren. |
| **Leistungseinbußen bei riesigen Dokumenten** | Der Warn‑Callback wird tausende Male aufgerufen. | Warnungen stapeln: Sammeln Sie sie in einer Liste und verarbeiten Sie sie nach dem Laden, oder filtern Sie nur eindeutige Schriftartnamen. |

Das Bewusstsein für diese Szenarien hilft Ihnen, **fehlende Schriftarten** ohne Überraschungen zu behandeln.

## Vollständiges funktionierendes Beispiel – Alle Teile zusammen

Unten finden Sie das komplette, sofort ausführbare Programm, das den gesamten Ablauf demonstriert. Kopieren Sie es in ein Konsolenprojekt, fügen Sie das Aspose.Words‑NuGet‑Paket hinzu, und es funktioniert sofort.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Wenn Sie dieses Programm ausführen**, wird:

1. Alle Schriftart‑Ersetzungs‑Warnungen in die Konsole ausgeben.  
2. Das ursprüngliche Layout als `output.pdf` speichern.  
3. Ein zweites PDF (`output-with-fallback.pdf`) speichern, das die Ersatzschriftart auf *Calibri* oder *Arial* zwingt.

## Häufig gestellte Fragen (FAQs)

**F: Funktioniert das für DOC-, RTF- oder HTML‑Dateien?**  
A: Ja. `LoadOptions` ist formatunabhängig; solange Sie den korrekten Dateipfad übergeben, wird der Warn‑Callback für fehlende Schriftarten in allen unterstützten Formaten ausgelöst.

**F: Kann ich die Warnungen vollständig unterdrücken?**  
A: Sie könnten einen No‑Op‑Callback zuweisen (`new IWarningCallback { Warning = _ => {} }`) oder `LoadOptions.WarningCallback = null` setzen. Allerdings verlieren Sie damit die Sichtbarkeit und könnten kritische Schriftart‑Probleme übersehen.

**F: Was ist, wenn ich fehlende Schriftarten durch eingebettete ersetzen muss?**  
A: Verwenden Sie `FontSettings`, um eine Ersatz‑Schriftartdatei einzubetten (`AddFontSource`). Kombinieren Sie das mit den Ersetzungsregeln für ein nahtloses Erlebnis.

**F: Ist der Callback thread‑sicher?**  
A: Der Callback kann bei parallelem Laden großer Dokumente aus mehreren Threads aufgerufen werden. Stellen Sie sicher, dass gemeinsam genutzte Ressourcen (z. B. Log‑Dateien) synchronisiert sind.

## Fazit

Wir haben gezeigt, **wie man LoadOptions** in Aspose.Words verwendet, um **fehlende Schriftarten** elegant zu **behandeln**. Durch das Definieren eines benutzerdefinierten `IWarningCallback`, das Anbinden an eine `LoadOptions`‑Instanz und das Laden Ihres Dokuments mit dieser Konfiguration erhalten Sie Echtzeit‑Einblicke in alle Schriftart‑Ersetzungs‑Ereignisse. Anschließend können Sie die Warnungen protokollieren, Ersatzschriftarten ersetzen oder einbetten, um sicherzustellen, dass Ihre Ausgabe exakt wie beabsichtigt aussieht.

Denken Sie daran, die wichtigsten Schritte sind:

1. Implementieren Sie einen Warn‑Callback, der sich auf `WarningType.FontSubstitution` konzentriert.  
2. Binden Sie den Callback in ein `LoadOptions`‑Objekt ein.  
3. Laden Sie Ihr Dokument mit diesen Optionen.  
4. (Optional) Wenden Sie weitere Schriftart‑Ersetzungs‑Regeln oder Protokollierung nach Bedarf an.

Fühlen Sie sich frei zu experimentieren – ersetzen Sie den Konsolen‑Logger durch einen strukturierten Logger, fügen Sie E‑Mail‑Benachrichtigungen für kritische fehlende Schriftarten hinzu oder integrieren Sie dieses Muster in eine größere Dokumentverarbeitungspipeline. Der Ansatz skaliert gut, egal ob Sie eine einzelne Datei verarbeiten oder tausende in einem Batch‑Job.

Viel Spaß beim Coden, und möge Ihre Dokumente stets mit den richtigen Schriftarten dargestellt werden!  

![Beispiel zur Verwendung von LoadOptions]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}