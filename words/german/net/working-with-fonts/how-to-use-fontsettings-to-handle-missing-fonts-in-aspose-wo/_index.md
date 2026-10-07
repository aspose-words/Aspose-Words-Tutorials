---
category: general
date: 2026-03-16
description: Erfahren Sie, wie Sie FontSettings in Aspose.Words verwenden, um fehlende
  Schriftarten elegant zu handhaben – vollständiger Code, Ereignisbehandlung und Tipps
  zu bewährten Methoden.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: de
og_description: Wie man FontSettings in Aspose.Words verwendet, um fehlende Schriftarten
  zu handhaben – Schritt‑für‑Schritt‑Anleitung mit vollständigem C#‑Beispiel und praktischen
  Tipps.
og_title: Wie man FontSettings verwendet, um fehlende Schriftarten in Aspose.Words
  zu behandeln
tags:
- Aspose.Words
- C#
- Font Management
title: Wie man FontSettings verwendet, um fehlende Schriften in Aspose.Words zu handhaben
url: /de/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man FontSettings verwendet, um fehlende Schriftarten in Aspose.Words zu behandeln

Haben Sie sich jemals gefragt **wie man FontSettings verwendet**, wenn Ihre Word-Dokumente Schriftarten referenzieren, die nicht auf dem Server installiert sind? Sie sind nicht allein. Fehlende Schriftarten können unschöne Ersatzdarstellungen verursachen oder sogar Ausnahmen auslösen, und die meisten Entwickler ignorieren das Problem einfach, bis es in der Produktion auftaucht.  

In diesem Tutorial zeigen wir Ihnen genau **wie man FontSettings verwendet**, um **fehlende Schriftarten** in Aspose.Words zu behandeln, detaillierte Warnungen zu erfassen und die Dokumenten‑Renderung vorhersehbar zu halten. Am Ende haben Sie ein sofort ausführbares C#‑Beispiel, verstehen, warum jede Zeile wichtig ist, und wissen, wie Sie die Lösung für größere Projekte anpassen können.

## Was dieser Leitfaden abdeckt

- Einrichten von **FontSettings** und Abonnieren des `SubstitutionWarning`‑Ereignisses.  
- Anfügen der Einstellungen an `LoadOptions`, damit sie beim Laden eines Dokuments berücksichtigt werden.  
- Ausführen eines Testdokuments, das bewusst Schriftarten fehlt, und Lesen der Konsolenausgabe.  
- Tipps für Logging, Deaktivieren der automatischen Substitution und Behandlung von Sonderfällen wie mehreren fehlenden Schriftarten.  

Keine externe Dokumentation ist erforderlich – alles, was Sie brauchen, finden Sie hier.

## Voraussetzungen

- .NET 6+ (oder .NET Framework 4.6.2+).  
- Aspose.Words für .NET 23.9 oder höher (die von uns verwendete API ist über aktuelle Versionen hinweg stabil).  
- Eine einfache `.docx`‑Datei, die eine Schriftart referenziert, von der Sie wissen, dass sie nicht installiert ist (z. B. *Comic Sans MS* in einem Linux‑Container).  

Das war’s – keine zusätzlichen NuGet‑Pakete außer Aspose.Words.

## Warum das Behandeln fehlender Schriftarten wichtig ist

Wenn ein Dokument eine Schriftart referenziert, die die Laufzeit nicht finden kann, ersetzt Aspose.Words automatisch die nächstgelegene Übereinstimmung. Diese Substitution ist oft akzeptabel, aber manchmal müssen Sie **protokollieren**, welche Schriftarten fehlten (für Compliance) oder die Substitution **vollständig verhindern** (z. B. für markenspezifische PDFs). Durch das Abhören von `FontSettings.SubstitutionWarning` erhalten Sie vollständige Sichtbarkeit und Kontrolle.

## Schritt 1: FontSettings erstellen und das Substitution‑Warning‑Ereignis abonnieren

Das Erste, was Sie tun, ist `FontSettings` zu instanziieren. Dieses Objekt enthält alle schriftbezogenen Konfigurationen für die Bibliothek. Der entscheidende Teil ist das Verbinden des `SubstitutionWarning`‑Ereignisses, das **jedes Mal** ausgelöst wird, wenn Aspose.Words eine angeforderte Schriftart nicht finden kann.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Warum das wichtig ist:**  
- **Sichtbarkeit:** Sie wissen sofort, welche Schriftarten fehlen.  
- **Auditierbarkeit:** Die Konsole (oder ein Logger) kann für Compliance‑Berichte in eine Datei umgeleitet werden.  
- **Kontrolle:** Später können Sie entscheiden, die Substitution durch eine eigene benutzerdefinierte Schriftart zu ersetzen.

> **Pro Tipp:** Wenn Sie ein Logging‑Framework (Serilog, NLog usw.) bevorzugen, ersetzen Sie die `Console.WriteLine`‑Aufrufe durch `logger.Information(...)`.

## Schritt 2: FontSettings an LoadOptions anhängen

`LoadOptions` ist das Mittel, das Aspose.Words mitteilt, wie die Datei während der Ladephase behandelt werden soll. Durch Zuweisen des `FontSettings`‑Objekts stellen Sie sicher, dass der Warn‑Handler *vor* dem Parsen von Inhalten aktiv ist.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Warum das wichtig ist:**  
- Wenn Sie ein Dokument ohne Übergabe von `LoadOptions` laden, greift die Standard‑Schriftartenbehandlung und Sie verpassen die Warnungen.  
- Dieser Ansatz ermöglicht es Ihnen außerdem, andere Ladeverhalten (z. B. Passwortschutz) im selben Objekt anzupassen.

