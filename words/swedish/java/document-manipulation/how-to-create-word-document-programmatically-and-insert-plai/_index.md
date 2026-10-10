---
category: general
date: 2026-10-10
description: Skapa Word‑dokument programatiskt med Aspose.Words och infoga en enkeltext‑innehållskontroll
  – en steg‑för‑steg‑guide för .NET‑utvecklare.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: sv
lastmod: 2026-10-10
og_description: Skapa Word-dokument programatiskt med Aspose.Words och lägg till en
  vanlig textinnehållskontroll som visar platshållartext, vilket möjliggör dynamiska
  formulärfält i .docx-filer.
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: Skapa Word-dokument programatiskt och lägg till en vanlig textinnehållskontroll
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: Hur man skapar ett Word‑dokument programatiskt och infogar en vanlig textinnehållskontroll
url: /sv/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument programatiskt och infogar en enkeltextinnehållskontroll

Om du behöver **skapa Word-dokument programatiskt**, visar den här guiden exakt hur du gör det med Aspose.Words för .NET. På bara några kodrader lär du dig också att **infoga en enkeltextinnehållskontroll** (även kallad Structured Document Tag) så att dokumentet kan fungera som ett ifyllbart formulär.

Du går igenom hela arbetsflödet—från att initiera ett nytt `Document`-objekt till att spara den slutgiltiga .docx-filen. Inga externa verktyg krävs, och exemplet fungerar med .NET 6, .NET 7 eller någon nyare .NET-runtime.

## Förutsättningar

* En giltig Aspose.Words för .NET-licens (eller använd gratis utvärderingsläge).  
* .NET 6+ SDK installerad.  
* En IDE såsom Visual Studio 2022, Rider eller VS Code.  

Om du ännu inte har installerat Aspose.Words NuGet-paketet, kör:

```bash
dotnet add package Aspose.Words
```

## Steg 1: Skapa ett Word-dokument programatiskt

Det första steget är att instansiera ett tomt `Document` och en `DocumentBuilder`. Buildern ger dig ett bekvämt API för att lägga till innehåll, sidor och Structured Document Tags (SDT:er).

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt** – `Document` representerar hela .docx-filen i minnet. Genom att skapa den programatiskt undviker du kostnaden för att öppna en mallfil, vilket är användbart för att generera rapporter, fakturor eller andra dokument i farten.

## Steg 2: Infoga en enkeltextinnehållskontroll

En **enkeltextinnehållskontroll** (SDT) låter användare skriva text i ett fördefinierat område. Den stöder också platshållartext som visas när kontrollen är tom.

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**Förklaring** – `InsertStructuredDocumentTag` skapar SDT:n på den aktuella markörpositionen i `DocumentBuilder`. Enum‑värdet `StructuredDocumentTagType.PlainText` talar om för Aspose.Words att rendera en enkeltextruta snarare än en kombinationsruta eller datumväljare. `PlaceholderName`‑egenskapen ger en visuell ledtråd till användaren, liknande den grå hint‑texten du ser i moderna Word‑formulär.

### Vanliga varianter

| Variation | Hur man uppnår det |
|-----------|-------------------|
| **Rich‑text content control** | Använd `StructuredDocumentTagType.RichText` istället för `PlainText`. |
| **Repeating section** | Använd `StructuredDocumentTagType.Group` och nästla andra taggar inuti. |
| **Custom XML mapping** | Anropa `plainTextTag.SetXmlMapping(xmlPart, xpath, false)` efter att ha skapat ett `XmlPart`. |

## Steg 3: Lägg till ytterligare dokumentinnehåll (valfritt)

Du kan lägga till vanliga stycken, tabeller eller bilder före eller efter innehållskontrollen. Här är ett snabbt exempel som lägger till en rubrik och ett stycke:

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**Tips** – Builderns markör flyttar automatiskt till slutet av den infogade SDT:n, så alla efterföljande `Writeln`‑anrop visas efter kontrollen.

## Steg 4: Spara dokumentet som innehåller innehållskontrollen

Till sist skriver du dokumentet till disk. Du kan välja vilket som helst av de stödda formaten (`.docx`, `.pdf`, `.html`, osv.). För den här handledningen sparar vi som en Word‑fil.

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Förväntat resultat

När du öppnar *SdtExample.docx* i Microsoft Word kommer du att se:

1. En rubrik **Employee Information**.  
2. En enkeltextinnehållskontroll med den grå platshållaren **Enter name**.  

Om du klickar i kontrollen försvinner platshållaren och du kan skriva vilken text som helst. Kontrollens tagg‑identifierare (`MyTag`) kan senare nås programatiskt för datautvinning eller validering.

## Fullt, körbart exempel

Nedan är en fristående konsolapplikation som samlar alla stegen. Kopiera koden till ett nytt .NET‑konsolprojekt och kör det.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

När programmet körs skrivs den fullständiga sökvägen till den genererade filen ut. Öppna filen i Word för att verifiera att **enkeltextinnehållskontrollen** visas med sin platshållare.

## Felsökning och kantfall

| Problem | Orsak | Lösning |
|-------|-------|-----|
| Platshållartext visas inte | Kontrollens redan är fylld med text eller dokumentet öppnas i ett läge som döljer platshållare. | Se till att SDT:n är tom innan du sparar, eller sätt `sdt.IsShowingPlaceholder = true` (tillgängligt i nyare Aspose.Words‑versioner). |
| Innehållskontrollen försvinner efter sparning som PDF | PDF‑export behåller inte interaktiva formulärfält som standard. | Använd `PdfSaveOptions` med `SaveFormat.Pdf` och sätt `ExportDocumentStructure = true`. |
| Tagg‑identifieraren hittas inte vid senare bearbetning | Taggnamnet stavades fel eller skrevs över. | Verifiera att identifieraren som skickas till `InsertStructuredDocumentTag` matchar namnet du frågar efter senare (`MyTag`). |

## Bästa praxis för att skapa Word-dokument programatiskt

* **Återanvänd en enda `DocumentBuilder`** per dokument för att undvika onödiga minnesallokeringar.  
* **Ställ in typsnitt och stilar innan du skriver text**; att ändra dem efter att innehåll har lagts till kan orsaka inkonsekvent formatering.  
* **Disposera stora objekt** (t.ex. `MemoryStream` om du strömmar dokumentet) med `using`‑satser.  
* **Validera dokumentet** med `doc.UpdateFields()` och `doc.UpdatePageLayout()` innan du sparar, särskilt när du lägger till tabeller eller bilder.  

## Slutsats

Du vet nu hur du **skapar Word-dokument programatiskt** och **infogar en enkeltextinnehållskontroll** med Aspose.Words för .NET. Det fullständiga exemplet visar dokumentinitiering, SDT‑infogning med platshållartext, valfritt ytterligare innehåll och sparning till en .docx‑fil.

Från detta kan du:

* Ersätt enkeltextkontrollen med **rich‑text**‑ eller **date picker**‑kontroller.  
* Fyll dokumentet med data från en databas och extrahera sedan de inmatade värdena senare med `StructuredDocumentTag.GetText()`.  
* Exportera samma dokument till PDF, HTML eller OpenXML‑format samtidigt som formulärfälten bevaras.

Experimentera med olika taggtyper och utforska Aspose.Words‑API:n för att bygga sofistikerade, ifyllbara Word‑mallar som integreras sömlöst i dina .NET‑applikationer. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}