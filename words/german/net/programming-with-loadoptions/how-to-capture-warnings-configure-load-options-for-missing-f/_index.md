---
category: general
date: 2026-03-30
description: Wie man Warnungen beim Laden einer DOCX-Datei erfasst – lernen Sie, fehlende
  Schriftarten zu erkennen, Schriftarteinstellungen zu konfigurieren und Ladeoptionen
  in C# festzulegen.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: de
og_description: Wie man Warnungen beim Laden einer DOCX-Datei erfasst – Schritt‑für‑Schritt‑Anleitung
  zum Erkennen fehlender Schriftarten und zum Konfigurieren von Schriftarteinstellungen
  in C#.
og_title: Warnungen erfassen – Ladeoptionen für fehlende Schriften konfigurieren
tags:
- Aspose.Words
- C#
- Font management
title: Warnungen erfassen – Ladeoptionen für fehlende Schriftarten konfigurieren
url: /de/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen erfasst – Load‑Optionen für fehlende Schriften konfigurieren

Haben Sie sich schon einmal gefragt, **wie man Warnungen** erfasst, die auftauchen, wenn ein Dokument versucht, eine Schrift zu verwenden, die nicht installiert ist? Das ist ein Szenario, das vielen Entwicklern, die mit Word‑Processing‑Bibliotheken arbeiten, Schwierigkeiten bereitet, besonders wenn Sie **fehlende Schriften** erkennen müssen, bevor sie Ihre PDF‑Export‑Pipeline zum Absturz bringen.  

In diesem Tutorial zeigen wir Ihnen eine praktische, sofort einsatzbereite Lösung, die **Schrifteinstellungen konfiguriert**, **Load‑Optionen setzt** und jede Substitutionswarnung in die Konsole ausgibt. Am Ende wissen Sie genau, **wie man fehlende Schriften** handhabt, sodass Ihre Anwendung robust bleibt und Ihre Nutzer zufrieden sind.

## Was Sie lernen werden

- Wie Sie **Load‑Optionen setzen**, damit die Bibliothek Schriftprobleme meldet, anstatt sie stillschweigend zu ersetzen.
- Die genauen Schritte, um **Schrifteinstellungen zu konfigurieren** für die Erfassung von Warnungen.
- Möglichkeiten, **fehlende Schriften** programmgesteuert zu **detektieren** und entsprechend zu reagieren.
- Ein vollständiges, copy‑paste‑C#‑Beispiel, das mit der neuesten Aspose.Words für .NET (v24.10 zum Zeitpunkt des Schreibens) funktioniert.
- Tipps, wie Sie die Lösung erweitern können, um Warnungen zu protokollieren, auf benutzerdefinierte Schriften zurückzugreifen oder die Verarbeitung abzubrechen, wenn kritische Schriften fehlen.

> **Voraussetzung:** Sie benötigen das NuGet‑Paket *Aspose.Words für .NET* (`Install-Package Aspose.Words`). Weitere externe Abhängigkeiten sind nicht erforderlich.

---

## Schritt 1: Namespaces importieren und das Projekt vorbereiten

Fügen Sie zunächst die notwendigen `using`‑Direktiven hinzu. Das ist nicht nur Boiler‑Plate; es teilt dem Compiler mit, wo `LoadOptions`, `FontSettings` und `Document` zu finden sind.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro‑Tipp:** Wenn Sie .NET 6+ verwenden, können Sie *global using*‑Anweisungen aktivieren, um diese Zeilen in jeder Datei zu vermeiden.

---

## Schritt 2: Load‑Optionen setzen und Schrift‑Substitutions‑Warnungen aktivieren

Der Kern von **wie man Warnungen erfasst** liegt im `LoadOptions`‑Objekt. Indem Sie eine neue `FontSettings`‑Instanz erstellen und einen Event‑Handler an `SubstitutionWarning` anhängen, lassen Sie die Bibliothek jedes Mal eine Meldung ausgeben, wenn eine angeforderte Schrift nicht gefunden wird.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Warum das wichtig ist:** Ohne das Event‑Abonnement weicht Aspose.Words stillschweigend auf eine Standardschrift aus, und Sie wissen nie, welche Glyphen ersetzt wurden. Durch das Abhören von `SubstitutionWarning` erhalten Sie eine vollständige Audit‑Spur – entscheidend für Umgebungen mit hohen Compliance‑Anforderungen.

---

## Schritt 3: Dokument mit den konfigurierten Optionen laden

Jetzt, wo die Warnungen verkabelt sind, laden Sie Ihr DOCX (oder ein anderes unterstütztes Format) mit den gerade vorbereiteten `loadOptions`. Der `Document`‑Konstruktor löst die Schrift‑Prüflogik sofort aus.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Wenn die Datei z. B. *„Comic Sans MS“* referenziert, aber auf dem Rechner nur *„Arial“* vorhanden ist, sehen Sie etwa Folgendes:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Diese Zeile wird direkt in die Konsole geschrieben, weil wir den Handler zuvor angehängt haben.

