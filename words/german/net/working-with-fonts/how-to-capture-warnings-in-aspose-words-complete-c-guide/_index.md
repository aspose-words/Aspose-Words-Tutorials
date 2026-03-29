---
category: general
date: 2026-03-28
description: Wie man Warnungen beim Laden einer DOCX‑Datei mit Aspose.Words erfasst
  und Warnmeldungen für fehlende Schriftarten erhält. Erfahren Sie, wie Sie fehlende
  Schriftarten effizient handhaben.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: de
og_description: Wie man Warnungen beim Laden einer DOCX mit Aspose.Words erfasst,
  Warnmeldungen erhält und fehlende Schriftarten mit praktischen Codebeispielen behandelt.
og_title: Wie man Warnungen in Aspose.Words erfasst – Vollständiger C#‑Leitfaden
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man Warnungen in Aspose.Words erfasst – Vollständiger C#‑Leitfaden
url: /de/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen in Aspose.Words erfasst – Vollständiger C#‑Leitfaden

Haben Sie sich jemals gefragt, **wie man Warnungen** erfasst, die beim Laden eines Word‑Dokuments mit Aspose.Words auftreten? Vielleicht sehen Sie seltsame Schriftartenänderungen und möchten genau wissen, warum. Kurz gesagt, Sie können sich in das Warnsystem der Bibliothek einklinken, **Warnmeldungen erhalten** und sogar **fehlende Schriften behandeln**, bevor sie Ihr Layout ruinieren.  

In diesem Tutorial führen wir Sie durch ein praxisnahes Szenario: Laden einer DOCX, Sammeln jeder Warnung, die die Engine ausgibt, und Ausgeben von Details zu jeder Schriftart‑Substitution. Am Ende haben Sie ein sofort ausführbares Code‑Beispiel, verstehen das „Warum“ hinter jedem Schritt und wissen, wie Sie den Ansatz für Ihre eigenen Projekte erweitern können.

## Was Sie lernen werden

- Wie Sie `LoadOptions` konfigurieren, damit Warnungen automatisch erfasst werden.  
- Die genaue Methode, **Warnmeldungen** aus der `WarningInfoCollection` zu **erhalten**.  
- Wie Sie **fehlende Schriften** über das Flag `WarningType.FontSubstitution` identifizieren und darauf reagieren.  
- Tipps zur Fehlersuche in Randfällen, wie Dokumente mit eingebetteten Schriften oder benutzerdefinierten Schriftordnern.  

Keine externen Referenzen nötig – alles, was Sie brauchen, finden Sie hier.

