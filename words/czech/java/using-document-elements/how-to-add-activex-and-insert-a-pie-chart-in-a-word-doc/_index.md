---
category: general
date: 2026-08-17
description: Jak přidat ActiveX ovládací prvky a vložit koláčový graf do dokumentu
  Word pomocí Aspose.Words. Rozbalit výseč a uložit jako DOCX během několika kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: cs
lastmod: 2026-08-17
og_description: Jak přidat ActiveX ovládací prvky, vložit koláčový graf, oddělit výsek
  a uložit jako DOCX pomocí Aspose.Words – kompletní krok‑za‑krokem průvodce.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Jak přidat ActiveX a vložit koláčový graf do dokumentu Word
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
title: Jak přidat ActiveX a vložit koláčový graf do dokumentu Word
url: /cs/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat ActiveX a vložit koláčový graf do dokumentu Word

Pokud potřebujete **jak přidat ActiveX** ovládací prvky a vložit graf do dokumentu Word, tento tutoriál vám ukáže kompletní, spustitelné řešení. Pomocí Aspose.Words můžete umístit ActiveX **CommandButton**, vytvořit koláčový graf, „explodovat“ výsek pro zdůraznění a nakonec **uložit jako DOCX** během několika řádků C#.

V následujících sekcích uvidíte všechny potřebné importy, úplný výpis kódu a vysvětlení, proč je každý krok důležitý. Na konci budete schopni integrovat interaktivní ovládací prvky a vizuální data do libovolného .docx souboru, který generujete programově.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.7+)
* Balíček **Aspose.Words for .NET** (k dispozici přes NuGet)
* Vývojové prostředí, např. Visual Studio 2022 nebo VS Code
* Základní znalosti C# a objektového modelu Wordu

Žádné další knihovny pro grafy nejsou potřeba — Aspose.Words poskytuje vestavěnou tvorbu grafů.

## Jak přidat ActiveX ovládací prvky pomocí Aspose.Words

ActiveX ovládací prvky umožňují vložit interaktivní UI elementy přímo do souboru Word. V tomto návodu přidáme **CommandButton**, který lze později propojit s VBA kódem.

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

**Proč to funguje:**  
`InsertForms2OleControl` vytvoří OLE kontejner, který uživatelské rozhraní Wordu rozpozná jako ActiveX ovládací prvek. Nastavením typu ovládacího prvku na `CommandButton` a přiřazením popisku se chová jako standardní tlačítko, když uživatel otevře soubor ve Wordu.

## Vložení koláčového grafu a „explodování“ výseku

Grafy jsou užitečné pro vizualizaci dat přímo v dokumentu. Následující kroky ukazují **jak vložit graf** a konkrétně **koláčový graf**, jehož první výsek je „explodován“.

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

**Proč explodovat výsek:**  
Volání `SetExplode(0, true)` říká Aspose.Words, aby posunulo první datový bod, čímž upoutá pozornost diváka na tento segment. Jedná se o běžnou techniku v prezentacích pro zvýraznění klíčové hodnoty.

## Uložení jako DOCX

Po přidání ActiveX tlačítka a grafu dokument uložíme na disk. Tento krok ukazuje **uložení jako DOCX** pomocí standardní metody.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Soubor `Output.docx` nyní obsahuje interaktivní tlačítko, koláčový graf s explodovaným výsekem a lze jej otevřít v Microsoft Word bez dalších pluginů.

## Kompletní spustitelný příklad

Spojením všech částí získáte samostatný program, který můžete zkopírovat do konzolové aplikace a okamžitě spustit.

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

**Očekávaný výsledek:**  
Otevření `Output.docx` ve Wordu zobrazí tlačítko s popiskem *Click Me* a koláčový graf, kde je první výsek (January) odsazen od zbytku. Tlačítko je připravené na zpracování VBA událostí a graf lze upravovat pomocí vestavěných nástrojů Wordu.

## Časté otázky a okrajové případy

* **Mohu přidat jiné typy ActiveX?**  
  Ano. Nahraďte `Forms2OleControlType.CommandButton` libovolnou hodnotou z výčtu `Forms2OleControlType` (např. `CheckBox`, `OptionButton`). Stejný vzor vložení platí.

* **Co když potřebuji jiný typ grafu?**  
  Použijte `ChartType.Bar`, `ChartType.Line` atd. v metodě `InsertChart`. Krok **jak vložit graf** zůstává stejný; mění se jen hodnota výčtu.

* **Jak ovládat velikost explodovaného výseku?**  
  Aspose.Words aktuálně podporuje binární příznak explodování (true/false). Pro jemnější nastavení (např. vzdálenost odsazení) by bylo nutné upravit podkladový OOXML po uložení.

* **Je dokument kompatibilní se staršími verzemi Wordu?**  
  Ukládání jako DOCX zajišťuje kompatibilitu s Word 2007 a novějšími. Pro Word 2003 můžete změnit na `SaveFormat.Doc`, ale podpora ActiveX v tomto formátu je omezená.

* **Musím odkazovat na `System.Drawing`?**  
  Ne. Všechny kreslicí objekty poskytuje Aspose.Words, takže jediný požadovaný NuGet balíček je `Aspose.Words`.

## Závěr

Nyní víte **jak přidat ActiveX**, **vložit koláčový graf**, **explodovat výsek koláče** a **uložit jako DOCX** pomocí Aspose.Words pro .NET. Kompletní příklad pokrývá každý krok od vytvoření dokumentu až po finální uložení a vysvětluje důvody jednotlivých volání API.

Dále můžete zkoumat:

* Přidání VBA maker reagujících na kliknutí CommandButton (**jak vložit graf** a automatizovat aktualizace dat)
* Přizpůsobení vzhledu grafu (barvy, popisky dat) tak, aby odpovídaly firemnímu stylu
* Vložení dalších ActiveX ovládacích prvků, jako je **ComboBox** nebo **ListBox**, pro bohatší formuláře

Neváhejte experimentovat s kódem, nahradit ukázková data a integrovat řešení do vlastních pipeline pro generování dokumentů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}