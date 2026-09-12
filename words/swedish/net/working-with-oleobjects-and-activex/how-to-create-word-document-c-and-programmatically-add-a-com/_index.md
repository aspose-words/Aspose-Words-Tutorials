---
category: general
date: 2026-09-11
description: Lär dig hur du skapar ett Word‑dokument i C# och programatiskt lägger
  till en kommandoknapp med Aspose.Words i några enkla steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: sv
lastmod: 2026-09-11
og_description: Skapa ett Word‑dokument i C# och lägg till en kommandoknapp programatiskt
  med Aspose.Words. Följ den här kompletta guiden för en fungerande lösning.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Skapa Word-dokument i C# – lägg till en kommandoknapp programatiskt
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Hur man skapar ett Word‑dokument i C# och programatiskt lägger till en kommandoknapp
url: /sv/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument c# och programatiskt lägger till en kommandoknapp

Om du behöver **skapa Word-dokument c#** och bädda in en interaktiv knapp, visar den här guiden exakt hur du gör det. Med Aspose.Words kan du programatiskt lägga till en kommandoknapp på bara några rader kod, vilket eliminerar behovet av manuellt UI‑arbete i Word.

I den här handledningen kommer du att lära dig hur du:

* Initierar ett tomt Word‑fil med C#.
* Infogar en ActiveX **CommandButton**‑kontroll.
* Ställer in knappens egenskaper såsom namn och rubrik.
* Sparar dokumentet så att knappen visas när filen öppnas i Microsoft Word.

Inga externa verktyg krävs utöver Aspose.Words för .NET‑biblioteket, och stegen fungerar med .NET 6+ eller .NET Framework 4.6.2 och senare.

## Förutsättningar

Innan du börjar, se till att du har:

| Krav | Orsak |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | Tillhandahåller runtime för C#‑projektet. |
| Visual Studio 2022 (or any C# IDE) | Gör det enkelt att skriva, bygga och köra koden. |
| Aspose.Words for .NET NuGet package | Tillhandahåller klasserna `Document`, `DocumentBuilder` och `Forms2OleControl` som används i exemplet. |
| Basic knowledge of C# syntax | Gör att du kan följa koden utan extra inlärningskurvor. |

Du kan lägga till Aspose.Words‑paketet via NuGet‑konsolen:

```powershell
Install-Package Aspose.Words
```

## Steg 1: Skapa ett nytt C#‑konsolprojekt

Skapa en konsolapplikation som ska generera Word‑filen. Öppna en terminal och kör:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Den genererade `Program.cs`‑filen kommer att innehålla koden som visas i följande steg.

## Steg 2: Skapa ett tomt dokument och en DocumentBuilder

Den första operationen är att instansiera ett `Document`‑objekt, som representerar en tom `.docx`‑fil, samt en `DocumentBuilder` som låter dig redigera dokumentets innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:**  
`Document` är behållaren för alla Word‑element (paragrafer, tabeller, kontroller). `DocumentBuilder` erbjuder ett flytande API för att infoga objekt vid den aktuella markörpositionen utan att behöva hantera lågnivå‑nodsamlingar.

## Steg 3: Infoga en ActiveX CommandButton‑kontroll

Aspose.Words stödjer infogning av äldre ActiveX‑kontroller via metoden `InsertForms2OleControl`. Metoden kräver kontrolltypen och önskad storlek i punkter.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Vad som händer under huven:**  
Word behandlar en ActiveX‑kontroll som ett OLE‑objekt (Object Linking and Embedding). Klassen `Forms2OleControl` omsluter OLE‑data och exponerar egenskaper som `Name` och `Caption`.

## Steg 4: Konfigurera knappens namn och rubrik

Efter att kontrollen har placerats kan du anpassa dess runtime‑egenskaper. Att sätta ett meningsfullt `Name` hjälper dig att identifiera knappen senare, medan `Caption` definierar texten som visas på knappen.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Proffstips:**  
Om du planerar att hantera knappens klick‑händelse med VBA blir `Name` makronamnet du refererar till, t.ex. `Sub btnSubmit_Click()`.

## Steg 5: Spara dokumentet till disk

Slutligen skriver du dokumentet till en `.docx`‑fil. Välj en mapp du har skrivbehörighet till; exemplet använder en relativ sökväg som löser sig till projektets utdata‑katalog.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kör programmet skapar `CommandButton.docx`. När du öppnar filen i Microsoft Word visas en klickbar **Submit**‑knapp:

![Word-dokument med en Submit‑knapp](/images/command-button.png "Skärmbild av ett Word-dokument som innehåller en Submit‑knapp skapad med C#")

*Bildens alt‑text (og_image_alt):* `Skärmbild av ett Word-dokument som innehåller en Submit‑knapp skapad med C#`

## Verifiera resultatet

1. Starta Word och öppna `CommandButton.docx`.  
2. Du bör se en knapp med etiketten **Submit** i dokumentets kropp.  
3. När du hovrar över knappen visas namnet `btnSubmit` i **Properties**‑panelen (Developer‑fliken → Properties).  

Om knappen inte visas, se till att **Developer**‑fliken är aktiverad i Word (File → Options → Customize Ribbon → markera *Developer*). ActiveX‑kontroller är dolda när fliken är inaktiverad.

## Hantera vanliga variationer och kantfall

| Situation | Rekommenderad justering |
|-----------|------------------------|
| **Olika knappstorlek** | Ändra bredd‑ och höjd‑argumenten i `InsertForms2OleControl`. Till exempel skapar `150, 40` en större knapp. |
| **Flera knappar** | Anropa `InsertForms2OleControl` upprepade gånger och flytta builderns markör mellan anropen (`builder.Writeln();`). |
| **Knapp utan ActiveX** | Använd `InsertFormField` för att lägga till ett äldre formulärfält (t.ex. en kryssruta) om du behöver kompatibilitet med äldre Word‑versioner som blockerar ActiveX. |
| **Plattformsoberoende användning** | ActiveX‑kontroller fungerar endast i Windows‑versioner av Word. För Mac eller webbaserade visare, överväg att infoga en hyperlänk stylad som en knapp istället. |
| **Säkerhetsvarningar** | Word kan visa en säkerhetsprompt när du öppnar ett dokument som innehåller ActiveX‑kontroller. Att signera dokumentet med ett betrott certifikat minskar detta friktion. |

## Fullständigt, körbart exempel

Nedan är hela programmet som du kan kopiera och klistra in i `Program.cs`. Det kompileras och körs utan ändringar efter att ha lagt till Aspose.Words‑NuGet‑paketet.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Förväntad utskrift i konsolen:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

När du öppnar den genererade filen visas **Submit**‑knappen klar för interaktion.

## Slutsats

Du vet nu hur du **skapar Word-dokument c#** och **programatiskt lägger till kommandoknapp**‑kontroller med Aspose.Words. Processen reduceras till att initiera ett `Document`, infoga ett `Forms2OleControl`, konfigurera dess egenskaper och spara filen. Härifrån kan du:

* Lägg till fler kontroller (t.ex. kryssrutor, textfält) genom att ändra `ControlType`.
* Bifoga VBA‑makron till knappen för anpassad logik.
* Kombinera denna teknik med andra Aspose.Words‑funktioner som mail‑merge eller mallfyllning.

Experimentera med olika storlekar, rubriker och flera knappar för att passa ditt automationsscenario. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Skapa Word-dokument med Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}