---
category: general
date: 2026-04-24
description: Wie man die Substitution fehlender Schriftarten in Aspose.Words mit C#
  erkennt. Dieser Leitfaden zeigt, wie man fehlende Schriftarten zuverlässig mit FontSettings‑Warnungen
  behandelt.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: de
og_description: Wie man die Substitution fehlender Schriftarten in Aspose.Words mit
  C# erkennt. Erfahren Sie, wie Sie fehlende Schriftarten mithilfe von FontSettings‑Warnungen
  behandeln.
og_title: Wie man Substitution in Aspose.Words erkennt – Vollständige Anleitung
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Wie man Substitution in Aspose.Words erkennt – Fehlende Schriftarten behandeln
url: /de/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Substitution in Aspose.Words erkennt – Fehlende Schriftarten behandeln

Haben Sie sich jemals gefragt, **wie man Substitution erkennt**, wenn ein Dokument versucht, eine Schriftart zu verwenden, die auf Ihrem Server nicht installiert ist? Das ist ein häufiges Problem, besonders wenn Sie PDFs oder Word‑Dateien in einer automatisierten Pipeline erzeugen. Die gute Nachricht ist, dass Aspose.Words einen integrierten Hook bereitstellt, um genau diese Situation zu erkennen, und Sie können **fehlende Schriftarten** ebenfalls elegant **behandeln**.

