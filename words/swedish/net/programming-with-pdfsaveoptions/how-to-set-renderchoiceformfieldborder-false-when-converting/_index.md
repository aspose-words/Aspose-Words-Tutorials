---
category: general
date: 2026-09-21
description: Lär dig hur du sätter RenderChoiceFormFieldBorder till false i Aspose.Words
  för att exportera Word‑formulärfält utan kanter. Inkluderar fullständig kod och
  tips.
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
language: sv
lastmod: 2026-09-21
og_description: Sätt RenderChoiceFormFieldBorder till false för att ta bort kanter
  från valformulärfält när du konverterar Word till PDF med Aspose.Words.
og_image_alt: PDF preview showing choice form fields without borders after setting
  RenderChoiceFormFieldBorder false
og_title: Sätt RenderChoiceFormFieldBorder till false för ren PDF‑export
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
title: Hur man ställer in RenderChoiceFormFieldBorder till false när man konverterar
  Word till PDF
url: /sv/net/programming-with-pdfsaveoptions/how-to-set-renderchoiceformfieldborder-false-when-converting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur du sätter RenderChoiceFormFieldBorder till false när du konverterar Word till PDF

Om du behöver **sätta RenderChoiceFormFieldBorder till false** när du exporterar ett Word‑dokument som innehåller valformulärfält, visar den här guiden exakt vilka steg du ska följa. Genom att inaktivera kantritningen blir den resulterande PDF‑filen renare och matchar layouten i originaldokumentet.

