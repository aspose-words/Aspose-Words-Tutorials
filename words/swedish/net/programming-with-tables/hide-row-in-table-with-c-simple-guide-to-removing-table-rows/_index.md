---
category: general
date: 2026-02-21
description: Dölj rad i en tabell med C# och Aspose.Words. Lär dig hur du döljer en
  rad, hur du döljer en rad i Word och tar bort en rad från en tabell snabbt och säkert.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: sv
og_description: Dölj rad i tabell med C# och Aspose.Words. Den här guiden visar hur
  du döljer en rad, tar bort en rad från tabellen och döljer en rad i Word-dokument.
og_title: Dölj rad i tabell med C# – Snabb, pålitlig metod
tags:
- C#
- Aspose.Words
- Word Automation
title: Dölj rad i tabell med C# – En enkel guide för att ta bort tabellrader
url: /sv/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dölj rad i tabell – Komplett C#‑handledning

Har du någonsin behövt **dölja rad i tabell** när du genererar ett Word‑dokument programatiskt? Du är inte ensam—utvecklare frågar ständigt *hur man döljer rad* utan att förstöra layouten. Den goda nyheten? Med några rader C# och det kraftfulla Aspose.Words‑biblioteket kan du dölja en rad, effektivt ta bort den från slutresultatet, och hålla koden ren.

I den här guiden går vi igenom hela processen: läsa in en `.docx`, välja exakt den rad du vill, sätta dess `Hidden`‑egenskap och spara resultatet. När du är klar vet du exakt hur du döljer rad i Word, hur du tar bort rad från tabell om du föredrar deletion, och du har ett färdigt kodexempel som du kan klistra in i vilket .NET‑projekt som helst. Inga externa referenser behövs—bara koden och tydliga förklaringar.

**Vad du får**  
- En steg‑för‑steg‑genomgång av C#‑API‑et.  
- Fullt körbar kod (inklusive imports).  
- Tips för kantfall som dolda rader i sammanslagna celler.  
- Pro‑tips om när du ska *dölja rad* kontra *ta bort rad från tabell*.

