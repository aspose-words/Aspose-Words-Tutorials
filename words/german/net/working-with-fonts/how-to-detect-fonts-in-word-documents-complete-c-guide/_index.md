---
category: general
date: 2026-02-24
description: Wie man Schriftarten in einem Word‑Dokument mit Aspose.Words erkennt.
  Erfahren Sie, wie Sie einen Callback festlegen und ein Word‑Dokument mit vollständigem
  Codebeispiel laden.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: de
og_description: Wie man Schriftarten in einem Word-Dokument mit einem Warn‑Callback
  erkennt. Dieser Leitfaden zeigt, wie man den Callback festlegt und ein Word‑Dokument
  mit Aspose.Words lädt.
og_title: Wie man Schriftarten in Word‑Dokumenten erkennt – Schritt‑für‑Schritt C#‑Tutorial
tags:
- C#
- Aspose.Words
- Document Processing
title: Wie man Schriftarten in Word-Dokumenten erkennt – Vollständiger C#‑Leitfaden
url: /de/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Schriftarten in Word-Dokumenten erkennt – Vollständiger C# Leitfaden

Schon einmal überlegt, **wie man Schriftarten** erkennt, die fehlen, wenn Sie eine Word‑Datei laden? Vielleicht sind Sie auf ein Dokument gestoßen, das im Editor gut aussieht, aber das von Ihnen erzeugte PDF tauscht im Hintergrund ein paar Schriftarten aus. Das ist ein klassisches Symptom für Schriftart‑Substitution, und ein frühes Erkennen kann Sie vor unschönen Layout‑Überraschungen bewahren.

In diesem Tutorial führen wir Sie durch eine praktische Lösung: Wir verwenden **Aspose.Words**, um ein `.docx` zu laden, hängen einen Warn‑Callback an und zeigen **wie man den Callback setzt**, der jede Schriftart‑Substitution meldet. Am Ende wissen Sie nicht nur **wie man Schriftarten** programmgesteuert erkennt, sondern verstehen auch **wie man den Callback** korrekt einstellt und **Word‑Dokument lädt** sicher – alles in einem einzigen, ausführbaren C#‑Beispiel.

> **Was Sie erhalten**
> * Ein vollständiges, copy‑paste‑bereites Code‑Beispiel  
> * Schritt‑für‑Schritt‑Erklärung jeder Zeile  
> * Tipps zum Umgang mit Sonderfällen wie mehreren fehlenden Schriftarten oder benutzerdefinierten Schriftordnern  
> * Erwartete Konsolenausgabe, damit Sie die Funktionsweise überprüfen können

---

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Core)  
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)  
- Eine Word‑Datei, die absichtlich eine Schriftart referenziert, die Sie nicht installiert haben (z. B. `MissingFont.docx`)  
- Visual Studio, Rider oder ein beliebiger Editor Ihrer Wahl

Keine weiteren Bibliotheken werden benötigt; alles andere ist Teil der Standard‑.NET‑Laufzeit.

---

## Wie man Schriftarten in einem Word‑Dokument erkennt

### Schritt 1: Load‑Optionen erstellen und einen Warn‑Callback anhängen

Das Erste, was wir tun, ist Aspose.Words mitzuteilen, dass wir über alle Probleme, die beim Laden der Datei auftreten, benachrichtigt werden möchten. Hier kommt **wie man den Callback setzt** ins Spiel.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Warum das wichtig ist:**  
`LoadOptions` ist das Tor zur Anpassung des Ladevorgangs. Indem wir einer Instanz von `FontWarningCollector` die Eigenschaft `WarningCallback` zuweisen, ruft Aspose.Words unsere `Warning`‑Methode jedes Mal auf, wenn es eine fehlende Schriftart durch eine Ersatzschriftart ersetzt. Das ist das Kernstück von **wie man Schriftarten** erkennt, die auf dem Rechner nicht vorhanden sind.

### Schritt 2: Die LoadOptions‑Instanz vorbereiten

Jetzt instanziieren wir `LoadOptions` und verbinden unseren Callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro‑Tipp:** Falls Sie steuern müssen, *wo* Aspose nach Ersatzschriftarten sucht, können Sie hier auch `loadOptions.FontSettings` setzen. Das ist nützlich, wenn Sie einen privaten Schriftordner auf dem Server haben.

### Schritt 3: Das Word‑Dokument laden

Mit den vorbereiteten Optionen **laden wir schließlich das Word‑Dokument**. Dies ist der Moment, in dem Aspose das DOCX parst und, falls Schriftarten fehlen, unser Callback ausgelöst wird.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Was passiert im Hintergrund?**  
Aspose.Words liest die XML‑Teile des DOCX, löst jede `<w:font>`‑Referenz auf und prüft die System‑Schriftartensammlung. Wann immer eine Referenz nicht erfüllt werden kann, ersetzt es die erste passende Ersatzschriftart und erzeugt eine `FontSubstitution`‑Warnung.