In diesem Tutorial führen wir Sie durch ein praxisnahes Beispiel, das **wie man Substitution erkennt** über das `FontSettings.Warning`‑Ereignis zeigt, und wir erklären, wie man **fehlende Schriftarten behandelt**, ohne Ihren Verarbeitungsablauf zu unterbrechen. Am Ende haben Sie ein sofort einsatzbereites Snippet, ein klares Verständnis dafür, warum jede Zeile wichtig ist, und einige Tipps, um typische Fallstricke zu vermeiden.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch unter .NET Framework)
- Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`) – Version 23.11 oder neuer
- Ein Beispieldokument, das eine Schriftart referenziert, die nicht installiert ist (z. B. `MissingFont.docx`)
- Visual Studio, VS Code oder eine beliebige C#‑IDE Ihrer Wahl  

Keine zusätzliche Konfiguration ist erforderlich, abgesehen vom Hinzufügen des NuGet‑Pakets.

---

## Wie man Substitution mit FontSettings erkennt

Der Kern von **wie man Substitution erkennt** liegt im `FontSettings.Warning`‑Ereignis. Wenn Aspose.Words eine angeforderte Schriftart nicht finden kann, löst es eine `WarningType.FontSubstitution`‑Warnung aus. Durch das Abonnieren dieses Ereignisses erhalten Sie eine Echtzeit‑Benachrichtigung, die den ursprünglichen Schriftartnamen sowie die als Ersatz verwendete Schriftart enthält.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Warum das funktioniert:**  
- `LoadOptions.FontSettings` weist Aspose.Words an, das von Ihnen erstellte `FontSettings`‑Objekt zu verwenden.  
- Das Abonnieren von `Warning` bietet Ihnen einen einzigen Ort, um *alle* schriftbezogenen Probleme zu überwachen, nicht nur fehlende Schriftarten.  
- Der Filter `WarningType.FontSubstitution` stellt sicher, dass Sie nur auf das genaue Szenario reagieren, das Sie interessiert – das Wesentliche von **wie man Substitution erkennt**.

### Erwartete Ausgabe

Wenn Sie den obigen Code mit einem Dokument ausführen, das eine nicht vorhandene Schriftart referenziert, wird etwas Ähnliches ausgegeben:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Verwendet das Dokument nur installierte Schriftarten, bleibt die Konsole still – ein klares Signal, dass **wie man Substitution erkennt** erfolgreich war, ohne Fehlalarme.

## Fehlende Schriftarten elegant behandeln

Eine Substitution zu erkennen ist nur die halbe Miete; Sie benötigen außerdem eine Strategie, um **fehlende Schriftarten zu behandeln**, damit das Endergebnis wie gewünscht aussieht. Nachfolgend drei praktische Ansätze, die Sie kombinieren können.

### 1. Einen Ersatz‑Schriftarten‑Ordner bereitstellen

Aspose.Words kann in zusätzlichen Verzeichnissen nach Schriftarten suchen. Wenn Sie es auf einen Ordner zeigen, der die von Ihnen erwarteten gängigsten Schriftarten enthält, verringern Sie die Wahrscheinlichkeit einer Substitution vollständig.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Warum:** Wenn die Originalschriftart fehlt, verfügt Aspose.Words nun über ein bekanntes Set an Alternativen, was häufig zu einem vorhersehbareren visuellen Ergebnis führt.

### 2. Fehlende Schriftarten programmgesteuert ersetzen

Wenn Sie die volle Kontrolle haben möchten, können Sie die fehlende Schriftart nach der Erkennung durch eine bestimmte ersetzen.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Warum:** Dies teilt der Engine exakt mit, welche Schriftarten versucht werden sollen, sodass Sie Corporate‑Branding oder Barrierefreiheitsstandards durchsetzen können.

### 3. Protokollieren und abbrechen (wenn Substitution nicht akzeptabel ist)

Manchmal bedeutet eine fehlende Schriftart, dass das Dokument für Ihren Anwendungsfall ungültig ist (z. B. Rechtsformulare). In diesem Szenario können Sie sofort eine Ausnahme auslösen, sobald eine Substitution auftritt.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Warum:** Ein sofortiges Scheitern verhindert nachgelagerte Fehler, wie z. B. falsch ausgerichtete Tabellen oder beschädigte Unterschriften.

## Vollständiges funktionierendes Beispiel – Alle Schritte kombiniert

Unten finden Sie ein einzelnes, copy‑paste‑fertiges Programm, das **wie man Substitution erkennt** *und* mehrere Methoden **fehlende Schriftarten zu behandeln** demonstriert. Kommentieren Sie gern die Abschnitte aus, die Sie nicht benötigen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Was zu erwarten ist:**  
- Wenn `MissingFont.docx` eine Schriftart referenziert, die nicht auf dem Rechner vorhanden ist, gibt die Konsole die Substitutionswarnung aus.  
- Das gespeicherte `Processed.docx` verwendet die von Ihnen konfigurierte Ersatzschriftart (oder den Standard der Bibliothek).  
- Es treten keine unbehandelten Ausnahmen auf, es sei denn, Sie brechen bei einer Substitution bewusst ab.

## Häufige Fragen & Sonderfälle

| Frage | Antwort |
|----------|--------|
| *Was ist, wenn das Dokument viele fehlende Schriftarten enthält?* | Das Warnungsereignis wird für **jede** Substitution ausgelöst, sodass Sie mehrere Zeilen sehen. Sie können sie zu einer Liste zusammenfassen, um einen Zusammenfassungsbericht zu erstellen. |
| *Funktioniert das mit der PDF-Konvertierung?* | Absolut. Die gleichen `FontSettings` werden berücksichtigt, wenn Sie `doc.Save("out.pdf")` aufrufen. Die Substitutionswarnung wird weiterhin ausgelöst, sodass Sie die visuelle Treue der PDF überprüfen können. |
| *Kann ich Substitution erkennen, nachdem das Dokument bereits geladen ist?* | Nicht direkt. Die Warnung wird **während** des Ladens oder Speicherns ausgelöst. Wenn Sie eine Analyse nach dem Laden benötigen, erfassen Sie die Warnungen während der Ladephase in einer Sammlung. |
| *Wie sieht es mit benutzerdefinierten, im DOCX eingebetteten Schriftarten aus?* | Eingebettete Schriftarten gelten als vorhanden, sodass keine Substitution erfolgt. Ist die eingebettete Schriftart beschädigt, löst Aspose.Words dennoch eine Warnung aus, die Sie auf dieselbe Weise abfangen können. |
| *Gibt es Auswirkungen auf die Performance?* | Minimal. Die Warnungsprüfung ist leichtgewichtig; die eigentlichen Kosten liegen im Laden des Dokuments. Das Hinzufügen eines Schriftarten‑Ordners kann die Suchzeit leicht erhöhen, jedoch nur beim ersten Laden. |

## Pro‑Tipps & Stolperfallen, die Sie vermeiden sollten

- **Pro‑Tipp:** Setzen Sie immer `recursive: true`, wenn Sie auf einen Ordner mit vielen Schriftarten zeigen; andernfalls werden Unterordner ignoriert.  
- **Achtung:** Groß‑/Kleinschreibung unter Linux. Schriftartnamen sind unter Windows nicht case‑sensitive, jedoch unter Linux schon, daher verwenden Sie den genauen Namen oder fügen beide Varianten hinzu.  
- **Denken Sie daran:** Wenn Sie in einer containerisierten Umgebung arbeiten, stellen Sie sicher, dass der Schriftarten‑Ordner Teil des Images ist oder zur Laufzeit gemountet wird.  
- **Tipp:** Speichern Sie Warnungen in einer `List<string>`, wenn Sie eine Zusammenfassung für Endbenutzer bereitstellen oder sie in ein Monitoring‑System protokollieren müssen.  

## Fazit

Wir haben **wie man Substitution** fehlender Schriftarten in Aspose.Words behandelt, Ihnen mehrere Methoden **fehlende Schriftarten zu behandeln** gezeigt und ein vollständiges, ausführbares Beispiel bereitgestellt, das Sie in jedes .NET‑Projekt einbinden können. Durch das Nutzen des `FontSettings.Warning`‑Ereignisses erhalten Sie Echtzeit‑Einblick in Schriftart‑Probleme, und mit Ersatz‑Ordnern oder expliziten Substitutionsregeln bleibt Ihre Ausgabe exakt wie erwartet.

Bereit für den nächsten Schritt? Versuchen Sie, die Lösung zu erweitern, indem Sie die Ersatzschriftart automatisch in das erzeugte PDF einbetten, oder binden Sie den Warnungs‑Handler in einen zentralen Logging‑Service für großskalige Dokument‑Pipelines ein. Die heute besprochenen Muster – ereignisgesteuerte Erkennung, eleganter Fallback und explizite Fehlerbehandlung – gelten für viele andere Aspose‑APIs, sodass Sie nun gerüstet sind, Schriftart‑bezogene Herausforderungen überall zu meistern.

Haben Sie weitere Fragen zur Schriftarten‑Verarbeitung, PDF‑Konvertierung oder Aspose.Words‑Tricks? Hinterlassen Sie unten einen Kommentar und happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}