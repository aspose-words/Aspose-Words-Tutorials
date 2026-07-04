---
category: general
date: 2026-06-02
description: Lernen Sie, wie Sie variable Schriftgewichte in C# verwenden und das
  Schriftgewicht programmgesteuert festlegen, während Sie den Schriftdehnungs‑Code
  für dynamische Typografie ändern.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: de
og_description: Verwenden Sie variable Gewichtsschrift in C#, um die Schriftstärke
  programmgesteuert festzulegen und den Schriftdehnungs‑Code zu ändern, wodurch dynamische
  Typografie in Ihren Dokumenten ermöglicht wird.
og_title: Variable Gewichtsschrift in C# verwenden – Vollständige Anleitung
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Verwendung von variablen Gewichtsschriften in C# – Vollständiger Programmierleitfaden
url: /de/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Variable Weight Font in C# – Vollständiger Programmierleitfaden

Haben Sie jemals **variable weight font** in einem .NET‑Projekt verwenden müssen, waren sich aber nicht sicher, wie Sie Gewicht und Stretch auf Benutzereingaben reagieren lassen? Sie sind nicht allein. In vielen UI‑ oder Reporting‑Szenarien soll sich der Text anpassen – vielleicht eine leichte Überschrift, die beim Hover fett wird, oder ein Absatz, der zur Betonung seine Breite erweitert. Die gute Nachricht: Mit Aspose.Words können Sie **font weight programmatically setzen** und sogar **font stretch code** zur Laufzeit **ändern**.

In diesem Tutorial führen wir Sie Schritt für Schritt durch ein praktisches Beispiel, das genau zeigt, wie man eine variable‑weight‑Font lädt, ein benutzerdefiniertes Gewicht anwendet und die Stretch‑Einstellung anpasst – alles mit klarem C#‑Code, den Sie copy‑paste können. Am Ende haben Sie eine ausführbare Konsolen‑App, die ein PDF erzeugt, das den Effekt demonstriert.

---

## Was Sie benötigen

- **Aspose.Words for .NET** (v23.12 oder neuer). Die Bibliothek enthält vollständige Unterstützung für variable‑weight‑Fonts.
- Ein Ordner, der mindestens eine variable‑weight‑Font‑Datei enthält, z. B. *RobotoFlex‑Variable.ttf*. Sie können sie von Google Fonts herunterladen.
- .NET 6 SDK (oder eine aktuelle .NET‑Version) und eine IDE Ihrer Wahl.
- Grundkenntnisse in C# – nichts Aufwändiges, nur ein paar Code‑Zeilen.

Das ist alles. Keine zusätzlichen NuGet‑Pakete außer Aspose.Words und keine obskuren Konfigurationsdateien.

