---
language: de
url: /german/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Fehlende Schriftarten in Aspose.Words-Dokumenten erkennen – Vollständige C#‑Anleitung

Haben Sie sich jemals gefragt, wie Sie **fehlende Schriftarten** erkennen können, wenn Sie eine Word‑Datei mit Aspose.Words laden? In meiner täglichen Arbeit bin ich auf ein paar PDFs gestoßen, die nicht richtig aussahen, weil das Originaldokument eine Schriftart verwendete, die ich nicht installiert hatte. Die gute Nachricht? Aspose.Words kann Ihnen genau mitteilen, wann es eine Schriftart ersetzt, und Sie können diese Information mit einem einfachen Warning‑Callback erfassen.  

In diesem Tutorial führen wir Sie durch ein **vollständiges, ausführbares Beispiel**, das zeigt, wie Sie jede Schriftart‑Ersetzung protokollieren, warum der Callback wichtig ist und ein paar zusätzliche Tricks für eine robuste Erkennung fehlender Schriftarten. Kein Schnickschnack, nur der Code und die Überlegungen, die Sie benötigen, um es noch heute zum Laufen zu bringen.

---

## Was Sie lernen werden

- Wie man **Aspose.Words warning callback** implementiert, um Schriftart‑Ersetzungs‑Ereignisse abzufangen.  
- Wie man **LoadOptions C#** konfiguriert, damit der Callback beim Laden eines Dokuments aufgerufen wird.  
- Wie man überprüft, dass die Erkennung fehlender Schriftarten wirklich funktioniert hat, und wie die Konsolenausgabe aussieht.  
- Optionale Anpassungen für große Stapelverarbeitungen oder headless Umgebungen.  

**Voraussetzungen** – Sie benötigen eine aktuelle Version von Aspose.Words für .NET (der Code wurde mit 23.12 getestet), .NET 6 oder höher und ein grundlegendes Verständnis von C#. Wenn Sie das haben, können Sie loslegen.

## Fehlende Schriftarten mit einem Warning‑Callback erkennen

Das Herzstück der Lösung ist eine Implementierung von `IWarningCallback`. Aspose.Words löst ein `WarningInfo`‑Objekt für viele Situationen aus, aber wir interessieren uns nur für `WarningType.FontSubstitution`. Sehen wir uns an, wie man sich daran anhängt.

### Schritt 1: Einen Font‑Warning‑Collector erstellen

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Warum das wichtig ist*: Durch das Filtern nach `WarningType.FontSubstitution` vermeiden wir Unordnung durch nicht verwandte Warnungen (wie veraltete Features). `info.Description` enthält bereits den ursprünglichen Schriftartnamen und die verwendete Ersatzschrift, was Ihnen eine klare Prüfspur liefert.

## LoadOptions konfigurieren, um den Callback zu verwenden

Jetzt teilen wir Aspose.Words mit, dass es unseren Collector beim Laden einer Datei verwenden soll.

### Schritt 2: LoadOptions einrichten

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Warum das wichtig ist*: `LoadOptions` ist der einzige Ort, an dem Sie den Callback, Verschlüsselungspasswörter und andere Ladeverhalten einbinden können. Wenn Sie es vom `Document`‑Konstruktor getrennt halten, wird der Code für viele Dateien wiederverwendbar.

## Das Dokument laden und fehlende Schriftarten erfassen

Mit dem angeschlossenen Callback besteht der nächste Schritt einfach darin, das Dokument zu laden.

### Schritt 3: Laden Sie Ihr DOCX (oder ein beliebiges unterstütztes Format)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Wenn der `Document`‑Konstruktor die Datei analysiert, löst jede fehlende Schriftart unseren `FontWarningCollector` aus. Die Konsole zeigt Zeilen wie:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Diese Zeile ist der konkrete Beweis, dass **fehlende Schriftarten erkennen** funktioniert hat.

## Die Ausgabe überprüfen – Was zu erwarten ist

