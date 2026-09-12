---
category: general
date: 2026-09-11
description: Lär dig hur du skapar forms2olecontrol i kod med Aspose.Words DocumentBuilder.
  Denna steg‑för‑steg‑guide täcker infogning av ActiveX‑kommandoknapp, användning
  av setOleClassName och storleksinställning.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: sv
lastmod: 2026-09-11
og_description: Skapa forms2olecontrol i kod med Aspose.Words. Följ den här guiden
  för att infoga en ActiveX‑kommandoknapp, ange dess klassnamn och justera dess storlek.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Skapa forms2olecontrol i kod – komplett Aspose.Words-guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Hur man skapar forms2olecontrol i kod med Aspose.Words
url: /sv/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här skapar du forms2olecontrol i kod med Aspose.Words

Om du behöver **create forms2olecontrol in code**, visar den här guiden exakt hur du gör det med Aspose.Words .NET API. Oavsett om du automatiserar en mall som kräver en ActiveX‑knapp eller bara vill berika ett Word‑dokument programmässigt, täcker stegen nedan allt från att infoga kontrollen till att konfigurera dess utseende.

I den här tutorialen lär du dig hur du använder **Aspose.Words DocumentBuilder** för att infoga en **ActiveX command button**, sätta dess klass med **setOleClassName‑metoden** och justera dess **Forms2OleControl‑storlek**. Inga externa verktyg behövs – bara en .NET‑utvecklingsmiljö och Aspose.Words‑biblioteket.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare installerat (koden fungerar också med .NET Framework 4.7+)
* En aktuell version av Aspose.Words for .NET NuGet‑paketet
* Grundläggande kunskap om C# och konceptet ActiveX‑kontroller i Word‑dokument

Om något av detta saknas, installera NuGet‑paketet med:

```bash
dotnet add package Aspose.Words
```

## Vad den här tutorialen täcker

* Skapa en `DocumentBuilder`‑instans
* Infoga en `Forms2OleControl` (det underliggande objektet för en ActiveX‑knapp)
* Tilldela rätt klassnamn med `setOleClassName`
* Ställa in den visuella bredden och höjden med **Forms2OleControl size**‑egenskaperna
* Spara dokumentet och verifiera resultatet

När du är klar har du en fullt funktionell Word‑fil som innehåller en klickbar knapp som du kan anpassa ytterligare eller binda till VBA‑makron.

---

## Så här skapar du forms2olecontrol i kod – steg‑för‑steg

### Steg 1: Initiera DocumentBuilder

`DocumentBuilder`‑klassen är ingångspunkten för de flesta dokumentgenereringsuppgifter i Aspose.Words. Den ger dig metoder för att lägga till text, bilder, tabeller och, viktigast för den här tutorialen, OLE‑kontroller.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:**  
`DocumentBuilder` behåller den aktuella markörpositionen i dokumentet. Genom att skapa den tidigt säkerställer du att alla efterföljande insättningar – såsom **ActiveX command button** – hamnar exakt där du vill ha dem.

### Steg 2: Infoga Forms2OleControl

`insertForms2OleControl`‑metoden returnerar ett `Forms2OleControl`‑objekt. Detta objekt representerar OLE‑kontrollens platshållare som Word renderar som en ActiveX‑knapp.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Varför detta är viktigt:**  
Utan detta anrop kan du inte manipulera kontrollens egenskaper. Det returnerade `Forms2OleControl` ger dig full åtkomst till **setOleClassName‑metoden**, storleksattribut och andra OLE‑specifika inställningar.

### Steg 3: Ange ActiveX‑klassen med setOleClassName

Word måste veta vilken typ av ActiveX‑kontroll som ska renderas. Klassnamnet för en standard‑command button är `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Varför detta är viktigt:**  
`setOleClassName`‑metoden är bryggan mellan den generiska OLE‑platshållaren och den konkreta **ActiveX command button**. Ett felaktigt klassnamn resulterar i ett tomt objekt eller ett körningsfel när dokumentet öppnas.

### Steg 4: Justera Forms2OleControl‑storleken

En knapp som är för liten eller för stor ser oprofessionell ut. Du kan styra dess dimensioner med `setWidth` och `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Varför detta är viktigt:**  
Dessa egenskaper utgör **Forms2OleControl size**. De påverkar hur knappen visas i Word‑gränssnittet och säkerställer att eventuell makro har tillräckligt klickbart område.

### Steg 5: Spara dokumentet och testa

Efter att du har konfigurerat kontrollen, spara dokumentet till en plats du väljer.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Öppna `ActiveXButton.docx` i Microsoft Word. Du bör se en knapp med etiketten “CommandButton1” (standardrubriken). Att klicka på den gör ingenting om du inte lägger till ett VBA‑makro, men själva kontrollen är fullt funktionell.