![Beispiel für variable weight font](https://example.com/variable-weight-sample.png "Demonstration der Verwendung von variable weight font")
*Alt-Text: Screenshot, der die Verwendung von variable weight font in einem erzeugten PDF‑Dokument zeigt.*

## Schritt 1: FontSettings einrichten und auf Ihren Schriftordner verweisen  

Zuerst muss Aspose.Words wissen, wo Ihre variable‑weight‑Fonts gespeichert sind. Das erreichen Sie, indem Sie ein `FontSettings`‑Objekt erstellen und eine `FolderFontSource` anhängen. Das `true`‑Flag weist die Engine an, auch Unterordner zu durchsuchen, was praktisch ist, wenn Sie mehrere Schriftfamilien zusammenhalten.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Warum das wichtig ist:** Ohne die Registrierung des Ordners greift Aspose.Words auf System‑Fonts zurück und ignoriert die in Ihrer benutzerdefinierten Font‑Datei eingebetteten variable‑weight‑Daten. Dieser Schritt ist die Grundlage für alles, was danach kommt.

## Schritt 2: FontSettings dem Dokument zuweisen  

Jetzt erstellen wir ein neues `Document` (oder laden ein bestehendes) und weisen ihm die gerade erstellten `FontSettings` zu. Diese Bindung stellt die variable‑weight‑Daten für jedes später hinzugefügte `Run` bereit.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Falls Sie bereits eine Vorlage haben – zum Beispiel eine Word‑Datei mit Platzhaltern – können Sie `new Document()` durch `new Document("Template.docx")` ersetzen. Die gleichen `FontSettings` werden dann angewendet.

## Schritt 3: Einen Run‑Text hinzufügen, der die Variable‑Weight‑Font verwendet  

Ein **Run** ist die kleinste Einheit der Textformatierung in Aspose.Words. Wir erstellen einen, fügen ihn in einen neuen Absatz ein und ändern später seine Schriftattribute.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

An diesem Punkt wird der Text mit der Standardschrift (in der Regel Times New Roman) gerendert. Die Magie tritt ein, sobald wir die variable‑weight‑Familie zuweisen.

## Schritt 4: Die Variable‑Weight‑Font‑Familie auswählen  

Hier verwenden wir tatsächlich **variable weight font**. Setzen Sie `Font.Name` auf den genauen Familiennamen, der in der variablen Font‑Datei definiert ist. Für Roboto Flex lautet der Name `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Falls Sie den Familiennamen nicht kennen, öffnen Sie die `.ttf`‑Datei in einem Font‑Viewer oder verwenden Sie die Methode `fontSettings.GetFonts()`, um die verfügbaren Familien aufzulisten.

## Schritt 5: Font Weight und Stretch programmgesteuert setzen  

Jetzt zum Kern des Tutorials: Wir **set font weight programmatically** und **change font stretch code**. Beide Eigenschaften akzeptieren Ganzzahlen, die der OpenType‑Spezifikation entsprechen.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Wählen Sie einen beliebigen Wert, den die variable Font unterstützt.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Der Standardwert ist 100 (Normal).

> **Pro‑Tipp:** Nicht jede variable Font stellt den gesamten Bereich bereit. Wenn Sie einen nicht unterstützten Wert setzen, wird die Engine auf das nächstgelegene verfügbare Gewicht oder Stretch begrenzen.

## Schritt 6: Dokument speichern und Ergebnis überprüfen  

Abschließend schreiben Sie das Dokument als PDF (oder DOCX) und öffnen es, um den Effekt zu sehen. PDF ist ein gutes Format für die visuelle Überprüfung, da das Rendering plattformübergreifend konsistent ist.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Wenn Sie *VariableWeightDemo.pdf* öffnen, sollten Sie den Text „Variable‑weight text demo“ in einer leichten, leicht erweiterten Version von Roboto Flex sehen. Ändern Sie `FontWeight` zu `700` und `FontStretch` zu `80` und führen Sie das Programm erneut aus – beobachten Sie, wie der Text fett und kompakter wird.

## Häufige Fragen & Sonderfälle  

### Was, wenn die Schriftart überhaupt nicht angezeigt wird?  

- **Missing FontSettings**: Stellen Sie sicher, dass `doc.FontSettings = fontSettings;` **vor** dem Hinzufügen von Text ausgeführt wird.
- **Incorrect family name**: Verwenden Sie `fontSettings.GetFonts()`, um alle gefundenen Familien aufzulisten; kopieren Sie den genauen String.
- **Unsupported weight/stretch**: Einige variable Fonts unterstützen nur einen Teilbereich des 100‑900 Gewichts. Verwenden Sie `run.Font.FontWeight = 400;` als sicheren Fallback.

### Kann ich das Gewicht ändern, nachdem das Dokument gespeichert wurde?  

Ja. Das `Run`‑Objekt ist veränderlich, sodass Sie `FontWeight` oder `FontStretch` jederzeit vor dem finalen `Save` anpassen können. Wenn Sie Gewichte dynamisch umschalten müssen (z. B. basierend auf Benutzereingaben), sollten Sie separate Runs für jeden Zustand erzeugen.

### Funktioniert das mit DOCX‑Ausgabe?  

Absolut. Die variable‑weight‑Metadaten werden im zugrunde liegenden OpenXML gespeichert, und moderne Word‑Versionen können sie interpretieren. Ältere Word‑Versionen könnten jedoch die Stretch‑Einstellung ignorieren.

## Vollständiges funktionierendes Beispiel  

Unten finden Sie ein komplettes Konsolenprogramm, das Sie sofort kompilieren und ausführen können. Es enthält alle erforderlichen `using`‑Direktiven, Fehlerbehandlung und Kommentare.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Erwartete Ausgabe:** Die Konsole gibt den Speicherort aus, und das erzeugte PDF zeigt den Text in einem leichten, erweiterten Stil – genau wie konfiguriert.

## Zusammenfassung  

Wir haben gezeigt, wie man **variable weight font** in C# mit Aspose.Words **verwendet**, wie man **font weight programmatically setzt** und den genauen **change font stretch code** zur Erweiterung oder Verdichtung der Glyphen anwendet. Die Schritte sind einfach: `FontSettings` konfigurieren, sie einem `Document` zuweisen, einen `Run` erstellen, die variable‑weight‑Familie auswählen und schließlich `FontWeight` sowie `FontStretch` anpassen.

## Was kommt als Nächstes?  

- **Dynamic UI integration**: Binden Sie dieselbe Logik in eine WinForms‑ oder WPF‑App ein, damit Benutzer Gewicht/Stretch über Schieberegler auswählen können.
- **Multiple runs**: Kombinieren Sie mehrere Runs mit unterschiedlichen Gewichten im selben Absatz für reichhaltige typografische Hierarchien.
- **Advanced axes**: Einige variable Fonts bieten zusätzliche Achsen (z. B. Schrägstellung, optische Größe). Verwenden Sie `run.Font.FontStyle` oder erkunden Sie `FontVariationSettings` für noch feinere Kontrolle.
- **Performance tips**: Cachen Sie die `FontSettings`‑Instanz beim Verarbeiten vieler Dokumente, um wiederholte Ordnerscans zu vermeiden.

Experimentieren Sie gern – tauschen Sie *Roboto Flex* gegen *Inter Variable* oder eine andere OpenType‑Variable‑Font aus und beobachten Sie, wie Ihre Dokumente ein neues Maß an visueller Flexibilität erhalten. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Verwenden von Schriftart vom Zielgerät](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Verwenden von Schriftart vom Zielgerät](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Verwenden von Schriftart vom Zielgerät](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}