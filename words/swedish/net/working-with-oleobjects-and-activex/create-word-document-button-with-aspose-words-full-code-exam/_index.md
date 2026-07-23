---
category: general
date: 2026-07-23
description: Skapa Word‑dokumentknapp med Aspose.Words – steg‑för‑steg‑guide för att
  infoga en ActiveX CommandButton i en .docx‑fil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: sv
lastmod: 2026-07-23
og_description: 'Skapa Word-dokumentknapp med Aspose.Words: lär dig hur du bäddar
  in en ActiveX CommandButton i en Word-fil på några minuter.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Skapa Word-dokumentknapp – Aspose.Words komplett guide
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Skapa Word‑dokumentknapp med Aspose.Words – Fullständigt kodexempel
url: /sv/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# skapa Word-dokumentknapp med Aspose.Words – Komplett programmeringsguide

Har du någonsin behövt **skapa en Word-dokumentknapp** men varit osäker på vilket API du ska använda? Du är inte ensam – de flesta utvecklare stöter på problem när de försöker bädda in interaktiva kontroller i en .docx‑fil. Den goda nyheten? Med Aspose.Words för .NET kan du lägga till en fullt fungerande ActiveX CommandButton i ett Word‑dokument med bara några rader kod.

I den här handledningen går vi igenom hela processen: från att sätta upp projektet, initiera en `DocumentBuilder`, infoga knappen med `InsertForms2OleControl` och slutligen spara filen så att Word känner igen kontrollen. När du är klar har du ett färdigt Word‑dokument som innehåller en klickbar knapp – utan någon COM‑interop‑gymnastik.

## Vad du behöver

Innan vi dyker ner, se till att du har följande förutsättningar:

- **.NET 6.0** eller senare (koden fungerar även med .NET Framework 4.6+).  
- **Aspose.Words for .NET** NuGet‑paket (version 23.9 eller nyare).  
- Grundläggande kunskaper i C# (vi håller syntaxen nybörjarvänlig).  
- Visual Studio 2022 eller någon annan IDE du föredrar.

Det är allt – inga extra COM‑referenser, ingen Office‑interop, bara ren hanterad kod.

---

## Steg 1: Installera Aspose.Words för att **skapa Word-dokumentknapp**

Först och främst, lägg till Aspose.Words‑paketet i ditt projekt:

```bash
dotnet add package Aspose.Words
```

Eller, om du använder Visual Studios NuGet‑UI, sök efter “Aspose.Words” och klicka på **Install**. Detta enda kommando ger dig tillgång till `Document`, `DocumentBuilder` och metoden `InsertForms2OleControl` som vi kommer att använda senare.

> **Proffstips:** Håll dina NuGet‑paket uppdaterade; nyare versioner innehåller ofta buggfixar för ActiveX‑hantering.

---

## Steg 2: Initiera **DocumentBuilder** för en **ActiveX CommandButton**

Nu skapar vi ett nytt Word‑dokument och startar en `DocumentBuilder`. Tänk på `DocumentBuilder` som penseln som låter dig rita innehåll på duken.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Observera att vi importerar `System.Drawing` – strukturen `Rectangle` definierar knappens placering och storlek. Här kommer **ActiveX CommandButton** att bo.

---

## Steg 3: Använd **InsertForms2OleControl** för att **lägga till en CommandButton**

Här kommer kärnan i handledningen: att infoga själva knappen. Metoden `InsertForms2OleControl` tar tre argument – kontrolltyp, en `Rectangle` och valfritt ett namn. Vi använder `OleControlType.CommandButton` för att specificera exakt den kontroll vi vill ha.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Det enda anropet gör mycket:

1. **Skapar** ett OLE‑objekt i Word‑filen.  
2. **Registrerar** det som en ActiveX CommandButton, som Word renderar som ett klickbart UI‑element.  
3. **Positionerar** det enligt den rektangel vi angav.

Om du vill ändra knappens rubrik eller andra egenskaper kan du göra det efter infogning genom att komma åt den underliggande `OleFormat`. I de flesta fall räcker standardrubriken (“CommandButton1”).

---

## Steg 4: Spara Word‑dokumentet som innehåller **CommandButton**

Sparandet är enkelt – peka bara på en mapp där du har skrivrättigheter. Filändelsen måste vara `.docx` för att knappen ska överleva hela processen.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När du öppnar `CommandButton.docx` i Microsoft Word ser du en liten knapp i övre vänstra hörnet på första sidan. Att klicka på den gör ingenting av sig själv (det skulle kräva VBA), men kontrollen är fullt funktionell och kan kopplas ihop senare.

> **Varför detta fungerar:** Aspose.Words skriver OLE‑strömmen direkt in i DOCX‑paketet, vilket kringgår behovet av att Word ska generera kontrollen vid körning. Detta garanterar att knappen visas exakt där du placerade den.

---

## Steg 5: Verifiera knappen i Word

Öppna den genererade filen:

1. Starta Microsoft Word.  
2. Gå till **File → Open** och välj `CommandButton.docx`.  
3. Du bör se en rektangulär knapp med etiketten “CommandButton1”.

Om du inte ser knappen, se till att **Design Mode** är aktiverat (Developer → Design Mode). Detta visar den visuella representationen av ActiveX‑kontroller.

---

## Steg 6: Avancerade alternativ – Anpassa **ActiveX CommandButton**

Nedan följer några snabba justeringar som kan vara praktiska:

| Mål | Kodsnutt |
|------|--------------|
| Ändra rubrik | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Ange makronamn (kräver Word‑makrostöd) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Ändra storlek efter infogning | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Dessa kodsnuttar demonstrerar flexibiliteten i `InsertForms2OleControl`. Du kan även bädda in andra ActiveX‑kontroller som `CheckBox` eller `ListBox` genom att byta `OleControlType`‑enum.

---

## Fullt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet som **skapar en Word‑dokumentknapp** från grunden:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Förväntad output när du kör programmet:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Öppna den resulterande filen så ser du knappen exakt där koden placerade den.

---

## Vanliga fallgropar & hur du undviker dem

- **Saknad `System.Drawing`‑referens** – `Rectangle`‑strukturen finns där; utan den får du kompileringsfel.  
- **Använder en äldre Aspose.Words‑version** – Tidiga versioner stödde inte fullt ut `InsertForms2OleControl`. Uppgradera till den senaste stabila paketet.  
- **Sparar som `.doc` istället för `.docx`** – OLE‑strömmen tas bort i det äldre binära formatet, vilket får knappen att försvinna.  
- **Kör på en huvudlös server utan Word installerat** – Knappen finns fortfarande i filen, men du kan inte förhandsgranska den utan Word. Detta är okej för automatiserade genereringspipeline‑scenarier.

---

## Nästa steg – Utöka **skapa Word-dokumentknapp**‑arbetsflödet

Nu när du behärskar grunderna, fundera på dessa mer avancerade idéer:

- **Bifoga VBA‑makron** till knappen för anpassad affärslogik.  
- **Generera flera knappar** i en loop för dynamiska formulär.  
- **Kombinera med Aspose.PDF** för att exportera samma dokument till PDF samtidigt som den visuella layouten bevaras (knappen blir en statisk bild i PDF).  
- **  

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Skapa Word‑dokument med Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Skapa rektangulär form i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Infoga inbäddad bild i Word‑dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}