### Schritt 4: Die Ausgabe überprüfen

Führen Sie das Programm aus und beobachten Sie die Konsole. Für jede fehlende Schriftart sehen Sie eine Zeile wie:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Enthält das Dokument keine fehlenden Schriftarten, bleibt die Konsole still – das bedeutet, **wie man Schriftarten** hat keine Treffer ergeben.

### Schritt 5: Vollständiges funktionierendes Beispiel (Konsolen‑App)

Unten finden Sie ein eigenständiges `Program.cs`, das Sie in ein neues Konsolen‑Projekt einfügen können. Es enthält alle besprochenen Bausteine sowie einen kleinen Helfer, um das Konsolen‑Fenster beim Debuggen offen zu halten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Erwartete Konsolenausgabe** (example):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Wenn Sie `MissingFont.docx` durch eine Datei ersetzen, die nur installierte Schriftarten verwendet, sehen Sie nur die Zeile „Press any key…“ – das bestätigt, dass die Erkennungs‑Logik wie vorgesehen funktioniert.

---

## Häufige Fragen & Sonderfälle

### Was tun, wenn ich *alle* Warnungen erfassen muss, nicht nur Schriftart‑Substitutionen?

Entfernen Sie einfach die Guard‑Anweisung `if (info.Type == WarningType.FontSubstitution)`. Das `WarningInfo`‑Objekt enthält ein `Type`‑Enum, das Sie für andere Szenarien (z. B. `DocumentStructure`, `ImageLoading`) abfragen können.

### Kann ich Warnungen in eine Datei statt in die Konsole protokollieren?

Absolut. Ersetzen Sie `Console.WriteLine` durch einen Aufruf eines beliebigen Logging‑Frameworks (`Serilog`, `NLog` usw.). Der Callback läuft im selben Thread, der das Dokument lädt, also stellen Sie sicher, dass Ihr Logger thread‑sicher ist.

### Wie verhält sich das in einer Web‑Anwendung?

In ASP.NET Core würden Sie typischerweise eine Singleton‑Implementierung von `IWarningCallback` injizieren und sie über `LoadOptions` übergeben. Denken Sie daran, nicht direkt in den Response‑Stream zu schreiben – loggen Sie stattdessen in eine Datenbank oder eine In‑Memory‑Collection, die Sie später über einen API‑Endpoint bereitstellen können.

### Was ist mit benutzerdefinierten Schriftarten in einem Nicht‑System‑Ordner?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Jetzt durchsucht Aspose.Words `C:\MyCustomFonts`, bevor es auf die OS‑Schriftarten zurückgreift, wodurch die Anzahl der Substitutions‑Warnungen reduziert wird.

---

## Visuelle Zusammenfassung

![Schriftarten‑Warnungs‑Callback in Aspose.Words](/images/font-warning-callback.png "Wie man Schriftarten mit einem Warn‑Callback erkennt")

*Der Screenshot zeigt die Konsolenausgabe, wenn eine fehlende Schriftart substituiert wird. Der Alt‑Text enthält das primäre Schlüsselwort für SEO.*

---

## Fazit

Sie haben nun ein solides, produktionsreifes Muster für **wie man Schriftarten** in jeder Word‑Datei zu erkennen, die Sie mit Aspose.Words laden. Durch **wie man den Callback setzt** erhalten Sie Echtzeit‑Einblick in fehlende oder substituierte Schriftarten, und Sie haben gelernt, wie man **Word‑Dokument lädt** auf die richtige Weise, während Ihr Code sauber und wartbar bleibt.

Nächste Schritte? Versuchen Sie, den Callback zu erweitern, um Warnungen in einer Liste zu sammeln und sie dann in einer UI oder einem automatisierten Bericht anzuzeigen. Sie können auch `FontSettings.SubstitutionSettings` erkunden, um zu steuern, *welche* Schriftarten als Ersatz gewählt werden.

Fühlen Sie sich frei zu experimentieren – tauschen Sie das Dokument aus, fügen Sie weitere fehlende Schriftarten hinzu oder integrieren Sie die Logik in eine größere Dokument‑Verarbeitungspipeline. Wenn Sie auf Probleme stoßen, hinterlassen Sie einen Kommentar unten oder kontaktieren Sie mich auf GitHub.

Viel Spaß beim Coden und möge Ihr Dokument immer mit den erwarteten Schriftarten dargestellt werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}