> **Förutsättning:** Visual Studio (eller någon C#‑IDE) och Aspose.Words for .NET NuGet‑paketet (version 23.9 eller senare). Om du är ny på Aspose.Words är biblioteket en ren‑managed lösning—ingen Office‑installation behövs.

---

## Dölj rad i tabell – Steg‑för‑steg‑implementation

Nedan följer det kompletta, självständiga exemplet. Det demonstrerar den **primära** uppgiften—*dölja rad i tabell*—och visar också hur du kan *ta bort rad från tabell* om du bestämmer dig för att radera den istället.

![Dölj rad i tabell exempel](hide-row-in-table.png "Skärmbild som visar en Word‑tabell med den tredje raden dold")

### 1. Läs in källdokumentet  

Först måste vi läsa in Word‑filen i minnet. Klassen `Document` representerar hela filen.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Varför detta är viktigt:* Att läsa in dokumentet ger dig åtkomst till sektioner, kroppar och tabeller. Utan detta steg kan du inte manipulera rader över huvudtaget.

### 2. Hitta den önskade tabellen  

För enkelhetens skull hämtar vi den första tabellen i den första sektionen, men du kan söka efter index, namn eller till och med innehåll.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Tips:** Om ditt dokument har flera tabeller, iterera `doc.GetChildNodes(NodeType.Table, true)` och plocka den du behöver.

### 3. Välj den rad du vill dölja  

Här riktar vi in oss på den tredje raden (noll‑baserat index `2`). Du kan också använda `Rows.Count` för att verifiera att indexet finns.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Varför detta är viktigt:* Att välja rätt rad är kärnan i **hur man döljer rad**. Ett felaktigt index döljer fel innehåll.

### 4. Dölj den valda raden  

Genom att sätta `Hidden = true` instruerar du Aspose.Words att utelämna raden när dokumentet sparas. Raden finns fortfarande kvar i objektmodellen, så du kan avdölj den senare om så behövs.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Pro‑tips:** Om du verkligen vill *ta bort rad från tabell* istället för att dölja, anropa `table.Rows.Remove(rowToHide);`. Att dölja bevarar radmetadata, vilket kan vara praktiskt för villkorlig formatering.

### 5. Spara det uppdaterade dokumentet  

Till sist skriver vi förändringarna tillbaka till disk.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

När du öppnar `output.docx` i Word kommer den tredje raden att vara osynlig—precis vad **dölj rad i word** betyder i praktiken.

---

## Så här döljer du rad – Vanliga varianter & kantfall

### Dölj flera rader  

Om du behöver dölja flera rader, loopa igenom samlingen:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Hantera sammanslagna celler  

En dold rad som innehåller en vertikalt sammanslagen cell kan ge layoutvarningar. Det säkra tillvägagångssättet är att dela upp sammanslagningen innan du döljer:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Kompatibilitet med äldre Word‑versioner  

Aspose.Words skriver attributet `w:hideMark`, vilket förstås av Word 2007+ och LibreOffice. Om du riktar dig mot Word 97‑2003 (`.doc`) kommer den dolda raden fortfarande att utelämnas, men komplexa tabeller kan renderas annorlunda. Håll dig till `.docx` för förutsägbara resultat.

### När du ska *dölja rad* kontra *ta bort rad från tabell*  

- **Dölj rad** – Behåll raden för eventuell senare avdöljning, bevara radens höjd för sidbrytningsberäkningar.  
- **Ta bort rad** – Minska filstorlek, radera data permanent. Använd `table.Rows.Remove(row)` om du är säker på att raden inte behövs igen.

---

## Pro‑tips & fallgropar

- **Pro‑tips:** Kontrollera alltid `table.Rows.Count` innan du åtkommer ett index för att undvika `ArgumentOutOfRangeException`.  
- **Se upp för:** Dolda rader deltar fortfarande i tabellberäkningar som totalhöjd. Om du märker oväntade mellanrum, överväg att sätta `row.Height = 0` efter döljning.  
- **Prestanda:** Att dölja rader är billigt; att ta bort rader triggar en omlayout av hela tabellen, vilket kan vara långsammare i stora dokument.  
- **Testning:** Öppna den sparade filen i Word och använd **Reveal Formatting** (`Shift+F1`) för att verifiera att radens `Hidden`‑flagga är satt.

---

## Komplett fungerande exempel (Kopiera‑klistra‑klart)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Förväntat resultat:** Öppna `output.docx` och du kommer att se att tabellen saknar den tredje raden, medan resten av innehållet förblir intakt. Den dolda raden är fortfarande en del av dokumentmodellen, så du kan senare sätta `row.Hidden = false` för att göra den synlig igen.

---

## Slutsats

Vi har precis gått igenom **hur man döljer rad** i en Word‑tabell med C#. Genom att läsa in dokumentet, lokalisera tabellen, välja mål‑rad, markera den som dold och spara, får du en ren *dölj rad i tabell*-operation utan att radera data. Samma mönster låter dig *ta bort rad från tabell* om du behöver en permanent förändring, och extra tips hjälper dig undvika vanliga fallgropar med sammanslagna celler eller äldre Word‑versioner.

Redo för nästa utmaning? Prova att kombinera tekniken med villkorlig logik—dölj rader baserat på användarinmatning, eller generera dynamiska rapporter där vissa sektioner försvinner automatiskt. Du kan också utforska **dölj rad i word** för rubriker, sidhuvuden eller hela sektioner.

Har du frågor om *dölj rad c#* eller behöver hjälp att integrera detta i ett större arbetsflöde? Lämna en kommentar nedan eller kolla in våra relaterade handledningar om **manipulering av tabeller i Word med Aspose.Words**. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}