I den här tutorialen lär du dig hur du konfigurerar **PdfSaveOptions** i Aspose.Words, varför inställningen är viktig, och hur du hanterar vanliga kantfall såsom dokument utan några formulärfält. Lösningen fungerar med den senaste Aspose.Words för .NET (v23.10 vid skrivande stund) och kräver bara några rader C#‑kod.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare installerat.  
* En giltig licens för Aspose.Words för .NET (eller en gratis utvärderingsnyckel).  
* Ett Word‑dokument (`.docx`) som innehåller valformulärfält (t.ex. rullgardinslistor eller kombinationsrutor).  
* Visual Studio 2022 (eller någon annan C#‑IDE).

## Steg 1: Läs in källdokumentet Word

Det första steget är att skapa ett `Document`‑objekt som representerar din källfil. Aspose.Words läser in filen i minnet, så att du kan inspektera eller ändra dess innehåll innan konverteringen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains choice form fields
Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");
```

**Varför det är viktigt:** När du har laddat dokumentet får du åtkomst till samlingen av formulärfält, som du senare kan fråga för att bekräfta att filen faktiskt innehåller valfält. Om dokumentet saknar sådana fält har inställningen `RenderChoiceFormFieldBorder` ingen visuell effekt, men koden körs ändå säkert.

## Steg 2: Konfigurera PdfSaveOptions och sätt RenderChoiceFormFieldBorder till false

`PdfSaveOptions` styr varje aspekt av PDF‑utdata, från bildkvalitet till renderning av formulärfält. Att sätta `RenderChoiceFormFieldBorder` till `false` instruerar renderaren att utelämna den grå rektangeln som normalt omger rullgardins‑ och kombinationsrutor.

```csharp
// Create PDF save options and disable the rendering of choice field borders
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false
};
```

**Varför det är viktigt:** Som standard ritar Aspose.Words en tunn kant runt valformulärfält så att användare kan se var de ska interagera. I många publiceringsscenario – såsom utskrivbara formulär eller polerade rapporter – är kanten oönskad. Flaggan `RenderChoiceFormFieldBorder` ger ett enkelt sätt att stänga av den.

### Ytterligare PdfSaveOptions du kanske vill sätta

| Alternativ                 | Typiskt värde                     | När du ska använda det |
|----------------------------|-----------------------------------|------------------------|
| `Compliance`               | `PdfCompliance.PdfA1b`            | För arkiverings‑PDF:er |
| `EmbedStandardFonts`       | `true`                            | För att undvika teckensnittsersättning på andra maskiner |
| `SaveFormat`               | `SaveFormat.Pdf`                  | Anger uttryckligen målformatet (valfritt) |

Du kan kedja dessa inställningar med kantflaggan:

```csharp
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false,
    Compliance = PdfCompliance.PdfA1b,
    EmbedStandardFonts = true
};
```

## Steg 3: Spara dokumentet som PDF med de konfigurerade alternativen

Nu när alternativen är satta, anropa `Document.Save` med destinationssökvägen och instansen av `PdfSaveOptions`.

```csharp
// Save the document as a PDF using the configured options
doc.Save("YOUR_DIRECTORY/NoBorderChoice.pdf", pdfOptions);
```

**Varför det är viktigt:** `Save`‑metoden utför själva konverteringen. Eftersom `pdfOptions` innehåller `RenderChoiceFormFieldBorder = false` kommer den genererade PDF‑filen att innehålla valfälten **utan** den omgivande kanten.

### Verifiera resultatet

Öppna `NoBorderChoice.pdf` i någon PDF‑visare (Adobe Acrobat, Foxit Reader eller webbläsaren). Du bör se rullgardins‑ eller kombinationsrutorna renderade som enkla textplatshållare – ingen grå rektangel syns. Fälten förblir interaktiva; ett klick visar fortfarande listan med val.

## Hantera kantfall

| Situation                                          | Rekommenderad åtgärd |
|----------------------------------------------------|----------------------|
| **Dokumentet har inga valformulärfält**           | Kanten har ingen effekt. Du kan valfritt kontrollera `doc.Range.FormFields.Count` innan konvertering för att hoppa över onödig konfiguration. |
| **Lösenordsskyddad Word‑fil**                     | Läs in dokumentet med ett `LoadOptions`‑objekt som innehåller lösenordet, och tillämpa sedan samma `PdfSaveOptions`. |
| **Stora dokument (> 100 MB)**                      | Använd `MemoryOptimization`‑alternativ på `PdfSaveOptions` för att minska minnesförbrukningen under konverteringen. |
| **Behov av att behålla kanten för specifika fält** | Efter att ha läst in dokumentet, iterera över `doc.Range.FormFields`, sätt `FieldType` till `FieldType.FieldFormDropDown` eller `FieldFormComboBox`, och justera egenskapen `Border` manuellt innan du sparar. |

### Exempelkod för att kontrollera formulärfält

```csharp
int choiceFieldCount = 0;
foreach (FormField field in doc.Range.FormFields)
{
    if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
        choiceFieldCount++;
}
Console.WriteLine($"Document contains {choiceFieldCount} choice form fields.");
```

Om `choiceFieldCount` är noll kan du hoppa över kantkonfigurationen helt, vilket sparar en liten mängd bearbetningstid.

## Fullt fungerande exempel

Nedan följer det kompletta, körbara programmet som sätter ihop allt. Ersätt `YOUR_DIRECTORY` med den faktiska sökvägen på din maskin.

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

**Förväntad utskrift i konsolen**

```
Found 3 choice form fields.
PDF saved to C:\MyProjects\NoBorderChoice.pdf with borders disabled.
```

När du öppnar `NoBorderChoice.pdf` visas rullgardinsfälten utan den förvalda grå kanten, vilket ger dokumentet ett renare utseende samtidigt som interaktiviteten bevaras.

## Pro‑tips och vanliga fallgropar

* **Pro‑tips:** Om du genererar PDF‑filer i en webbtjänst, sätt `pdfOptions.SaveFormat = SaveFormat.Pdf` explicit för att undvika oavsiktliga formatdetekteringsproblem.  
* **Se upp för:** Äldre versioner av Aspose.Words (före v20) exponerar inte `RenderChoiceFormFieldBorder`. Uppgradera till den senaste releasen för att kunna använda flaggan.  
* **Prestandatips:** Återanvänd en enda `PdfSaveOptions`‑instans när du konverterar många dokument i en batch; att skapa ett nytt objekt varje gång ger onödig overhead.  
* **Testtips:** Inkludera ett enhetstest som läser in ett känt `.docx` med en rullgardinslista, kör konverteringen och verifierar att den resulterande PDF‑strömmen inte innehåller PDF‑annoteringen `/Border` för dessa fält.

## Slutsats

Du vet nu **hur du sätter RenderChoiceFormFieldBorder till false** för att generera PDF‑filer utan kantlinjer på valfält med Aspose.Words. Lösningen täcker inläsning av dokumentet, konfiguration av `PdfSaveOptions`, sparande av PDF‑filen och hantering av kantfall såsom saknade formulärfält eller lösenordsskyddade källor.  

Nästa steg kan vara att utforska relaterade ämnen som **disable choice field border** för andra formulärfälttyper, eller lära dig hur du **konverterar Word till PDF** med anpassad bildupplösning via `ImageSaveOptions`. Båda ämnena fördjupar din behärskning av **Aspose.Words PDF‑konvertering** och ger dig full kontroll över det slutgiltiga dokumentets utseende.

Happy coding!

## Vad bör du lära dig härnäst?

De följande handledningarna behandlar nära besläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringssätt i dina egna projekt.

- [convert word to pdf in C# using Aspose.Words – Guide](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [Aspose Words के साथ Word को PDF के रूप में सहेजें – पूर्ण C# गाइड](/words/hindi/net/programming-with-pdfsaveoptions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}