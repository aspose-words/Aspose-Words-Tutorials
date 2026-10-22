---
category: general
date: 2026-04-01
description: Aktivieren Sie Schriftwarnungen beim Laden von Word‑Dokumenten mit Aspose.Words.
  Erfahren Sie, wie Sie Schriftart‑Ersetzungsereignisse mit C# LoadOptions und Schrifteinstellungen
  abfangen können.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: de
og_description: Schriftartwarnungen beim Laden von Word-Dokumenten mit Aspose.Words
  aktivieren. Dieses Tutorial zeigt, wie Sie Schriftart‑Ersetzungsereignisse in C#
  erfassen.
og_title: Schriftwarnungen in Aspose.Words aktivieren – Vollständiger C#‑Leitfaden
tags:
- Aspose.Words
- C#
- Font Management
title: Schriftwarnungen in Aspose.Words aktivieren – Vollständiger C#‑Leitfaden
url: /de/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font-Warnungen in Aspose.Words aktivieren – Vollständige C#-Anleitung

Haben Sie sich jemals gefragt, warum ein Word-Dokument plötzlich anders aussieht, nachdem Sie es programmgesteuert geladen haben? **Enable Font Warnings** und Sie erfahren sofort, wann Aspose.Words eine fehlende Schriftart durch eine Ersatzschriftart ersetzt. In diesem Tutorial führen wir Sie durch ein praxisnahes Beispiel, das nicht nur diese Ersetzungen abfängt, sondern auch erklärt, *warum* sie auftreten.

Wir behandeln alles, was Sie benötigen, um sofort loszulegen: das erforderliche NuGet‑Paket, die genaue `LoadOptions`‑Konfiguration und eine übersichtliche Konsolenausgabe, die Ihnen mitteilt, welche Schriftarten ersetzt wurden. Am Ende haben Sie ein solides, wiederverwendbares Muster für **C# document processing**, das mit jeder Version von Aspose.Words funktioniert.

## Was Sie lernen werden

- Wie man eine `LoadOptions`‑Instanz erstellt, die Schriftartänderungen verfolgt.  
- Der Zweck des `SubstitutionWarning`‑Events und wie man es einbindet.  
- Ein vollständiges, ausführbares Codebeispiel, das klare Warnungen in der Konsole ausgibt.  
- Tipps zum Umgang mit Randfällen, wie Dokumenten, die nur Standardschriftarten enthalten.  

Vorkenntnisse mit Aspose.Words sind nicht erforderlich – nur ein grundlegendes Verständnis von C# und .NET.

---

![Diagramm zur Aktivierung von Font-Warnungen](placeholder-image.png "Diagramm zur Aktivierung von Font-Warnungen")

*Alt-Text: Diagramm zur Aktivierung von Font-Warnungen, das den Ereignisablauf zeigt, wenn eine fehlende Schriftart ersetzt wird.*

## Schritt 1: LoadOptions einrichten und Font-Warnungen aktivieren

Das Erste, was Sie benötigen, ist ein `LoadOptions`‑Objekt. Dieser Container teilt Aspose.Words mit, wie die Datei, die Sie laden möchten, behandelt werden soll. Durch das Zuweisen einer neuen `FontSettings`‑Instanz öffnen Sie die Tür zu schriftbezogenen Ereignissen.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Warum das wichtig ist:**  
Wenn Sie die Zuweisung von `FontSettings` überspringen, wird Aspose.Words fehlende Schriftarten weiterhin ersetzen, aber Sie erhalten keine Benachrichtigung. Der Warnmechanismus befindet sich in `FontSettings`, sodass dessen Initialisierung für unser Ziel *entscheidend* ist.

> **Pro‑Tipp:** Sie können `FontSettings` auch mit `SetFontsFolder` auf einen benutzerdefinierten Schriftartenordner verweisen. Das reduziert die Anzahl der Warnungen, die Sie sehen, weil Aspose.Words die fehlenden Schriftarten tatsächlich finden kann.

## Schritt 2: Das SubstitutionWarning‑Event abonnieren (Schriftart‑Ersetzung)

Jetzt, da das `FontSettings`‑Objekt existiert, binden wir uns in sein `SubstitutionWarning`‑Event ein. Dieses Event wird **jedes Mal** ausgelöst, wenn Aspose.Words eine angeforderte Schriftart durch eine andere ersetzt.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Warum das wichtig ist:**  
Ohne diesen Listener hätten Sie keine Sichtbarkeit auf den Ersetzungsprozess. Die Konsolenausgabe liefert Ihnen eine schnelle Prüfspur, die besonders praktisch bei automatisierten Builds oder bei der Erstellung von PDFs für stark regulierte Branchen ist.

