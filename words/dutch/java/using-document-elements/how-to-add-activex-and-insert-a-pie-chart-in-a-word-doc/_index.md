---
category: general
date: 2026-08-17
description: Hoe ActiveX‑besturingselementen toe te voegen en een taartdiagram in
  een Word‑document in te voegen met Aspose.Words. Een part laten exploderen en opslaan
  als DOCX in enkele stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: nl
lastmod: 2026-08-17
og_description: Hoe ActiveX‑besturingselementen toe te voegen, een cirkeldiagram in
  te voegen, een partje te exploderen en op te slaan als DOCX met Aspose.Words – volledige
  stapsgewijze handleiding.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Hoe ActiveX toe te voegen en een taartdiagram in een Word‑document in te
  voegen
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
title: Hoe ActiveX toe te voegen en een taartdiagram in een Word‑document in te voegen
url: /nl/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe ActiveX toe te voegen en een taartdiagram in een Word‑document in te voegen

Als je **hoe ActiveX toe te voegen** besturingselementen en een diagram in een Word‑document wilt insluiten, laat deze tutorial je een volledige, uitvoerbare oplossing zien. Met Aspose.Words kun je een ActiveX CommandButton plaatsen, een taartdiagram maken, een partitie laten uitbarsten voor nadruk, en tenslotte **opslaan als DOCX** in slechts een paar regels C#.

In de onderstaande secties zie je elke benodigde import, een volledige code‑listing en uitleg waarom elke stap belangrijk is. Aan het einde kun je interactieve besturingselementen en visuele data integreren in elk .docx‑bestand dat je programmatisch genereert.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
* Aspose.Words for .NET‑pakket (beschikbaar via NuGet)
* Een ontwikkelomgeving zoals Visual Studio 2022 of VS Code
* Basiskennis van C# en het Word‑objectmodel

Er zijn geen extra externe diagram‑bibliotheken nodig — Aspose.Words biedt ingebouwde diagramcreatie.

## Hoe ActiveX‑besturingselementen toe te voegen met Aspose.Words

ActiveX‑besturingselementen laten je interactieve UI‑onderdelen direct in een Word‑bestand insluiten. In deze gids voegen we een **CommandButton** toe die later kan worden gekoppeld aan VBA‑code.

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

**Waarom dit werkt:**  
`InsertForms2OleControl` maakt een OLE‑container aan die de Word‑UI herkent als een ActiveX‑besturingselement. Het instellen van het besturingselementtype op `CommandButton` en het geven van een bijschrift zorgt ervoor dat het zich gedraagt als een standaardknop wanneer de gebruiker het bestand in Word opent.

## Taartdiagram invoegen en een partitie laten uitbarsten

Diagrammen zijn handig om data te visualiseren zonder het document te verlaten. De volgende stappen demonstreren **hoe een diagram in te voegen** en specifiek een **taartdiagram** waarvan de eerste partitie wordt uitgebarsten.

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

**Waarom de partitie uitbarsten:**  
Het aanroepen van `SetExplode(0, true)` vertelt Aspose.Words om het eerste datapunten te verschuiven, waardoor de aandacht van de lezer naar dat segment wordt getrokken. Dit is een veelgebruikte techniek in presentaties om een belangrijke waarde te benadrukken.

## Opslaan als DOCX

Na het toevoegen van de ActiveX‑knop en het diagram, sla je het document op schijf op. Deze stap demonstreert **opslaan als DOCX** met de standaardmethode.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Het bestand `Output.docx` bevat nu een interactieve knop, een taartdiagram met een uitgebarsten partitie, en kan worden geopend in Microsoft Word zonder extra plug‑ins.

## Volledig uitvoerbaar voorbeeld

Alles bij elkaar genomen, hier is een zelfstandig programma dat je kunt kopiëren naar een console‑applicatie en direct kunt uitvoeren.

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

**Verwacht resultaat:**  
Het openen van `Output.docx` in Word toont een knop met de tekst *Click Me* en een taartdiagram waarbij de eerste partitie (January) is verschoven ten opzichte van de rest. De knop staat klaar voor VBA‑event‑afhandeling, en het diagram kan worden bewerkt met de ingebouwde diagramtools van Word.

## Veelgestelde vragen en randgevallen

* **Kan ik andere ActiveX‑typen toevoegen?**  
  Ja. Vervang `Forms2OleControlType.CommandButton` door een willekeurige waarde uit de `Forms2OleControlType`‑enum (bijv. `CheckBox`, `OptionButton`). Hetzelfde invoegpatroon geldt.

* **Wat als ik een ander diagramtype nodig heb?**  
  Gebruik `ChartType.Bar`, `ChartType.Line`, enz. in de `InsertChart`‑aanroep. De **hoe diagram in te voegen** stap blijft identiek; alleen de enum‑waarde verandert.

* **Hoe de grootte van de uitgebarsten partitie regelen?**  
  Aspose.Words ondersteunt momenteel alleen een binaire explode‑vlag (true/false). Voor fijnmazigere controle (bijv. afstand van verschuiving) moet je de onderliggende OOXML bewerken na het opslaan.

* **Is het document compatibel met oudere Word‑versies?**  
  Opslaan als DOCX zorgt voor compatibiliteit met Word 2007 en later. Voor Word 2003 kun je `SaveFormat.Doc` gebruiken, maar ActiveX‑ondersteuning is beperkt in dat formaat.

* **Moet ik `System.Drawing` refereren?**  
  Nee. Alle tekenobjecten worden geleverd door Aspose.Words, dus het enige vereiste NuGet‑pakket is `Aspose.Words`.

## Conclusie

Je weet nu **hoe ActiveX toe te voegen**, **een taartdiagram in te voegen**, **een taartpartitie te laten uitbarsten**, en **opslaan als DOCX** met Aspose.Words voor .NET. Het volledige voorbeeld behandelt elke stap van documentcreatie tot uiteindelijke opslag, en legt de reden achter elke API‑aanroep uit.

Vervolgens kun je verkennen:

* Het toevoegen van VBA‑macro’s die reageren op de CommandButton‑klik (**hoe diagram in te voegen** en data‑updates automatiseren)
* Het aanpassen van de diagram­uitstraling (kleuren, gegevenslabels) om te passen bij de huisstijl
* Het insluiten van extra ActiveX‑besturingselementen zoals **ComboBox** of **ListBox** voor rijkere formulieren

Voel je vrij om met de code te experimenteren, de voorbeelddata te vervangen, en de oplossing te integreren in je eigen document‑generatie‑pijplijnen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Kolomdiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Eenvoudig kolomdiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Bubbeldiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}