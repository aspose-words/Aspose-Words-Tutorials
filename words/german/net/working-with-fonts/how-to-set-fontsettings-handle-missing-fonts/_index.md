---
category: general
date: 2026-05-29
description: Erfahren Sie, wie Sie FontSettings in Aspose.Words festlegen und fehlende
  Schriftarten elegant handhaben. Schritt‑für‑Schritt‑Anleitung mit vollständigem
  Code und bewährten Methoden.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: de
og_description: Wie man FontSettings in Aspose.Words festlegt und fehlende Schriftarten
  schnell behandelt. Folgen Sie diesem Leitfaden für eine vollständige, ausführbare
  Lösung.
og_title: So setzen Sie FontSettings – Umgang mit fehlenden Schriftarten
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Wie man FontSettings einstellt – Umgang mit fehlenden Schriften
url: /de/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So setzen Sie FontSettings – Umgang mit fehlenden Schriften

Haben Sie sich jemals gefragt, **wie man FontSettings setzt**, wenn man mit Aspose.Words arbeitet und plötzlich auf ein Dokument stößt, das eine Schriftart referenziert, die nicht installiert ist? Das ist ein häufiges Problem, besonders beim Verarbeiten von vom Kunden bereitgestellten Dateien auf einem Server, der nur über einen minimalen Schriftsatz verfügt. Die gute Nachricht? Sie können diese Lücken abfangen und **fehlende Schriften behandeln**, ohne dass Ihre Anwendung abstürzt oder unschöne PDFs erzeugt.

In diesem Tutorial führen wir Sie durch ein praxisnahes Szenario: das Laden einer DOCX, die nach „Calibri“ verlangt, während Ihr Linux‑Container nur „DejaVu Sans“ bereitstellt. Sie sehen genau, wie Sie FontSettings konfigurieren, sich für Substitutionswarnungen anmelden und Ersatzschriften bereitstellen, damit das Dokument genau so gerendert wird, wie es der Autor beabsichtigt hat. Kein Schnickschnack – nur der Code, den Sie noch heute in Ihr Projekt übernehmen können.

## Voraussetzungen

- .NET 6.0 oder höher (die API funktioniert identisch auf .NET Framework 4.7+)
- Aspose.Words für .NET 23.10 oder neuer (der NuGet‑Paketname ist `Aspose.Words`)
- Eine grundlegende C#‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code)

Wenn Sie das haben, legen wir los.

## Schritt 1: FontSettings erstellen und auf Substitutions‑Ereignisse hören

Das Herzstück der Lösung ist das Objekt `FontSettings`. Indem Sie einen Handler an dessen `FontSubstitutionWarning`‑Ereignis anhängen, erhalten Sie einen Live‑Report jedes Mal, wenn Aspose.Words eine fehlende Schriftart ersetzen muss.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Warum das wichtig ist:**  
Wenn die Engine *Calibri* nicht finden kann, fällt sie möglicherweise stillschweigend auf *Arial* zurück. Durch das Abhören der Warnung behalten Sie eine transparente Prüfspur – ideal für Debugging oder Compliance‑Berichte.

> **Pro‑Tipp:** Wenn Sie dies auf einem CI‑Server ausführen, leiten Sie die Ausgabe in eine Log‑Datei um, damit Sie nach einem Batch‑Durchlauf prüfen können, welche Schriften fehlten.

## Schritt 2: FontSettings an LoadOptions anhängen

`LoadOptions` ist das Tor zur Steuerung, wie ein Dokument geparst wird. Durch das Zuweisen der gerade konfigurierten `FontSettings` respektiert jeder nachfolgende `Document`‑Ladevorgang unsere Substitutionslogik.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Was im Hintergrund passiert:**  
Während des `Document`‑Konstruktors liest Aspose.Words das XML der DOCX, löst Schriftart‑Verweise auf und – falls eine Schriftart nicht gefunden wird – löst die zuvor eingerichtete Warnung aus. Ohne diesen Hook wüssten Sie nie, dass eine Substitution stattgefunden hat.

## Schritt 3: Dokument laden und (optional) Ersatzschriften definieren

Jetzt laden wir die Datei endlich in den Speicher. Wenn Sie bereits einen Ordner mit Ersatzschriften haben (z. B. ein Verzeichnis mit OpenType‑Schriften, das mit Ihrer Anwendung ausgeliefert wird), teilen Sie `FontSettings` mit, wo es suchen soll. Dieser Schritt ist optional, aber oft der sauberste Weg, *fehlende Schriften zu behandeln*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Hinweis zu Sonderfällen:**  
Wenn das Dokument eine benutzerdefinierte Schriftart enthält, die als Binärstrom eingebettet ist, verwendet Aspose.Words sie automatisch – keine Substitution nötig. Die Warnung wird nur bei *fehlenden* Systemschriften ausgelöst.

