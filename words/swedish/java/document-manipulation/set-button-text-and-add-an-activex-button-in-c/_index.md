---
category: general
date: 2026-10-10
description: Ställ in knapptext och lägg till en ActiveX‑knapp i C# med Aspose.Words.
  Lär dig hur du infogar en knapp, skapar knappkontroll och anpassar rubriken i ett
  Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: sv
lastmod: 2026-10-10
og_description: Ställ in knapptext och lägg till en ActiveX‑knapp i C# med Aspose.Words.
  Följ den här steg‑för‑steg‑guiden för att infoga en knapp, skapa knappkontrollen
  och anpassa dess etikett.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Ställ in knapptext och lägg till en ActiveX‑knapp i C# – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Ställ in knapptext och lägg till en ActiveX‑knapp i C#
url: /sv/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set button text and add an ActiveX button in C#

Om du behöver **set button text** på en ActiveX‑knapp i ett Word‑dokument, visar den här guiden exakt hur du gör. I slutet av tutorialen kommer du att kunna **insert button**, skapa en **button control** och anpassa dess rubrik med bara några rader C#‑kod.

Att arbeta med ActiveX‑kontroller är vanligt när du vill ha interaktiva formulär i Word—oavsett om du bygger en kontraktsmall, en enkät eller ett internt verktyg. Exemplet använder Aspose.Words for .NET, ett bibliotek som låter dig manipulera Word‑filer utan att Microsoft Office är installerat.

## Prerequisites

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat  
* Visual Studio 2022 (eller någon IDE som stödjer C#)  
* En Aspose.Words for .NET‑licens (den fria utvärderingen fungerar för lärande)  

Du behöver också en referens till NuGet‑paketet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## How to insert button into a Word document

Det första steget är att skapa ett nytt `Document` och en `DocumentBuilder`. Buildern är ingångspunkten för att lägga till innehåll, inklusive ActiveX‑kontroller.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:** `Document` representerar hela .docx‑filen, medan `DocumentBuilder` erbjuder hög‑nivå‑metoder som `InsertParagraph` och `InsertFormField`. Att börja med ett tomt dokument säkerställer att knappen visas exakt där du vill ha den.

## Create button control with Forms2OleControl

Nu skapar vi själva knappkontrollen. `Forms2OleControl` är klassen som Aspose.Words använder för alla ActiveX‑objekt, och typen `COMMANDBUTTON` renderas som en klickbar knapp i Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Förklaring:**  
* `InsertForms2OleControl` placerar kontrollen på de exakta koordinater du anger.  
* Storleken definieras i punkter (1 point = 1/72 tum). Justera dessa siffror för att passa din layout.

## Add ActiveX control and give it a unique name

Varje ActiveX‑objekt bör ha ett unikt namn så att du kan referera till det senare (t.ex. när du hanterar händelser i VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tips:** Undvik mellanslag eller specialtecken i namnet; Word behandlar namnet som en identifierare i sin interna formulärmodell.

## Set button text (caption) on the ActiveX button

Här kommer det primära nyckelordet **set button text** in i bilden. `Caption`‑egenskapen definierar den etikett som användarna ser på knappen.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Du kan ändra rubriken när som helst innan du sparar dokumentet. Om du senare behöver lokalisera UI:t, anropa helt enkelt `SetCaption` igen med en annan sträng.

## Save the document and verify the result

Till sist skriver du dokumentet till disk. När du öppnar filen i Microsoft Word visas knappen med den anpassade rubriken.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Förväntat resultat:** När du öppnar *ActiveXButton.docx* i Word kommer du att se en knapp placerad på de angivna koordinaterna, med etiketten **Click Me**. Att klicka på knappen utlöser standardbeteendet för Word‑kommandomknappen (som du senare kan anpassa med VBA).

![Set button text example](https://example.com/activex-button.png){alt="Exempel på att sätta knapptext"}

## Add ActiveX button and handle events (optional)

Om du vill att knappen ska utföra en anpassad åtgärd kan du lägga till ett VBA‑makro som reagerar på `Click`‑händelsen. Makrot kan injiceras programatiskt, men det ligger utanför denna tutorials omfattning. Det viktiga är att knappen redan finns och dess rubrik är satt—redo för den händelsehantering du väljer.

## Common pitfalls and how to avoid them

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| Knappen visas feljusterad | Koordinaterna är i punkter, inte pixlar | Konvertera pixelvärden till punkter (`points = pixels * 72 / DPI`) |
| Rubriken ändras inte efter sparning | `SetCaption` anropad efter `Save` | Sätt alltid rubriken **innan** du anropar `doc.Save` |
| Kontrollen syns inte i äldre Word‑versioner | Vissa äldre Word‑versioner saknar full ActiveX‑support | Testa i mål‑Word‑versionen; överväg att använda en `CheckBox` eller `DropDownList` som reserv |
| Licensvarning i utdata | Utvärderingslicensen går ut | Applicera en giltig Aspose.Words‑licens via `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Full, runnable example

Nedan är det kompletta programmet som du kan kopiera, klistra in och köra. Det innehåller alla nödvändiga `using`‑direktiv och demonstrerar hela arbetsflödet från dokumentskapande till sparning.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Kör programmet med `dotnet run`. Efter körning, öppna *ActiveXButton.docx* för att bekräfta att knappens rubrik är **Click Me**.

## Recap of what you learned

* Du har lärt dig hur du **set button text** på en ActiveX‑knapp med Aspose.Words.  
* Du har sett de exakta stegen för **how to insert button**, **create button control** och **add activex control** i ett Word‑dokument.  
* Du har nu ett återanvändbart kodexempel som du kan anpassa för vilket formulär‑baserat Word‑automatiseringsprojekt som helst.

## Next steps

* Utforska andra `Forms2OleControlType`‑värden såsom `CHECKBOX` eller `LISTBOX` för att bygga rikare formulär.  
* Kombinera knappen med ett VBA‑makro för att utföra beräkningar eller datavalidering.  
* Använd Aspose.Words `FormField`‑API för att läsa användarinmatning efter att dokumentet har fyllts i.

Känn dig fri att experimentera med storlek, position och rubrik för att matcha dina designkrav. Om du stöter på problem ger Aspose.Words‑dokumentationen detaljerade referenser för varje klass som används i denna tutorial.

Lycka till med kodningen!

## What Should You Learn Next?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa tomt Word‑dokument med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Lägg till skugga på form i Word med Aspose.Words – Steg‑för‑steg](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Lägg till sidnummer i sidfoten på ett Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}