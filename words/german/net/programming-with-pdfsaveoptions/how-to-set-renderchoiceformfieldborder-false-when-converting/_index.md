---
category: general
date: 2026-09-21
description: Erfahren Sie, wie Sie RenderChoiceFormFieldBorder in Aspose.Words auf false setzen,
  um Word‑Formularfelder ohne Rahmen zu exportieren. Enthält vollständigen Code und
  Tipps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set renderchoiceformfieldborder false
- Aspose.Words PDF conversion
- disable choice field border
- PdfSaveOptions configuration
- Word form fields
- convert Word to PDF
language: de
lastmod: 2026-09-21
og_description: Setzen Sie RenderChoiceFormFieldBorder auf false, um beim Konvertieren
  von Word nach PDF mit Aspose.Words die Rahmen von Auswahlformularfeldern zu entfernen.
og_image_alt: PDF preview showing choice form fields without borders after setting
  RenderChoiceFormFieldBorder false
og_title: Setze RenderChoiceFormFieldBorder auf false für sauberen PDF‑Export
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  headline: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  type: TechArticle
- description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  name: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  steps:
  - name: Additional PdfSaveOptions you may want to set
    text: '| Option | Typical value | When to use it | |----------------------------|---------------|----------------|
      | `Compliance` | `PdfCompliance.PdfA1b` | For archival PDFs | | `EmbedStandardFonts`
      | `true` | To avoid font substitution on other machines | | `SaveFormat` | `SaveFormat.Pdf`
      | Explicitly st'
  - name: Verifying the result
    text: Open `NoBorderChoice.pdf` in any PDF viewer (Adobe Acrobat, Foxit Reader,
      or the browser). You should see the drop‑down or combo‑box fields rendered as
      plain text placeholders—no gray rectangle is visible. The fields remain interactive;
      clicking on them still displays the list of choices.
  - name: Sample code for checking form fields
    text: '```csharp int choiceFieldCount = 0; foreach (FormField field in doc.Range.FormFields)
      { if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
      choiceFieldCount++; } Console.WriteLine($"Document contains {choiceFieldCount}
      choice form fields."); ```'
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- C#
- Form fields
title: Wie man RenderChoiceFormFieldBorder beim Konvertieren von Word in PDF auf false
  setzt
url: /de/net/programming-with-pdfsaveoptions/how-to-set-renderchoiceformfieldborder-false-when-converting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man RenderChoiceFormFieldBorder auf false setzt beim Konvertieren von Word zu PDF

Wenn Sie **RenderChoiceFormFieldBorder auf false setzen** müssen, während Sie ein Word‑Dokument exportieren, das Auswahl‑Formularfelder enthält, zeigt Ihnen diese Anleitung die genauen Schritte. Durch das Deaktivieren der Rahmen­darstellung sieht das resultierende PDF sauberer aus und entspricht dem Layout des Originaldokuments.

In diesem Tutorial lernen Sie, wie Sie **PdfSaveOptions** in Aspose.Words konfigurieren, warum die Einstellung wichtig ist und wie Sie gängige Sonderfälle wie Dokumente ohne Formularfelder behandeln. Die Lösung funktioniert mit dem neuesten Aspose.Words für .NET (v23.10 zum Zeitpunkt des Schreibens) und erfordert nur wenige Zeilen C#‑Code.

## Voraussetzungen

* .NET 6.0 oder höher installiert.
* Eine gültige Aspose.Words für .NET Lizenz (oder ein kostenloser Evaluierungsschlüssel).
* Ein Word‑Dokument (`.docx`), das Auswahl‑Formularfelder enthält (z. B. Dropdown‑Listen oder Kombinationsfelder).
* Visual Studio 2022 (oder jede C#‑IDE).

## Schritt 1: Laden des Quell‑Word‑Dokuments

Der erste Schritt besteht darin, ein `Document`‑Objekt zu erstellen, das Ihre Quelldatei repräsentiert. Aspose.Words liest die Datei in den Speicher, sodass Sie den Inhalt vor der Konvertierung prüfen oder ändern können.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains choice form fields
Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");
```

**Warum das wichtig ist:** Das Laden des Dokuments gibt Ihnen Zugriff auf die Formularfeld‑Sammlung, die Sie später abfragen können, um zu bestätigen, dass die Datei tatsächlich Auswahlfelder enthält. Hat das Dokument keine solchen Felder, hat die Einstellung `RenderChoiceFormFieldBorder` keine visuelle Auswirkung, aber der Code läuft dennoch sicher.

## Schritt 2: PdfSaveOptions konfigurieren und RenderChoiceFormFieldBorder auf false setzen

`PdfSaveOptions` steuert jeden Aspekt der PDF‑Ausgabe, von der Bildqualität bis zur Darstellung von Formularfeldern. Das Setzen von `RenderChoiceFormFieldBorder` auf `false` weist den Renderer an, das graue Rechteck, das normalerweise Dropdown‑ und Kombinationsfelder umgibt, wegzulassen.

```csharp
// Create PDF save options and disable the rendering of choice field borders
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false
};
```

**Warum das wichtig ist:** Standardmäßig zeichnet Aspose.Words einen dünnen Rahmen um Auswahl‑Formularfelder, damit Benutzer sehen, wo sie interagieren können. In vielen Publikationsszenarien – wie druckbaren Formularen oder aufbereiteten Berichten – ist der Rahmen unerwünscht. Das Flag `RenderChoiceFormFieldBorder` bietet eine einzeilige Möglichkeit, ihn zu deaktivieren.

### Zusätzliche PdfSaveOptions, die Sie ggf. setzen möchten

| Option                     | Typischer Wert                | Wann zu verwenden |
|----------------------------|------------------------------|-------------------|
| `Compliance`               | `PdfCompliance.PdfA1b`       | Für Archiv‑PDFs |
| `EmbedStandardFonts`       | `true`                       | Um Schriftart‑Ersetzung auf anderen Rechnern zu vermeiden |
| `SaveFormat`               | `SaveFormat.Pdf`             | Gibt das Zielformat explizit an (optional) |

Sie können diese Einstellungen mit dem Rahmen‑Flag verketten:

```csharp
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false,
    Compliance = PdfCompliance.PdfA1b,
    EmbedStandardFonts = true
};
```

## Schritt 3: Dokument als PDF speichern mit den konfigurierten Optionen

Jetzt, wo die Optionen gesetzt sind, rufen Sie `Document.Save` mit dem Zielpfad und der `PdfSaveOptions`‑Instanz auf.

```csharp
// Save the document as a PDF using the configured options
doc.Save("YOUR_DIRECTORY/NoBorderChoice.pdf", pdfOptions);
```

**Warum das wichtig ist:** Die Methode `Save` führt die eigentliche Konvertierung aus. Da `pdfOptions` `RenderChoiceFormFieldBorder = false` enthält, wird das erzeugte PDF die Auswahlfelder **ohne** den umgebenden Rahmen enthalten.

### Ergebnis überprüfen

Öffnen Sie `NoBorderChoice.pdf` in einem beliebigen PDF‑Betrachter (Adobe Acrobat, Foxit Reader oder im Browser). Sie sollten die Dropdown‑ oder Kombinationsfelder als reine Text‑Platzhalter sehen – kein graues Rechteck ist sichtbar. Die Felder bleiben interaktiv; ein Klick darauf zeigt weiterhin die Auswahlliste an.

## Sonderfälle behandeln

| Situation                              | Empfohlener Ansatz |
|----------------------------------------|----------------------|
| **Dokument hat keine Auswahl‑Formularfelder** | Das Rahmen‑Flag hat keine Wirkung. Sie können optional `doc.Range.FormFields.Count` vor der Konvertierung prüfen, um unnötige Konfiguration zu überspringen. |
| **Passwortgeschützte Word‑Datei**       | Laden Sie das Dokument mit einem `LoadOptions`‑Objekt, das das Passwort enthält, und wenden Sie anschließend dieselben `PdfSaveOptions` an. |
| **Große Dokumente (> 100 MB)**         | Verwenden Sie `MemoryOptimization`‑Optionen in `PdfSaveOptions`, um den Speicherverbrauch während der Konvertierung zu reduzieren. |
| **Erforderlich, den Rahmen für bestimmte Felder beizubehalten** | Nach dem Laden des Dokuments iterieren Sie über `doc.Range.FormFields`, setzen `FieldType` auf `FieldType.FieldFormDropDown` oder `FieldFormComboBox` und passen die `Border`‑Eigenschaft manuell vor dem Speichern an. |

### Beispielcode zum Prüfen von Formularfeldern

```csharp
int choiceFieldCount = 0;
foreach (FormField field in doc.Range.FormFields)
{
    if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
        choiceFieldCount++;
}
Console.WriteLine($"Document contains {choiceFieldCount} choice form fields.");
```

Wenn `choiceFieldCount` null ist, können Sie die Rahmen‑Konfiguration vollständig überspringen, was eine kleine Menge Verarbeitungszeit spart.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, ausführbare Programm, das alles zusammenführt. Ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Pfad auf Ihrem Rechner.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");

        // Optional: verify that the document contains choice fields
        int choiceCount = 0;
        foreach (FormField field in doc.Range.FormFields)
        {
            if (field.Type == FieldType.FieldFormDropDown ||
                field.Type == FieldType.FieldFormComboBox)
                choiceCount++;
        }
        Console.WriteLine($"Found {choiceCount} choice form fields.");

        // 2️⃣ Configure PdfSaveOptions and set RenderChoiceFormFieldBorder false
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            RenderChoiceFormFieldBorder = false,
            // Example of additional options you might need
            Compliance = PdfCompliance.PdfA1b,
            EmbedStandardFonts = true
        };

        // 3️⃣ Save the PDF
        string outputPath = "YOUR_DIRECTORY/NoBorderChoice.pdf";
        doc.Save(outputPath, pdfOptions);
        Console.WriteLine($"PDF saved to {outputPath} with borders disabled.");
    }
}
```