---

## Schritt 4: Erfasste Warnungen prüfen und darauf reagieren

Warnungen zu erfassen ist nur die halbe Miete; meist muss entschieden werden, was als Nächstes geschieht. Unten finden Sie ein kurzes Muster, das Warnungen in einer Liste speichert, um sie später zu analysieren – ideal, wenn Sie sie in eine Datei protokollieren oder den Import abbrechen wollen, sobald eine kritische Schrift fehlt.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Umgang mit Sonderfällen:**  
- **Mehrere fehlende Schriften:** Die Liste enthält einen Eintrag pro Substitution, sodass Sie iterieren und einen detaillierten Bericht erstellen können.  
- **Benutzerdefinierte Fallback‑Schriften:** Wenn Sie eigene Schriftdateien besitzen, fügen Sie sie vor dem Laden zu `FontSettings` hinzu: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Die Warnungen zeigen dann den benutzerdefinierten Fallback anstelle des System‑Defaults.

---

## Schritt 5: Vollständiges, lauffähiges Beispiel (Copy‑Paste‑bereit)

Alles zusammengeführt, hier eine eigenständige Konsolen‑App, die Sie jetzt kompilieren und ausführen können.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Erwartete Konsolenausgabe** (wenn das DOCX eine fehlende Schrift referenziert):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Fehlt eine *kritische* Schrift wie „Times New Roman“, sehen Sie stattdessen die Abbruch‑Meldung.

---

## Häufige Fragen & Stolperfallen

| Frage | Antwort |
|----------|--------|
| **Muss ich `SetFontsFolder` aufrufen, um Warnungen zu erfassen?** | Nein. Das Warn‑Event funktioniert mit den Standardsystemschriften. `SetFontsFolder` verwenden Sie nur, wenn Sie zusätzliche Fallback‑Schriften bereitstellen wollen. |
| **Funktioniert das unter .NET Core / .NET 5+?** | Absolut. Aspose.Words 24.10 unterstützt alle modernen .NET‑Laufzeiten. Stellen Sie lediglich sicher, dass das NuGet‑Paket zu Ihrem Ziel‑Framework passt. |
| **Wie kann ich Warnungen in eine Datei statt in die Konsole protokollieren?** | Ersetzen Sie `Console.WriteLine(msg);` durch einen Aufruf Ihres Logging‑Frameworks, z. B. `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Kann ich Warnungen für bestimmte Schriften unterdrücken?** | Ja. Im Event‑Handler können Sie filtern: `if (e.FontName == "SomeFont") return;`. So erhalten Sie feinkörnige Kontrolle. |
| **Gibt es eine Möglichkeit, fehlende Schriften als Fehler zu behandeln?** | Werfen Sie im Handler manuell eine Ausnahme, wenn eine Bedingung erfüllt ist, oder setzen Sie ein Flag und brechen Sie nach dem `Document`‑Konstruktor wie im Beispiel ab. |

---

## Fazit

Sie verfügen nun über ein solides, produktionsreifes Muster, **wie man Warnungen erfasst**, die beim Laden von Dokumenten mit fehlenden Schriften auftreten. Durch **Erkennen fehlender Schriften**, **Konfigurieren von Schrifteinstellungen** und **Setzen der Load‑Optionen** erhalten Sie vollständige Sichtbarkeit auf Schrift‑Substitutions‑Ereignisse und können entscheiden, ob Sie protokollieren, fallbacken oder abbrechen.  

Integrieren Sie diese Logik in Ihre PDF‑Konvertierungspipeline, fügen Sie benutzerdefinierte Fallback‑Schriften hinzu oder leiten Sie die Warnungsliste an ein Monitoring‑System weiter. Der Ansatz skaliert von kleinen Hilfsprogrammen bis hin zu enterprise‑tauglichen Dokumenten‑Verarbeitungs‑Services.

---

### Weiterführende Literatur & nächste Schritte

- **Entdecken Sie weitere FontSettings‑Funktionen** – Einbetten benutzerdefinierter Schriften, Steuerung der Fallback‑Reihenfolge und Lizenz‑Überlegungen.  
- **Kombinieren Sie mit PDF‑Konvertierung** – Nachdem Sie Warnungen erfasst haben, rufen Sie `doc.Save("output.pdf");` auf und prüfen Sie, ob das PDF die erwarteten Schriften verwendet.  
- **Automatisieren Sie Tests** – Schreiben Sie Unit‑Tests, die Dokumente mit bekannten fehlenden Schriften laden und prüfen, dass die Warnungsliste die erwarteten Meldungen enthält.  

Wenn Sie auf Probleme stoßen oder Verbesserungsvorschläge haben, hinterlassen Sie gern einen Kommentar. Viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}