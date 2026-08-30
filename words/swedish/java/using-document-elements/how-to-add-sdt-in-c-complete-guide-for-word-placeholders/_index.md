---
category: general
date: 2026-08-14
description: Hur man snabbt lägger till SDT med Aspose.Words. Lär dig att skapa en
  ordplatshållare och infoga en enkeltextkontroll i en .docx‑fil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: sv
lastmod: 2026-08-14
og_description: Hur man lägger till SDT i C# med Aspose.Words. Följ den här handledningen
  för att skapa en Word‑platshållare och infoga en vanlig textkontroll för dynamiska
  dokument.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Hur man lägger till SDT i C# – steg‑för‑steg guide för Word‑platshållare
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Hur du lägger till SDT i C# – komplett guide för Word‑platshållare
url: /sv/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till SDT i C# – komplett guide för Word‑platshållare

Om du behöver **how to add sdt** i en Word‑fil, visar den här handledningen de exakta stegen med Aspose.Words för .NET. I slutet av guiden kommer du att kunna **create word placeholder**‑taggar som låter slutanvändare skriva direkt i ett dokument, och du kommer att förstå hur du **insert plain text control** på ett pålitligt sätt.

Att arbeta med Structured Document Tags (SDT) eliminerar behovet av manuella formulärfält och ger dig ett rent, programatiskt sätt att bygga dynamiska kontrakt, rapporter eller brev. Exemplet nedan täcker allt från projektuppsättning till att spara den slutgiltiga .docx‑filen, så att du kan kopiera‑klistra koden i din egen lösning utan att missa någon beroende.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- Visual Studio 2022 eller någon C#‑IDE du föredrar
- En Aspose.Words för .NET‑licens (en gratis tillfällig licens fungerar för testning)
- Grundläggande kunskap om C#‑syntax och konceptet med SDT

> **Pro tip:** Om du planerar att distribuera de genererade dokumenten, bädda in en licensfil för att undvika utvärderingsvattenstämpeln.

## Steg 1: Ställ in projektet och importera Aspose.Words

Skapa en ny konsolapplikation och lägg till Aspose.Words NuGet‑paketet:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Dessa `using`‑direktiv ger dig åtkomst till klasserna `Document`, `DocumentBuilder` och `StructuredDocumentTag` som krävs för **insert plain text control**‑operationer.

## Steg 2: Initiera dokumentet och byggaren

Det första kodblocket skapar ett tomt Word‑dokument och en `DocumentBuilder` som låter dig skriva innehåll i det.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fungerar som en markör; varje efterföljande anrop lägger till innehåll på den aktuella positionen. Att initiera dokumentet är grunden för varje **how to add sdt**‑scenario eftersom SDT måste tillhöra en levande `Document`‑instans.

## Steg 3: Infoga en plain‑text Structured Document Tag (SDT)

Nu **insert plain text control** som fungerar som en platshållare där en användare kan skriva ett namn, ett datum eller något anpassat värde.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` talar om för Aspose.Words att skapa ett enkelt textfält.
- `SdtAppearanceTags.Default` ger taggen den standardiserade Word‑visuella stilen (en skuggad ruta när dokumentet öppnas i Word).

## Steg 4: Konfigurera SDT med en titel och platshållartext

En välnamngiven SDT gör dokumentet självförklarande för slutanvändare. Här **create word placeholder** metadata och sätter hinten som visas i fältet.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` är den interna identifieraren du kan använda senare när du extraherar eller uppdaterar värdet programatiskt.
- `PlaceholderName` är den gråtonade hinten som visas i Word, och låter användaren veta vad som ska skrivas.

## Steg 5: Lägg till omgivande innehåll

Ett dokument består sällan av en enda SDT. Du behöver vanligtvis vanliga stycken före och efter platshållaren. Använd byggarens `WriteLine`‑metod för att lägga till statisk text.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Anropet till `InsertNode` placerar den tidigare skapade SDT exakt där du behöver den, och bevarar den omgivande textflödet.

## Steg 6: Spara dokumentet till en .docx‑fil

Slutligen, spara dokumentet till disk. Sökvägen kan vara absolut eller relativ till projektmappen.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar `SDT.docx` i Microsoft Word visas en grå platshållare som läser **Enter name here**. Användare kan klicka på fältet, skriva ett värde, och dokumentet behåller det värdet när det sparas igen.

## Fullt, körbart exempel

När du sätter ihop alla bitar får du ett självständigt program som du kan köra omedelbart:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Förväntad output** när du kör programmet:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

När du öppnar den genererade `SDT.docx` visas:

```
Dear [Enter name here],
After the SDT
```

Den hakparentes‑omslutna texten är **insert plain text control**‑platshållaren som användare kan ersätta.

## Vanliga variationer och kantfall

| Situation | Hur man anpassar koden |
|-----------|-----------------------|
| **Flera platshållare** | Anropa `InsertStructuredDocumentTag` upprepade gånger och ge varje tagg en unik `Title`. |
| **Rich‑text SDT** | Använd `StructuredDocumentTagType.RichText` istället för `PlainText`. |
| **Lås platshållaren** | Sätt `plainTextTag.LockContentControl = true;` för att förhindra att användare tar bort fältet. |
| **Förifylla med ett värde** | Tilldela `plainTextTag.Text = "John Doe";` innan du sparar. |
| **Villkorlig visning** | Använd `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` för en kryssrutan‑kontroll. |

Dessa variationer låter dig **create word placeholder**‑strukturer som matchar nästan alla formulärliknande scenarier.

## Felsökningstips

- **Placeholder not visible** – Se till att du öppnar filen i Microsoft Word (eller en kompatibel visare). Vissa lätta redigerare döljer SDT.
- **License warning** – Om du ser en utvärderingsvattenstämpel, verifiera att din licensfil är korrekt inläst (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Efter att ha infogat en SDT, förblir byggarens markör *efter* taggen. Om du behöver lägga till text *inuti* taggen, använd `builder.MoveTo(plainTextTag);` innan du skriver.

## Slutsats

Du vet nu **how to add sdt** till ett Word‑dokument med Aspose.Words för .NET, hur man **create word placeholder**‑taggar, och hur man **insert plain text control** som användare kan redigera direkt i Word. Det kompletta exemplet demonstrerar initiering, tagg‑infogning, konfiguration, omgivande innehåll och sparande – allt i ett enda körbart program.

Nästa steg, utforska relaterade ämnen som **insert rich text control**, **populate SDTs from a database**, eller **convert the final document to PDF**. Alla dessa bygger på samma grunder som behandlats här, så du kan utöka din automationspipeline med förtroende.

Lycka till med kodandet, och känn dig fri att experimentera med olika SDT‑typer för att passa dina dokumentautomatiseringsbehov!

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hur man skapar redigerbara områden i skrivskyddade dokument med Aspose.Words för Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Lägg till bokmärken i Word med Aspose.Words för Java – Infoga, uppdatera, ta bort](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}