## Schritt 3: Dokument mit den konfigurierten Optionen laden

Jetzt lesen wir endlich die Word‑Datei. Der Pfad kann absolut oder relativ sein; Aspose.Words respektiert die gerade vorbereiteten `LoadOptions`.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Wenn das Dokument eine Schriftart enthält, die nicht installiert ist, wird das `SubstitutionWarning`‑Ereignis ausgelöst und Sie sehen eine Ausgabe, die dem untenstehenden Beispiel ähnelt.

### Erwartete Konsolenausgabe

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Der genaue Ersatz kann je nach Schriftart‑Fallback‑Kette des Betriebssystems variieren, aber der **Name der fehlenden Schriftart** wird immer gemeldet.

## Schritt 4: Ergebnis überprüfen (optionale Darstellung)

Oft möchten Sie sicherstellen, dass das Dokument nach der Substitution noch gut aussieht. Eine schnelle Methode ist, es als PDF zu speichern und das Ergebnis zu öffnen.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Wenn Sie die Substitution vollständig **verhindern** müssen, setzen Sie `FontSettings.SubstitutionSettings.TableSubstitution = false` vor dem Laden. Dann wirft Aspose.Words eine Ausnahme für fehlende Schriftarten, die Sie abfangen und behandeln können.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort ausführbare Programm. Fügen Sie es in eine Konsolenanwendung ein, passen Sie den Dateipfad an und drücken Sie **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Was Sie erwarten können

- Die Konsole gibt jede fehlende Schriftart zusammen mit dem gewählten Ersatz aus.  
- Das resultierende PDF (wenn Sie das optionale Speichern beibehalten haben) zeigt das Dokument mit der Ersatzschriftart an und gewährleistet die Layout‑Integrität.

## Häufige Fragen & Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Was ist, wenn mehrere Schriftarten fehlen?** | Das Ereignis wird für jede fehlende Schriftart einmal ausgelöst, sodass Sie für jede eine separate Protokollzeile erhalten. |
| **Kann ich den Ersatz durch eine benutzerdefinierte Schriftart ersetzen?** | Ja. Im Ereignishandler können Sie `e.SubstitutedFont = new FontInfo("MyCustomFont")` aufrufen. |
| **Wird die Warnung auch für eingebettete Schriftarten ausgelöst, die nicht geladen werden können?** | Absolut – unabhängig davon, ob die Schriftart extern oder eingebettet ist, wird die gleiche Warnung ausgelöst. |
| **Muss ich `Document` entsorgen?** | `Document` implementiert `IDisposable`. Umwickeln Sie die Nutzung mit einem `using`‑Block, wenn Sie viele Dateien in einer Schleife laden. |
| **Funktioniert das in Linux‑Containern?** | Solange Aspose.Words Systemschriftarten finden kann (z. B. über `fontconfig`), funktioniert derselbe Ereignismechanismus. |

## Best Practices & Pro‑Tipps

- **Logging zentralisieren:** Erstellen Sie eine Hilfsmethode, die sowohl in die Konsole als auch in eine persistente Protokolldatei schreibt.  
- **Batch‑Verarbeitung:** Beim Konvertieren von Dutzenden Dokumenten verwenden Sie eine einzelne `FontSettings`‑Instanz, um wiederholte Ereignis‑Abonnements zu vermeiden.  
- **Performance:** Substitutionswarnungen verursachen nur vernachlässigbare Overhead, aber wenn Sie Tausende von Dateien verarbeiten, sollten Sie sie nach der Verifizierung des Schriftartensatzes deaktivieren.  
- **Versionssicherheit:** Die `SubstitutionWarning`‑API ist seit Aspose.Words 16.0 stabil, sodass Sie sich für zukünftige Upgrades darauf verlassen können.

## Fazit

Wir haben gezeigt, **wie man FontSettings** in Aspose.Words verwendet, um **fehlende Schriftarten** elegant zu behandeln. Durch das Erstellen eines `FontSettings`‑Objekts, das Abonnieren von `SubstitutionWarning` und das Laden von Dokumenten über `LoadOptions` erhalten Sie vollständige Sichtbarkeit auf Schriftart‑Probleme und können entscheiden, ob Sie protokollieren, ersetzen oder bei fehlenden Schriftarten abbrechen möchten.  

Von der einfachen Konsolenausgabe bis hin zu benutzerdefinierter Substitutionslogik skaliert das Muster zu großen Dokument‑Batch‑Pipelines und stellt sicher, dass Ihre Ausgabe konsistent und auditierbar bleibt.

**Nächste Schritte:**  

- Erkunden Sie **benutzerdefinierte Schriftart‑Substitution**, indem Sie `e.SubstitutedFont` im Ereignis zuweisen.  
- Kombinieren Sie diesen Ansatz mit **Dokumenten‑Rendering zu Bildern** für die Thumbnail‑Erstellung.  
- Schauen Sie sich **Aspose.PDF** an, wenn Sie die substituierten Schriftarten direkt in das endgültige PDF einbetten müssen, um vollständige Portabilität zu erreichen.

Viel Spaß beim Coden, und möge Ihre Dokumente nie wieder unter einer fehlenden Schriftart leiden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}