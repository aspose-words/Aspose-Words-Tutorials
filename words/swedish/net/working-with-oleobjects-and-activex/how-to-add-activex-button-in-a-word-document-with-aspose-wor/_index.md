---
category: general
date: 2026-08-14
description: Hur man lägger till en ActiveX‑knapp i ett Word‑dokument med Aspose.Words
  – lär dig att skapa ett tomt Word‑dokument och infoga en ActiveX‑knapp programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: sv
lastmod: 2026-08-14
og_description: Hur man lägger till en ActiveX‑knapp i ett Word‑dokument med Aspose.Words.
  Denna handledning visar hur du skapar ett tomt Word‑dokument, infogar en ActiveX‑knapp
  och sparar resultatet.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Hur du lägger till en ActiveX‑knapp i Word – Aspose.Words‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Hur man lägger till en ActiveX‑knapp i ett Word‑dokument med Aspose.Words
url: /sv/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till en ActiveX‑knapp i ett Word‑dokument med Aspose.Words

Om du behöver **how to add ActiveX**‑kontroller i en genererad Word‑fil, visar den här guiden de exakta stegen. Du kommer att lära dig att **insert ActiveX button** programatiskt, med början från ett **create empty Word document** och slutar med en sparad fil som kan öppnas i Microsoft Word.

Att lägga till en knapp som kör VBA‑kod eller triggar ett makro är ett vanligt krav för automatiska rapportgeneratorer, formulärmallar eller interaktiva kontrakt. Att använda Aspose.Words för .NET låter dig bygga dokumentet utan att starta Office, vilket gör processen snabb och servervänlig.

## Förutsättningar

* .NET 6.0 (eller senare) SDK installerat.
* Visual Studio 2022 eller någon C#‑kompatibel IDE.
* Aspose.Words för .NET NuGet‑paket (`Aspose.Words` version 24.9 eller nyare).  
  Installera det med:
  ```bash
  dotnet add package Aspose.Words
  ```
* En Windows‑miljö om du planerar att testa ActiveX‑knappen, eftersom ActiveX‑kontroller kräver Windows‑versionen av Microsoft Word.

## Steg 1: Skapa ett tomt Word‑dokument

Den första uppgiften är att **create empty Word document** i minnet. Aspose.Words tillhandahåller `Document`‑klassen för detta ändamål.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` representerar hela .docx‑filen. Vid detta tillfälle innehåller dokumentet inga sidor, men du kan börja lägga till innehåll omedelbart.

## Steg 2: Initiera en DocumentBuilder

`DocumentBuilder` är ett hjälpmedel som låter dig infoga text, bilder och andra objekt i dokumentet. Det fungerar på `Document`‑instansen du just skapade.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern behåller en markörposition; allt du infogar efter den här raden visas i början av den första sidan.

## Steg 3: Infoga en ActiveX CommandButton‑kontroll

Aspose.Words exponerar metoden `InsertForms2OleControl` för att lägga till äldre formulärkontroller, inklusive ActiveX. Metoden kräver kontrolltypen och dess storlek i punkter.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Det returnerade `Forms2OleControl`‑objektet låter dig konfigurera egenskaper såsom kontrollens namn och rubrik.

## Steg 4: Konfigurera knappens egenskaper

Att sätta ett meningsfullt `Name` gör att du kan referera till kontrollen från VBA‑kod senare. `Caption` är den text som användaren ser på knappen.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Håll namnet kort och alfanumeriskt; Word kommer att avvisa namn som innehåller mellanslag eller specialtecken.

## Steg 5: Spara dokumentet

Slutligen, skriv dokumentet till disk. Använd `.docx`‑extensionen för moderna Word‑filer; ActiveX‑knappen fungerar på samma sätt i `.doc`‑filer, men `.docx` är det föredragna formatet för nya projekt.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

När du öppnar `ActiveXButton.docx` i Microsoft Word kommer du att se en klickbar **Submit**‑knapp. Om du aktiverar makron kan du bifoga VBA‑kod till `btnSubmit_Click` och låta den köras när användaren klickar på knappen.

## Fullt, körbart exempel

Genom att sätta ihop alla delar får du ett självständigt program som du kan kopiera, klistra in och köra.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output** – Efter att programmet har körts skriver konsolen ut sparplatsen, och när du öppnar den genererade filen i Word visas en knapp med etiketten **Submit** placerad högst upp på den första sidan.

## Hantera vanliga frågor och kantfall

### Fungerar knappen i alla Word‑versioner?

ActiveX‑kontroller stöds i skrivbordsversionen av Word på Windows. De renderas inte i Word Online, Word för macOS eller mobila klienter. Om du behöver plattformsoberoende interaktivitet, överväg att använda innehållskontroller eller HTML‑baserade lösningar istället.

### Vad händer om jag behöver en annan storlek eller position?

`InsertForms2OleControl` placerar kontrollen vid den aktuella builder‑markören. För att flytta den, justera markören med `builder.MoveTo` före infogning, eller ändra kontrollens `Left`‑ och `Top`‑egenskaper efter skapandet:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Kan jag lägga till andra ActiveX‑typer?

Ja. Uppräkningen `Forms2OleControlType` innehåller `CheckBox`, `OptionButton`, `ListBox` och fler. Ersätt `CommandButton` med det önskade enum‑värdet och justera egenskaperna därefter.

### Krävs ett makro för att knappen ska göra något?

Knappen i sig gör ingenting förrän du bifogar VBA‑kod. I Word, tryck **Alt+F11** för att öppna VBA‑editorn, hitta `btnSubmit_Click` och skriv den önskade logiken. Det genererade dokumentet behåller VBA‑projektet om du använder **SaveFormat.Doc** (legacy `.doc`) format, men `.docx`‑filer kan inte lagra VBA‑makron. Använd `.doc`‑formatet om du behöver inbäddad VBA.

## Slutsats

Du vet nu **how to add ActiveX**‑kontroller till en Word‑fil med hjälp av Aspose.Words. Genom att följa stegen för att **create empty Word document**, initiera en `DocumentBuilder`, **insert ActiveX button**, konfigurera dess egenskaper och spara filen, kan du generera interaktiva Word‑mallar direkt från din .NET‑kod.

Nästa steg är att utforska relaterade ämnen såsom **insert ActiveX button**‑händelsehantering, lägga till **create word document aspose** för tabeller eller bilder, och säkra makro‑aktiverade dokument för företagsdistribution. Experimentera med olika kontrolltyper och layoutalternativ för att anpassa användarupplevelsen efter ditt programs behov.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word‑dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa ett Word‑dokument med tabell med Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}