---
category: general
date: 2026-07-19
description: Skapa Word-dokument med Aspose.Words C# och lär dig hur du lägger till
  en ActiveX‑kommandoknapp, sätter knappens storlek och infogar knappen programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: sv
lastmod: 2026-07-19
og_description: Skapa Word-dokument med Aspose.Words C# och bädda in en ActiveX‑kommandoknapp
  på några sekunder. Följ den steg‑för‑steg‑guiden för att enkelt ställa in knappens
  storlek och infoga knappen.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Skapa Word-dokument med ActiveX-knapp – C#-handledning
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Skapa Word-dokument med ActiveX‑knapp – C#‑guide
url: /sv/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word‑dokument med ActiveX‑knapp – Komplett C#‑guide

Har du någonsin funderat på hur man **skapar word‑dokument** som innehåller en fungerande ActiveX‑knapp? Kanske automatiserar du en rapport och behöver en klickbar ”Godkänn”‑kontroll direkt i filen. I den här handledningen går vi igenom exakt det – med Aspose.Words för .NET för att lägga till en ActiveX‑kommandoknapp, sätta dess storlek och infoga den där du vill ha den.  

Om du någonsin har frågat dig *hur man lägger till activex*‑kontroller utan att öppna Word manuellt, är du på rätt plats. I slutet har du ett körbart exempel, en tydlig förklaring av varje steg och tips för att hantera vanliga fallgropar.

## Vad du kommer att lära dig

- Hur du konfigurerar Aspose.Words i ett C#‑projekt  
- Den exakta koden för att **skapa word‑dokument** och bädda in en ActiveX‑kommandoknapp  
- Sätt att **sätta knappstorlek** och anpassa dess rubrik och namn  
- Den korrekta metoden för att **infoga kommandoknapp** och **hur man infogar knapp** på valfri plats i dokumentet  
- Edge‑case‑överväganden (Word‑version, plattformsbegränsningar, säkerhetsvarningar)

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.7+).  
- En giltig Aspose.Words för .NET‑licens (eller en gratis utvärderingsnyckel).  
- Visual Studio 2022 (eller någon annan IDE du föredrar).  
- Grundläggande kunskap om C# och objektorienterad programmering.

Inga andra tredjepartsbibliotek behövs.

---

## Steg 1: Skapa Word‑dokument – Projektuppsättning

Innan vi kan **infoga kommandoknapp** behöver vi en tom Word‑fil att arbeta med. Detta steg visar också det klassiska “skapa word‑dokument”-mönstret med Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Varför detta är viktigt:** `Document` representerar hela .docx‑filen, medan `DocumentBuilder` spårar den aktuella markörpositionen. Alla efterföljande insättningar (inklusive vår ActiveX‑kontroll) sker relativt till denna builder.

---

## Steg 2: Hur man lägger till ActiveX – Bygg kommandoknappen

Nu när dokumentet finns, låt oss ta itu med **hur man lägger till activex**‑delen. Aspose.Words exponerar klassen `Forms2OleControl` för ActiveX‑objekt. Här skapar vi en kommandoknapp och konfigurerar dess egenskaper, inklusive kravet på **sätta knappstorlek**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Proffstips:** Storleken mäts i punkter (1 punkt = 1/72 tum). Justera värdena så att de passar ditt layout; för en typisk verktygsfältsknapp fungerar 120 × 30 bra.

---

## Steg 3: Infoga kommandoknapp – Kärnan i **Insert Command Button**

När kontrollen är klar, **infogar vi kommandoknapp** i dokumentet på builderns aktuella plats. Du kan flytta buildern var som helst (t.ex. efter ett stycke) innan du anropar den här metoden.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Om du behöver **hur man infogar knapp** på ett specifikt bokmärke, flytta bara buildern först:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Vad händer bakom kulisserna?** Aspose.Words skriver de nödvändiga OLE‑objektströmmarna in i .docx‑paketet, så att Word kan rendera knappen utan extra makron.

---

## Steg 4: Spara dokumentet – Avslutar **Create Word Document**‑cykeln

Det sista steget är enkelt: skriv filen till disk. Detta fullbordar rundresan för **skapa word‑dokument**, bädda in ActiveX och spara.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Öppna den resulterande filen i Microsoft Word (endast Windows). Du bör se en klickbar knapp med etiketten “Click Me”. Att klicka på den triggar standardåtgärden för en CommandButton – inget händer om du inte kopplar VBA‑kod, men kontrollen är fullt funktionell.

> **Förväntat resultat:** En .docx‑fil med en enda sida, en knapp centrerad vid infogningspunkten, storlek 120 × 30 pt, med rubriken “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Bildtext:* **ActiveX‑knapp infogad i ett Word‑dokument med C#** (matches `og_image_alt`).

---

## Steg 5: Edge‑cases, säkerhet och bästa praxis

### Plattformbegränsningar
- ActiveX‑kontroller körs endast i Windows‑versionen av Word. Om din målgrupp inkluderar macOS‑ eller Word‑Online‑användare visas knappen som en statisk bild.
- Vissa företagsmiljöer inaktiverar ActiveX av säkerhetsskäl; du kan behöva signera dokumentet eller informera användarna om att aktivera innehåll.

### VBA‑interaktion (valfritt)
Om du vill att knappen ska köra ett makro måste du lägga till ett VBA‑projekt i dokumentet efter sparning. Aspose.Words genererar inte VBA‑kod automatiskt, men du kan använda `Document.VbaProject`‑API:t för att injicera den.

### Namnkollisioner
Ge alltid varje kontroll ett unikt `Name`. Att återanvända samma namn kan leda till körfel när Word försöker lösa kontrollen.

### Prestandatips
När du infogar många kontroller, återanvänd en enda `DocumentBuilder`‑instans och undvik att anropa `doc.Save` i en loop. Batcha insättningarna och spara en gång i slutet.

---

## Fullt fungerande exempel

Här är allt samlat i ett komplett, kopiera‑och‑klistra‑klart program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kör programmet, öppna den sparade filen, och du ser knappen exakt där buildern var placerad.

---

## Slutsats

Vi har just **skapat word‑dokument** från grunden, lärt oss **hur man lägger till activex** genom att konfigurera en `Forms2OleControl`, bemästrat **sätta knappstorlek**‑egenskaperna och demonstrerat det korrekta sättet att **infoga kommandoknapp** och **hur man infogar knapp** på valfri plats i filen.  

Från ett enda kodexempel har du nu en solid grund för rikare Word‑automatisering – oavsett om du bygger mallar med interaktiva formulär, genererar kontrakt som kräver användarbekräftelse, eller bara vill strö spridda praktiska kontroller i en rapport.

### Vad blir nästa steg?

- **Styla knappen** – ändra typsnitt, färger eller lägg till en bildbakgrund.  
- **Bifoga VBA‑makron** – låt knappen utföra beräkningar eller starta externa program.  
- **Kombinera med andra kontroller** – kryssrutor, listrutor eller till och med inbäddade Excel‑blad.  

Experimentera gärna, och om du stöter på problem, lämna en kommentar nedan. Lycka till med kodandet och ha kul med att automatisera Word med Aspose.Words!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker nära besläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringssätt i dina egna projekt.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}