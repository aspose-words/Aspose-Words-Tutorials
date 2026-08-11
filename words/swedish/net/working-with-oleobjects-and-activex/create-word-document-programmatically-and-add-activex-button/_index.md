---
category: general
date: 2026-08-10
description: Skapa ett Word‑dokument programatiskt med Aspose.Words, och lägg sedan
  till en ActiveX‑kontrollknapp i Word. Infoga en ActiveX‑kommandoknapp på några minuter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: sv
lastmod: 2026-08-10
og_description: Skapa Word-dokument programatiskt med Aspose.Words och lägg sedan
  till en ActiveX‑kontroll för en Word‑knapp. Lär dig hur du snabbt infogar en ActiveX‑kommandoknapp.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Skapa Word-dokument programatiskt – lägg till en ActiveX-knapp i C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Skapa Word-dokument programatiskt och lägg till en ActiveX‑knapp
url: /sv/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt och lägg till ActiveX‑knapp

Om du behöver **skapa Word-dokument programatiskt**, guidar den här artikeln dig genom hela processen med Aspose.Words för .NET. Du får också lära dig hur du **lägger till ActiveX‑kontrollelement** och **infogar ActiveX‑kommandoknapp** i ett enda, självständigt exempel.

Att generera Word‑filer från kod tar bort det manuella steget att öppna Microsoft Word, så att du kan bygga rapporter, fakturor eller datadrivna kontrakt automatiskt. I slutet av den här handledningen har du en färdig C#‑konsolapp som producerar en `.docx`‑fil som innehåller en interaktiv ActiveX‑CommandButton.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare (koden fungerar även med .NET Framework 4.6+)
* Visual Studio 2022 eller någon IDE som stödjer .NET‑utveckling
* En giltig Aspose.Words för .NET‑licens (du kan använda den kostnadsfria utvärderingsnyckeln för testning)
* Grundläggande kunskap om C#‑syntax och konceptet COM/ActiveX‑kontroller

> **Pro tip:** Om du planerar att distribuera det genererade dokumentet till användare som inte har Word installerat, bädda in ActiveX‑kontrollens körfiler tillsammans med `.docx`‑filen eller tillhandahåll en makro‑aktiverad mall.

## Skapa Word-dokument programatiskt – initial konfiguration

Först, lägg till Aspose.Words‑NuGet‑paketet i ditt projekt:

```bash
dotnet add package Aspose.Words
```

Skapa sedan ett nytt konsolprojekt (om du inte redan har ett):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Öppna den genererade `Program.cs`‑filen – vi kommer att ersätta dess innehåll med den fullständiga lösningen nedan.

## Steg 1: Importera namnrymder och konfigurera licensen

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Varför detta är viktigt*: Genom att importera `Aspose.Words.Drawing` får du tillgång till `Forms2OleControl`, klassen som representerar en ActiveX‑kontroll i ett Word‑dokument. Att ange licensen tidigt förhindrar varningsmeddelanden i produktion.

## Steg 2: Skapa ett tomt dokument och en DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`‑objektet är den minnesbaserade representationen av en `.docx`‑fil. `DocumentBuilder` fungerar som en markör som du flyttar runt i dokumentet för att infoga element.

## Steg 3: Infoga en ActiveX‑CommandButton‑kontroll

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` skapar ett OLE‑objekt som Word behandlar som en ActiveX‑kontroll. Koordinatsystemet använder punkter (1 punkt = 1/72 tum), vilket matchar Words layoutmotor.

## Steg 4: Ställ in knappens rubrik och valfria egenskaper

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Att sätta `Caption`‑egenskapen är det vanligaste sättet att märka knappen. Om du vill att knappen ska köra ett VBA‑makro, tilldela makronamnet till `OnAction`. Den här handledningen fokuserar på den visuella delen; makro‑integration behandlas i avsnittet “Nästa steg”.

## Steg 5: Spara dokumentet

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

När du kör programmet får du ett konsolmeddelande som bekräftar att `ActiveX_CommandButton.docx` har skrivits till disk.

### Fullständig källkod (klar för kopiering)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

När du kör kodsnutten får du en Word‑fil som innehåller en klickbar **ActiveX‑kommandoknapp**. Öppna filen i Microsoft Word, växla till **Designläge** (Fliken Utvecklare → Designläge), så ser du knappen renderad exakt där du placerade den.

## Steg 6: Verifiera resultatet

1. Öppna `ActiveX_CommandButton.docx` i Microsoft Word.  
2. Aktivera fliken **Utvecklare** om den inte syns (`Arkiv → Alternativ → Anpassa menyfliksområdet → markera Utvecklare`).  
3. Klicka på **Designläge**. Knappen ska visas med etiketten “Submit”.  
4. Om du har lagt till ett `OnAction`‑makro, klicka på knappen när Designläge är avstängt för att köra makrot.

Om knappen inte visas, kontrollera att Words säkerhetsinställningar tillåter ActiveX‑kontroller (`Arkiv → Alternativ → Säkerhetscenter → Inställningar för Säkerhetscenter → ActiveX‑inställningar`).

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| **Kan jag infoga andra ActiveX‑typer?** | Ja. `Forms2OleControlType`‑enum innehåller `CheckBox`, `OptionButton`, `ComboBox` osv. Byt ut `CommandButton` mot önskat enum‑värde |

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}