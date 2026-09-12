---
category: general
date: 2026-09-11
description: Mail merge i Aspose låter dig ladda en Word‑mall och fylla i Word‑mallen
  med data, vilket automatiserar dokumentgenerering för att skapa personliga brev.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: sv
lastmod: 2026-09-11
og_description: Mail merge aspose låter dig ladda Word‑mall och fylla i Word‑mallen,
  vilket effektiviserar dokumentgenerering så att du snabbt kan skapa personliga brev.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mailmerge Aspose: fyll i en Word‑mall på några minuter'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Hur man utför mailmerge med Aspose för att fylla i en Word-mall
url: /sv/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man utför mail merge med Aspose för att fylla i en Word-mall

Om du behöver **mail merge aspose** för att generera en batch av personliga brev, visar den här guiden exakt hur du laddar en Word-mall, fyller den med data och automatiserar dokumentgenerering i några rader C#. Oavsett om du bygger ett utskicksystem eller ett rapportverktyg, låter det kompletta exemplet nedan dig skapa personliga brev utan att skriva någon manuell merge‑logik.

Du kommer att lära dig hur du **load word template**, använder den låga‑kod `MailMerger`‑klassen och **populate word template** med en anonym datakälla. I slutet av handledningen har du en färdig‑att‑köra konsolapp som producerar ett sammanslaget Word-dokument som du kan e‑posta, skriva ut eller arkivera.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* En giltig Aspose.Words för .NET-licens (eller en gratis utvärderingsnyckel)  
* NuGet‑paketet `Aspose.Words` (version 23.10 eller nyare) installerat i ditt projekt  
* En Word‑fil (`MailMergeTemplate.docx`) som innehåller MERGEFIELD‑platshållare såsom **«Name»** och **«Age»**  

Du kan skapa mallen i Microsoft Word genom att infoga *Insert → Quick Parts → Field → MergeField* och namnge fälten exakt som egenskapsnamnen i din datakälla.

## Steg 1 – Förbered datakällan för mail merge

Den låga‑kod‑sammanfogningen fungerar med vilken enumererbar samling som helst. I det här exemplet använder vi en array av anonyma objekt, men du kan också skicka en `DataTable`, en lista med POCOs eller data lästa från en databas.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Varför detta är viktigt:**  
Varje objekts egenskapsnamn (`Name`, `Age`) måste matcha ett MERGEFIELD i mallen. `MailMerger`‑klassen mappar automatiskt egenskaperna till fälten, vilket eliminerar behovet av manuella `FieldMerging`‑händelser.

## Steg 2 – Ladda Word‑mallen som innehåller MERGEFIELD‑fält

Att ladda mallen är enkelt med `Document`‑klassen. Sökvägen kan vara absolut eller relativ till den körbara filens arbetskatalog.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Proffstips:**  
Om du kör koden från Visual Studio, ställ in *Copy to Output Directory* för mallfilen till **Copy always**. Detta garanterar att filen är tillgänglig när den kompilerade binären körs.

## Steg 3 – Skapa en MailMerger‑instans bunden till mallen

`MailMerger`‑klassen finns i `Aspose.Words.LowCode`‑namnrymden och tillhandahåller en enda `Execute`‑metod som accepterar datakällan.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Varför använda MailMerger?**  
`MailMerger` abstraherar bort den repetitiva `MailMerge.Execute`‑koden, hanterar fältidentifiering, databindning och dokumentkloning internt. Detta gör koden idealisk för scenarier som **automate document generation** där du vill ha en ren, låga‑kod‑lösning.

## Steg 4 – Utför den låga‑kod‑sammanfogningen med den förberedda datan

Att anropa `Execute` returnerar ett nytt `Document` som innehåller

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Byt namn på Word Merge-fält med Aspose.Words för Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Skapa Word-dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Skapa och formatera ett Word-dokument i Aspose.Words för .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}