---
category: general
date: 2026-09-08
description: Hur man sparar docx när man infogar en ActiveX‑kontroll i C#. Följ den
  här steg‑för‑steg‑guiden för att lägga till en kommandoknapp programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: sv
lastmod: 2026-09-08
og_description: Hur man sparar docx när man infogar en ActiveX‑kontroll i C#. Denna
  handledning guidar dig genom att programatiskt skapa ett Word‑dokument, lägga till
  en kommandoknapp och spara filen.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Hur man sparar docx och bäddar in en ActiveX‑knapp i C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Hur man sparar docx och infogar en ActiveX‑knapp med C#
url: /sv/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man sparar docx och infogar en ActiveX‑knapp med C#

Om du behöver programmera fram ett Word‑dokument och sedan spara docx med en interaktiv knapp, visar den här guiden hur du gör det. Du kommer att lära dig att infoga en ActiveX‑kontroll, lägga till en ActiveX‑knapp och spara den resulterande .docx‑filen med C# och Aspose.Words‑biblioteket.

Handledningen täcker varje steg som krävs för att **create word document programmatically**, bädda in en **command button** och lagra filen på disk. Ingen tidigare erfarenhet av COM‑objekt krävs, men du bör ha grundläggande kunskaper i C# och ha Visual Studio installerat.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare  
* Visual Studio 2022 (eller någon C#‑IDE)  
* Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)  
* Förståelse för C#‑projektstruktur  

Dessa komponenter garanterar att koden kompileras och körs utan ytterligare konfiguration.

## Steg 1: Skapa ett nytt C#‑konsolprojekt

Skapa en konsolapplikation som kommer att innehålla Word‑automatiseringslogiken.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Kommandot ovan skapar en mapp med namnet **WordActiveXDemo**, lägger till Aspose.Words‑referensen och förbereder projektet för kompilering.

## Steg 2: Skapa ett Word‑dokument programatiskt

Öppna den genererade filen `Program.cs` och lägg till de nödvändiga `using`‑direktiven.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Instansiera nu ett tomt `Document`‑objekt. Detta objekt representerar hela Word‑filen i minnet.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document`‑klassen är ingångspunkten för alla Word‑behandlingsoperationer. I detta skede innehåller dokumentet inga sidor, men Aspose.Words kommer automatiskt att skapa ett standardavsnitt när du lägger till innehåll.

## Steg 3: Infoga en ActiveX‑kontroll – lägg till en ActiveX‑knapp

Ett **Forms2OleControl**‑objekt låter dig bädda in en ActiveX‑kontroll i ett Word‑stycke. Följande kod infogar en **CommandButton** med en bredd på 150 pt och en höjd på 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` skapar kontrollen och returnerar en starkt typad `Forms2OleControl`‑instans, som du kan konfigurera vidare. Metoden lägger automatiskt till ett nytt stycke för att hysa kontrollen, så du behöver inte hantera styckeobjekt manuellt.

## Steg 4: Konfigurera kommandoknappen – hur man lägger till egenskaper för kommandoknappen

Ställ in knappens **Name**‑ och **Caption**‑egenskaper för att göra den identifierbar vid körning och användarvänlig i gränssnittet.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

`Name`‑attributet är användbart när du senare hanterar knappens klick‑händelse via VBA eller ett Word‑makro. `Caption` är den text som slutanvändaren ser på knappens yta.

### Proffstips
Om du planerar att automatisera klick‑hanteringen från C#, bädda in ett VBA‑makro som refererar till `cmdSubmit`. Word kommer att be användaren att aktivera makron när dokumentet öppnas, vilket är standardbeteende för säkerhet kring ActiveX‑kontroller.

## Steg 5: Så sparar du docx

När kontrollen är på plats, lagra dokumentet till en .docx‑fil. `Save`‑metoden väljer automatiskt rätt format baserat på filändelsen.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Att spara filen slutför arbetsflödet **how to save docx**. Den resulterande filen kan öppnas i Microsoft Word, där ActiveX‑knappen visas på första sidan. När du klickar på knappen visar Word ett platshållarmeddelande om inget makro är bifogat.

## Steg 6: Kör programmet och verifiera resultatet

Kompilera och kör konsolappen:

```bash
dotnet run
```

När programmet är klart, öppna `C:\Temp\CommandButton.docx` i Microsoft Word:

* Dokumentet innehåller en enda sida med en **Submit**‑knapp nära toppen.  
* När du håller muspekaren över knappen visas verktygstipset med namnet `cmdSubmit`.  
* Inget innehåll går förlorat, och filstorleken är jämförbar med en standardtom .docx.

Om knappen inte visas, kontrollera att:

1. Word‑inställningarna i **Trust Center** tillåter ActiveX‑kontroller.  
2. Filen sparades med filändelsen `.docx` (inte `.doc`).  

## Kantfall och vanliga variationer

| Situation | Rekommenderad justering |
|-----------|------------------------|
| Du behöver en annan knappstorlek | Ändra bredd‑ och höjduppgifterna i `InsertForms2OleControl`. |
| Du vill ha knappen på en specifik sida | Använd `builder.MoveToDocumentEnd();` efter att ha lagt till sidor, eller infoga ett sidbrytning före kontrollen. |
| Du måste stödja miljöer utan Aspose.Words | Använd Open XML SDK för att infoga ett `w:object`‑element, men koden blir avsevärt mer komplex. |
| Makro‑aktiverat dokument krävs | Spara med filändelsen `.docm` (`document.Save("MyDoc.docm");`) och bädda in en VBA‑modul som hanterar `cmdSubmit_Click`. |

## Komplett källkod

Nedan är det fullständiga, fristående programmet som du kan kopiera in i `Program.cs` och köra utan ändringar (förutom utsökvägen).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Förväntad utskrift i konsolen

```
Document saved to C:\Temp\CommandButton.docx
```

När filen öppnas i Word visas en knapp med etiketten **Submit**. Att klicka på knappen utlöser standard‑ActiveX‑beteendet (en meddelanderuta som indikerar att inget makro är bifogat).

## Slutsats

Denna handledning demonstrerade **how to save docx** samtidigt som en **ActiveX control**, specifikt en **add activex button** som fungerar som en kommandoknapp. Du vet nu hur du **create word document programmatically**, konfigurerar knappens egenskaper och lagrar filen för slutanvändarinteraktion.

Härifrån kan du utforska:

* Lägga till VBA‑makron för att hantera `cmdSubmit_Click`.  
* Infoga andra ActiveX‑kontroller såsom kryssrutor eller kombinationsrutor.  
* Generera flersidiga dokument med flera interaktiva element.  

Experimentera med olika kontrolltyper och layoutalternativ för att bygga rika, interaktiva Word‑mallar som effektiviserar dina affärsprocesser.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}