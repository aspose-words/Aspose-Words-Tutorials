---
category: general
date: 2026-08-23
description: Skapa en submit‑knapp i C# Word‑automation. Lär dig att lägga till en
  ActiveX‑knapp, sätta knappens namn, rubrik och text programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: sv
lastmod: 2026-08-23
og_description: Skapa en skicka‑knapp i C# Word‑automation. Den här guiden visar hur
  du lägger till en ActiveX‑knapp, sätter dess namn, rubrik och text med Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Skapa en skicka‑knapp i C# Word‑automatisering
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Hur man skapar en submit‑knapp i C# Word‑automation
url: /sv/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar en submit‑knapp i C# Word‑automatisering

Om du behöver **skapa en submit‑knapp** i ett Word‑dokument med C#, så guidar den här guiden dig genom hela processen. Du kommer att se hur du lägger till en ActiveX‑knapp, tilldelar ett programatiskt namn och sätter knappens rubrik så att den ser ut som en vanlig *Submit*-kontroll.

Att automatisera formulärkontroller i Word kan ersätta manuellt layoutarbete och säkerställa konsekvens i hundratals dokument. I stegen nedan lär du dig också hur du **sätter knapptext**, **sätter knappnamn** och **sätter knapprubrik** – allt som är nödvändigt när knappen deltar i ett makro‑drivet arbetsflöde.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 (eller senare) installerat.  
* En referens till **Aspose.Words for .NET** (biblioteket som tillhandahåller `DocumentBuilder.InsertForms2OleControl`).  
* Grundläggande kunskap om C# och Word’s ActiveX‑formulärkontroller.

Du kan installera Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Använd den senaste stabila versionen av Aspose.Words för att dra nytta av buggfixar och nya funktioner relaterade till ActiveX‑kontroller.

## Översikt av lösningen

Guiden är organiserad i tre tydliga steg:

1. **Add ActiveX button** – använd metoden `InsertForms2OleControl` för att placera en kommandoknapp i dokumentet.  
2. **Set button name** – tilldela en unik programmatisk identifierare med egenskapen `Name`.  
3. **Set button caption** – definiera den synliga texten på knappen via egenskapen `Caption` (som också styr **set button text** du ser i UI).

När du har gått igenom guiden kommer du att ha en fullt fungerande **create submit button**‑rutin som du kan återanvända i alla Word‑automatiseringsprojekt.

## Steg 1: Lägg till en ActiveX‑knapp i dokumentet

Den första uppgiften är att **add activex button** till Word‑filen. Aspose.Words exponerar enum‑värdet `Forms2OleControlType.CommandButton` för detta ändamål.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Varför detta steg är viktigt:**  
ActiveX‑kontroller är de enda Word‑formelementen som kan köra VBA‑makron eller interagera med extern kod. Att lägga till kontrollen skapar en platshållare som senare steg kan konfigurera.

> **Edge case:** Om dokumentet redan innehåller en kontroll med samma namn kommer Word automatiskt att byta namn på den nya (t.ex. `CommandButton1`). Att explicit sätta namn i nästa steg undviker sådana kollisioner.

## Steg 2: Sätt knappnamnet

Ett pålitligt **set button name** är avgörande när du behöver referera till kontrollen från VBA eller från andra delar av din C#‑kod. Egenskapen `Name` ger knappen en programmatisk identifierare.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Varför du bör sätta ett namn:**  
När dokumentet öppnas kan VBA hämta knappen via `ActiveDocument.InlineShapes("btnSubmit")`. Ett meningsfullt namn som `btnSubmit` klargör även avsikten när du granskar dokumentets XML.

> **Pro tip:** Håll namn korta, alfanumeriska och börja med en bokstav för att vara kompatibel med VBA‑namnregler.

## Steg 3: Sätt knapprubriken (synlig text)

Texten som användarna ser på knappen styrs av egenskapen **set button caption**. I Word‑gränssnittet visas detta som knappens etikett, vilket också är **set button text** du vill visa.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Varför rubriken är viktig:**  
Rubriken är den användar‑synliga etiketten. Att ändra den senare påverkar inte knappens namn, så du kan lokalisera UI utan att bryta någon kod som är beroende av `btnSubmit`.

> **Common question:** *Can I set both Caption and Value?*  
> För en `CommandButton` styr `Caption` etiketten, medan `Value` inte används. Om du behöver ett dolt värde, lagra det i en anpassad dokumentegenskap istället.

## Fullt fungerande exempel

Att sätta ihop de tre stegen ger dig en komplett rutin som du kan klistra in i vilken konsol‑ eller Windows‑app som helst:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Förväntat resultat

När programmet körs skapas `SubmitButton.docx`. När du öppnar filen i Microsoft Word:

* En **Submit**‑knapp visas på den angivna platsen.  
* Knappens namn är `btnSubmit` (kontrollera via *Developer → Design Mode → Properties*).  
* Att klicka på knappen i designläge visar rubriken *Submit*.

Du har nu ett återanvändbart byggblock för alla formulär‑drivna Word‑lösningar.

## Ytterligare överväganden

### Hantera namn‑kollisioner

Om du kör rutinen flera gånger på samma dokument kan Word automatiskt byta namn på duplicerade kontroller. För att garantera unikhet kan du lägga till ett GUID före namnet:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Lokalisera knapprubriken

För flerspråkiga dokument, lagra rubriker i en resurssfil och tilldela dem vid körning:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Hantera knappklick

Knappen i sig innehåller ingen klick‑logik i C#. Du kopplar vanligtvis ett VBA‑makro:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Eftersom du har **set button name** till `btnSubmit` följer makronamnet automatiskt konventionen `<Name>_Click`.

## Vanliga frågor och svar

| Fråga | Svar |
|----------|--------|
| **Varför visas knappen tom?** | Se till att du har satt egenskapen `Caption`; utan den visar knappen ingen text. |
| **Kan jag använda en annan ActiveX‑kontroll?** | Ja. Byt ut `Forms2OleControlType.CommandButton` mot `CheckBox`, `OptionButton` osv., men egenskaperna skiljer sig. |
| **Är detta kompatibelt med .NET Core?** | Aspose.Words for .NET stödjer .NET 6+, så samma kod fungerar på .NET Core och .NET Framework. |
| **Vad händer om dokumentet redan har en knapp?** | Använd ett unikt `Name` (t.ex. lägg till ett GUID) för att undvika konflikter. |

## Slutsats

Du vet nu hur du **create submit button** programatiskt i ett Word‑dokument med C#. Genom att följa de tre stegen – **add activex button**, **set button name** och **set button caption** – kan du på ett pålitligt sätt **set button text**, **set button name** och **set button caption** för vilken automatiserad formulärlösning som helst.  

Härifrån kan du utforska:

* Att lägga till VBA‑makron som reagerar på **submit button**‑klicket.  
* Att styla knappen med anpassade teckensnitt eller färger via den underliggande XML‑strukturen.  
* Att generera flera knappar i en loop för dynamiska formulär.

Känn dig fri att experimentera med olika rubriker, namn och positioner för att passa ditt specifika arbetsflöde. Lycka till med automatiseringen!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word‑dokument med Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa ett linjediagram i Word med Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Skapa Word‑dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}