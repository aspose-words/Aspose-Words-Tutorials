---
category: general
date: 2026-10-13
description: Wie man den Fußnotentrennzeichen in einem Word-Dokument mit Aspose.Words
  ändert. Erfahren Sie, wie man die Schriftfarbe in einem Word-Dokument programmgesteuert
  ändert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: de
lastmod: 2026-10-13
og_description: Wie man den Fußnotentrennzeichen in einem Word‑Dokument mit Aspose.Words
  ändert. Dieses Tutorial zeigt, wie man die Schriftfarbe in einem Word‑Dokument mit
  C# ändert.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Wie man die Fußnotentrennlinie in einem Word‑Dokument ändert – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Wie man den Fußnotenseparator ändert und dessen Stil in einem Word‑Dokument
  anpasst
url: /de/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man den Fußnotentrennzeichen ändert und seinen Stil in einem Word‑Dokument anpasst

Wenn Sie **how to change footnote separator** in einem Word‑Dokument benötigen, bietet Ihnen dieser Leitfaden eine vollständige, sofort einsatzbereite Lösung. Mit Aspose.Words für .NET können Sie auch **change font color in Word document** Elemente wie Fuß‑ und Endnoten‑Trennzeichen ändern, sodass die endgültige Datei Ihrer Marken‑ oder Stilrichtlinie entspricht.

Dokumentautoren fragen häufig: *Warum sieht das Standard‑Fußnotentrennzeichen schlicht aus, und wie kann ich es hervorheben?* Die Antwort lautet, direkt auf die Trennzeichen‑Absatzobjekte zuzugreifen, deren Schriftarteigenschaften anzupassen und das Ergebnis zu speichern. Dieses Tutorial führt Sie durch jeden Schritt, vom Laden einer .docx‑Datei bis zum Persistieren des gestylten Outputs.

Sie lernen, wie man:

* Eine Word‑Datei lädt, die bereits Fuß‑ und Endnoten enthält.  
* Die Absatz‑Objekte für das Fuß‑ und Endnoten‑Trennzeichen findet.  
* Die Schriftfarbe jedes Trennzeichens ändert (rot für Fußnoten, blau für Endnoten).  
* Das modifizierte Dokument speichert, ohne vorhandenen Inhalt zu verlieren.

Es werden keine externen Werkzeuge benötigt, außer der Aspose.Words‑Bibliothek und einer .NET‑Entwicklungsumgebung.

## Voraussetzungen

* .NET 6.0 SDK oder höher (der Code funktioniert auch mit .NET Framework 4.7+).  
* Visual Studio 2022, Rider oder ein beliebiger C#‑Editor Ihrer Wahl.  
* Aspose.Words für .NET NuGet‑Paket (`Aspose.Words`).  
* Eine Beispiel‑Word‑Datei (`Footnotes.docx`), die mindestens eine Fußnote und eine Endnote enthält.

> **Pro‑Tipp:** Wenn Sie keine Beispieldatei haben, erstellen Sie ein neues Word‑Dokument, fügen Sie eine Fußnote (`Verweise → Fußnote einfügen`) und eine Endnote (`Verweise → Endnote einfügen`) ein. Speichern Sie es als `Footnotes.docx` in einem Ordner, den Sie im Code referenzieren können.

## Wie man das Fußnotentrennzeichen mit Aspose.Words ändert

Der Kern der Aufgabe besteht darin, die speziellen Absätze abzurufen, die Aspose.Words als *separator*‑Knoten bereitstellt. Diese Knoten sind vom Typ `Paragraph` und können wie jeder andere Absatz formatiert werden.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Warum jede Zeile wichtig ist

* **Laden des Dokuments** (`new Document`) liefert Ihnen eine In‑Memory‑Repräsentation, die Aspose.Words manipulieren kann.  
* **`GetChild` mit `ParagraphNodeType.FootnoteSeparator`** gibt den verborgenen Absatz zurück, den Word verwendet, um die Linie zu zeichnen, die Fußnoten vom Haupttext trennt. Die gleiche Methode funktioniert für das Endnoten‑Trennzeichen.  
* **Ändern von `Font.Color`** wirkt sich direkt auf das Aussehen der Linie aus, weil Word das Trennzeichen als Absatz mit einem einzelnen „‑“-Zeichen rendert. Das Setzen der Farbe auf `Color.Red` (oder irgendeine `System.Drawing.Color`) aktualisiert den visuellen Stil.  
* **Speichern** schreibt die Änderungen zurück in eine .docx‑Datei, die jeder Textverarbeitungs‑Editor öffnen kann.

### Erwarteter Output

Wenn Sie `FootnoteSeparatorsStyled.docx` in Microsoft Word öffnen:

* Die Fußnotentrennlinien erscheinen **rot**.  
* Die Endnotentrennlinien erscheinen **blau**.  

Der gesamte ursprüngliche Fuß‑ und Endnoten‑Inhalt bleibt unverändert.

## Schriftfarbe in Word‑Dokument mit C# ändern

