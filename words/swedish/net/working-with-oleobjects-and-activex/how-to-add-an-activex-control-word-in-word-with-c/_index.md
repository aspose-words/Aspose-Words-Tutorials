---
category: general
date: 2026-09-30
description: Lägg till ett ActiveX‑kontrollord i ett Word‑dokument med C#. Lär dig
  hur du infogar en ActiveX‑knapp, lägger till en kommandoknapp och gör den klickbar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: sv
lastmod: 2026-09-30
og_description: Lägg till en ActiveX‑kontroll i ett Word‑dokument med C#. Följ den
  här kompletta guiden för att infoga en ActiveX‑knapp, lägga till en kommandoknapp
  och göra den klickbar.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Lägg till en ActiveX‑kontroll i Word‑dokument – steg‑för‑steg C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Hur man lägger till en ActiveX‑kontroll i Word med C#
url: /sv/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till ett ActiveX‑kontrollord i Word med C#

Om du behöver bädda in ett **ActiveX control word** i en Microsoft Word‑fil, visar den här guiden exakt hur du gör det. Du får se ett komplett, körbart exempel som infogar en klickbar knapp, sparar dokumentet och fungerar med den senaste Aspose.Words för .NET.

Att lägga till ett ActiveX control word låter dig skapa interaktiva formulär, anpassade dialogrutor eller enkla UI‑element som beter sig som inbyggda Word‑kontroller. Oavsett om du bygger en kontraktsmall som kräver användarinteraktion eller en rapport som behöver en “Run”-knapp, täcker stegen nedan allt du behöver.

## Förutsättningar

