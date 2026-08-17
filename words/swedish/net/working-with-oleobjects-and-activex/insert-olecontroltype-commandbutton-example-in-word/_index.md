---
category: general
date: 2026-08-17
description: Infoga OleControlType.CommandButton‑exempel i Word med Aspose.Words.
  Lär dig hur du programatiskt lägger till formulärkontroller i ett Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: sv
lastmod: 2026-08-17
og_description: Infoga OleControlType.CommandButton‑exempel i Word med Aspose.Words.
  Följ den här guiden för att lägga till formulärkontroller i ett Word‑dokument.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Infoga OleControlType.CommandButton‑exempel i Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Infoga OleControlType.CommandButton‑exempel i Word
url: /sv/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga OleControlType.CommandButton-exempel i Word

Om du behöver **infoga OleControlType.CommandButton-exempel** i en Word-fil, visar den här guiden hur du gör. Du kommer att lära dig **hur du lägger till formulärkontroller i ett Word-dokument** med Aspose.Words, med ett komplett, körbart C#-program.

Formulärkontroller såsom ActiveX-knappar låter dig skapa interaktiva Word-mallar—användbara för kontrakt, frågeformulär eller interna verktyg. Stegen nedan täcker allt från projektuppsättning till att verifiera att knappen visas korrekt i den sparade `.docx`-filen.

## Förutsättningar

- .NET 6.0 SDK eller senare installerat  
- Visual Studio 2022 (eller någon C#-IDE)  
- En Aspose.Words för .NET-licens eller en gratis tillfällig licens  
- Grundläggande kunskap om C# och Word-filkoncept  

> **Proffstips:** Om du använder gratisversionen, placera licensfilen i samma mapp som den körbara filen och ladda den i början av `Main`.

## Steg 1: Skapa ett nytt konsolprojekt och lägg till Aspose.Words

Öppna en terminal och kör:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Detta skapar ett rent projekt och hämtar det senaste Aspose.Words-paketet, som tillhandahåller `Document`, `DocumentBuilder` och `InsertForms2OleControl`-API:erna som behövs för **infoga OleControlType.CommandButton-exempel**.

## Steg 2: Skriv hela programmet

Skapa eller ersätt `Program.cs` med följande kod. Den innehåller alla nödvändiga `using`-direktiv, licensladdning och det fyrastegsarbetsflöde som visas i det ursprungliga kodavsnittet.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Varför varje rad är viktig

* **License loading** – säkerställer att du inte är begränsad av utvärderingsrestriktioner.  
* **`Document doc = new Document();`** – skapar behållaren för allt Word-innehåll; detta är grunden för **infoga OleControlType.CommandButton-exempel**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – tillhandahåller ett flytande API för att lägga till text, bilder och kontroller.  
* **`InsertForms2OleControl`** – kärnmetoden som implementerar **hur du lägger till formulärkontroller i ett Word-dokument**. `OleControlType.CommandButton`-enumvärdet talar om för Aspose.Words att skapa en ActiveX-knapp.  
* **`new Rectangle(100, 100, 80, 30)`** – placerar knappen 100 pt från vänster- och toppmarginalerna, med en bredd på 80 pt och en höjd på 30 pt. Justera dessa siffror för att passa din layout.  
* **`doc.Save`** – skriver .docx-filen till disk; filen innehåller nu den inbäddade knappen.

## Steg 3: Bygg och kör programmet

Från projektmappen, kör:

```bash
dotnet run
```

Du bör se konsolmeddelandet:

```
Document saved to ActiveXButton.docx
```

Öppna `ActiveXButton.docx` i Microsoft Word. Du kommer att se en knapp med etiketten **ClickMe** placerad ungefär i mitten av sidan. Att klicka på knappen utlöser standardbeteendet för ActiveX (vilket vanligtvis är en ingen‑operation om du inte bifogar ett makro).

![infoga olecontroltype.commandbutton exempel](/images/activex-button.png "ActiveX CommandButton infogad i ett Word-dokument")

*Bildtext:* infoga olecontroltype.commandbutton exempel – en ActiveX CommandButton som visas i ett Word-dokument.

## Steg 4: Anpassa knappen (valfritt)

Det grundläggande **infoga OleControlType.CommandButton-exempel** skapar en standardknapp. Du kan ändra dess rubrik, teckensnitt eller till och med bifoga ett makro genom att redigera det underliggande OLE-objektet. Nedan är ett koncist sätt att ändra knappens rubrik efter infogning:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Obs:** Direkt manipulation av OLE-egenskaper kräver förståelse för det underliggande COM-gränssnittet. För de flesta scenarier är standardrubriken tillräcklig.

## Steg 5: Vanliga fallgropar och hur du undviker dem

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| Knappen visas inte i Word | Dokumentet sparades som `.docx` men öppnades i en visare som tar bort OLE-kontroller (t.ex. Google Docs). | Öppna filen i Microsoft Word eller Word Online med redigeringsrättigheter. |
| Körtidsfel `ArgumentOutOfRangeException` | `Rectangle`-koordinaterna ligger utanför sidans marginaler. | Använd värden inom sidstorleken (t.ex. 0‑500 för A4). |
| Licensundantag | En provlicens går ut efter 30 dagar. | Ladda en giltig licensfil eller begär en förlängd provperiod från Aspose. |

## Steg 6: Hur detta exempel passar in i större automationsprojekt

När du behöver **lägga till formulärkontroller i Word-dokument** i stor skala—t.ex. generera hundratals kontraktsmallar—paketera insättningslogiken i en återanvändbar metod:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Du kan sedan anropa `AddCommandButton` i loopar som bearbetar datarader, vilket säkerställer att varje genererat dokument innehåller en unikt namngiven knapp (t.ex. `Approve_001`, `Approve_002`).

## Slutsats

Du har nu ett komplett **infoga OleControlType.CommandButton-exempel** som demonstrerar **hur du lägger till formulärkontroller i ett Word-dokument** med Aspose.Words för .NET. Handledningen täckte projektuppsättning, fullständig källkod, anpassningstips och vanliga felsökningssteg.

Från här kan du utforska:

- Lägga till andra kontroller såsom **CheckBox** eller **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Koppla knappen till ett VBA-makro för rikare interaktivitet.  
- Generera PDF-filer från samma dokument samtidigt som formulärfälten bevaras.

Experimentera med olika storlekar, positioner och kontrollnamn för att passa ditt specifika användningsfall. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Infoga kombinationsruta formulärfält i Word-dokument](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Infoga kryssruta formulärfält i Word-dokument](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Infoga textinmatningsfält i Word-dokument](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}