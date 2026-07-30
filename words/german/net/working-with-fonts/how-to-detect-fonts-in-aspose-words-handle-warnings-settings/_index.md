---
category: general
date: 2026-01-03
description: Wie man Schriftarten in Aspose.Words erkennt und Warnungen mit den Aspose‑Schrifteinstellungen
  verarbeitet – eine Schritt‑für‑Schritt‑Anleitung für Entwickler.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: de
og_description: Wie man Schriftarten in Aspose.Words erkennt und Warnungen mit den
  Aspose‑Schrifteinstellungen konfiguriert. Lernen Sie den kompletten Workflow in
  wenigen Minuten.
og_title: Wie man Schriftarten in Aspose.Words erkennt – Warnungen behandeln
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man Schriftarten in Aspose.Words erkennt – Warnungen & Einstellungen
url: /de/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Schriftarten in Aspose.Words erkennt – Warnungen & Einstellungen handhabt

Haben Sie sich jemals gefragt, **wie man Schriftarten** in einem Word‑Dokument erkennt, bevor es in die Produktion geht? Sie sind nicht der Einzige. Fehlende Schriftarten können Layout‑Albträume verursachen, und ohne entsprechende Warnungen könnten Sie ein fehlerhaftes PDF oder DOCX ausliefern, ohne es zu merken.  

In diesem Tutorial zeigen wir Ihnen **wie man Schriftarten** mit Aspose.Words erkennt, **wie man Warnungen** behandelt und **Aspose Font Settings** anpasst, sodass Sie **Warnungen** genau nach Ihren Bedürfnissen konfigurieren können. Am Ende haben Sie ein sofort ausführbares Snippet, das jede von Aspose vorgenommene Substitution ausgibt, und Sie wissen, wie Sie es für Ihre eigenen Projekte anpassen.

## Voraussetzungen

- .NET 6+ (oder .NET Framework 4.6+).  
- Aspose.Words für .NET über NuGet installiert (`Install-Package Aspose.Words`).  
- Eine Word‑Datei, die bewusst eine fehlende Schriftart referenziert (z. B. *DocumentWithMissingFonts.docx*).  

Wenn Sie das bereits haben, großartig — lassen Sie uns loslegen.

