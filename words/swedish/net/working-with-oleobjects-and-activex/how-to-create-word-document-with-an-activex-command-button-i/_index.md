---
category: general
date: 2026-09-05
description: Skapa Word-dokument med Aspose.Words C# och lär dig hur du infogar en
  ActiveX‑kommandoknapp, ställer in knappens storlek och lägger till interaktiv knappfunktionalitet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: sv
lastmod: 2026-09-05
og_description: Skapa ett Word-dokument i C# och infoga en ActiveX‑kommandoknapp.
  Denna handledning visar hur man ställer in knappens storlek och lägger till interaktiva
  knappfunktioner.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Skapa Word-dokument med ActiveX‑kommandoknapp i C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Hur man skapar ett Word‑dokument med en ActiveX‑kommandoknapp i C#
url: /sv/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument med en ActiveX‑kommandoknapp i C#

Om du behöver **skapa Word-dokument** programatiskt och bädda in ett klickbart UI‑element, visar den här guiden exakt hur. Med Aspose.Words för .NET kan du **skapa Word-dokument**, **lägga till en kommandoknapp** och styra dess utseende — utan att öppna Microsoft Word.

Du kommer att lära dig **hur man infogar ActiveX**‑kontroller, **sätter knappstorlek**, och får knappen att fungera som en interaktiv UI‑komponent. Ingen tidigare erfarenhet av COM eller VBA krävs; bara en .NET‑utvecklingsmiljö och Aspose.Words‑biblioteket.

## Vad du kommer att uppnå

* **Skapa ett Word-dokument** från början med C#.
* **Infoga en ActiveX‑kommandoknapp** (den klassiska “Click Me”-kontrollen).
* **Ställ in knappens storlek** och position exakt.
* Lägg eventuellt till enkel **interaktiv knapp**‑logik (t.ex. en makro‑platshållare).
* Spara filen som en `.docx` som kan öppnas i Microsoft Word eller någon kompatibel visare.

### Förutsättningar

