---
category: general
date: 2026-08-10
description: Generera flera Word-dokument med Aspose.Words i C#. Lär dig hur du skapar
  fakturor från en mall och batchgenererar Word-filer effektivt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate multiple word documents
- create invoices from template
- batch generate word files
- Aspose.Words mail merge
- C# document automation
language: sv
lastmod: 2026-08-10
og_description: Skapa flera Word‑dokument med Aspose.Words. Denna handledning visar
  hur du skapar fakturor från en mall och batchgenererar Word‑filer i C#.
og_image_alt: Screenshot of generate multiple word documents result
og_title: Skapa flera Word‑dokument – Aspose.Words steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  headline: Generate multiple word documents with Aspose.Words
  type: TechArticle
- description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  name: Generate multiple word documents with Aspose.Words
  steps:
  - name: Prepare the data that will populate the merge fields
    text: The mail‑merge engine expects a collection of objects whose property names
      match the `MERGEFIELD` names in the template. In this example we use an anonymous
      type array, but you can replace it with a list of strongly‑typed DTOs.
  - name: Load the Word template that contains MERGEFIELD placeholders
    text: '```csharp // Step 2 – load template Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
      ```'
  - name: Merge the data into the template – one‑line call creates a single document
    text: '```csharp // Step 3 – perform the merge Document mergedDocument = MailMerger.Merge(template,
      invoiceData); ```'
  - name: Split the merged document into separate files and save each one
    text: '```csharp // Step 4 – split and save each invoice int invoiceNumber = 1;
      foreach (Document singleInvoice in mergedDocument.Split()) { string outputPath
      = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx"; singleInvoice.Save(outputPath);
      } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- MailMerge
- Document Automation
title: Skapa flera Word‑dokument med Aspose.Words
url: /sv/net/add-content-using-document-builder/generate-multiple-word-documents-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generera flera Word-dokument med Aspose.Words

Om du behöver **generera flera Word-dokument** i C#, erbjuder Aspose.Words ett koncist API som tar bort boilerplate‑koden för filhantering. Oavsett om du bygger ett faktureringssystem eller behöver producera en uppsättning personliga brev, visar den här guiden hur du **skapar fakturor från mall** och **batch‑genererar Word‑filer** med bara några rader kod.

Du kommer att lära dig hur du:

* Förbereda data för en mail‑merge‑operation.  
* Ladda en Word‑mall som innehåller `MERGEFIELD`‑platshållare.  
* Sammanfoga data till ett enda dokument och dela upp det i enskilda filer.  
* Spara varje genererad fil med ett unikt namn.

Ingen extern verktyg behövs utöver Aspose.Words för .NET‑biblioteket, och det kompletta kodexemplet körs på .NET 6 eller senare.

## Förutsättningar och installation

Innan du börjar, se till att du har:

| Krav | Orsak |
|------|-------|
| .NET 6 SDK (or newer) | Koden använder moderna C#‑funktioner såsom target‑typed `new`. |
| Aspose.Words for .NET NuGet package | Tillhandahåller API:erna `Document`, `MailMerger` och `Split`. |
| A Word template (`InvoiceTemplate.docx`) containing `MERGEFIELD` tags | Fungerar som källa för **skapa fakturor från mall**. |
| An IDE (Visual Studio, Rider, or VS Code) | För att bygga och felsöka projektet. |

Install the NuGet package with the following command:

```bash
dotnet add package Aspose.Words
```

Placera `InvoiceTemplate.docx` i en mapp som du kan referera till från koden, till exempel `YOUR_DIRECTORY`.

## Så genererar du flera Word-dokument med en mail‑merge

Kärnan i lösningen består av fyra logiska steg. Varje steg är inbäddat i ett tydligt metodanrop, vilket gör koden lätt att läsa och underhålla.

### Steg 1: Förbered data som ska fylla i merge‑fälten

Mail‑merge‑motorn förväntar sig en samling objekt vars egenskapsnamn matchar `MERGEFIELD`‑namnen i mallen. I det här exemplet använder vi en anonym typ‑array, men du kan ersätta den med en lista av starkt typade DTO:er.

```csharp
// Step 1 – data preparation
var invoiceData = new[]
{
    new { Name = "Alice", Amount = 123.45 },
    new { Name = "Bob",   Amount = 678.90 }
};
```

**Varför detta är viktigt:**  
Att tillhandahålla en starkt typad datakälla garanterar att varje platshållare får rätt värde, vilket är avgörande när du **batch‑genererar Word‑filer** för många mottagare.

### Steg 2: Ladda Word‑mallen som innehåller MERGEFIELD‑platshållare

```csharp
// Step 2 – load template
Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
```

**Varför detta är viktigt:**  
`Document`‑klassen representerar hela Word‑filen i minnet. Att ladda mallen en gång och återanvända den undviker onödig I/O när du senare **genererar flera Word-dokument**.

### Steg 3: Sammanfoga data i mallen – ett‑rad‑anrop skapar ett enda dokument

```csharp
// Step 3 – perform the merge
Document mergedDocument = MailMerger.Merge(template, invoiceData);
```

`MailMerger.Merge` itererar över datainsamlingen, infogar en kopia av mallen för varje rad och fyller i `MERGEFIELD`‑värdena. Resultatet är ett enda `Document` som innehåller alla fakturor i följd.

### Steg 4: Dela det sammanslagna dokumentet i separata filer och spara varje fil