![Screenshot zur Schriftartenerkennung](https://example.com/detect-fonts.png "Beispielausgabe zur Schriftartenerkennung")

## Wie man Schriftarten mit Aspose.Words erkennt

Der erste Schritt besteht darin, Aspose.Words mitzuteilen, dass Sie an Font‑Substitution‑Ereignissen interessiert sind. Dies geschieht, indem Sie über **Aspose Font Settings** einen benutzerdefinierten Warnungs‑Callback bereitstellen. Der Callback erhält für jede Substitution ein `WarningInfo`‑Objekt, sodass Sie **Schriftarten** zur Laufzeit **erkennen** können.

### Schritt 1: Eine Warnungs‑Callback‑Klasse erstellen

Implementieren Sie das Interface `IWarningCallback`. Im `Warning`‑Methodenkörper filtern Sie nach `WarningType.FontSubstitution` und protokollieren die Details.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Pro‑Tipp:** Der String `info.Description` enthält sowohl den Namen der fehlenden Schriftart als auch die von Aspose gewählte Ersatzschriftart. Sie können ihn parsen, wenn Sie einen strukturierten Bericht benötigen.

### Schritt 2: LoadOptions mit Aspose Font Settings konfigurieren

Erzeugen Sie eine Instanz von `LoadOptions`, hängen Sie ein frisches `FontSettings`‑Objekt an und setzen Sie `WarningCallback` auf den Handler, den wir gerade gebaut haben. Damit teilen Sie Aspose mit, **wie Warnungen konfiguriert** werden sollen.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Wenn Sie einen privaten Schriftarten‑Ordner haben, können Sie ihn wie folgt hinzufügen:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Diese Zeile zeigt einen weiteren Aspekt der **Aspose Font Settings** — Sie bestimmen exakt, wo Aspose nach Schriftarten sucht, bevor es zu einer Substitution kommt.

### Schritt 3: Das Dokument laden und den Callback auslösen

Laden Sie nun das Ziel‑Dokument mit den `loadOptions`. Während Aspose die Datei parst, löst jede fehlende Schriftart den Warnungs‑Handler aus und **erkennt Schriftarten** on‑the‑fly.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Wenn Sie das Programm ausführen, sehen Sie eine Ausgabe ähnlich der folgenden:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Schritt 4: (Optional) Warnungen für spätere Verwendung sammeln

Falls Sie die Substitutions‑Daten für einen Bericht speichern müssen, passen Sie den Handler an, sodass er Nachrichten in einer Liste sammelt.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Später können Sie `handler.Substitutions` in eine JSON‑Datei schreiben, an einen Logging‑Service senden oder in einer UI anzeigen.

### Schritt 5: Das Ergebnis programmgesteuert überprüfen

Manchmal möchten Sie sicherstellen, dass *keine* Substitution stattgefunden hat (z. B. in einem CI‑Build). Hier ein kurzer Check:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Dieses Snippet demonstriert **wie man Warnungen** deterministisch behandelt und Ihnen die volle Kontrolle über die Build‑Pipeline gibt.

## Häufig gestellte Fragen (und Randfälle)

**Was ist, wenn ich bestimmte Substitutionen ignorieren muss?**  
Sie können innerhalb von `Warning` eine Bedingung einbauen und einfach zurückkehren, ohne zu protokollieren, für Schriftarten, die Sie als akzeptabel ansehen.

**Kann ich alle Warnungen unterdrücken und nur ein boolesches Ergebnis erhalten?**  
Ja — setzen Sie `loadOptions.WarningCallback = null` und prüfen Sie anschließend `doc.FontInfo` nach dem Laden (Sie verlieren dabei jedoch das detaillierte Log).

**Funktioniert das auch bei der PDF‑Konvertierung?**  
Absolut. Der gleiche Warnungs‑Mechanismus wird ausgelöst, wenn Sie `doc.Save("out.pdf")` aufrufen. Der Callback erfasst dann alle während der Konvertierung vorgenommenen Schriftart‑Austausche.

**Gibt es einen Performance‑Einbruch?**  
Der Overhead ist minimal — nur ein paar zusätzliche Methodenaufrufe pro fehlender Schriftart. Bei großen Stapeln möchten Sie die Ergebnisse eventuell cachen.

## Zusammenfassung: Was wir behandelt haben

- **Wie man Schriftarten** erkennt, indem man ein benutzerdefiniertes `IWarningCallback` implementiert.  
- **Wie man Warnungen** über `LoadOptions.WarningCallback` behandelt.  
- Feinabstimmung der **Aspose Font Settings** (Hinzufügen benutzerdefinierter Schriftarten‑Ordner, Aktivieren/Deaktivieren von Warnungen).  
- **Wie man Warnungen** sowohl für sofortige Konsolenausgabe als auch für spätere Analysen konfiguriert.  

Mit diesen Bausteinen können Sie Word‑Dokumente sicher verarbeiten, garantieren, dass fehlende Schriftarten gemeldet werden, und Ihre Ausgabe über verschiedene Umgebungen hinweg konsistent halten.

## Nächste Schritte

- Erkunden Sie `FontSettings.SubstitutionSettings` für eine granularere Kontrolle (z. B. Zuordnung bestimmter fehlender Schriftarten zu ausgewählten Ersatzschriften).  
- Kombinieren Sie diesen Ansatz mit Aspose.PDF, um PDFs zu erzeugen, die die exakte Typografie beibehalten.  
- Automatisieren Sie die Warnungs‑Prüfung in einer CI/CD‑Pipeline, um Releases zu blockieren, die Schriftart‑Probleme enthalten — perfekt für Teams, die **Warnungen** als Teil von Qualitäts‑Gates behandeln.

Haben Sie weitere Fragen zu **Aspose Font Settings** oder benötigen Hilfe bei der Integration in einen größeren Service? Hinterlassen Sie einen Kommentar unten, und happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}