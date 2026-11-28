---
category: general
date: 2026-11-18
description: Skapa ett tomt Word‑dokument och infoga en ActiveX‑knapp med C#. Lär
  dig hur du lägger till kontroll, sätter knappens rubrik och sparar filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: sv
lastmod: 2026-11-18
og_description: Skapa ett tomt Word‑dokument och infoga en ActiveX‑knapp med C#. Följ
  den här kompletta handledningen för att lägga till kontrollen, sätta knappens rubrik
  och spara resultatet.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Skapa ett tomt Word‑dokument och infoga en ActiveX‑knapp – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Skapa ett tomt Word‑dokument och infoga en ActiveX‑knapp
url: /sv/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument och infoga en ActiveX-knapp

Om du behöver **skapa ett tomt Word-dokument** och placera en interaktiv ActiveX-knapp i det, visar den här guiden exakt hur du gör det med Aspose.Words för .NET. Du får se hela koden, förstå varför varje rad är viktig, och lära dig hur du **anger knapptext** så att kontrollen ser klar ut för användarinteraktion.

Förutom huvudmålet kommer vi att gå igenom **hur man infogar ActiveX**, stegen **hur man lägger till kontroll** i en Word-fil, och nyanserna av **infoga ActiveX-knapp** med en anpassad rubrik. I slutet har du ett återanvändbart mönster för alla dokument‑automatiseringsscenarier som kräver inbäddade UI‑element.

## Vad du kommer att lära dig

* Hur man **skapar ett tomt Word-dokument** programatiskt.  
* De exakta API-anrop som krävs för att **infoga ActiveX-knapp** och konfigurera dess egenskaper.  
* Hur man **anger knapptext** så att kontrollen visar önskad text.  
* Tips för att spara filen på en plats du väljer och hantera vanliga fallgropar.

### Förutsättningar

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+).  
* Aspose.Words för .NET installerat (`Install-Package Aspose.Words`).  
* Grundläggande kunskap om C# och Visual Studio eller någon .NET‑kompatibel IDE.

---

## Skapa ett tomt Word-dokument med Aspose.Words

Det första steget är att instansiera ett tomt `Document`-objekt. Detta objekt representerar en Word-fil som inte innehåller något innehåll förrän vi lägger till något.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Varför detta är viktigt*: Ett tomt `Document` ger dig en ren canvas. Du kan senare lägga till stycken, tabeller eller kontroller utan att oroa dig för befintlig formatering.

---

## Initiera en DocumentBuilder för att arbeta med dokumentet

`DocumentBuilder` är en hjälparklass som låter dig infoga innehåll vid den aktuella markörpositionen. Den spårar automatiskt var du befinner dig i dokumentet.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt*: Utan en `DocumentBuilder` skulle du behöva manipulera nodträdet på låg nivå manuellt. Buildern förenklar infogning av text, bilder och ActiveX‑kontroller.

---

## Hur man infogar en ActiveX-knapp (insert activex button)

Nu använder vi `InsertForms2OleControl` för att bädda in en ActiveX‑kontroll. Metoden kräver tre argument:

1. Typen av kontroll (`OleControlType.CommandButton`).  
2. Ett internt namn för kontrollen (används av VBA eller makrokod).  
3. En `RectangleF` som definierar position och storlek på sidan.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Varför detta är viktigt*: Detta är kärnan i **hur man infogar activex** i ett Word-dokument. Rektangelns koordinater uttrycks i punkter (1 punkt = 1/72 tum). Justera dem för att placera knappen där du behöver den.

### Tips

Om du behöver att knappen ska visas på en specifik sida, flytta först builderns markör:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Hur man anger knapptext (set button caption)

Efter att kontrollen har placerats kan du ändra dess egenskaper. Den mest synliga egenskapen är `Caption`, som bestämmer texten som visas på knappen.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Varför detta är viktigt*: Användare ser rubriken, inte det interna namnet. Att ändra den gör knappen meningsfull i det slutgiltiga dokumentet.

---

## Spara dokumentet som innehåller knappen

Till sist skriver du dokumentet till disk. Du kan välja vilket som helst av de stödjade formaten (`.docx`, `.pdf`, etc.). Här sparar vi som ett Word-dokument.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Varför detta är viktigt*: Att spara filen gör att du kan öppna den i Microsoft Word och testa knappen. När dokumentet öppnas kommer knappen att visas med rubriken “Press”.

### Förväntat resultat

Att öppna `with_button.docx` i Word visar en tom sida med en rektangulär knapp märkt **Press**. Att klicka på knappen gör ingenting som standard eftersom ingen VBA-makro är bifogad, men kontrollen är fullt funktionell och kan kopplas till kod senare.

---

## Hur man lägger till kontroll i ett specifikt stycke (how to add control)

Ibland vill du ha knappen i ett specifikt stycke, till exempel efter någon instruktionstext. Använd `MoveTo` för att placera buildern innan du infogar kontrollen.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Varför detta är viktigt*: Detta mönster demonstrerar **hur man lägger till kontroll** i kontext, vilket säkerställer att dokumentlayouten förblir logisk.

---

## Vanliga fallgropar och hur man undviker dem

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| Knappen visas utanför sidan | Rektangelkoordinaterna ligger utanför sidmarginalerna | Använd `builder.PageSetup` för att få sidans dimensioner och beräkna en säker `RectangleF`. |
| Rubriken visas inte | `Caption` sattes innan kontrollen är helt initierad | Sätt `Caption` **efter** anropet till `InsertForms2OleControl`, som visas i steg 4. |
| Dokumentet sparas utan knappen | Builderns markör flyttades efter infogning utan att bekräfta ändringarna | Behåll buildern på samma sida eller anropa `builder.Document.UpdatePageLayout()` innan du sparar. |

---

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera, klistra in och köra. Det skapar en tom Word-fil, infogar en ActiveX-knapp, anger dess rubrik och sparar resultatet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultat**: Efter att ha kört programmet, öppna `C:\Temp\with_button.docx` i Microsoft Word. Du kommer att se en enda sida med texten “Below is an ActiveX button created programmatically:” följt av en knapp märkt **Press**.

---

## Slutsats

Du vet nu hur man **skapar ett tomt Word-dokument**, **infogar en ActiveX-knapp**, **anger knapptext**, och **sparar** resultatet med Aspose.Words för .NET. Samma mönster kan utökas till andra ActiveX‑kontroller (kryssrutor, listboxar osv.) genom att ändra `OleControlType`.

Nästa steg kan vara att utforska **hur man infogar ActiveX-knapp**‑händelser med VBA, eller **hur man lägger till kontroll** i befintliga dokument som redan innehåller innehåll. Båda ämnena bygger direkt på de koncept som behandlats här.

Lycka till med kodandet, och känn dig fri att experimentera med olika storlekar, positioner och rubriker för att passa ditt programs UI‑krav!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar Word-dokument C# med en ActiveX‑kommandoknapp](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Hur man lägger till ActiveX‑knapp i ett Word-dokument med Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}