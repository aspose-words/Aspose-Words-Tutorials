---
category: general
date: 2026-10-23
description: Skapa ett tomt Word‑dokument med C# och lär dig hur du infogar ActiveX‑kontroller,
  inklusive en knapp, med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: sv
lastmod: 2026-10-23
og_description: Skapa ett tomt Word‑dokument med C# och lär dig hur du infogar ActiveX‑kontroller,
  inklusive en knapp, med Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Skapa ett tomt Word‑dokument och lägg till en ActiveX‑knapp i C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Skapa ett tomt Word‑dokument och lägg till en ActiveX‑knapp i C#
url: /sv/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument och lägg till en ActiveX-knapp i C#

Om du behöver **create blank Word document** programatiskt, visar den här guiden exakt hur. Du kommer att se ett komplett, körbart exempel som skapar ett nytt dokument, infogar en ActiveX CommandButton och sparar filen — allt med Aspose.Words för .NET.

Att arbeta med Word-filer kräver ofta mer än vanlig text. Att lägga till en **ActiveX button** låter dig bädda in interaktiv funktionalitet som kan användas i makro‑aktiverade mallar eller Windows‑endast lösningar. I slutet av den här handledningen kommer du att kunna infoga vilken ActiveX‑kontroll som helst, men vi fokuserar på det vanligaste scenariot: en **word document activex button** som skickar ett formulär.

## Förutsättningar

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
* Visual Studio 2022 (eller någon C#‑IDE)
* **Aspose.Words for .NET** NuGet‑paket  
  ```bash
  dotnet add package Aspose.Words
  ```
* Grundläggande kunskap om C#‑syntax

> **Pro tip:** Aspose.Words är ett kommersiellt bibliotek, men det erbjuder en gratis tillfällig licens för testning. Installera licensen tidigt för att undvika utvärderingsvattenstämpeln.

## Steg 1: Skapa ett tomt Word-dokument med Aspose.Words

Det första steget är att instansiera ett `Document`‑objekt. Detta representerar en tom `.docx`‑fil i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` startar utan sektioner, sidor eller innehåll. Det är den rena tavlan du behöver för **create blank word document**‑scenarier, såsom att generera rapporter från grunden.

## Steg 2: Skaffa en DocumentBuilder för att redigera dokumentet

`DocumentBuilder` erbjuder ett bekvämt API för att lägga till text, bilder och kontroller. Vi kommer att använda den för att placera ActiveX‑kontrollen.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Buildern lägger automatiskt till en standardsektion och en första sida, så du kan börja infoga objekt omedelbart.

## Steg 3: Hur man infogar ActiveX‑kontroller i dokumentet

Aspose.Words exponerar `InsertForms2OleControl` för att bädda in OLE/ActiveX‑objekt. Metoden kräver kontrollerstyp, bredd och höjd (i punkter). Nedan infogar vi en **CommandButton** — den klassiska formulärknappen du ser i äldre Word‑mallar.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Why this works:** `Forms2OleControlType.COMMANDBUTTON` talar om för Word att skapa en knapp som kan svara på klickhändelser när dokumentet öppnas i en Windows‑miljö som stöder ActiveX.

## Steg 4: Skapa en ActiveX‑kontroll – ställ in dess egenskaper

Nu ger vi knappen ett programatiskt namn och en synlig rubrik. Detta är delen av **create activex control** som utvecklare ofta förbiser.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` är identifieraren du kommer att referera till från VBA‑makron (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` är etiketten som visas på själva knappen.

## Steg 5: Spara Word-dokumentet med ActiveX‑knappen

Slutligen skriver du dokumentet till disk. Filändelsen måste vara `.docx` (eller `.docm` om du planerar att lägga till makron senare). Exemplet sparar till en platshållarmapp — ersätt den med din egen sökväg.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar den resulterande filen i Microsoft Word (endast Windows) kommer du att se en funktionell **word document activex button** som kan kopplas till VBA‑kod.

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i ett nytt konsolprojekt.

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
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntad output när du kör programmet**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Öppna den genererade `ActiveXButton.docx` i Word, så kommer du att se en knapp med etiketten **Submit** placerad högst upp på den första sidan.

## Edge cases och vanliga fallgropar

| Situation | Vad att hålla utkik efter | Rekommendation |
|-----------|---------------------------|----------------|
| Kör på macOS eller Linux | ActiveX är en Windows‑endast teknik, så knappen visas som en platshållare. | Använd handledningen endast för Windows‑inriktade mallar. |
| Dokument öppnat i Word Online | ActiveX‑kontroller stöds inte i webbläsarvyn. | Tillhandahåll ett reserv‑UI eller instruera användare att öppna filen i skrivbordsklienten. |
| Behöver en makro‑aktiverad fil | `.docx`‑filer kan inte lagra VBA‑kod. | Spara som `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) och lägg till makrot separat. |
| Kontrollens storlek matchar inte | Bredd-/höjd‑värden är i punkter (1 pt ≈ 1/72 tum). | Justera de numeriska värdena för att uppnå den visuella storlek du önskar. |

## Vanliga frågor

**Hur infogar man ActiveX‑kontroller förutom en knapp?**  
Använd samma `InsertForms2OleControl`‑metod men skicka ett annat `Forms2OleControlType`‑enum‑värde, såsom `COMBOBOX` eller `LISTBOX`.

**Kan jag ändra knappens teckensnitt eller färg?**  
Utseendet på ActiveX‑knappen styrs av värdapplikationen (Word) och det underliggande Windows‑temat. Du kan ändra egenskaper som `ForeColor` och `BackColor` via VBA efter att dokumentet har öppnats.

**Finns det ett sätt att lägga till en klick‑hanterare direkt från C#?**  
Nej. Klick‑händelsen måste hanteras av VBA eller ett Word‑tillägg eftersom knappen körs i Words process, inte i din .NET‑applikation.

## Slutsats

Du vet nu hur du **create blank Word document** programatiskt och bäddar in en **ActiveX button** med Aspose.Words för .NET. Stegen som täcktes:

1. Instansiera ett `Document`.
2. Använd `DocumentBuilder` för att arbeta med filen.
3. Anropa `InsertForms2OleControl` för att **how to insert activex**‑kontroller.
4. Konfigurera kontrollens egenskaper (**create activex control**).
5. Spara filen, vilket ger en **word document activex button** klar för VBA‑integration.

Härifrån kan du utforska att lägga till andra kontrolltyper, koppla VBA‑makron, eller konvertera dokumentet till PDF samtidigt som du bevarar knappen (som en statisk bild). Experimentera med olika storlekar, rubriker och namn.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}