Führen Sie das Programm in einem Terminal oder Visual Studio aus. Wenn das Quell‑Dokument eine Schriftart enthält, die Sie nicht installiert haben, sehen Sie mindestens eine Zeile „Font substituted“. Wenn das Dokument nur installierte Schriftarten verwendet, bleibt der Callback still und Sie erhalten nur die Meldung „Document loaded successfully.“.

**Tipp**: Öffnen Sie die Word‑Datei in Microsoft Word und schauen Sie sich die Schriftartenliste an. Jede Schriftart, die unter *Replace Fonts* in der Gruppe *Home → Font* erscheint, ist ein Kandidat für eine Ersetzung.

## Fortgeschritten: Fehlende Schriftarten in großen Mengen erkennen

Oft müssen Sie Dutzende von Dateien scannen. Das gleiche Muster skaliert gut:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Da der `FontWarningCollector` jedes Mal, wenn er aufgerufen wird, in die Konsole schreibt, erhalten Sie einen Bericht pro Datei ohne zusätzlichen Aufwand. Für Produktionsszenarien möchten Sie vielleicht in eine Datei oder Datenbank protokollieren – ersetzen Sie einfach `Console.WriteLine` durch Ihren bevorzugten Logger.

## Häufige Fallstricke & Profi‑Tipps

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Keine Warnungen erscheinen** | Das Dokument enthält tatsächlich nur installierte Schriftarten. | Überprüfen Sie dies, indem Sie die Datei in Word öffnen oder bewusst eine Schriftart von Ihrem System entfernen. |
| **Callback wird nicht aufgerufen** | `LoadOptions.WarningCallback` wurde nie zugewiesen oder später wurde eine neue `LoadOptions`‑Instanz verwendet. | Behalten Sie ein einzelnes `LoadOptions`‑Objekt und verwenden Sie es für jedes Laden wieder. |
| **Zu viele nicht verwandte Warnungen** | Sie haben nicht nach `WarningType.FontSubstitution` gefiltert. | Fügen Sie die `if (info.Type == WarningType.FontSubstitution)`‑Abfrage wie gezeigt hinzu. |
| **Leistungsabfall bei riesigen Dateien** | Der Callback wird bei jeder Warnung ausgeführt, was bei großen Dokumenten sehr häufig sein kann. | Deaktivieren Sie andere Warnungstypen über `LoadOptions.WarningCallback` oder setzen Sie `LoadOptions.LoadFormat` auf einen bestimmten Typ, wenn Sie diesen kennen. |

## Voll funktionsfähiges Beispiel (Copy‑Paste‑bereit)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Erwartete Konsolenausgabe** (wenn eine fehlende Schriftart gefunden wird):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Wenn keine Ersetzung erfolgt, sehen Sie nur die Erfolgszeile.

## Fazit

Sie haben jetzt eine **vollständige, produktionsreife Methode, um fehlende Schriftarten** in jedem von Aspose.Words verarbeiteten Dokument zu erkennen. Durch die Nutzung des **Aspose.Words warning callback** und die Konfiguration von **LoadOptions C#** können Sie jede Schriftart‑Ersetzung protokollieren, Layout‑Probleme beheben und sicherstellen, dass Ihre PDFs das beabsichtigte Aussehen behalten.  

Ob einzelne Datei oder riesiger Stapel, das Muster bleibt gleich – implementieren Sie `IWarningCallback`, binden Sie ihn in `LoadOptions` ein und lassen Sie Aspose.Words die schwere Arbeit erledigen.  

Bereit für den nächsten Schritt? Versuchen Sie, dies mit **font embedding** oder **fallback font families** zu kombinieren, um das Problem automatisch zu beheben, oder erkunden Sie die **DocumentVisitor**‑API für eine tiefere Inhaltsanalyse. Viel Spaß beim Coden, und möge jede Ihrer Schriftarten dort bleiben, wo Sie sie erwarten!

---

![Fehlende Schriftarten in Aspose.Words – Konsolenausgabe Screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}