---
category: general
date: 2026-10-07
description: Lär dig hur du infogar en OLE‑kommandoknapp i ett Word‑dokument med Aspose.Words
  C#. Steg‑för‑steg‑guide som täcker DocumentBuilder, egenskaper och sparande av filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: sv
lastmod: 2026-10-07
og_description: Infoga en OLE‑kommandoknapp i ett Word‑dokument med C#. Följ den här
  kortfattade handledningen för att lägga till, konfigurera och spara en funktionell
  CommandButton med Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Infoga OLE‑kommandoknapp i Word med C# – komplett guide för Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Hur man infogar en OLE‑kommandoknapp i ett Word‑dokument med C#
url: /sv/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar OLE‑kommandoknapp i ett Word‑dokument med C#

Om du behöver **infoga OLE‑kommandoknapp** i en Word‑fil programatiskt, visar den här guiden exakt hur du gör det med Aspose.Words för .NET. Oavsett om du bygger en formulärifylld rapport eller automatiserar en mall som kräver användarinteraktion, ger stegen nedan en komplett, körbar lösning.

Du kommer att lära dig hur du skapar ett tomt dokument, använder `DocumentBuilder` för att placera en `Forms2OleControl`, sätter knappens rubrik och namn, och slutligen sparar `.docx`. Inga externa verktyg krävs utöver Aspose.Words‑biblioteket.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.7+)
* En giltig Aspose.Words för .NET-licens eller en gratis utvärderingsnyckel
* Visual Studio 2022 (eller någon C#‑IDE du föredrar)
* Grundläggande kunskap om C#‑syntax och Word OLE‑koncept

> **Proffstips:** Om du använder den gratis utvärderingen kommer det genererade dokumentet att innehålla ett litet vattenstämpel. En licensierad version tar bort den automatiskt.

## Steg 1: Installera Aspose.Words

Lägg till Aspose.Words‑paketet i ditt projekt via NuGet:

```bash
dotnet add package Aspose.Words
```

Paketet innehåller namnutrymmena `Aspose.Words.Drawing` och `Aspose.Words.Drawing.Ole` som krävs för OLE‑kontroller.

## Steg 2: Infoga OLE‑kommandoknapp med DocumentBuilder

Kärnan i handledningen är metoden `InsertForms2OleControl`. Den skapar en **Forms2 OLE CommandButton** på en specifik plats och storlek.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Varför detta fungerar

* `DocumentBuilder` är det primära API‑et för att programatiskt bygga Word‑dokument.  
* `InsertForms2OleControl` instruerar Aspose.Words att bädda in en **Forms2 OLE‑kontroll**, vilket är den äldre Word‑formtekniken som stödjer kommandoknappar, kryssrutor osv.  
* Enum‑värdet `OleControlType.CommandButton` specificerar att den infogade kontrollen är en **command button**—den exakta typ du begärde när du ville **infoga OLE‑kommandoknapp**.  
* `Rectangle` bestämmer den visuella placeringen. Justera X/Y‑koordinaterna eller bredd/höjd för att passa din layout.

## Steg 3: Spara dokumentet

Efter att ha konfigurerat knappen, skriv dokumentet till disk. Du kan välja vilket format som helst som stöds av Aspose.Words (`.docx`, `.pdf`, `.odt`, …). För den här handledningen sparar vi som ett Word‑dokument.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar `CommandButton.docx` i Microsoft Word ser du en klickbar knapp med etiketten **Click Me**. Att trycka på den i Word utlöser standarddialogen “Run Macro” eftersom knappen är en OLE‑formkontroll; du kan senare bifoga ett makro eller VBA‑kod om så behövs.

## Steg 4: Verifiera resultatet (förväntat utdata)

Öppna den genererade filen:

1. Knappen visas på de koordinater du angav (ungefär 1,4 tum från vänster och toppen av sidan).  
2. Etiketten visar **Click Me**.  
3. Namnegenskapen (`cmdSubmit`) är synlig i Word's **Developer → Properties**-panel, vilket är användbart när du behöver referera till kontrollen från VBA.

![Exempel på infogad OLE‑kommandoknapp i Word‑dokument](insert-ole-button.png)

*Bildens alt‑text*: **Exempel på infogad OLE‑kommandoknapp i Word‑dokument** (inkluderar primärt nyckelord för tillgänglighet och SEO).

## Särskilda fall & Vanliga frågor

### 1. Vad händer om knappen inte visas där jag förväntar mig?

* Word använder punkter, inte pixlar. Konvertera skärm‑pixlar till punkter (`points = pixels * 72 / DPI`).  
* Se till att rektangeln inte skär in i sidmarginalerna; annars kan Word flytta kontrollen.

### 2. Kan jag infoga knappen i ett befintligt dokument?

Ja. Ladda dokumentet med `new Document("Existing.docx")` och använd samma `DocumentBuilder`‑arbetsflöde. Kom bara ihåg att flytta builderns markör (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` osv.) innan du anropar `InsertForms2OleControl`.

### 3. Hur bifogar jag ett makro till knappen?

Aspose.Words skapar inte VBA‑kod, men du kan bädda in ett makro efter att dokumentet har genererats:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Fungerar detta med .NET Core på Linux?

OLE‑kontrollen är en Windows‑specifik funktion eftersom den förlitar sig på COM. På Linux kommer knappen att infogas, men den visas som en statisk bild utan interaktivt beteende. För plattformsoberoende interaktiva formulär, överväg att använda innehållskontroller (`StructuredDocumentTag`) istället.

### 5. Vad om jag behöver en annan storlek eller flera knappar?

Skapa ytterligare `Rectangle`‑objekt med unika koordinater och upprepa anropet till `InsertForms2OleControl`. Varje knapp kan ha sin egen `Caption` och `Name`.

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i en konsolapplikation. Det inkluderar alla nödvändiga `using`‑direktiv, felhantering och kommentarer.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Kör programmet, öppna den genererade `CommandButton.docx`, och du kommer att se **Click Me**‑knappen redo för vidare anpassning.

## Slutsats

Du vet nu hur du **infogar OLE‑kommandoknapp** i ett Word‑dokument med C# och Aspose.Words. Handledningen täckte:

* Installera Aspose.Words‑paketet  
* Använda `DocumentBuilder.InsertForms2OleControl` med `OleControlType.CommandButton`  
* Ställa in knappens egenskaper (`Caption`, `Name`)  
* Spara och verifiera resultatet  

Härifrån kan du utforska relaterade ämnen som **Aspose.Words OLE control** för kryssrutor, kombinationsrutor eller inbäddning av hela Excel‑arbetsblad. Du kan också experimentera med **Word OLE command button**‑automatisering i större mallar, eller ersätta OLE‑kontroller med moderna **content controls** för bättre plattformsstöd.

Känn dig fri att anpassa rektangelvärdena, lägga till flera knappar eller bifoga VBA‑makron för att möta ditt programs behov. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga Ole‑objekt i Word‑dokument](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Infoga Ole‑objekt i Word‑dokument som ikon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Infoga Ole‑objekt i Word med Ole‑paket](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}