### Ergebnis überprüfen

Nach dem Laden möchten Sie das Dokument möglicherweise als PDF oder Word speichern, um zu bestätigen, dass alles korrekt aussieht.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Wenn Sie das Programm ausführen, gibt die Konsole Zeilen aus wie:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Wenn Sie diese Meldungen sehen, haben Sie **fehlende Schriften erfolgreich behandelt** und wissen genau, welche Substitutionen stattgefunden haben.

## Schritt 4: Fortgeschritten – Benutzerdefinierte Schriftart‑Substitutionsregeln (optional)

Manchmal benötigen Sie eine deterministische Zuordnung, z. B. immer *Times New Roman* durch *Liberation Serif* zu ersetzen. Das können Sie mit `FontSettings.SubstitutionTable` erreichen.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Warum das Ganze?**  
Explizite Regeln geben Ihnen Kontrolle über die Typografie und sorgen für Marken‑konsistenz in erzeugten PDFs, besonders wenn Sie Marketing‑Materialien produzieren.

## Häufige Fallstricke & wie man sie vermeidet

| Fallstrick | Symptom | Lösung |
|------------|---------|--------|
| **Keine Warnungsausgabe** | Sie denken, die Schriften sind in Ordnung, aber das Dokument sieht falsch aus. | Stellen Sie sicher, dass `FontSubstitutionWarning` **vor** dem Laden des Dokuments angehängt ist. |
| **Fallback‑Ordner nicht durchsucht** | Substitutionen fallen weiterhin auf System‑Standard zurück. | Rufen Sie `SetFontsFolder(path, true)` mit dem zweiten Argument `true` auf, um Unterordner rekursiv zu durchsuchen. |
| **Leistungseinbußen bei großen Stapeln** | Das Laden von 10 000 Dokumenten wird langsam. | Cachen Sie eine einzelne `FontSettings`‑Instanz und verwenden Sie sie bei mehreren Ladevorgängen wieder; vermeiden Sie das wiederholte Erzeugen. |
| **Eingebettete Schriften ignoriert** | Sie erwarteten, dass eine benutzerdefinierte eingebettete Schrift verwendet wird, aber es erfolgt eine Substitution. | Prüfen Sie, ob die Quell‑DOCX die Schrift tatsächlich einbettet (nachprüfen in Word → Datei → Info → Schriften). |

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort einsetzbare Programm. Es demonstriert alles von der Ereignisbehandlung bis zum Speichern des finalen PDFs.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Erwartete Konsolenausgabe** (Beispiel):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Führen Sie das Programm aus, öffnen Sie `Output.pdf` und Sie werden den Text mit den Ersatzschriften gerendert sehen – keine fehlenden Glyphen‑Quadrate, keine Abstürze.

## Fazit

Sie haben nun ein solides, produktionsreifes Muster, **wie man FontSettings** in Aspose.Words **elegant setzt und fehlende Schriften behandelt**. Durch das Anschließen des `FontSubstitutionWarning`‑Ereignisses, das Verweisen auf ein Ersatzschrift‑Verzeichnis und (falls nötig) das Definieren expliziter Substitutionsregeln erhalten Sie volle Sichtbarkeit und Kontrolle über die Typografie in automatisierten Dokument‑Pipelines.

Was kommt als Nächstes? Versuchen Sie, eine benutzerdefinierte Schriftart‑Sammlung für markenspezifische Schriften hinzuzufügen, oder erkunden Sie die `FontSourceBase`‑API, um Schriften aus einer Datenbank oder Cloud‑Speicherung zu laden. Die gleichen Prinzipien gelten – einfach eine andere Quelle in `FontSettings` einbinden.

Haben Sie Fragen zu Sonderfällen, z. B. zur Handhabung von Rechts‑nach‑Links‑Skripten oder Emoji‑Schriften? Hinterlassen Sie unten einen Kommentar und viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

- [Wie man Schriften in Aspose.Words erfasst – Komplettanleitung](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Wie man Schriften in Aspose.Words erkennt – Warnungen & Einstellungen behandeln](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Wie man DOCX lädt und fehlende Schriften erkennt – Vollständiger C#‑Leitfaden](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}