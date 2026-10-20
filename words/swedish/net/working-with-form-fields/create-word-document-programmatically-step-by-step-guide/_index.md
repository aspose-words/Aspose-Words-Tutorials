---
category: general
date: 2026-08-04
description: Skapa Word‑dokument programatiskt med C#. Lär dig hur du programatiskt
  lägger till en kommandoknapp med Aspose.Words på bara några steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: sv
lastmod: 2026-08-04
og_description: Skapa Word‑dokument programatiskt med Aspose.Words. Denna guide visar
  hur du programatiskt lägger till en kommandoknapp, konfigurerar den och sparar filen.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Skapa Word-dokument programatiskt – fullständig C#-handledning
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa Word‑dokument programatiskt – steg‑för‑steg‑guide
url: /sv/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt – komplett C#-handledning

Om du behöver **create word document programmatically**, den här guiden visar exakt hur du gör det med Aspose.Words för .NET. På bara några rader C# kan du generera en tom `.docx`-fil, **programmatically add command button**-kontroller, sätta deras egenskaper och spara resultatet.

Stegen nedan täcker allt från projektuppsättning till hantering av edge cases, så att du kan kopiera koden till din egen applikation och köra den utan ändringar.

## Vad du kommer att uppnå

* Initiera ett nytt Word-dokument helt i minnet.  
* **Programmatically add command button** OLE-kontroller på valfri plats och storlek.  
* Konfigurera knappens rubrik, interna namn och andra OLE-egenskaper.  
* Spara det genererade dokumentet till disk eller en ström för vidare bearbetning.

### Förutsättningar

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+).  
* En giltig Aspose.Words för .NET-licens (eller en gratis utvärdering).  
* Grundläggande kunskap om C# och Visual Studio (eller någon IDE du föredrar).

> **Pro tip:** Om du kör exemplet utan licens kommer Aspose.Words att lägga till ett litet utvärderingsvattenmärke på den första sidan.

## Steg 1: Ställ in projektet och importera nödvändiga namnrymder

Skapa en ny Console App (eller integrera i en befintlig tjänst) och lägg till Aspose.Words NuGet-paketet:

```bash
dotnet add package Aspose.Words
```

Inkludera sedan de nödvändiga namnrymderna högst upp i din `.cs`-fil:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Dessa importeringar ger dig åtkomst till `Document`, `DocumentBuilder`, `Forms2OleControl` och `RectangleF`-strukturen som används för positionering.

## Steg 2: Initiera ett nytt Word-dokument

Den första operationen i alla **create word document programmatically**-arbetsflöden är att instansiera ett `Document`-objekt. Detta objekt existerar endast i minnet tills du explicit sparar det.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fungerar som en markör som spårar var nästa element kommer att placeras. Att använda den håller koden koncis och speglar hur du skulle skriva direkt i Word.

## Steg 3: Infoga en command button OLE-kontroll

Aspose.Words tillhandahåller metoden `InsertForms2OleControl` för att bädda in OLE-objekt såsom command buttons, kryssrutor eller kombinationsrutor. Metoden kräver tre argument:

1. `ControlType`-enumvärdet (här `CommandButton`).  
2. Ett `RectangleF` som definierar X‑Y-positionen och bredd‑höjd på kontrollen (mätt i punkter, där 72 pt = 1 inch).  
3. Valfritt ytterligare OLE-egenskaper (behövs inte för den grundläggande knappen).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Why this works:** `InsertForms2OleControl` skapar en OLE-behållare i dokumentet och returnerar en `Forms2OleControl`-wrapper. Wrappern låter dig manipulera det underliggande OLE-objektet (den faktiska knappen) utan att behöva hantera låg‑nivå COM-interoperabilitet.

## Steg 4: Konfigurera knappens rubrik och interna namn

Efter infogning vill du vanligtvis ge knappen en användarsynlig etikett och en intern identifierare som ditt makro eller tillägg kan referera till senare.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` är den text som visas på knappen i Word‑gränssnittet.  
* `Name` är den programatiska identifieraren som används av VBA eller externa automationsskript.

### Valfritt: Tilldela ett makro till knappen

Om du planerar att köra ett VBA-makro när knappen klickas, kan du bifoga makronamnet:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Edge case:** När mål‑dokumentet öppnas på en maskin utan makrot kommer Word att visa en säkerhetsvarning. Signera alltid dina makron eller informera användarna om de nödvändiga inställningarna.

## Steg 5: Spara dokumentet

Du kan skriva filen till disk, en `MemoryStream` eller direkt till ett svar‑objekt i ett web‑API. Det enklaste tillvägagångssättet för en konsol‑demo är att spara till en lokal mapp:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Den resulterande `.docx`‑filen öppnas i Microsoft Word med en funktionell command button som visar “Click Me”. Att klicka på knappen kommer att utlösa det tilldelade makrot (om något) eller helt enkelt visa ett standardmeddelande.

## Fullt fungerande exempel

Kopiera följande program till `Program.cs` och kör det. Det demonstrerar hela **create word document programmatically**‑flödet, inklusive felhantering.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Förväntat resultat:** När du öppnar `CommandButton.docx` i Word visas en knapp med etiketten “Click Me”. När du för musen över knappen visas namnet `cmdClickMe` i egenskapspanelen.

## Vanliga frågor och felsökning

| Question | Answer |
|----------|--------|
| *Kan jag lägga till knappen i ett befintligt dokument?* | Ja. Ladda filen med `new Document("Existing.docx")`, använd sedan samma `InsertForms2OleControl`‑anrop. |
| *Vilka enheter använder `RectangleF`?* | Punkter (1 inch = 72 pt). Justera värdena för att placera knappen exakt. |
| *Fungerar knappen i Word för Mac?* | OLE‑kontroller stöds endast i Windows‑Word. På Mac visas knappen som en statisk bild. |
| *Behöver jag en licens för produktionsanvändning?* | En kommersiell licens tar bort utvärderingsvattenmärken och låser upp full funktionalitet. |
| *Hur ändrar jag knappens storlek efter infogning?* | Modifiera `commandButton.Width` och `commandButton.Height` eller återinfoga med ett nytt `RectangleF`. |

## Utöka lösningen

Nu när du vet hur du **programmatically add command button**‑kontroller, kan du utforska dessa relaterade ämnen:

* **Insert other form controls** – använd `ControlType.CheckBox`, `ControlType.OptionButton` osv. (täcker sekundärt nyckelord *Aspose.Words InsertForms2OleControl*).  
* **Populate the document with dynamic data** – slå samman data från en databas i tabeller eller kopplade fält.  
* **Export to PDF** – efter att ha lagt till knappen, anropa `doc.Save("output.pdf", SaveFormat.Pdf)` för att skapa en PDF‑version (relevant för *C# Word automation*).  

## Slutsats

Du har nu ett komplett, produktionsklart mönster för **create word document programmatically** och **programmatically add command button** med Aspose.Words för .NET. Handledningen täckte projektuppsättning, dokumentinitiering, OLE‑knappinfogning, egenskapskonfiguration och sparande av filen. Känn dig fri att anpassa koden för att infoga andra formulärkontroller, bifoga makron eller integrera logiken i webbtjänster eller bakgrundsjobb.

Lycka till med kodningen, och njut av att automatisera Word‑dokument!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}