> **Häufige Frage:** *Was, wenn ich die Warnungen unterdrücken möchte?*  
> Sie können den Handler einfach abkoppeln oder `FontSettings.SubstitutionWarning += null;` setzen. Allerdings ist das Beibehalten der Warnungen in der Regel der sicherste Weg, da stille Ersetzungen zu Layout‑Fehlern führen können.

## Schritt 3: Dokument mit konfigurierten Optionen laden (C# document processing)

Mit dem Warnsystem bereit ist das Laden des Dokuments unkompliziert. Übergeben Sie die `LoadOptions`‑Instanz dem `Document`‑Konstruktor, und Aspose.Words erledigt den Rest.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Warum das wichtig ist:**  
Das `LoadOptions`‑Objekt ist die Brücke zwischen der Rohdatei und der Warnungsinfrastruktur. Wenn Sie es weglassen, wird das Dokument stillschweigend geladen und fehlende Schriftarten werden ohne Hinweis ersetzt.

> **Randfall:** Einige Dokumente betten die exakt benötigten Schriftdateien ein. In diesem Szenario erscheint keine Warnung, weil Aspose.Words die eingebettete Schriftart findet. Der obige Code funktioniert weiterhin; Sie erhalten lediglich eine leere Konsolenausgabe.

## Schritt 4: Ausgabe überprüfen und häufige Fallstricke

Führen Sie das Programm in einer Eingabeaufforderung oder im Debugger Ihrer IDE aus. Wenn das Quelldokument eine Schriftart enthält, die nicht auf dem Rechner installiert ist (oder im benutzerdefinierten Schriftartenordner nicht verfügbar ist), sehen Sie Zeilen wie:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Wenn nichts ausgegeben wird, liegt entweder:

1. Alle Schriftarten wurden gefunden, **oder**  
2. Der `SubstitutionWarning`‑Handler wurde nicht korrekt angehängt (prüfen Sie Schritt 2 erneut).

### Warum treten Schriftart‑Ersetzungen auf?

- **Fehlende Systemschriftart:** Das Betriebssystem hat die angeforderte Schriftart nicht.  
- **Nicht unterstütztes Schriftformat:** Aspose.Words kann TrueType und OpenType lesen, aber nicht jedes proprietäre Format.  
- **Lizenzbeschränkungen:** Einige kommerzielle Schriftarten blockieren das Einbetten, wodurch ein Ersatz verwendet wird.

Das Verständnis des *Warum* hilft Ihnen zu entscheiden, ob Sie die fehlenden Schriftarten mit Ihrer Anwendung ausliefern oder das Styling des Dokuments anpassen.

## Bonus: Steuerung der Ersatzschriftart

Wenn Sie möchten, dass jede fehlende Schriftart zu einer bestimmten Familie (z. B. „Calibri“) zurückfällt, können Sie eine globale Ersetzungsregel festlegen:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Jetzt wird die Konsole Sie weiterhin warnen, aber das visuelle Ergebnis ist bei allen fehlenden Schriftarten konsistent.

---

## Zusammenfassung

- **Font-Warnungen aktivieren** durch Erstellen eines `LoadOptions` mit einer neuen `FontSettings`.  
- Binden Sie das `SubstitutionWarning`‑Event ein, um Echtzeit‑Warnungen zu erhalten, wenn eine Schriftart ersetzt wird.  
- Laden Sie Ihr Dokument mit den konfigurierten Optionen und speichern Sie optional als PDF, um den visuellen Effekt zu sehen.  
- Diagnostizieren Sie, warum eine Ersetzung stattgefunden hat und setzen Sie bei Bedarf eine bestimmte Ersatzschriftart durch.

Sie haben gerade ein Sicherheitsnetz zu Ihrem **Aspose.Words**‑Workflow hinzugefügt, das stille Layout‑Änderungen verhindert. Als Nächstes könnten Sie **Font‑Settings** wie `DefaultFontName` erkunden oder in **Document‑Rendering**‑Optionen eintauchen, um die PDF‑Ausgabe fein abzustimmen.

---

### Was Sie als Nächstes ausprobieren können?

- **Weitere FontSettings‑Funktionen erkunden**: `SetFontsFolder`, `LoadFontSources` und `DefaultFontName`.  
- **Warnungen mit Logging‑Frameworks kombinieren** (Serilog, NLog) für produktionsreife Diagnosen.  
- **Mit verschiedenen Dokumentformaten experimentieren** (`.doc`, `.rtf`, `.html`), um zu sehen, wie jedes fehlende Schriftarten handhabt.  

Haben Sie Fragen oder ein ungewöhnliches Szenario? Hinterlassen Sie unten einen Kommentar, und viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}