**Erwartete Ausgabe in der Konsole**

```
Found 3 choice form fields.
PDF saved to C:\MyProjects\NoBorderChoice.pdf with borders disabled.
```

Wenn Sie `NoBorderChoice.pdf` öffnen, erscheinen die Dropdown‑Felder ohne den standardmäßigen grauen Rahmen, wodurch das Dokument sauberer wirkt und die Interaktivität erhalten bleibt.

## Pro‑Tipps und häufige Fallstricke

* **Pro‑Tipp:** Wenn Sie PDFs in einem Web‑Service erzeugen, setzen Sie `pdfOptions.SaveFormat = SaveFormat.Pdf` explizit, um versehentliche Format‑Erkennungsprobleme zu vermeiden.
* **Achten Sie auf:** Ältere Versionen von Aspose.Words (vor v20) stellen `RenderChoiceFormFieldBorder` nicht bereit. Aktualisieren Sie auf die neueste Version, um dieses Flag zu nutzen.
* **Performance‑Tipp:** Verwenden Sie eine einzelne `PdfSaveOptions`‑Instanz, wenn Sie viele Dokumente stapelweise konvertieren; jedes Mal ein neues Objekt zu erstellen, verursacht unnötigen Overhead.
* **Test‑Tipp:** Fügen Sie einen Unit‑Test hinzu, der ein bekanntes `.docx` mit einem Dropdown lädt, die Konvertierung ausführt und prüft, dass der resultierende PDF‑Stream die PDF‑Annotation `/Border` für diese Felder nicht enthält.

## Fazit

Sie wissen jetzt **wie man RenderChoiceFormFieldBorder auf false setzt**, um PDFs ohne Rahmen für Auswahl‑Formularfelder mit Aspose.Words zu erzeugen. Die Lösung umfasst das Laden des Dokuments, das Konfigurieren von `PdfSaveOptions`, das Speichern des PDFs und das Behandeln von Sonderfällen wie fehlenden Formularfeldern oder passwortgeschützten Quellen.  

Als Nächstes könnten Sie verwandte Themen erkunden, wie **disable choice field border** für andere Formularfeldtypen, oder lernen, wie man **Word zu PDF konvertiert** mit benutzerdefinierter Bildauflösung mittels `ImageSaveOptions`. Beide Themen vertiefen Ihr Können in der **Aspose.Words PDF‑Konvertierung** und geben Ihnen volle Kontrolle über das endgültige Erscheinungsbild des Dokuments.

Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word zu PDF konvertieren in C# mit Aspose.Words – Anleitung](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [Word mit Aspose Words als PDF speichern – Vollständiger C#‑Leitfaden](/words/hindi/net/programming-with-pdfsaveoptions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Word zu PDF konvertieren mit Aspose.Words für Java](/words/english/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}