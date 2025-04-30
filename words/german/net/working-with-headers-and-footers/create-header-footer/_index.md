---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Kopf- und Fußzeilen in Word-Dokumenten hinzufügen und anpassen. Diese Schritt-für-Schritt-Anleitung gewährleistet eine professionelle Dokumentformatierung."
"linktitle": "Kopf- und Fußzeile erstellen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Kopf- und Fußzeile erstellen"
"url": "/de/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kopf- und Fußzeile erstellen

## Einführung

Das Hinzufügen von Kopf- und Fußzeilen zu Ihren Dokumenten verbessert deren Professionalität und Lesbarkeit. Mit Aspose.Words für .NET können Sie Kopf- und Fußzeilen für Ihre Word-Dokumente einfach erstellen und anpassen. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess und stellen sicher, dass Sie diese Funktionen nahtlos implementieren können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Aspose.Words für .NET: Herunterladen und installieren von der [Download-Link](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Wie etwa Visual Studio, zum Schreiben und Ausführen Ihres Codes.
- Grundkenntnisse in C#: Verständnis von C# und .NET Framework.
- Beispieldokument: Ein Beispieldokument zum Anwenden der Kopf- und Fußzeilen oder zum Erstellen eines neuen Dokuments, wie im Lernprogramm gezeigt.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces importieren, um auf die Klassen und Methoden von Aspose.Words zuzugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Schritt 1: Definieren Sie das Dokumentverzeichnis

Definieren Sie das Verzeichnis, in dem Ihr Dokument gespeichert wird. Dies erleichtert die effektive Pfadverwaltung.

```csharp
// Der Pfad zum Dokumentenverzeichnis
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Schritt 2: Erstellen Sie ein neues Dokument

Erstellen Sie ein neues Dokument und ein `DocumentBuilder` um das Hinzufügen von Inhalten zu erleichtern.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Seiteneinrichtung konfigurieren

Richten Sie die Seiteneinstellungen ein, einschließlich der Angabe, ob die erste Seite eine andere Kopf-/Fußzeile haben soll.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Schritt 4: Fügen Sie der ersten Seite eine Kopfzeile hinzu

Wechseln Sie zum Kopfzeilenbereich für die erste Seite und konfigurieren Sie den Kopfzeilentext.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Schritt 5: Primäre Kopfzeile hinzufügen

Wechseln Sie zum primären Kopfzeilenbereich und fügen Sie ein Bild und Text ein.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Fügen Sie ein Bild in die Kopfzeile ein
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Schritt 6: Fügen Sie eine primäre Fußzeile hinzu

Wechseln Sie zum primären Fußzeilenabschnitt und erstellen Sie eine Tabelle, um den Fußzeileninhalt zu formatieren.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Seitennummerierung hinzufügen
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Schritt 7: Inhalt und Seitenumbrüche hinzufügen

Gehen Sie zum Ende des Dokuments, fügen Sie einen Seitenumbruch hinzu und erstellen Sie einen neuen Abschnitt mit anderen Seiteneinstellungen.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Schritt 8: Kopf- und Fußzeilen aus dem vorherigen Abschnitt kopieren

Wenn Sie Kopf- und Fußzeilen aus einem vorherigen Abschnitt wiederverwenden möchten, kopieren Sie sie und nehmen Sie die erforderlichen Änderungen vor.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Abschluss

Mit diesen Schritten können Sie mit Aspose.Words für .NET Kopf- und Fußzeilen in Ihren Word-Dokumenten effektiv hinzufügen und anpassen. Dies verbessert das Erscheinungsbild und die Professionalität Ihres Dokuments und macht es lesbarer und ansprechender.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?

Aspose.Words für .NET ist eine Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert in .NET-Anwendungen zu erstellen, zu bearbeiten und zu konvertieren.

### Kann ich der Kopf- oder Fußzeile Bilder hinzufügen?

Ja, Sie können ganz einfach Bilder zur Kopf- oder Fußzeile hinzufügen, indem Sie `DocumentBuilder.InsertImage` Verfahren.

### Wie lege ich unterschiedliche Kopf- und Fußzeilen für die erste Seite fest?

Sie können verschiedene Kopf- und Fußzeilen für die erste Seite festlegen, indem Sie die `DifferentFirstPageHeaderFooter` Eigentum der `PageSetup` Klasse.

### Wo finde ich weitere Dokumentation zu Aspose.Words?

Eine umfassende Dokumentation finden Sie auf der [Aspose.Words API-Dokumentationsseite](https://reference.aspose.com/words/net/).

### Gibt es Support für Aspose.Words?

Ja, Aspose bietet Support über ihre [Support-Forum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}