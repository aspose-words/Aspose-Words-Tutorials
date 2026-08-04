---
category: general
date: 2026-08-04
description: Skapa ett tomt Word‑dokument och infoga en kommandoknapp med Aspose.Words.
  Lär dig att ställa in knappens storlek och lägga till en klickbar knapp i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: sv
lastmod: 2026-08-04
og_description: Skapa ett tomt Word‑dokument med Aspose.Words och infoga en kommandoknapp.
  Denna guide visar hur du ställer in knappens storlek, lägger till en klickbar knapp
  och sparar filen.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Skapa ett tomt Word‑dokument och lägg till en kommandoknapp – fullständig
  C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa ett tomt Word‑dokument med en kommandoknapp – steg‑för‑steg‑guide
url: /sv/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word‑dokument med en kommandoknapp – steg‑för‑steg‑guide

Om du behöver **skapa ett tomt Word‑dokument** som innehåller en interaktiv knapp, visar den här handledningen exakt hur du gör det med Aspose.Words för .NET. Du kommer att lära dig att **infoga kommandoknapp**, justera dess utseende och göra den klickbar – allt i några rader C#.

Guiden täcker allt från projektuppsättning till sparande av den slutliga filen, så att du kan kopiera‑klistra in den kompletta lösningen i ditt eget program. På vägen förklarar vi också hur du **lägger till en klickbar knapp**, **ställer in knappens storlek**, och **skapar en kommandoknapp** programatiskt.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat.
* Visual Studio 2022 (eller någon IDE som stödjer .NET).
* Aspose.Words for .NET NuGet‑paket (`Aspose.Words` version 23.12 eller nyare).
* Grundläggande kunskaper i C# och objekt‑orienterad programmering.

Inga ytterligare Office interop‑assemblys krävs eftersom Aspose.Words fungerar helt oberoende av Microsoft Word.

## Steg 1: Ställ in .NET‑projektet

Skapa en konsolapplikation som kommer att innehålla Word‑automatiseringskoden.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Detta kommando skapar en ny mapp `WordButtonDemo` med en färdig‑att‑köra `Program.cs` och lägger till Aspose.Words‑biblioteket.

## Steg 2: Skapa ett tomt Word‑dokument

Den första operationen är att **skapa ett tomt Word‑dokument**. Aspose.Words tillhandahåller en `Document`‑klass som representerar en tom Word‑fil direkt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Att skapa ett tomt dokument ger dig en ren canvas där du kan lägga till stycken, tabeller eller, i det här fallet, en OLE‑kommandoknapp.

## Steg 3: Initiera DocumentBuilder

`DocumentBuilder` är hjälpen som låter dig infoga innehåll i dokumentet. Du måste koppla den till dokumentet du just skapade.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern håller reda på den aktuella markörpositionen, så varje efterföljande infogning sker exakt där du vill ha den.

## Steg 4: Infoga kommandoknapp

Nu **infogar vi en kommandoknapp** (en OLE `Forms2OleControl`) i dokumentet. Metoden `InsertForms2OleControl` kräver tre argument:

1. ProgID för OLE‑kontrollen – `"CommandButton"` för en standardknapp.
2. En `Rectangle` som definierar **ställer in knappens storlek** och position.
3. Bildtexten som visas på knappen.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

När dokumentet öppnas i Word beter sig knappen som någon annan inbyggd formulärkontroll – du kan klicka på den, och Word kommer att köra den associerade makron (om en sådan finns). Detta uppfyller kravet på **lägga till en klickbar knapp**.

### Varför använda Forms2OleControl?

`Forms2OleControl` bäddar in ett OLE‑objekt direkt i DOCX‑filen, vilket bevarar kontrollens egenskaper utan att behöva Word Interop‑assemblyn. Det är det mest pålitliga sättet att **skapa en kommandoknapp** som fungerar över Word‑versioner.

## Steg 5: Anpassa knappen (valfritt)

Du kanske vill **ställa in knappens storlek** mer exakt eller ändra ytterligare egenskaper som teckensnitt eller bakgrundsfärg. Aspose.Words exponerar det underliggande OLE‑objektet, vilket möjliggör ytterligare justeringar.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Om du behöver en annan storlek, justera helt enkelt `Rectangle`‑värdena i Steg 4. Koordinaterna mäts i punkter (1 pt = 1/72 tum), så `120` motsvarar ungefär 1,67 tum i bredd.

## Steg 6: Spara dokumentet

Slutligen skriver du dokumentet till disk. Den resulterande filen innehåller ett **tomt Word‑dokument** med en fullt funktionell kommandoknapp.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

När du öppnar `CommandButtonDemo.docx` i Microsoft Word ser du en knapp med etiketten “Click Me”. Att klicka på knappen visar standardmakrodialogen om du inte bifogar en egen makro.

## Fullständig källkod

Nedan är hela programmet som du kan kopiera till `Program.cs`. Det innehåller alla stegen som beskrivits ovan och kompileras utan ändringar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Förväntat resultat

När programmet körs produceras `CommandButtonDemo.docx`. När filen öppnas i Word visas:

* En enda sida som innehåller en knapp med etiketten **Click Me**.
* Knappen respekterar **ställer in knappens storlek** (120 × 30 punkter).
* Att klicka på knappen triggar Word:s standard‑kommandoknapp‑beteende, vilket bekräftar att **lägga till en klickbar knapp**‑operationen lyckades.

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| **Fungerar detta med .doc‑filer?** | Ja. Ändra filändelsen i `doc.Save("file.doc")`. OLE‑kontrollen lagras även i det äldre binära formatet. |
| **Vad händer om jag behöver flera knappar?** | Anropa `InsertForms2OleControl` upprepade gånger och justera `Rectangle` för varje ny knapp så att de inte överlappar. |
| **Kan jag bifoga ett makro till knappen?** | Knappen i sig innehåller ingen makrokod. Du måste manuellt lägga till ett VBA‑makro i dokumentet eller via `Document`‑objektets `Modules`‑samling. |
| **Syns knappen vid PDF‑export?** | När du exporterar DOCX till PDF med Aspose.Words renderas knappen som en statisk bild, inte som en interaktiv kontroll. |
| **Vilka Word‑versioner stöds?** | OLE‑kommandoknappen fungerar i Word 2007 och senare, eftersom den följer standarden Forms2.0. |

## Slutsats

Du vet nu hur du **skapar ett tomt Word‑dokument**, **infogar en kommandoknapp**, **lägger till en klickbar knapp** och **ställer in knappens storlek** med Aspose.Words för .NET. Det kompletta exemplet demonstrerar **skapa kommandoknapp**‑arbetsflödet från början till slut, vilket ger dig en solid grund för mer avancerade Word‑automatiseringsuppgifter.

## Nästa steg

* Utforska andra OLE‑kontroller (t.ex. `CheckBox`, `ListBox`) genom att ändra ProgID i `InsertForms2OleControl`.
* Kombinera knappen med ett VBA‑makro för att utföra anpassade åtgärder när användaren klickar på den.
* Använd Aspose.Words `DocumentBuilder` för att lägga till ytterligare innehåll såsom tabeller, bilder eller fotnoter innan du infogar knappen.
* Experimentera med **ställer in knappens storlek**‑värden för att matcha ditt dokuments layoutkrav.

Lycka till med kodningen, och njut av att bygga rikare Word‑dokument med interaktiva kontroller!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}