```csharp
// Step 4 – split and save each invoice
int invoiceNumber = 1;
foreach (Document singleInvoice in mergedDocument.Split())
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
    singleInvoice.Save(outputPath);
}
```

`Split()`‑extensionen går igenom det sammanslagna dokumentet och returnerar en ny `Document`‑instans för varje datarad. Att spara varje `singleInvoice` skapar en separat fil, vilket slutför arbetsflödet för **batch‑generera Word‑filer**.

#### Fullt körbart exempel

Nedan är det kompletta programmet som knyter ihop de fyra stegen. Kopiera det till ett nytt konsolprojekt och kör det efter att du justerat sökvägarna.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Step 1 – prepare data
        var invoiceData = new[]
        {
            new { Name = "Alice", Amount = 123.45 },
            new { Name = "Bob",   Amount = 678.90 }
        };

        // Step 2 – load the template
        Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");

        // Step 3 – merge data into a single document
        Document mergedDocument = MailMerger.Merge(template, invoiceData);

        // Step 4 – split and save each invoice
        int invoiceNumber = 1;
        foreach (Document singleInvoice in mergedDocument.Split())
        {
            string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
            singleInvoice.Save(outputPath);
        }

        System.Console.WriteLine("Invoices generated successfully.");
    }
}
```

**Förväntad output:**  
När programmet körs skapas `Invoice_1.docx`, `Invoice_2.docx`, … i den angivna katalogen. Varje fil innehåller fakturadata för en kund, där merge‑fälten har ersatts med värdena från `invoiceData`.

## Skapa fakturor från mall – hantera vanliga fallgropar

När du **skapar fakturor från mall** kan du stöta på några problem. Nedan följer praktiska tips för att undvika dem.

| Problem | Lösning |
|---------|---------|
| Mallens fältnamn matchar inte egenskapsnamnen | Se till att egenskapsnamnen (`Name`, `Amount`) exakt matchar `MERGEFIELD`‑taggarna i Word‑filen. |
| Stora datamängder orsakar hög minnesanvändning | Bearbeta data i delar: slå ihop en delmängd, dela, spara och släng sedan det mellanstegsdokumentet innan nästa batch. |
| Specialtecken (t.ex. “&”, “<”) visas felaktigt | Aspose.Words kodar automatiskt XML‑osäkra tecken, men kontrollera mallens kodning om du laddar den från en källa som inte är UTF‑8. |
| Behöver anpassade filnamn (t.ex. inkludera kundnamn) | Byt ut `outputPath`‑strängen till `$\"YOUR_DIRECTORY/Invoice_{singleInvoice.MailMergeData[\"Name\"]}.docx\"` efter att ha extraherat fältvärdet från det delade dokumentet. |

## Batch‑generera Word‑filer – prestandaöverväganden

Om du planerar att **batch‑generera Word‑filer** för tusentals poster, håll dessa riktlinjer i åtanke:

1. **Återanvänd mallobjektet** – att ladda mallen en gång (som visas i Steg 2) förhindrar upprepade läsningar från disk.
2. **Frigör mellandokument** – `foreach`‑loopen frigör automatiskt minnet efter varje `singleInvoice.Save`, men du kan anropa `singleInvoice.Dispose()` explicit för mycket stora batcher.
3. **Parallellisera sparsteget** – split‑operationen ger oberoende `Document`‑objekt, så du kan använda `Parallel.ForEach` för att skriva filer samtidigt, förutsatt att lagringsmediet klarar parallell I/O.

```csharp
using System.Threading.Tasks;

// ...

Parallel.ForEach(mergedDocument.Split(), (singleInvoice, state, index) =>
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{index + 1}.docx";
    singleInvoice.Save(outputPath);
});
```

**Varför detta fungerar:**  
`Split()` returnerar ett `IEnumerable<Document>` som kan itereras säkert parallellt eftersom varje `Document`‑instans äger sitt eget minne.

## Förväntade resultat och verifiering

Efter att programmet har avslutats, öppna någon genererad faktura i Microsoft Word:

* Platshållaren `«Name»` har ersatts med “Alice” eller “Bob”.  
* Platshållaren `«Amount»` visar motsvarande numeriska värde formaterat med dokumentets standardnummerformat.  
* Sidlayout, sidhuvuden och sidfötter från den ursprungliga mallen bevaras.

Om något fält förblir tomt, dubbelkolla `MERGEFIELD`‑namnen i mallen mot egenskapsnamnen i `invoiceData`.

## Slutsats

Du vet nu hur du **genererar flera Word-dokument** med Aspose.Words, hur du **skapar fakturor från mall**, och hur du **batch‑genererar Word‑filer** effektivt. Det fyrastegsmönster – förbered data, ladda mall, slå ihop, dela & spara – täcker de vanligaste dokument‑automatiseringsscenarierna.

Härifrån kan du utöka lösningen genom att lägga till bilder, tabeller eller villkorlig logik i mallen, eller genom att integrera arbetsflödet i ett webb‑API som levererar fakturor på begäran.

---

![Skärmdump av generera flera Word-dokument](generate-multiple-word-documents.png){: .align-center alt="Skärmdump av resultatet för att generera flera Word-dokument"}

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Lägg till och sätt in innehåll i Word-dokument med Aspose.Words](/words/english/net/document-sections/append-section-content/)
- [Kombinera flera Word-filer med Aspose.Words för Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)
- [Applicera radformatering i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-table-styles-and-formatting/apply-row-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}