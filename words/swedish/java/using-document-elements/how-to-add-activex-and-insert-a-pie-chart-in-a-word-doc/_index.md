---
category: general
date: 2026-08-17
description: Hur man lägger till ActiveX‑kontroller och infogar ett cirkeldiagram
  i ett Word‑dokument med Aspose.Words. Explodera en del och spara som DOCX på några
  få steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: sv
lastmod: 2026-08-17
og_description: Hur man lägger till ActiveX‑kontroller, infogar ett cirkeldiagram,
  exploderar ett segment och sparar som DOCX med Aspose.Words – komplett steg‑för‑steg‑guide.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Hur man lägger till ActiveX och infogar ett cirkeldiagram i ett Word‑dokument
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
title: Hur man lägger till ActiveX och infogar ett cirkeldiagram i ett Word-dokument
url: /sv/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till ActiveX och infogar ett cirkeldiagram i ett Word-dokument

Om du behöver **how to add ActiveX**-kontroller och bädda in ett diagram i ett Word-dokument, visar den här handledningen en komplett, körbar lösning. Med Aspose.Words kan du placera en ActiveX CommandButton, skapa ett cirkeldiagram, explodera en skiva för betoning, och slutligen **save as DOCX** på bara några rader C#.

I avsnitten nedan kommer du att se alla nödvändiga importeringar, en fullständig kodlista och förklaringar till varför varje steg är viktigt. I slutet kommer du att kunna integrera interaktiva kontroller och visuella data i vilken .docx-fil du än genererar programatiskt.

## Förutsättningar

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
* Aspose.Words for .NET-paketet (tillgängligt via NuGet)
* En utvecklingsmiljö såsom Visual Studio 2022 eller VS Code
* Grundläggande kunskap om C# och Word-objektmodellen

Inga ytterligare tredjepartsdiagrambibliotek krävs—Aspose.Words tillhandahåller inbyggd diagramskapning.

## Hur man lägger till ActiveX‑kontroller med Aspose.Words

ActiveX‑kontroller låter dig bädda in interaktiva UI‑element direkt i en Word‑fil. I den här guiden lägger vi till en **CommandButton** som senare kan kopplas till VBA‑kod.

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

**Varför detta fungerar:**  
`InsertForms2OleControl` skapar en OLE‑behållare som Word‑UI identifierar som en ActiveX‑kontroll. Genom att sätta kontrolltypen till `CommandButton` och ge den en rubrik får den bete sig som en standardknapp när användaren öppnar filen i Word.

## Infoga cirkeldiagram och explodera en skiva

Diagram är användbara för att visualisera data utan att lämna dokumentet. Följande steg demonstrerar **how to insert chart** och specifikt ett **pie chart** där den första skivan är exploderad.

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

**Varför explodera skivan:**  
Genom att anropa `SetExplode(0, true)` instrueras Aspose.Words att förskjuta den första datapunkten, vilket drar betraktarens blick till det segmentet. Detta är en vanlig teknik i presentationer för att framhäva ett nyckeltal.

## Spara som DOCX

Efter att ha lagt till ActiveX‑knappen och diagrammet, sparas dokumentet till disk. Detta steg demonstrerar **save as DOCX** med den standardmetod.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Filen `Output.docx` innehåller nu en interaktiv knapp, ett cirkeldiagram med en exploderad skiva, och kan öppnas i Microsoft Word utan extra tillägg.

## Fullt körbart exempel

När allt sätts ihop, här är ett fristående program som du kan kopiera in i en konsolapplikation och köra omedelbart.

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

**Förväntat resultat:**  
När du öppnar `Output.docx` i Word visas en knapp med etiketten *Click Me* och ett cirkeldiagram där den första skivan (January) är förskjuten från resten. Knappen är klar för VBA‑händelsehantering, och diagrammet kan redigeras med Words inbyggda diagramverktyg.

## Vanliga frågor och specialfall

* **Kan jag lägga till andra ActiveX-typer?**  
  Ja. Ersätt `Forms2OleControlType.CommandButton` med vilket värde som helst från `Forms2OleControlType`‑enumet (t.ex. `CheckBox`, `OptionButton`). Samma insättningsmönster gäller.

* **Vad händer om jag behöver en annan diagramtyp?**  
  Använd `ChartType.Bar`, `ChartType.Line` osv. i `InsertChart`‑anropet. Steget **how to insert chart** förblir identiskt; endast enum‑värdet förändras.

* **Hur styr jag storleken på den exploderade skivan?**  
  Aspose.Words stödjer för närvarande en binär explode‑flagga (true/false). För finare kontroll (t.ex. förskjutningsavstånd) måste du redigera den underliggande OOXML‑filen efter sparning.

* **Är dokumentet kompatibelt med äldre Word‑versioner?**  
  Att spara som DOCX säkerställer kompatibilitet med Word 2007 och senare. För Word 2003 kan du ändra till `SaveFormat.Doc`, men ActiveX‑stöd är begränsat i det formatet.

* **Behöver jag referera `System.Drawing`?**  
  Nej. Alla ritobjekt tillhandahålls av Aspose.Words, så det enda nödvändiga NuGet‑paketet är `Aspose.Words`.

## Slutsats

Du vet nu **how to add ActiveX**, **insert a pie chart**, **explode a pie slice**, och **save as DOCX** med Aspose.Words för .NET. Det kompletta exemplet täcker varje steg från dokumentskapande till slutlig lagring, och förklarar resonemanget bakom varje API‑anrop.

Nästa steg, du kan utforska:

* Lägga till VBA‑makron som svarar på CommandButton‑klick (**how to insert chart** och automatisera datauppdateringar)
* Anpassa diagrammets utseende (färger, datalabels) för att matcha företagets varumärke
* Bädda in ytterligare ActiveX‑kontroller såsom **ComboBox** eller **ListBox** för rikare formulär

Känn dig fri att experimentera med koden, ersätta exempeldata och integrera lösningen i dina egna dokument‑genereringspipelines. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Infoga ett enkelt stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Infoga ett bubbeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}