Der oben gezeigte Vorgang ist ein spezieller Anwendungsfall einer breiteren Fähigkeit: **change font color in Word document** programmgesteuert. Sobald Sie ein `Paragraph`, `Run` oder irgendeinen `Node` besitzen, der Text enthält, können Sie dessen `Font.Color`‑Eigenschaft anpassen.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Dieses Snippet iteriert über jeden Absatz, prüft, ob er den Stil `Heading 1` verwendet, und setzt dessen Schriftfarbe.  
* Sie können die Bedingung anpassen, um Fußnoten, Tabellen oder andere Knotentypen zu adressieren.

## Schritt‑für‑Schritt‑Aufschlüsselung

### 1. Aspose.Words installieren

Öffnen Sie ein Terminal in Ihrem Projektordner und führen Sie aus:

```bash
dotnet add package Aspose.Words
```

Das Paket enthält alle für den zuvor gezeigten Code erforderlichen Assemblies.

### 2. Eingabedatei vorbereiten

Legen Sie `Footnotes.docx` in einem bekannten Verzeichnis ab (z. B. `C:\Docs`). Stellen Sie sicher, dass die Datei mindestens eine Fußnote und eine Endnote enthält, damit die Trennzeichen‑Knoten existieren.

### 3. C#‑Programm schreiben

Erstellen Sie ein neues Konsolenprojekt (`dotnet new console -n FootnoteStyler`) und ersetzen Sie die erzeugte `Program.cs` durch den vollständigen Code‑Block aus dem Abschnitt **How to change footnote separator**. Passen Sie die Dateipfade an Ihre Umgebung an.

### 4. Ausführen und prüfen

Führen Sie das Programm aus:

```bash
dotnet run
```

Nach Abschluss des Laufs öffnen Sie `FootnoteSeparatorsStyled.docx`. Sie sollten die roten und blauen Trennlinien wie beschrieben sehen.

### 5. Lösung erweitern

* **Andere Farben:** Verwenden Sie jeden `System.Drawing.Color`‑Wert, z. B. `Color.FromArgb(255, 128, 0)` für Orange.  
* **Benutzerdefinierter Linienstil:** Anstatt nur die Farbe zu ändern, können Sie `ParagraphFormat`‑Eigenschaften wie `LineSpacing`, `Shading` oder sogar das Trennzeichen‑Zeichen selbst anpassen.  
* **Mehrere Dokumente:** Kapseln Sie die Logik in einer Methode, die Eingabe‑ und Ausgabepfade akzeptiert, und rufen Sie sie in einer Schleife für die Batch‑Verarbeitung auf.

## Häufige Stolperfallen und wie man sie vermeidet

| Symptom | Ursache | Lösung |
|---------|---------|--------|
| `GetChild` gibt `null` zurück | Das Quell‑Dokument enthält kein Fuß‑/Endnoten‑Trennzeichen (z. B. keine Fußnoten). | Fügen Sie mindestens eine Fuß‑ oder Endnote hinzu oder prüfen Sie vor dem Zugriff auf `Font` auf `null`. |
| Farbänderung nicht sichtbar | Das Trennzeichen wird in einigen Word‑Versionen als Linie statt als Zeichen gerendert. | Setzen Sie `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` und `ParagraphFormat.LineSpacing = 1`, um ein sichtbares Zeichen zu erzwingen. |
| Laufzeit‑Exception `FileNotFoundException` | Falscher Dateipfad. | Verwenden Sie absolute Pfade oder `Path.Combine` mit `Environment.CurrentDirectory`. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in eine Konsolen‑App kopieren‑und‑einfügen können. Es enthält Fehlerbehandlung und Kommentare, die jeden Schritt erläutern.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Das Ausführen dieses Programms erzeugt eine Word‑Datei, bei der die Fußnotentrennlinie rot und die Endnotentrennlinie blau ist, wodurch die Anforderung **how to change footnote separator** erfüllt wird und gleichzeitig **change font color in word document** demonstriert wird.

## Fazit

Sie wissen jetzt, **how to change footnote separator** in einem Word‑Dokument mit Aspose.Words für .NET zu ändern und **change font color in Word document** programmgesteuert anzupassen. Der Ansatz lautet:

1. Dokument laden.  
2. Die verborgenen Trennzeichen‑Absätze abrufen.  
3. deren `Font.Color`‑Eigenschaften setzen.  
4. Die modifizierte Datei speichern.

Ab hier können Sie weiterführende Stil‑Anpassungen erkunden – Linienstärke anpassen, verschiedene Schriften anwenden oder den Prozess über viele Dateien hinweg automatisieren. Das Beherrschen dieser Techniken gibt Ihnen eine feinkörnige Kontrolle über das Aussehen von Word‑Dokumenten direkt aus C#‑Code.

---


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Abrufen des Absatzstiltrennzeichens in Word‑Dokument](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Word‑Dokument mit Kopf‑ und Fußzeile erstellen mit Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Seitenzahlen in die Fußzeile eines Word‑Dokuments einfügen mit Aspose.Words für .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}