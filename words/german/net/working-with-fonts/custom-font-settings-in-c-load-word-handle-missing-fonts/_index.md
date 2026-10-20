---
category: general
date: 2026-03-08
description: Benutzerdefinierte Schriftarteinstellungen ermöglichen es Ihnen, Schriftarteinstellungen
  festzulegen, Word‑Dokumente sicher zu laden und fehlende Schriften mit Aspose.Words
  zu verarbeiten.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: de
og_description: Benutzerdefinierte Schriftarteinstellungen ermöglichen das Festlegen
  von Schriftarten, das sichere Laden von Word‑Dokumenten und das Behandeln fehlender
  Schriften mit Aspose.Words.
og_title: Benutzerdefinierte Schriftarteinstellungen in C# – Word laden und fehlende
  Schriften behandeln
tags:
- Aspose.Words
- C#
- Font Management
title: Benutzerdefinierte Schriftarteinstellungen in C# – Word laden & fehlende Schriften
  behandeln
url: /de/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Benutzerdefinierte Schriftarteinstellungen in C# – Word laden & fehlende Schriften behandeln

Haben Sie sich jemals gefragt, wie **benutzerdefinierte Schriftarteinstellungen** funktionieren, wenn eine Word‑Datei Schriften referenziert, die Sie nicht installiert haben? Das ist ein häufiges Problem – Ihr Dokument sieht auf einem Rechner gut aus, und plötzlich wechselt jeder Absatz auf einem anderen Rechner zu einer Ersatzschrift.  

Die gute Nachricht? Mit Aspose.Words können Sie **Schriftarteinstellungen festlegen**, **Word‑Dokument**‑Inhalte **laden** und **fehlende Schriften behandeln** – alles in einem übersichtlichen Ablauf. Im Folgenden finden Sie ein vollständiges, sofort ausführbares Beispiel, das genau zeigt, wie das geht, sowie das „Warum“ hinter jedem Schritt.

## Was Sie lernen werden

In diesem Leitfaden behandeln wir:

* Erstellen eines `LoadOptions`‑Objekts und Anhängen einer `FontSettings`‑Instanz.  
* Registrieren eines Warn‑Callbacks, damit Sie sehen können, welche Schriften ersetzt werden.  
* Laden einer DOCX‑Datei, bei der Schriften fehlen könnten, und Ausgeben der Ersetzungsdetails in die Konsole.  

Am Ende können Sie Ihre C#‑App mit Zuversicht ausliefern, weil Sie wissen, dass jedes Szenario mit fehlenden Schriften protokolliert wird und später behoben werden kann.

> **Voraussetzung:** Aspose.Words für .NET (v23.12 oder neuer) über NuGet installiert und grundlegende Kenntnisse von C#‑Konsolenanwendungen.

---

## Benutzerdefinierte Schriftarteinstellungen – LoadOptions konfigurieren

Das Erste, was Sie benötigen, ist ein `LoadOptions`‑Objekt. Dieses teilt Aspose.Words mit, wie die eingehende Datei behandelt werden soll. Durch das Zuweisen einer neuen `FontSettings`‑Instanz geben wir der Bibliothek einen Ort, an dem sie nach benutzerdefinierten Schriften suchen kann.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Warum das wichtig ist:**  
Wenn Sie `FontSettings` weglassen, greift Aspose.Words auf die standardmäßige Schriftartensammlung des Systems zurück. Das bedeutet, dass jede fehlende Schriftstillschweigend ersetzt wird und Sie nicht wissen, welche ausgetauscht wurden. Durch das Erstellen eines expliziten `FontSettings`‑Containers erhalten Sie die volle Kontrolle über den Suchvorgang.

---

## Schriftarteinstellungen auf LoadOptions setzen

Jetzt, wo wir ein `FontSettings`‑Objekt haben, fragen Sie sich vielleicht, wohin es zeigen soll. Typischerweise fügen Sie einen Ordner hinzu, der die Schriften enthält, die Sie mit Ihrer Anwendung ausliefern:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Wenn Sie keinen privaten Ordner haben, können Sie diesen Block weglassen – Aspose.Words wird fehlende Schriften weiterhin über den Warn‑Callback melden.*

**Pro‑Tipp:** Verwenden Sie das Flag `recursive: true`, wenn Ihre Schriften über Unterordner verteilt sind. Das erspart Ihnen das manuelle Hinzufügen jedes Pfads.