* .NET 6.0 SDK eller senare (koden fungerar även med .NET Framework 4.8)
* Visual Studio 2022 (eller någon IDE som stödjer C#)
* Aspose.Words för .NET installerat (`dotnet add package Aspose.Words`)
* Grundläggande kunskap om C# och Word‑dokumentstruktur

> **Pro tip:** Metoden `InsertForms2OleControl` fungerar endast med de äldre “Forms 2.0”-kontrollerna, vilka är de ActiveX‑kontroller som Word använder för formulärfält. Om du riktar dig mot nyare Office‑versioner renderas kontrollen fortfarande korrekt i skrivbordsklienten.

## Steg 1: Ställ in projektet och importera namnrymder

Skapa ett nytt konsolprojekt och lägg till de nödvändiga `using`‑satserna. Detta säkerställer att kompilatorn kan hitta klasserna `Document`, `DocumentBuilder` och `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words`‑namnrymden tillhandahåller hög‑nivå‑API:er för Word‑behandling, medan `Aspose.Words.Drawing` innehåller uppräkningen `OleControlType` som behövs för att ange typen av ActiveX‑kontroll.

## Steg 2: Ladda källdokumentet Word

Du måste börja med en Word‑fil som du vill ändra. Följande kod laddar `input.docx` från en mapp du anger.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Om filen inte finns, kastar Aspose.Words ett `FileNotFoundException`. Omge anropet med ett `try/catch`‑block om du behöver hantera fel på ett smidigt sätt.

## Steg 3: Skapa en DocumentBuilder för att redigera dokumentet

`DocumentBuilder` är arbetshästen för att infoga text, bilder och kontroller. Den håller ett markör som pekar på den plats där nästa element kommer att placeras.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Som standard är builder‑markören placerad i början av den första sektionen. Du kan flytta den med metoder som `MoveToDocumentEnd()` eller `MoveToParagraph(index)` om du vill ha knappen någon annanstans.

## Steg 4: Infoga en ActiveX CommandButton‑kontroll

Nu kommer kärnan i handledningen: att infoga ett **ActiveX control word** som visas som en klickbar knapp. Metoden `InsertForms2OleControl` tar två argument – kontrolltypen och en rubrik (eller namn) för kontrollen.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Varför använda `OleControlType.CommandButton`?**  
  Det instruerar Word att skapa en klassisk Forms 2.0‑kommandoknapp, som visar en rubrik och kan kopplas till ett makro eller VBA‑skript senare.

* **Vad gör rubriken?**  
  Strängen `"ClickMe"` blir knappens synliga text. Du kan ändra den till vad som helst som passar ditt UI.

### Infoga knappen på en specifik plats

Om du behöver knappen efter ett specifikt stycke, flytta builder först:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Steg 5: Spara det ändrade dokumentet

Efter att ha infogat kontrollen, spara ändringarna till en ny fil (eller skriv över originalet).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar `output.docx` i skrivbordsversionen av Word ser du knappen med etiketten **ClickMe** (eller **Submit**, beroende på vilken rubrik du använde). Att klicka på knappen i designläge gör ingenting som standard; du kan tilldela ett makro senare via Words “Developer”-flik.

## Fullt, körbart exempel

Nedan är ett fristående program som demonstrerar hela arbetsflödet. Kopiera det till `Program.cs` i en ny konsolapp och kör det.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Förväntad output

* Konsolen skriver ut framgångsmeddelandet med sökvägen till output‑filen.
* När du öppnar `output.docx` visas en **ClickMe**‑knapp på den plats där builder infogade den.
* Knappen kan väljas, ändras i storlek eller tilldelas ett makro via Words **Developer → Design Mode**.

## Vanliga frågor och hantering av kantfall

| Question | Answer |
|----------|--------|
| **Hur infogar man en ActiveX‑knapp i sidhuvudet/sidfoten?** | Flytta builder till sidhuvudet/sidfoten med `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` innan du anropar `InsertForms2OleControl`. |
| **Vad om jag behöver en kryssruta istället för en knapp?** | Använd `OleControlType.CheckBox` och ange en rubrik som `"Agree"`. |
| **Fungerar knappen i Word Online?** | Nej. Word Online stödjer inte äldre Forms 2.0‑ActiveX‑kontroller. Knappen renderas endast i skrivbordsklienten. |
| **Kan jag ställa in knappens storlek programatiskt?** | Efter infogning, hämta `Shape`‑objektet via `builder.CurrentParagraph.Runs[0].GetShape()` och justera `Width`/`Height`. |
| **Finns det ett sätt att tilldela ett makro via kod?** | Aspose.Words exponerar inte makroredigering. Du måste öppna dokumentet i Word och fästa ett makro manuellt eller använda Office Interop‑API:et. |

## Tips för produktionsanvändning

* **Undvik hårdkodade sökvägar** – använd `Path.Combine` och konfigurationsfiler.
* **Disposera `Document`** – omge den med ett `using`‑statement om du arbetar med stora filer för att frigöra minnet snabbt.
* **Validera output** – programatiskt kontrollera att dokumentet innehåller en shape av typen `OleControl` genom att iterera `doc.GetChildNodes(NodeType.Shape, true)`.
* **Säkerhetsnotering** – ActiveX‑kontroller kan köra kod på klientmaskinen. Distribuera endast dokument till betrodda användare och överväg digitala signaturer.

## Slutsats

Du vet nu hur du lägger till ett **ActiveX control word** i ett Word‑dokument med C#. Genom att ladda ett dokument, skapa en `DocumentBuilder`, infoga en kommandoknapp med `InsertForms2OleControl` och spara filen kan du automatisera skapandet av interaktiva Word‑formulär. Experimentera med andra `OleControlType`‑värden, placera kontroller i sidhuvuden eller tabeller och kombinera dem med makron för rikare användarupplevelser.

---

*Nästa steg*: utforska **how to insert ActiveX**‑kontroller av andra typer, lär dig **how to add command button**‑händelsehanterare via VBA, och läs om **insert ActiveX button**‑bästa praxis för plattformsoberoende kompatibilitet.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Bädda in OLE‑objekt och ActiveX‑kontroller i Word‑dokument](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Lägg till ett kombinationsruta‑formulärfält i ett Word‑dokument med Aspose.Words för .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Lägg till ett kryssruta‑formulärfält i ett Word‑dokument med Aspose.Words för .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}