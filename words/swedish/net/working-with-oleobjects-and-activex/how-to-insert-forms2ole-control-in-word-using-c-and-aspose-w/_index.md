---
category: general
date: 2026-11-22
description: Lär dig att infoga en Forms2Ole‑kontroll i Word med C#. Denna steg‑för‑steg‑guide
  täcker DocumentBuilder, placering av kommandoknapp och sparande av .docx‑filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: sv
lastmod: 2026-11-22
og_description: Infoga Forms2Ole‑kontroll i Word med C#. Följ den här guiden för att
  lägga till en kommandoknapp med Aspose.Words och DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Infoga Forms2Ole‑kontrollen i Word med C# – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man infogar Forms2Ole‑kontrollen i Word med C# och Aspose.Words
url: /sv/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar Forms2Ole‑kontroll i Word med C# och Aspose.Words

Om du behöver **infoga Forms2Ole‑kontroll i Word**, visar den här handledningen exakt hur du gör det med C#. Oavsett om du bygger en ifyllbar mall eller automatiserar formulärskapande, låter lösningen nedan dig lägga till en kommandoknapp programmässigt.

Du kommer att lära dig hur du skapar ett tomt dokument, använder `DocumentBuilder` för att placera kontrollen och sparar resultatet som en `.docx`. Guiden täcker också vanliga fallgropar, såsom koordinatsystem och kompatibilitet med äldre Word‑versioner.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.6+)
* Aspose.Words för .NET (NuGet‑paket `Aspose.Words`)
* Grundläggande kunskap om C# och Word‑objektmodellen
* En IDE som Visual Studio eller VS Code

## Steg 1: Ställ in projektet och importera namnrymder

Skapa en ny konsolapplikation och lägg till Aspose.Words‑paketet:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

I `Program.cs` importerar du de nödvändiga namnrymderna:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Pro tip:** Använd den senaste versionen av Aspose.Words för att få fullt stöd för `Forms2OleControl`‑API‑et.

## Steg 2: Skapa ett tomt dokument och initiera DocumentBuilder

`Document`‑klassen representerar Word‑filen, medan `DocumentBuilder` tillhandahåller metoder för att infoga innehåll.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fungerar som en markör; efter den här raden kan du börja placera element var som helst i dokumentet.

## Steg 3: Definiera knappens position och storlek

Word mäter koordinater i punkter (1 pt ≈ 1/72 tum). `Rectangle`‑strukturen från `System.Drawing` beskriver kontrollens gränser.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` placerar kontrollen i det övre vänstra hörnet på den aktuella sidan.
* Justera `x` och `y` för att flytta knappen någon annanstans (t.ex. `new Rectangle(150, 200, 100, 30)`).

## Steg 4: Infoga Forms2Ole‑kommandoknappen

Använd nu `InsertForms2OleControl` för att lägga till kontrollen. Metoden kräver kontrolltypen, ett namn och de ovan definierade gränserna.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Det returnerade `Forms2OleControl`‑objektet låter dig ändra egenskaper som `Enabled`, `Visible` eller till och med bifoga ett makronamn senare.

### Varför använda Forms2Ole?

* **Legacy‑kompatibilitet** – Forms2Ole‑kontroller fungerar i Word 97‑2003 (`.doc`) och nyare `.docx`‑filer.
* **Makrostöd** – De kan trigga VBA‑makron, vilket gör dem idealiska för interaktiva mallar.
* **Precisionsplacering** – Till skillnad från innehållskontroller styr du exakta koordinater.

## Steg 5: Spara dokumentet

Skriv slutligen filen till disk. Välj en mapp där du har skrivrättigheter.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Öppna `output.docx` i Microsoft Word. Du kommer att se en knapp med etiketten **ClickMe** i det övre vänstra hörnet på första sidan. Att klicka på den i Word gör ingenting förrän du tilldelar ett makro, men kontrollen är fullt funktionell.

## Hantera vanliga kantfall

| Situation | Hur du hanterar det |
|-----------|---------------------|
| **Knappen visas utanför sidan** | Verifiera att `Rectangle`‑koordinaterna ligger inom sidmarginalerna. Använd `builder.PageSetup.PageWidth` och `PageHeight` för att beräkna säkra gränser. |
| **Kontrollen syns inte i äldre Word‑versioner** | Spara dokumentet som `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) för att garantera Forms2Ole‑kompatibilitet med Word 97‑2003. |
| **Behöver ändra rubriken** | Efter infogning, sätt `commandButton.Caption = "Submit";`. |
| **Tilldela ett makro** | Sätt `commandButton.MacroName = "MyMacro"`; makrot måste finnas i dokumentets VBA‑projekt. |
| **Flera knappar** | Upprepa Steg 4 med olika `Rectangle`‑värden och unika namn. |

## Komplett, körbart exempel

När allt sätts ihop ser du ett självständigt program som du kan kopiera, klistra in och köra:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntat resultat:** Efter att programmet har körts öppnas `output.docx` i Word med en klickbar knapp märkt *Click Me!* placerad i det övre vänstra hörnet på första sidan.

## Slutsats

Du vet nu hur du **infogar Forms2Ole‑kontroll i Word** med C# och Aspose.Words. Processen innebär att skapa ett `Document`, positionera en `Rectangle` och anropa `InsertForms2OleControl` via `DocumentBuilder`. Med hela kodexemplet och vägledning för kantfall kan du integrera kommandoknappar i vilket automatiserat Word‑arbetsflöde som helst.

### Nästa steg

* Utforska andra `ControlType`‑värden såsom `CheckBox` eller `OptionButton`.
* Kombinera Forms2Ole‑kontroller med VBA‑makron för interaktiva formulär.
* Använd `DocumentBuilder.MoveTo` för att placera knappar på specifika stycken eller tabeller.
* Granska Aspose.Words‑**Forms2Ole**‑dokumentation för avancerade egenskapsinställningar.

Lycka till med kodandet, och njut av att bygga rikare Word‑dokument med C# och Aspose.Words!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närliggande ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [How to insert OLE command button in a Word document using C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [how to add activex control in Word with Aspose.Words – step‑by‑step guide](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}