---

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+).  
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`).  
- Eine Beispiel‑DOCX (`input.docx`), die entweder einige Schriften nicht enthält oder Schriften verwendet, die nicht auf Ihrem Rechner installiert sind.  

Das war’s. Wenn Sie bereits mit C# und Visual Studio vertraut sind, können Sie den Code einfach kopieren und sofort ausführen.

---

## Schritt 1: Load‑Optionen und einen Warn‑Callback vorbereiten

Das Erste, was Aspose.Words tut, wenn Sie `new Document(path, loadOptions)` aufrufen, ist das Parsen der Datei. Beim Parsen kann es auf fehlende Schriften, nicht unterstützte Features oder veraltetes Markup stoßen. Um diese Ereignisse abzufangen, benötigen Sie ein **Warn‑Callback**‑Objekt.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Warum das wichtig ist:** Ohne einen Callback protokolliert Aspose.Words Warnungen stillschweigend in die Konsole (oder verwirft sie), sodass Sie blind gegenüber Schriftart‑Substitutionen bleiben, die das Layout beeinflussen könnten. Durch die Bereitstellung einer dedizierten `WarningInfoCollection` erhalten Sie vollständige Sichtbarkeit.

> **Pro‑Tipp:** Wenn Sie nur an schriftenbezogenen Warnungen interessiert sind, können Sie später filtern – das Sammeln *aller* Warnungen bietet Ihnen ein Sicherheitsnetz für zukünftige Probleme.

---

## Schritt 2: Dokument mit den konfigurierten Optionen laden

Jetzt, wo der Callback bereit ist, laden Sie die Datei. Der `Document`‑Konstruktor ruft den Callback automatisch für alle gefundenen Probleme auf.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Was im Hintergrund passiert:** Aspose.Words parsed das Open‑XML, löst Stile auf und versucht, jede Schriftreferenz einer systeminstallierten Schrift zuzuordnen. Wird kein Treffer gefunden, erzeugt es einen `WarningInfo`‑Eintrag vom Typ `FontSubstitution`.

---

## Schritt 3: Gesammelte Warnungen abrufen und prüfen

Nachdem das Laden abgeschlossen ist, enthält Ihr `warningCollector` nun jede aufgetretene Warnung. Lassen Sie uns diese herausziehen und uns auf Schriftart‑Substitutionsnachrichten konzentrieren.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Beispielausgabe** (Ihre Konsole könnte etwa Folgendes anzeigen):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Wenn Sie *alle* Warnungen wollen, entfernen Sie einfach die `if`‑Prüfung oder protokollieren Sie `warning.Type` für jeden Eintrag.

---

## Schritt 4: Fehlende Schriften behandeln – über reines Logging hinaus

Warnungen zu erfassen ist nützlich, aber oft müssen Sie **fehlende Schriften** programmgesteuert **behandeln**. Hier sind zwei gängige Strategien:

### 4.1 Fehlende Schriften durch einen bestimmten Fallback ersetzen

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Jetzt wird jede fehlende Schrift durch *Calibri* ersetzt, anstatt den Standard‑Fallback der Bibliothek zu verwenden.

### 4.2 Ersatzschrift dynamisch einbetten

Wenn Sie eine benutzerdefinierte Schriftdatei haben (z. B. `MyFallback.ttf`), können Sie sie zur Laufzeit registrieren:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Dieser Ansatz ist praktisch, wenn Sie eine bestimmte Unternehmensschrift mit Ihrer Anwendung ausliefern.

> **Randfall:** Dokumente, die die erforderliche Schrift bereits eingebettet haben, ignorieren die System‑Substitutionsregeln. In diesem Szenario ist die Warnsammlung für diese Schrift leer, was genau das gewünschte Ergebnis ist.

---

## Schritt 5: Vollständiges funktionierendes Beispiel (Kopieren‑Einfügen bereit)

Unten finden Sie ein eigenständiges Programm, das alles von Anfang bis Ende demonstriert. Ersetzen Sie einfach `YOUR_DIRECTORY/input.docx` durch den Pfad zu Ihrer Testdatei.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Was Sie erwarten können**

- Die Konsole gibt jede Schrift‑Substitutionswarnung aus, vorangestellt mit einem Warn‑Emoji zur besseren Sichtbarkeit.  
- Das Ausgabedokument DOCX (`output.docx`) verwendet *Calibri* überall dort, wo eine fehlende Schrift erkannt wurde.  
- Keine unbehandelten Ausnahmen – das Warnsystem verarbeitet jede unbekannte Schrift elegant.

---

## Häufige Fragen & Antworten

**F: Funktioniert das mit PDFs, die aus Word erzeugt wurden?**  
**A:** Ja. Aspose.Words behandelt PDFs als ein weiteres Ausgabeformat. Das Erfassen von Warnungen erfolgt während der *Lade*‑Phase, sodass es unabhängig vom finalen Export ist.

**F: Was, wenn ich Warnungen für **alle** Dokumentoperationen (Speichern, Konvertieren usw.) erfassen muss?**  
**A:** Sie können dieselbe `WarningInfoCollection` wiederverwenden, indem Sie sie nach der Instanziierung des Dokuments `Document.WarningCallback` zuweisen. Jede nachfolgende Operation fügt neue Einträge in dieselbe Sammlung ein.

**F: Beeinflusst der Warn‑Callback die Performance?**  
**A:** Vernachlässigbar. Die Sammlung speichert einfach Objekte; solange Sie nicht tausende Warnungen in einer engen Schleife verarbeiten, werden Sie keinen merklichen Geschwindigkeitsverlust bemerken.

**F: Wie unterdrücke ich Warnungen, die mich nicht interessieren?**  
**A:** Implementieren Sie eine benutzerdefinierte Klasse, die `IWarningCallback` erbt, und filtern Sie innerhalb der `Warning`‑Methode. Die eingebaute `WarningInfoCollection` speichert nur, sie filtert nicht.

---

## Pro‑Tipps & Fallstricke

- **Pro‑Tipp:** Prüfen Sie stets `Warning.Description` – sie enthält den genauen Namen der fehlenden Schrift. Das kann Ihnen helfen zu entscheiden, ob Sie die Schrift mit Ihrer Anwendung ausliefern sollten.  
- **Achten Sie auf eingebettete Schriften:** Wenn das Quell‑DOCX die benötigte Schrift bereits einbettet, gibt Aspose.Words keine Substitutionswarnung aus, selbst wenn die Schrift lokal nicht installiert ist.  
- **Thread‑Sicherheit:** `WarningInfoCollection` ist nicht thread‑sicher. Wenn Sie mehrere Dokumente gleichzeitig laden, geben Sie jedem Thread seine eigene Sammlung.  
- **Versions‑Check:** Die Warn‑API ist seit Aspose.Words 20.8 stabil. Stellen Sie sicher, dass Sie eine aktuelle Version verwenden, um neuere Warnungstypen nicht zu verpassen.

---

## Fazit

Wir haben **wie man Warnungen** von Aspose.Words erfasst, gezeigt, wie man **Warnmeldungen erhält**, und praktische Methoden **fehlende Schriften** über Fallback‑Schriften oder benutzerdefinierte Schriftordner zu behandeln. Das vollständige Beispiel kann in jedes .NET‑Projekt übernommen werden, und die Konzepte skalieren auf größere Automatisierungspipelines.

Als Nächstes könnten Sie erkunden:

- Verwendung von `Document.WarningCallback`, um Warnungen während **Speicher**‑Operationen zu erfassen.  
- Protokollieren von Warnungen in eine Datei oder ein Telemetriesystem für die Produktionsüberwachung.  
- Erweitern des Callbacks, um fehlende Schriften automatisch durch markenspezifische Schriftarten zu ersetzen.

Fühlen Sie sich frei zu experimentieren – tauschen Sie die Fallback‑Schrift aus, fügen Sie weitere Dokumente zum Batch hinzu oder integrieren Sie den Warn‑Collector in eine CI‑Pipeline, die schriftenbezogene Regressionen meldet. Viel Spaß beim Programmieren, und möge Ihr Dokument stets genau so gerendert werden, wie Sie es erwarten!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}