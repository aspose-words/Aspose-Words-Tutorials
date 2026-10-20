---
category: general
date: 2026-04-05
description: Aspose-Schriftart-Substitutionsleitfaden zum Erkennen fehlender Schriftarten
  beim Laden eines Word-Dokuments. Erfahren Sie, wie Sie Schriftarteinstellungen konfigurieren
  und fehlende Schriftarten effizient handhaben.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: de
og_description: Aspose-Schriftartenersatzleitfaden zum Erkennen fehlender Schriftarten
  beim Laden eines Word-Dokuments. Erfahren Sie, wie Sie Schriftarteinstellungen konfigurieren
  und fehlende Schriftarten effizient handhaben.
og_title: Aspose-Schriftartenersetzung – Fehlende Schriftarten in Word-Dokumenten
  erkennen
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose-Schriftarten-Substitution – Fehlende Schriftarten in Word-Dokumenten
  erkennen
url: /de/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Fehlende Schriftarten in Word-Dokumenten erkennen

Sind Sie schon einmal auf eine Word‑Datei gestoßen, die auf einem Rechner perfekt aussieht, auf einem anderen jedoch merkwürdige Schriftarten‑Änderungen zeigt? Das ist das klassische **aspose font substitution**‑Problem und bedeutet in der Regel, dass einige Schriftarten auf dem Zielsystem fehlen. In diesem Tutorial zeigen wir Ihnen Schritt für Schritt, wie Sie **fehlende Schriftarten** erkennen, wenn Sie ein **Word‑Dokument laden**, wie Sie **Schrifteinstellungen konfigurieren** und was Sie tun können, um **fehlende Schriftarten** elegant zu **handhaben**.

Wir gehen ein komplettes, ausführbares C#‑Beispiel durch, erklären, warum jede Zeile wichtig ist, und zeigen Ihnen sogar die Konsolenausgabe, die Sie erwarten sollten. Am Ende können Sie Schriftarten‑Substitutionen im Moment des Ladens eines Dokuments erkennen – ohne Rätselraten.

## Was Sie lernen werden

- Wie Sie den Diagnose‑Collector von Aspose.Words für Schriftarten‑Warnungen aktivieren.  
- Den genauen Code, der benötigt wird, um ein **Word‑Dokument zu laden** mit benutzerdefinierten **Schrifteinstellungen**.  
- Wie Sie über `WarningInfo`‑Objekte iterieren, um jede ersetzte Schriftart aufzulisten.  
- Tipps zum Unterdrücken unerwünschter Warnungen oder zum Bereitstellen von Ersatzschriftarten.  
- Ein sofort ausführbares Beispiel, das Sie in Visual Studio kopieren‑und‑einfügen können.

### Voraussetzungen