---

## Word‑Dokument mit benutzerdefinierten Schriftarteinstellungen laden

Mit den vorbereiteten Optionen ist das Laden des Dokuments ein Kinderspiel. Der `Document`‑Konstruktor akzeptiert den Dateipfad und die `LoadOptions`, die wir gerade erstellt haben.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Was im Hintergrund passiert:**  
Aspose.Words analysiert das DOCX, prüft jede `<w:font>`‑Referenz und konsultiert die von Ihnen bereitgestellten `FontSettings`. Wird eine Schrift nicht gefunden, wird eine Warnung vom Typ `FontSubstitution` ausgelöst. Unser benutzerdefinierter Handler (im Folgenden gezeigt) fängt diese Warnungen ab.

---

## Fehlende Schriften mit Warn‑Callback behandeln

Das `IWarningCallback`‑Interface ermöglicht es Ihnen, auf alle beim Laden auftretenden Probleme zu reagieren. Die Implementierung ist unkompliziert:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Wenn das Dokument geladen ist, erzeugt jede fehlende Schrift eine Zeile wie:

```
Font substituted: Arial -> Liberation Sans
```

**Warum Sie das protokollieren sollten:**  
In der Produktion können Sie diese Meldungen in eine Datei oder ein Telemetriesystem umleiten, sodass Sie leicht erkennen, welche Schriften Sie bündeln oder lizenzieren müssen.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie ein eigenständiges Konsolenprogramm, das alles zusammenführt. Kopieren Sie es in ein neues .NET‑Core‑Konsolenprojekt und klicken Sie auf **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Erwartete Ausgabe** (angenommen, `input.docx` verwendet eine Schrift, die Sie nicht haben):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Wenn alle Schriften vorhanden sind, sehen Sie nur die abschließende Bestätigungszeile.

---

## Häufige Fragen & Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Was ist, wenn ich die fehlenden Schriften in das PDF einbetten muss?** | Nach dem Laden rufen Sie `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` auf und aktivieren das Einbetten mit `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Kann ich die Warnungen unterdrücken, anstatt sie zu protokollieren?** | Ja – setzen Sie `loadOptions.WarningCallback = null;` oder implementieren Sie den Callback, um Nicht‑Schrift‑Warnungen zu ignorieren. |
| **Funktioniert das mit `.doc`‑ und `.rtf`‑Dateien?** | Absolut. Das gleiche `LoadOptions`‑Objekt gilt für jedes von Aspose.Words unterstützte Format. |
| **Ist der Callback thread‑sicher?** | Der Callback läuft im selben Thread, der das Dokument lädt, sodass Sie sicher in die Konsole schreiben können. Für Mehr‑Thread‑Szenarien verwenden Sie eine nebenläufige Sammlung oder ein Logging‑Framework. |

---

## Pro‑Tipps & Fallstricke

* **Pro‑Tipp:** Wenn Sie eine Schrift ausliefern, die auf dem Zielrechner nicht installiert ist, fügen Sie sie dem Ordner hinzu, den Sie an `SetFontsFolder` übergeben. Das garantiert ein deterministisches Rendering.
* **Achten Sie auf Lizenzierung:** Einige Schriften benötigen kommerzielle Lizenzen für das Einbetten. Überprüfen Sie stets die EULA der Schrift, bevor Sie sie bündeln.
* **Hinweis zur Leistung:** Das Laden großer Schriftbibliotheken kann die Dokumenten‑Analyse verlangsamen. Halten Sie den Ordner schlank – nur die tatsächlich benötigten Schriften einbinden.
* **Sonderfall:** Wenn ein Dokument eine Schrift über ihren *PostScript‑Namen* statt des Familiennamens referenziert, löst Aspose.Words sie trotzdem auf, solange die Schriftdatei im Suchpfad vorhanden ist.

---

## Fazit

Sie haben nun ein vollständiges, produktionsreifes Muster für die Verwendung von **benutzerdefinierten Schriftarteinstellungen** in C#. Durch das Konfigurieren von `LoadOptions`, das Registrieren eines Warn‑Callbacks und optional das Verweisen auf einen privaten Schriftordner können Sie **Schriftarteinstellungen festlegen**, **Word‑Dokument**‑Inhalte zuverlässig **laden**.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}