**Förväntat resultat:**  

![Word-dokument med en infogad ActiveX‑knapp](/images/activeX-button.png "Skärmbild av ett Word‑dokument som visar en nyss skapad ActiveX‑knapp infogad via kod")

*Alt‑texten för bilden innehåller huvudnyckelordet för tillgänglighet och SEO.*

---

## Förstå klassen ActiveX Forms2OleControl

`Forms2OleControl`‑klassen omsluter den lågnivå‑OLE‑infrastruktur som Word använder för ActiveX‑element. Den ärver från `Shape`, vilket betyder att du även kan tillämpa vanlig formatering (t.ex. kantlinjer, rotation) om så behövs.

* **ActiveX command button** – Det vanligaste användningsfallet; du kan binda den till ett makro via Words utvecklarverktyg.
* **setOleClassName‑metoden** – Bestämmer vilken COM‑klass Word laddar; andra giltiga värden inkluderar `"Forms.TextBox.1"` och `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Styrs via `SetWidth`/`SetHeight`. Dessa metoder tar emot punkter (1 pt = 1/72 in).

### När du ska använda Forms2OleControl vs. innehållskontroller

Om du bara behöver enkel datainmatning (t.ex. ett vanligt textfält) är Words inbyggda innehållskontroller lättare. Använd `Forms2OleControl` när du kräver full ActiveX‑funktionalitet såsom händelsehantering eller anpassad VBA‑interaktion.

---

## Ställa in ytterligare egenskaper (valfritt)

Även om kärnstegen räcker för att **create forms2olecontrol in code**, vill du ofta finjustera knappens utseende eller beteende.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Varför detta är viktigt:**  
`SetOleData` låter dig skriva godtyckliga egenskapsvärden direkt i OLE‑strömmen. Detta är det mest flexibla sättet att anpassa en **ActiveX command button** utan att behöva VBA.

---

## Vanliga fallgropar och felsökning

| Symptom | Trolig orsak | Lösning |
|--------|--------------|-----|
| Knappen visas som en grå ruta | Fel klassnamn skickat till `setOleClassName` | Verifiera att strängen är exakt `"Forms.CommandButton.1"` (skiftlägeskänslig) |
| Storleken ändras inte | Bredd/Höjd satt innan kontrollen infogades | Anropa alltid `SetWidth`/`SetHeight` **efter** `InsertForms2OleControl` |
| Dokumentet ger felet “OLE object not found” vid öppning | Saknad Aspose.Words‑licens (utvärderingsversion kan begränsa OLE) | Applicera en giltig licens eller använd gratisprov med full OLE‑support |
| Knappens rubrik förblir “CommandButton1” | `SetOleData` används inte eller makro läser inte egenskapen | Använd ett VBA‑makro för att läsa `"Caption"`‑egenskapen eller sätt rubriken via Word‑UI |

---

## Fullt körbart exempel

Nedan är ett komplett konsolprogram som du kan kopiera, klistra in och köra. Det demonstrerar allt som täcks i den här tutorialen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förklaring av varje avsnitt**

* **Using‑direktiv** – Importerar Aspose.Words‑namnutrymmet som krävs för `Document`, `DocumentBuilder` och `Forms2OleControl`.
* **Dokument‑skapande** – Instansierar en tom Word‑fil.
* **InsertForms2OleControl** – Placera OLE‑kontrollen vid builderns aktuella markör.
* **SetOleClassName** – Berättar för Word att kontrollen är en **ActiveX command button**.
* **SetWidth / SetHeight** – Justera **Forms2OleControl size** för ett professionellt utseende.
* **SetOleData (valfritt)** – Visar hur du skriver extra egenskaper som en rubrik.
* **Save** – Skriver den färdiga `.docx`‑filen till disk.

Kör programmet (`dotnet run`) och öppna `ActiveXButton.docx`. Du bör se en knapp som du senare kan länka till ett makro.

---

## Slutsats

Du vet nu hur du **create forms2olecontrol in code** med Aspose.Words, från att initiera `DocumentBuilder` till att konfigurera **ActiveX command button** med `setOleClassName` och styra dess **Forms2OleControl size**. Detta tillvägagångssätt låter dig automatisera komplexa Word‑dokument, bädda in interaktiva UI‑element och hålla all logik inom

## Vad bör du lära dig härnäst?

De följande tutorialerna behandlar närliggande ämnen som bygger på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur du skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa rektangel‑form i Word med Aspose.Words – steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}