---
category: general
date: 2026-09-08
description: Hämta slutnotseparator och visa fotnotseparator när du laddar ett Word‑dokument
  med Aspose.Words för .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: sv
lastmod: 2026-09-08
og_description: Hämta slutnotseparator och visa fotnotseparator när du laddar ett
  Word-dokument med Aspose.Words för .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Hämta slutnotseparator vid inläsning av ett Word‑dokument i C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Hämta slutnotseparator när du läser in ett Word‑dokument i C#
url: /sv/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hämta slutnotseparator vid inläsning av ett Word-dokument i C#

Om du behöver **retrieve endnote separator** från en Word-fil visar den här guiden exakt hur du gör det. Du kommer också att lära dig hur du **load Word document** med Aspose.Words och **display footnote separator**-text i konsolen, allt i ett enda körbart exempel.

Att arbeta med fotnoter och slutnoter är ett vanligt krav för juridiska, akademiska eller publiceringsapplikationer. Denna handledning täcker allt du behöver—från att öppna filen till att hantera fall där en separator saknas—så att du kan integrera lösningen i vilket .NET-projekt som helst utan gissningar.

## Vad den här handledningen täcker

* Hur man **load Word document** med Aspose.Words API.  
* Hur man **retrieve endnote separator** och varför separatorn är viktig.  
* Hur man **display footnote separator** i konsolen för felsökning eller loggning.  
* Hantera edge‑case när ett dokument saknar fotnoter eller slutnoter.  
* Ett komplett, copy‑paste‑klart kodexempel som körs på .NET 6 eller senare.

### Förutsättningar

| Krav | Orsak |
|-------------|--------|
| .NET 6 SDK eller nyare | Tillhandahåller runtime för C#‑exemplet. |
| Aspose.Words for .NET (NuGet‑paket `Aspose.Words`) | Biblioteket som exponerar `Document.Footnotes` och `Document.Endnotes`. |
| En Word‑fil (`Footnotes.docx`) som innehåller minst en fotnot eller slutnot | Visar separatorerna. |
| Valfri IDE (Visual Studio, Rider, VS Code) | För att kompilera och köra programmet. |

> **Pro tip:** Om du inte har ett dokument med fotnoter, skapa ett snabbt i Microsoft Word: Insert → Footnote → skriv lite text, spara sedan som `Footnotes.docx`.

## Ladda Word-dokument med Aspose.Words

Det första steget är att **load word document** i minnet. Aspose.Words läser filformatet och bygger en objektmodell som du kan fråga.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Varför detta är viktigt*: Att ladda dokumentet är förutsättningen för all vidare manipulation. Om filsökvägen är felaktig kastar `Document` ett `FileNotFoundException`, så verifiera sökvägen innan du kör.

## Hämta fotnotseparator‑paragraf

En fotnotseparator är paragrafen som visuellt separerar huvudtexten från listan med fotnoter. Att hämta den låter dig inspektera eller ändra dess formatering.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Varför detta är viktigt*: **Display footnote separator** hjälper dig att verifiera att rätt paragraf nås, särskilt när du behöver tillämpa anpassad stil (t.ex. en linje eller ett specifikt teckensnitt).

## Hämta slutnotseparator‑paragraf

Nu **retrieve endnote separator**. Processen speglar fotnotshantering men använder `Endnotes`‑samlingen.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Varför detta är viktigt*: Steget **retrieve endnote separator** är avgörande när du behöver justera den visuella brytningen mellan huvudinnehållet och listan med slutnoter—vanligt i akademisk publicering där slutnoter visas i slutet av ett kapitel.

### Hantera saknade separatorer

Både `Footnotes.Separator` och `Endnotes.Separator` returnerar `null` när dokumentet inte definierar en separator. Kontrollera alltid `null` innan du anropar `GetText()` för att undvika ett `NullReferenceException`. Om du behöver en standardsseparator kan du skapa en:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Denna kod injicerar en minimal separator så att senare bearbetning kan lita på dess existens.

## Förväntad konsolutdata

När exemplet körs mot ett dokument som innehåller en fotnot och en slutnot bör du se något liknande:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Om dokumentet saknar fotnoter eller slutnoter skriver programmet ut motsvarande “not found”-meddelanden, vilket visar på elegant felhantering.

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera in i ett nytt C#‑konsolprojekt. Ingen extra kod behövs.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Spara filen som `Program.cs`, lägg till Aspose.Words‑NuGet‑paketet (`dotnet add package Aspose.Words`), och kör `dotnet run`. Programmet kommer att skriva ut separatortexterna eller meddela dig om de saknas.

## Vanliga variationer och vad‑om‑scenarier

| Scenario | Hur man anpassar koden |
|----------|-----------------------|
| **Multiple custom separators** | Använd `doc.Footnotes.Separator` för att ersätta standarden, lägg sedan till ytterligare separatorparagrafer manuellt med `doc.Footnotes.Add(separatorParagraph)`. |
| **Changing separator style** | Efter att ha hämtat separatorn, ändra dess `ParagraphFormat` (t.ex. `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Working with .doc files** | Samma API fungerar; se bara till att filsökvägen slutar med `.doc`. |
| **Processing many documents** | Omslut inläsning och separatorhämtning i en `foreach`‑loop; återanvänd en enda `Document`‑instans endast om du återställer den med `doc = new Document(path)`. |

## Checklista för bästa praxis

- ✅ **Always check for `null`** innan du får åtkomst till separatortexten.  
- ✅ **Trim** resultatet av `GetText()` för att ta bort dolda radbrytningstecken.  
- ✅ **Dispose** stora `Document`‑objekt om du bearbetar många filer i en batch (använd `using` eller anropa `doc.Dispose()`).  
- ✅ **Log** separatortext endast i utveckling; undvik att exponera den i produktionsloggar om det inte krävs.  

## Slutsats

Du vet nu hur du **retrieve endnote separator** medan du **load Word document** och **display footnote separator** i en .NET‑konsolapplikation. Det kompletta exemplet demonstrerar inläsning, frågning och säker hantering av saknade separatorer, vilket ger dig en solid grund för alla fotnot‑ eller slutnot‑manipuleringsuppgifter.

Nästa steg kan du utforska:

* **Customizing footnote/endnote formatting** – justera teckensnitt, ramar eller numreringsstilar.  
* **Extracting footnote/endnote content** – iterera `doc.Footnotes` eller `doc.Endnotes`‑samlingarna.  
* **Saving the modified document** – använd `doc.Save("output.docx")` för att spara ändringarna.

Känn dig fri att experimentera med olika Word‑filer, separatorstilar och Aspose.Words‑funktioner. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man laddar Word-dokument med Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Hämta styckeformatseparator i Word-dokument](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Skapa och formatera ett Word-dokument i Aspose.Words för .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}