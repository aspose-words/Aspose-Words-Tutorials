---
category: general
date: 2026-08-10
description: Formatieren Sie den Fußnotentrennstrich in C# mit Aspose.Words, um Fuß‑
  und Endnotenlinien anzupassen. Lernen Sie die Fußnotenformatierung in C# in wenigen
  Minuten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: de
lastmod: 2026-08-10
og_description: Formatieren Sie den Fußnotentrennzeichen in C# mit Aspose.Words. Folgen
  Sie diesem Tutorial, um Fußnoten‑ und Endnotentrennzeichen schnell und zuverlässig
  zu formatieren.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Fußnotentrennzeichen in C# formatieren – vollständiger Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Fußnotentrennzeichen in C# mit Aspose.Words formatieren
url: /de/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fußnotentrennzeichen in C# mit Aspose.Words formatieren

Wenn Sie **Fußnotentrennzeichen** in einem Word‑Dokument formatieren müssen, zeigt Ihnen diese Anleitung, wie Sie das mit Aspose.Words für .NET erledigen. Sie sehen ein vollständiges, ausführbares Beispiel, das die Ausrichtung und Farbe des Trennabsatzes ändert, und lernen, wie Sie dieselbe Technik auf Endnotentrennzeichen anwenden.

Das Tutorial deckt jeden Schritt ab – vom Laden der Quelldatei bis zum Speichern des modifizierten Dokuments – sodass Sie den Code einfach in Ihr eigenes Projekt kopieren können, ohne weitere Recherche.

## Was Sie benötigen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz (die kostenlose Testversion funktioniert für Evaluierungen)
* Eine Word‑Datei, die mindestens eine Fuß‑ oder Endnote enthält (z. B. `Footnotes.docx`)
* Visual Studio 2022 oder eine andere C#‑IDE Ihrer Wahl

Wenn diese Dinge bereitstehen, können Sie sich auf die **C#‑Fußnoten‑Formatierung** konzentrieren, anstatt Zeit mit der Umgebungseinrichtung zu verlieren.

## Schritt 1: Das Dokument laden, das Fuß‑ und Endnoten enthält

Der erste Vorgang besteht darin, ein `Document`‑Objekt zu erstellen, das auf Ihre Quelldatei verweist. Aspose.Words liest das gesamte DOCX‑Paket in den Speicher und gibt Ihnen vollen Zugriff auf Fuß‑ und Endnoten‑Knoten.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Warum das wichtig ist*: Das Laden des Dokuments ist die Voraussetzung für jede Manipulation. Wenn der Dateipfad falsch ist, wirft Aspose.Words eine `FileNotFoundException`, also prüfen Sie den Pfad, bevor Sie fortfahren.

## Schritt 2: Die Trenn‑ und Fortsetzungs‑Trenn‑Knoten abrufen

Fuß‑ und Endnotentrenner werden als spezielle Knoten innerhalb der `Footnotes`‑ bzw. `Endnotes`‑Sammlungen gespeichert. Jede Sammlung stellt die Eigenschaften `Separator` und `ContinuationSeparator` bereit, die eine `Node`‑Referenz zurückgeben.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Warum das wichtig ist*: Der `Separator`‑Knoten stellt die Linie dar, die den Haupttext visuell vom Fußnoten‑Block trennt. Durch das Abrufen einer Referenz können Sie das Absatzformat, die Schriftart oder sogar den gesamten Knoten ändern.

## Schritt 3: Das visuelle Aussehen des Fußnotentrennzeichens ändern

In den meisten Word‑Dokumenten ist das Trennzeichen ein einzelner Absatz, der einen Bindestrich oder ein Sternchen enthält. Der untenstehende Code prüft, ob das Trennzeichen ein `Paragraph` ist und zentriert es gegebenenfalls und ändert die Textfarbe zu Grau.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Das Fortsetzungs‑Trennzeichen stylen (optional)

Das Fortsetzungs‑Trennzeichen erscheint, wenn eine Fußnote über mehrere Seiten hinweg reicht. Sie können es ähnlich stylen:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Warum das wichtig ist*: Das Ausrichten des Trennzeichens verbessert die Lesbarkeit, und das Ändern der Farbe hebt es vom normalen Absatztext ab. Sie können `ParagraphAlignment.Center` durch `Left` oder `Right` ersetzen, um den Gestaltungsrichtlinien Ihres Dokuments zu entsprechen.

## Schritt 4: Das modifizierte Dokument speichern

Nachdem Sie den gewünschten Stil angewendet haben, schreiben Sie das Dokument zurück auf die Festplatte. Sie können die Originaldatei überschreiben oder eine neue Version erstellen.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Wenn Sie `Footnotes_Styled.docx` in Microsoft Word öffnen, erscheint das Fußnotentrennzeichen zentriert und grau, genau wie im Code angegeben.

## Erweiterte Varianten

### Das Endnotentrennzeichen formatieren

Verwendet Ihr Dokument auch Endnoten, können Sie dieselbe Logik auf die `Endnotes`‑Sammlung anwenden:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Einen eigenen String für das Trennzeichen verwenden

Manchmal soll das Trennzeichen aus einer Reihe von Sternchen (`***`) bestehen. Ersetzen Sie die vorhandenen Runs durch einen neuen Run:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Dokumente ohne Trennzeichen‑Knoten behandeln

Ein seltener Sonderfall ist ein Dokument, das den Trennzeichen‑Knoten weggelassen hat (z. B. weil der Autor ihn gelöscht hat). In diesem Szenario gibt `document.Footnotes.Separator` `null` zurück. Schützen Sie sich dagegen:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Häufige Stolperfallen und wie man sie vermeidet

| Stolperfalle | Warum das passiert | Lösung |
|--------------|--------------------|--------|
| **Separator ist kein `Paragraph`** | Einige Word‑Vorlagen verwenden eine `Table` oder ein `Shape` als Trennzeichen. | Prüfen Sie den Knotentyp mit `is Paragraph`, bevor Sie casten. |
| **`Runs`‑Sammlung ist leer** | Das Trennzeichen kann ein leerer Absatz sein. | Stellen Sie sicher, dass `Runs.Count > 0` ist, bevor Sie auf `Runs[0]` zugreifen. |
| **Lizenz nicht angewendet** | Ohne Lizenz fügt Aspose.Words ein Wasserzeichen ein und kann API‑Nutzungen einschränken. | Rufen Sie zu Beginn Ihres Programms `License license = new License(); license.SetLicense("Aspose.Words.lic");` auf. |
| **Speichern in einem schreibgeschützten Ordner** | Die `Save`‑Methode wirft eine `UnauthorizedAccessException`. | Stellen Sie sicher, dass das Zielverzeichnis Schreibrechte hat. |

Das frühzeitige Behandeln dieser Probleme verhindert Laufzeit‑Exceptions und sorgt für ein reibungsloses **Fußnotentrennzeichen‑Ändern**‑Erlebnis.

## Vollständiges, ausführbares Beispiel

Unten finden Sie eine eigenständige Konsolenanwendung, die jeden oben besprochenen Schritt demonstriert. Kopieren Sie den Code in ein neues .NET‑Konsolenprojekt, passen Sie die Dateipfade an und führen Sie ihn aus.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Erwartetes Ergebnis**  

Wenn Sie `Footnotes_Styled.docx` öffnen:

* Das Fußnotentrennzeichen wird zentriert unter dem Haupttext angezeigt.
* Seine Farbe erscheint als helles Grau, wodurch es sich visuell abhebt.
* Enthält das Dokument Endnoten, werden deren Trennzeichen ebenfalls zentriert und grau (oder Schiefer) dargestellt.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}