| Krav | Orsak |
|------|-------|
| .NET 6.0 or later | Tillhandahåller runtime för C#‑kod. |
| Aspose.Words for .NET (latest version) | Tillhandahåller `Document`, `DocumentBuilder` och `Forms2OleControl`‑API:erna som används i exemplet. |
| Visual Studio 2022 (or any C# IDE) | Gör det enkelt att kompilera och köra provkoden. |
| Basic C# knowledge | Behövs för att förstå kodflödet. |

> **Pro tip:** Om du använder en provversion av Aspose.Words, se till att ange licensen innan du kör koden för att undvika utvärderingsvattenstämplar.

## Så här skapar du Word-dokument – övergripande arbetsflöde

Processen består av fyra logiska steg:

1. **Initiera ett nytt dokument** och en `DocumentBuilder` för att redigera det.  
2. **Infoga en ActiveX‑kommandoknapp** med `InsertForms2OleControl`.  
3. **Konfigurera knappen** – rubrik, storlek och position.  
4. **Spara** dokumentet till disk.

Varje steg förklaras i sin egen sektion nedan.

![Word-dokument med en ActiveX‑knapp](/images/activex-button.png "Skärmdump av ett Word-dokument som innehåller en ActiveX‑kommandoknapp skapad med C#")

## Så här infogar du en ActiveX‑kommandoknapp

**Hur man infogar ActiveX**‑delen startar med `InsertForms2OleControl`‑metoden. Denna metod skapar en COM‑baserad kontroll som Word behandlar som ett ActiveX‑objekt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Varför detta fungerar:** `OleControlType.CommandButton` talar om för Aspose.Words att skapa den klassiska VB‑stils‑knappen. Storlek och position uttrycks i punkter (1 punkt = 1/72 tum), vilket ger exakt kontroll över layouten.

## Så här lägger du till en kommandoknapp och sätter knappstorlek

Efter att kontrollen har infogats kan du justera dess visuella egenskaper. Steget **lägg till kommandoknapp** täcker också **sätta knappstorlek**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Förklaring:**  

* `Caption` är etiketten som visas på knappen.  
* `Width` och `Height` låter dig **sätta knappstorlek** efter den initiala infogningen — användbart när storleken beror på data vid körning.  
* `Left` och `Top` flyttar kontrollen utan att återskapa dokumentet.

> **Vanligt fallgropp:** Att glömma att använda punkter istället för pixlar gör att knappen blir för liten eller för stor. Konvertera alltid pixelvärden (`px * 72 / DPI`) om du utgår från skärm‑mått.

## Så här lägger du till en interaktiv knapp (valfritt)

En ActiveX‑knapp kan köra ett makro när den klickas, men att bädda in VBA‑kod från C# ligger utanför räckvidden för ett rent Aspose.Words‑arbetsflöde. Istället kan du lägga till en platshållar‑egenskap som Word kommer att känna igen som ett makronamn.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

När användaren öppnar den genererade `.docx`‑filen i Word, kommer ett klick på knappen att försöka köra `MyMacroName`. Om makrot inte finns, kommer Word att be användaren att skapa det.

**Varför du kan vilja använda detta:** För företagsformulär där ett makro fyller i fält, behöver C#‑koden bara placera knappen; makrologiken finns i dokumentets VBA‑projekt.

## Spara dokumentet och verifiera resultatet

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Förväntat resultat:** När `CommandButton.docx` öppnas i Microsoft Word visas en knapp med etiketten **Click Me** placerad 100 pts från vänstermarginalen och 120 pts från toppen. Knappens dimensioner är **200 pts × 80 pts**. Ett klick på knappen utlöser makro‑platshållaren (om den finns).

## Fullt fungerande exempel

Nedan är det kompletta, körbara programmet som sätter ihop allt. Kopiera det till ett nytt Console‑App‑projekt, lägg till Aspose.Words‑NuGet‑paketet och kör.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Kör programmet, öppna sedan den genererade filen. Du kommer att se den **interaktiva knappen** redo för vidare anpassning.

## Vanliga frågor

| Fråga | Svar |
|-------|------|
| **Fungerar detta med .NET Core?** | Ja. Aspose.Words stödjer .NET Standard, så samma kod körs på .NET 5/6/7. |
| **Kan jag använda andra ActiveX‑kontroller (t.ex. CheckBox)?** | Absolut. Ersätt `OleControlType.CommandButton` med `OleControlType.CheckBox`, `OleControlType.OptionButton` osv. |
| **Vad händer om jag behöver en större knapp på en liggande sida?** | Justera egenskaperna `Width`, `Height`, `Left` och `Top` proportionellt. Kom ihåg att punkter förblir desamma oavsett sidorientering. |
| **Krävs ett makro för att knappen ska vara klickbar?** | Nej. Knappen är fullt funktionell som ett UI‑element; ett makro lägger bara till anpassat beteende vid klick. |

## Slutsats

Du vet nu hur du **skapar Word-dokument** med Aspose.Words, **lägger till en kommandoknapp**, **sätter knappstorlek**, och eventuellt länkar knappen till ett makro för **interaktiv knapp**‑beteende. Detta tillvägagångssätt låter dig automatisera formulärskapande, generera dynamiska rapporter eller bygga Word‑baserade UI‑prototyper direkt från C#.

Nästa steg kan du utforska:

* **Hur man infogar ActiveX‑kryssrutor** för enkätformulär.  
* **Hur man lägger till rik textinnehåll** runt knappen med `DocumentBuilder`.  
* **Hur man skyddar dokumentet** samtidigt som knappen förblir funktionell.  

Känn dig fri att experimentera med olika kontrolltyper, storlekar och makronamn för att passa ditt specifika scenario. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument med Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Infoga inbäddad bild i Word-dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Skapa ett Word-dokument med tabell med Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}