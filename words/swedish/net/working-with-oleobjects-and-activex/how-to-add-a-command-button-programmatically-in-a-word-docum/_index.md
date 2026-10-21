---
category: general
date: 2026-10-13
description: Lär dig hur du lägger till en kommandoknapp programatiskt med Aspose.Words.
  Den här guiden visar också hur du skapar en Word‑dokumentknapp med fullständig C#‑kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: sv
lastmod: 2026-10-13
og_description: Lägg till en kommandoknapp programatiskt i ett Word‑dokument med Aspose.Words.
  Följ den här kompletta handledningen för att skapa en Word‑dokumentknapp med C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Lägg till en kommandoknapp programatiskt i ett Word‑dokument – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man lägger till en kommandoknapp programatiskt i ett Word-dokument
url: /sv/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till en kommandoknapp programatiskt i ett Word‑dokument  

Om du behöver **lägga till en kommandoknapp programatiskt**, erbjuder Aspose.Words ett rent API som låter dig bädda in OLE‑formulärkontroller direkt i en .docx‑fil. Denna handledning guidar dig genom varje steg som krävs för att **skapa en Word‑dokumentknapp** som beter sig som en vanlig formulärknapp när dokumentet öppnas i Microsoft Word.  

Du kommer att lära dig hur du ställer in utvecklingsmiljön, infogar knappen, konfigurerar dess egenskaper och verifierar resultatet. Inga externa verktyg behövs – bara ett .NET‑projekt och Aspose.Words för .NET‑biblioteket.  

## Förutsättningar  

Innan du börjar, se till att du har:  

* .NET 6.0 SDK eller senare installerat.  
* En aktuell version av Aspose.Words för .NET (exemplen använder 23.12, men alla 22.x+‑utgåvor fungerar).  
* En IDE såsom Visual Studio 2022 eller Visual Studio Code.  

Koden körs på Windows, macOS och Linux eftersom Aspose.Words är plattformsoberoende.  

## Steg 1: Skapa projektet och referera Aspose.Words  

1. Skapa ett nytt konsol‑projekt:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Lägg till Aspose.Words NuGet‑paketet:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Öppna **Program.cs** och ersätt innehållet med den kod som visas i nästa steg.  

Att sätta upp projektet på detta sätt säkerställer att kompilatorn kan hitta namnutrymmena `Aspose.Words` och `Aspose.Words.Drawing.Forms` som krävs för formulärkontroller.  

## Steg 2: Initiera ett tomt dokument och en DocumentBuilder  

Klassen `Document` representerar hela Word‑filen, medan `DocumentBuilder` erbjuder ett flytande API för att lägga till innehåll.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Varför detta steg är viktigt* – Utan en `DocumentBuilder` kan du inte placera knappen exakt på sidan. Buildern respekterar även den aktuella markörens position, vilket gör det enkelt att infoga flera kontroller senare.  

## Steg 3: Infoga OLE‑kontrollen för kommandoknappen  

Aspose.Words behandlar en kommandoknapp som en OLE‑kontroll av typen `ControlType.CommandButton`. Du definierar dess placering och storlek med ett `RectangleF` som mäts i punkter (1 punkt = 1/72 tum).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Viktiga punkter**  

* Rektangelns ursprung (X, Y) är relativt till sidans övre vänstra hörn.  
* Att ändra `Width` eller `Height` ändrar den visuella storleken på knappen.  
* `InsertForms2OleControl` returnerar ett `Forms2OleControl`‑objekt som du kan konfigurera vidare.  

## Steg 4: Konfigurera knappens namn och rubrik  

**Namnet** används av Words makro‑motor för att identifiera kontrollen, medan **rubriken** är den text användaren ser.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Om du planerar att lägga till VBA‑makron senare, använd ett beskrivande namn eftersom Word‑makro‑inspelningsverktyget refererar till denna egenskap.  

## Steg 5: (Valfritt) Spara dokumentet och verifiera resultatet  

Att spara filen låter dig öppna den i Microsoft Word för att bekräfta att knappen visas och fungerar.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

När du öppnar *CommandButtonDemo.docx* i Word bör du se en knapp med etiketten **Submit** placerad ungefär 1,4 tum från vänstermarginalen och 2,1 tum från sidans överkant. Att klicka på knappen gör ingenting som standard eftersom inget makro är kopplat, men den visuella kontrollen är fullt funktionell.  

## Steg 6: Edge cases och vanliga fallgropar  

| Situation | Vad du bör hålla utkik efter | Rekommenderad åtgärd |
|-----------|------------------------------|----------------------|
| **Knappen överlappar befintlig text** | Rektangeln kan skära igenom ett stycke, vilket ger layoutproblem. | Infoga knappen efter att ha anropat `builder.Writeln()` för att flytta markören till en ny rad, eller justera `Y`‑koordinaten. |
| **Dokumentet öppnas med en varning** | Vissa Word‑versioner flaggar OLE‑kontroller som saknar ett länkat program. | Säkerställ att kontrolltypen är `CommandButton`; Word behandlar den som ett standardformulärelement och kräver inget externt program. |
| **Kör på Linux i ett huvudlöst miljö** | Word kan inte startas för att testa UI‑delen, men filen är fortfarande giltig. | Använd ett enhetstest som läser kontrollens egenskaper (`commandButton.Name`, `commandButton.Caption`) för att verifiera att de satts korrekt. |
| **Flera knappar behövs** | Återanvändning av samma `DocumentBuilder` utan att flytta markören lägger knappen ovanpå den föregående. | Anropa `builder.MoveToDocumentEnd()` eller justera rektangelns `Y`‑värde före varje infogning. |

Att hantera dessa edge cases tidigt sparar tid när lösningen skalas upp till fullständiga formulär med dussintals kontroller.  

## Steg 7: Fullt körbart exempel  

Nedan finns ett självständigt program som du kan kopiera, klistra in och köra utan ändringar (förutom NuGet‑återställning).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Förväntad output**  

När programmet körs skrivs en sökväg liknande följande ut:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Att öppna den genererade *CommandButtonDemo.docx* visar en enda **Submit**‑knapp placerad på de koordinater som definierats i koden. Inga ytterligare UI‑element visas, vilket bekräftar att arbetsflödet **add command button programmatically** lyckades.  

## Slutsats  

Du vet nu hur du **lägger till en kommandoknapp programatiskt** i ett Word‑dokument med Aspose.Words, och du förstår också hur du **skapar en Word‑dokumentknapp** som senare kan kopplas till VBA‑makron eller externa automationsverktyg. Processen består av att initiera ett dokument, infoga en OLE‑`CommandButton`‑kontroll, konfigurera dess egenskaper och spara filen.  

Härifrån kan du:  

* Lägg till fler kontroller (checkboxes, textfält) genom att upprepa steg 3 med olika `ControlType`‑värden.  
* Koppla VBA‑makron till knappen för att utföra åtgärder som att spara ett formulär eller skicka ett e‑postmeddelande.  
* Generera hela formulär dynamiskt genom att loopa över en datadriven samling av fältdefinitioner.  

Experimentera med rektangelkoordinaterna och knappens rubrik för att matcha din UI‑design. Lycka till med kodningen!  


## Vad bör du lära dig härnäst?


Följande handledningar täcker närliggande ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}