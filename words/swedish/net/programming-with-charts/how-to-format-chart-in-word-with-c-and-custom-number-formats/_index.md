---
category: general
date: 2026-10-13
description: Hur man formaterar diagram i Word med C# genom att tillämpa ett anpassat
  talformat, t.ex. valuta, på diagramaxlarna. Steg‑för‑steg kodexempel inkluderat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: sv
lastmod: 2026-10-13
og_description: Hur du formaterar diagram i Word med C# låter dig tillämpa ett anpassat
  talformat på diagramaxlarna, så att värden visas som valuta, procent eller vilket
  mönster du än behöver. Följ den steg‑för‑steg‑guiden.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Hur man formaterar diagram i Word med C# – anpassade talformat
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Hur man formaterar diagram i Word med C# och anpassade talformat
url: /sv/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man formaterar diagram i Word med C# och anpassade talformat

Att formatera diagram i Word med C# är ett vanligt krav när du behöver presentera data professionellt. Denna guide visar hur du applicerar ett anpassat talformat på ett diagramaxel med hjälp av **Aspose.Words for .NET**, så att värdena visas exakt som du förväntar dig.

Du kommer att lära dig hur du laddar en DOCX‑fil, hittar det första diagrammet, läser det aktuella formatet och sedan sätter ett nytt mönster, till exempel valuta med två decimaler. Handledningen täcker också hur du ändrar diagramaxelformat för ytterligare serier och hur du återställer formatet om det behövs.

## Förutsättningar

* .NET 6.0 eller senare installerat  
* Ett Visual Studio 2022‑projekt (eller någon IDE som stödjer .NET)  
* NuGet‑paketet **Aspose.Words for .NET** (`Aspose.Words`)  
* Ett Word‑dokument (`input.docx`) som innehåller minst ett diagram

Du kan lägga till paketet med följande kommando:

```bash
dotnet add package Aspose.Words
```

## Så formaterar du diagram i Word med Aspose.Words

Det följande kompletta programmet demonstrerar varje steg som krävs för att **formatera diagram**‑axelvärden. Spara filen som `Program.cs` och kör den från kommandoraden eller din IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Förklaring av varje steg

| Steg | Vad det betyder | Nyckelkod |
|------|----------------|-----------|
| **Läs in dokumentet** | Du behöver ett `Document`‑objekt för att arbeta med Word‑filen. | `new Document("input.docx")` |
| **Hämta diagrammet** | `Chart`‑objekt lagras som `Shape`‑noder; en castning låter dig använda diagram‑specifika API:er. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Åtkomst till X‑värden** | Axelformatering appliceras på värdesamlingen för en dataserie. | `chart.ChartData.Series[0].XValues` |
| **Läs aktuellt format** | Att känna till det befintliga `FormatCode` hjälper dig avgöra om du ska ersätta eller utöka det. | `xValues.FormatCode` |
| **Ange anpassat format** | `FormatCode`‑egenskapen accepterar vilket Excel‑kompatibelt mönster som helst, vilket möjliggör valuta, procent, datum osv. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Spara dokumentet** | Att spara ändringarna skriver tillbaka det nya axelformatet till DOCX‑filen. | `doc.Save("output_formatted.docx")` |

Att köra programmet producerar `output_formatted.docx`. Öppna det i Word så ser du diagrammets X‑axelvärden visas som **$1,234.00**, **$2,345.00**, … istället för rena siffror.

## Applicera anpassat talformat på diagramaxel

Om du behöver **applicera anpassat talformat** på Y‑axeln eller på ytterligare serier är processen identisk – bara rikta in dig på en annan samling:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Proffstips:** Använd dubbla citationstecken i formatsträngen för att bädda in bokstavliga tecken (t.ex. `"$"` för valuta). Escapea citationstecknen som visas ovan.

## Anpassat talformat i Word – hantera Word‑lokal

Word respekterar dokumentets lokal när talformat tolkas. Om dokumentet använder en icke‑US‑lokal kan du behöva justera formatsträngen:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Att testa formatet i ett dokument med tyska språkinställningar bekräftar att värdena visas som **€ 1.234,00**.

## Så sätter du diagramegenskaper programatiskt

Utöver axelformatering vill du ofta **sätta diagram**‑titlar, förklaringar eller datamärkningar. Här är ett snabbt kodexempel som demonstrerar hur du sätter en diagramtitel efter att du har formaterat axeln:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Att kombinera detta med det anpassade talformatet ger dig ett fullt polerat diagram redo för rapportering.

## Ändra diagramaxelformat dynamiskt baserat på användarinput

I verkliga applikationer kan du låta användare välja ett format vid körning. Följande metod kapslar in formateringslogiken:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Du kan anropa `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` för valuta eller `SetAxisFormat(chart, 0, "0%")` för procent. Detta tillvägagångssätt håller din huvudkod ren och stödjer framtida utökningar.

## Kantfall och vanliga fallgropar

| Situation | Vad att hålla utkik efter | Föreslagen lösning |
|-----------|---------------------------|--------------------|
| Dokumentet innehåller **inget diagram** | `GetChild` returnerar `null`, vilket orsakar ett cast‑undantag. | Kontrollera `null` innan du castar (se exempel). |
| Flera diagram i samma dokument | Koden hämtar alltid det första diagrammet (`index 0`). | Loopa igenom `doc.GetChildNodes(NodeType.Shape, true)` och filtrera på `ShapeType.Chart`. |
| Serier **utan X‑värden** (t.ex. pajdiagram) | Åtkomst till `XValues` kan kasta `ArgumentOutOfRangeException`. | Verifiera att `Series[i].XValues` inte är tomt innan formatering. |
| Lokalmismatch | Valutasymbolen kan visas felaktigt. | Ställ explicit in `xValues.FormatCode` med lämpliga lokalsymboler. |

## Förväntat resultat

Efter att ha kört exempelprogrammet, öppna **output_formatted.docx**. Diagrammets X‑axel bör visa siffror i det valda anpassade formatet. För valutaexemplet ser axel­etiketterna ut så här:

```
$1,000.00
$2,000.00
$3,000.00
```

Om du använde procentformatet på Y‑värdena visas Y‑axel­etiketterna så här:

```
10%
20%
30%
```

## Slutsats

Denna handledning visade dig **hur du formaterar diagram** i Word med C# genom att **applicera ett anpassat talformat** på axelvärden. Du har nu ett återanvändbart mönster för att sätta valuta, procent eller vilket annat numeriskt mönster som helst, samt vägledning för att hantera lokaler, flera serier och dynamisk användarinput.

Nästa steg kan vara att utforska **hur du sätter diagram**‑titlar, datamärkningar eller till och med exporterar diagrammet som en bild med `ChartRenderer`. Dessa ämnen bygger direkt på koncepten som behandlats här och hjälper dig att skapa helt automatiserade rapporteringslösningar.

---


## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Talformat för axel i ett diagram](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Formatera tal för datamärkning i ett diagram](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formatera sekundär X‑axel och sätt displayenheter till tusental i Word-linjediagram med Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}