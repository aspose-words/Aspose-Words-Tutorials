---
category: general
date: 2026-08-17
description: Wie man ActiveX‑Steuerelemente hinzufügt und ein Kreisdiagramm in ein
  Word‑Dokument mit Aspose.Words einfügt. Ein Segment herauslösen und das Dokument
  in wenigen Schritten als DOCX speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: de
lastmod: 2026-08-17
og_description: Wie man ActiveX‑Steuerelemente hinzufügt, ein Kreisdiagramm einfügt,
  ein Segment hervorhebt und mit Aspose.Words als DOCX speichert – vollständige Schritt‑für‑Schritt‑Anleitung.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Wie man ActiveX hinzufügt und ein Kreisdiagramm in ein Word‑Dokument einfügt
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Wie man ActiveX hinzufügt und ein Kreisdiagramm in ein Word‑Dokument einfügt
url: /de/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ActiveX hinzufügt und ein Kreisdiagramm in ein Word‑Dokument einfügt

Wenn Sie **wie man ActiveX**‑Steuerelemente hinzufügt und ein Diagramm in ein Word‑Dokument einbettet, zeigt Ihnen dieses Tutorial eine komplette, ausführbare Lösung. Mit Aspose.Words können Sie eine ActiveX CommandButton platzieren, ein Kreisdiagramm erstellen, ein Segment hervorheben und schließlich **als DOCX speichern** – alles in nur wenigen Zeilen C#.

In den nachfolgenden Abschnitten sehen Sie alle erforderlichen Importe, ein vollständiges Code‑Listing und Erklärungen, warum jeder Schritt wichtig ist. Am Ende können Sie interaktive Steuerelemente und visuelle Daten in jede .docx‑Datei integrieren, die Sie programmgesteuert erzeugen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
* Aspose.Words for .NET‑Paket (verfügbar über NuGet)
* Eine Entwicklungsumgebung wie Visual Studio 2022 oder VS Code
* Grundlegende Kenntnisse in C# und dem Word‑Objektmodell

Keine zusätzlichen Drittanbieter‑Diagrammbibliotheken sind erforderlich – Aspose.Words stellt die integrierte Diagrammerstellung bereit.

## Wie man ActiveX‑Steuerelemente mit Aspose.Words hinzufügt

ActiveX‑Steuerelemente ermöglichen das Einbetten interaktiver UI‑Elemente direkt in eine Word‑Datei. In diesem Leitfaden fügen wir einen **CommandButton** hinzu, der später an VBA‑Code angebunden werden kann.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Warum das funktioniert:**  
`InsertForms2OleControl` erstellt einen OLE‑Container, den die Word‑UI als ActiveX‑Steuerelement erkennt. Durch das Festlegen des Steuerelementtyps auf `CommandButton` und das Setzen einer Beschriftung verhält es sich wie ein Standard‑Button, wenn der Benutzer die Datei in Word öffnet.

## Kreisdiagramm einfügen und ein Segment hervorheben

Diagramme sind nützlich, um Daten zu visualisieren, ohne das Dokument zu verlassen. Die folgenden Schritte zeigen **wie man ein Diagramm einfügt** und speziell ein **Kreisdiagramm**, bei dem das erste Segment hervorgehoben ist.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Warum das Segment hervorgehoben wird:**  
Der Aufruf `SetExplode(0, true)` weist Aspose.Words an, den ersten Datenpunkt zu versetzen und so den Blick des Betrachters auf dieses Segment zu lenken. Das ist eine gängige Technik in Präsentationen, um einen Schlüsselwert zu betonen.

## Als DOCX speichern

Nachdem der ActiveX‑Button und das Diagramm hinzugefügt wurden, wird das Dokument auf dem Datenträger gespeichert. Dieser Schritt demonstriert **save as DOCX** mit der Standard‑Methode.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Die Datei `Output.docx` enthält nun einen interaktiven Button, ein Kreisdiagramm mit hervorgehobenem Segment und kann in Microsoft Word ohne zusätzliche Plugins geöffnet werden.

## Vollständiges ausführbares Beispiel

Alles zusammengeführt, hier ein eigenständiges Programm, das Sie in eine Konsolenanwendung kopieren und sofort ausführen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Erwartetes Ergebnis:**  
Beim Öffnen von `Output.docx` in Word wird ein Button mit der Aufschrift *Click Me* sowie ein Kreisdiagramm angezeigt, bei dem das erste Segment (Januar) vom Rest abgesetzt ist. Der Button ist bereit für VBA‑Ereignis‑Handling, und das Diagramm kann mit den integrierten Word‑Diagramm‑Tools bearbeitet werden.

## Häufige Fragen und Sonderfälle

* **Kann ich andere ActiveX‑Typen hinzufügen?**  
  Ja. Ersetzen Sie `Forms2OleControlType.CommandButton` durch einen beliebigen Wert aus dem `Forms2OleControlType`‑Enum (z. B. `CheckBox`, `OptionButton`). Das Einfügemuster bleibt gleich.

* **Was, wenn ich einen anderen Diagrammtyp benötige?**  
  Verwenden Sie `ChartType.Bar`, `ChartType.Line` usw. im Aufruf von `InsertChart`. Der **how to insert chart**‑Schritt bleibt identisch; nur der Enum‑Wert ändert sich.

* **Wie kann ich die Größe des hervorgehobenen Segments steuern?**  
  Aspose.Words unterstützt derzeit nur ein binäres Hervorhebungs‑Flag (true/false). Für feinere Einstellungen (z. B. Abstand) müssten Sie das zugrunde liegende OOXML nach dem Speichern bearbeiten.

* **Ist das Dokument mit älteren Word‑Versionen kompatibel?**  
  Das Speichern als DOCX gewährleistet Kompatibilität mit Word 2007 und neuer. Für Word 2003 könnten Sie `SaveFormat.Doc` verwenden, jedoch ist die ActiveX‑Unterstützung in diesem Format eingeschränkt.

* **Muss ich `System.Drawing` referenzieren?**  
  Nein. Alle Zeichenobjekte werden von Aspose.Words bereitgestellt, sodass das einzige erforderliche NuGet‑Paket `Aspose.Words` ist.

## Fazit

Sie wissen jetzt **wie man ActiveX** hinzufügt, **ein Kreisdiagramm einfügt**, **ein Segment hervorhebt** und **als DOCX speichert** mit Aspose.Words für .NET. Das vollständige Beispiel deckt jeden Schritt von der Dokumenterstellung bis zur finalen Persistenz ab und erklärt die Gründe hinter jedem API‑Aufruf.

Als Nächstes könnten Sie:

* VBA‑Makros hinzufügen, die auf den CommandButton‑Klick reagieren (**how to insert chart** und Daten‑Updates automatisieren)
* Das Aussehen des Diagramms anpassen (Farben, Datenbeschriftungen), um das Corporate‑Branding zu treffen
* Weitere ActiveX‑Steuerelemente wie **ComboBox** oder **ListBox** einbetten, um reichhaltigere Formulare zu erstellen

Experimentieren Sie gern mit dem Code, ersetzen Sie die Beispieldaten und integrieren Sie die Lösung in Ihre eigenen Dokument‑Generierungspipelines. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren Projekten zu erkunden.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}