- .NET 6.0 oder höher (die API funktioniert genauso unter .NET Framework).  
- Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`).  
- Eine Word‑Datei, die eine Schriftart referenziert, die Sie nicht installiert haben (z. B. `MissingFont.docx`).  

Wenn Sie das haben, legen wir los.

## Schritt 1 – Diagnose‑Collector aktivieren (Schrifteinstellungen konfigurieren)

Zuerst: Aspose.Words zeichnet Schriftarten‑Substitutions‑Warnungen nur auf, wenn Sie es ihm sagen. Das geschieht, indem Sie ein `FontSettings`‑Objekt erstellen und es einer `LoadOptions`‑Instanz zuweisen. Denken Sie dabei an das Einschalten der „Debug‑Lichter“ für die Schriftarten‑Verarbeitung.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Warum?**  
Ohne ein `FontSettings`‑Objekt bleibt der Warn‑Collector stumm, und Sie erfahren nie, welche Schriftarten ausgetauscht wurden. Durch die leere Initialisierung lassen wir Aspose die Standardsystem‑Schriftarten verwenden *und* jede Substitution nachverfolgen.

> **Pro‑Tipp:** Wenn Sie wissen, dass ein bestimmter Ordner Unternehmens‑Schriftarten enthält, verweisen Sie `FontSettings` mit `SetFontsFolder("path")` darauf. Das kann die Anzahl der Fehlermeldungen reduzieren.

## Schritt 2 – Dokument mit den konfigurierten Optionen laden (Word‑Dokument laden)

Jetzt, wo der Collector aktiv ist, laden Sie Ihre `.docx`‑Datei mit denselben `LoadOptions`. In diesem Moment scannt Aspose das Dokument, sucht jede Schriftarten‑Referenz und entscheidet, ob eine Substitution nötig ist.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Warum ist das wichtig?**  
Wenn Sie einfach `new Document("MissingFont.docx")` aufrufen, gelten die Standardeinstellungen *und* die Warnliste bleibt leer. Das Übergeben von `loadOptions` stellt sicher, dass der Diagnose‑Collector in die Ladeschleife eingebunden ist.

## Schritt 3 – Schriftarten‑Substitutions‑Warnungen abrufen und anzeigen (fehlende Schriftarten erkennen)

Nachdem das Dokument im Speicher ist, speichert Aspose alle Warnungen in `document.WarningCallback.Warnings`. Durchlaufen Sie diese Sammlung, filtern Sie nach `WarningType.FontSubstitution` und geben Sie die Beschreibung aus. Jede Beschreibung sagt Ihnen, welche Schriftart fehlte und welche stattdessen verwendet wurde.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Erwartete Konsolenausgabe**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Das Ergebnis zeigt genau, welche Schriftarten auf dem Rechner, auf dem der Code läuft, fehlen. Sie können nun entscheiden, ob Sie die fehlenden Schriftarten installieren, sie ins Dokument einbetten oder die Substitution beibehalten.

![Konsolenausgabe, die Aspose‑Schriftarten‑Substitutions‑Warnungen zeigt](/images/aspose-font-substitution-console.png)

*Bild‑Alt‑Text:* aspose font substitution – console output listing substituted fonts

## Schritt 4 – Optional: Substitutions‑Verhalten anpassen (fehlende Schriftarten handhaben)

Manchmal wollen Sie nicht nur wissen, *dass* eine Substitution stattgefunden hat – Sie wollen steuern, *wie* sie erfolgt. Aspose.Words lässt Sie eine benutzerdefinierte `IFontSubstitutionRule` registrieren. Das folgende Beispiel zwingt jede fehlende Schriftart, auf `Tahoma` zurückzugreifen.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Wann würden Sie das verwenden?**  
Wenn Sie PDFs für einen Web‑Service erzeugen und wissen, dass jeder Client `Tahoma` rendern kann, garantiert das Erzwingen des Fallbacks visuelle Konsistenz, ohne Dutzende von Schriftdateien ausliefern zu müssen.

## Vollständiges funktionierendes Beispiel (Alle Schritte kombiniert)

Hier ist das gesamte Programm, das Sie in ein neues Konsolen‑Projekt einfügen können. Es kompiliert sofort, vorausgesetzt, Sie haben das Aspose.Words‑NuGet‑Paket installiert.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Starten Sie das Programm, beobachten Sie die Konsole, und Sie sehen jedes Ereignis einer fehlenden Schriftart. Anschließend können Sie entscheiden, ob Sie die fehlenden Schriftarten installieren, einbetten oder das Fallback beibehalten.

## Häufig gestellte Fragen

**F: Funktioniert das mit PDF‑Konvertierung?**  
Ja. Wenn Sie später `doc.Save("output.pdf")` aufrufen, werden die während des Ladens substituierten Schriftarten in das PDF eingebettet. Das frühzeitige Abfangen der Warnungen hilft, überraschende Schriftarten‑Änderungen im finalen PDF zu vermeiden.

**F: Was, wenn ich viele Dokumente verarbeiten muss?**  
Packen Sie die Ladelogik in einen `try‑catch`‑Block und verwenden Sie eine einzige `FontSettings`‑Instanz für mehrere Dokumente. Das reduziert den Overhead und hält den Warn‑Collector für jede Datei aktiv.

**F: Kann ich die Warnungen komplett unterdrücken?**  
Sie können `loadOptions.WarningCallback = null;` setzen, bevor Sie laden, aber dann verlieren Sie die Möglichkeit, **fehlende Schriftarten zu erkennen** – was in den meisten Fällen nicht gewünscht ist.

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **aspose font substitution** zu meistern: den Diagnose‑Collector aktivieren, ein Word‑Dokument mit benutzerdefinierten **Schrifteinstellungen** laden, die Liste fehlender Schriftarten extrahieren und sogar die Standard‑Substitutions‑Regel überschreiben, um **fehlende Schriftarten** nach Ihren Vorgaben zu **handhaben**. Mit nur wenigen Zeilen C# erhalten Sie volle Transparenz über Schriftarten‑Probleme, die sonst hinter subtilen Layout‑Änderungen verborgen bleiben.

Nächste Schritte? Versuchen Sie, die Original‑Schriftarten mit `FontSettings.SetFontsFolder` ins Dokument einzubetten oder erkunden Sie `FontSourceBase`, um Schriftarten aus einer Datenbank zu laden. Sie können auch mit der `Document.BuiltInStyle`‑Sammlung experimentieren, um zu sehen, wie Stil‑ebene Schriftarten‑Änderungen sich auswirken.

Haben Sie weitere Fragen zu Aspose.Words oder zum Schriftarten‑Management? Hinterlassen Sie einen Kommentar, stöbern Sie in der offiziellen Aspose‑Dokumentation oder starten Sie ein neues Projekt und probieren Sie den obigen Code aus. Viel Spaß beim Coden, und möge Ihr Dokument stets exakt wie beabsichtigt dargestellt werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}