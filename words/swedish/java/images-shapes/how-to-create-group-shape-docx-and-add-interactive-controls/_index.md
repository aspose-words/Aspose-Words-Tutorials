---
category: general
date: 2026-09-05
description: Lär dig hur du skapar en gruppform i docx, infogar en ActiveX‑kommandoknapp
  och laddar Markdown i ett Word‑dokument med ett komplett C#‑exempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: sv
lastmod: 2026-09-05
og_description: Skapa gruppform i docx, infoga en ActiveX‑kommandoknapp och ladda
  Markdown i ett Word‑dokument med C#. Följ den här steg‑för‑steg‑handledningen.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Skapa gruppform i docx och bädda in ActiveX‑kontroller – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Hur man skapar en gruppform i docx och lägger till interaktiva kontroller i
  C#
url: /sv/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar gruppform‑docx och lägger till interaktiva kontroller i C#

Om du behöver **skapa gruppform‑docx**‑filer programatiskt visar den här guiden exakt hur du gör. Du får också se hur du **infogar ActiveX‑kommandoknapp**‑kontroller och **laddar Markdown i ett Word‑dokument** utan att förlora understrykning. I slutet av handledningen har du ett fullt fungerande `.docx`‑dokument som kombinerar vektorgrafik, interaktiva UI‑element och markdown‑baserat innehåll.

Denna handledning förutsätter att du har en grundläggande C#‑utvecklingsmiljö och att Aspose.Words för .NET‑biblioteket är installerat. Inga externa verktyg krävs – allt körs i en standard .NET‑konsol‑ eller skrivbordsapplikation.

## Förutsättningar

- .NET 6.0 SDK eller senare (koden fungerar också med .NET Framework 4.7+)
- Aspose.Words för .NET (NuGet‑paket `Aspose.Words`)
- Ett giltigt X.509‑certifikat (`.pfx`) om du vill testa signeringssteget
- En bildfil (t.ex. `logo.png`) och en markdown‑fil (`sample.md`) placerade i en känd mapp

> **Proffstips:** Håll alla indatafiler i en enda *resources*-mapp för att förenkla relativa sökvägar.

## Steg 1: Skapa projektet och importera namnrymder

Skapa ett nytt konsolprojekt och lägg till de nödvändiga `using`‑direktiven. Detta block demonstrerar också hur du refererar till de Aspose.Words‑klasser du kommer att använda senare.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using`‑satserna ger dig direkt åtkomst till `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` och andra typer som används genom hela handledningen.

## Steg 2: **Skapa gruppform‑docx** – lägg till en grupperad form med underordnade element

En *group shape* låter dig behandla flera ritobjekt som en enhet. Detta är användbart för att flytta eller ändra storlek på relaterade grafikobjekt tillsammans.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Varför en gruppform?**  
Gruppering håller rektangeln och ellipsen i linje när användaren drar dem i Word. Det förenklar också senare operationer som att applicera en gemensam kantlinje eller att flytta hela grafiken programatiskt.

## Steg 3: Infoga en ren‑text innehållskontroll (platshållare för användarinmatning)

Innehållskontroller ger slutanvändare ett strukturerat område att skriva text i. Platshållartexten försvinner så snart användaren börjar skriva.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName`‑egenskapen är vad Word visar i en ljusgrå cue. Användare kan ersätta den med sin egen text, och den underliggande XML‑strukturen förblir välformad.

## Steg 4: **Infoga ActiveX‑kommandoknapp** – lägg till interaktiv UI i dokumentet

ActiveX‑kontroller stöds fortfarande i moderna Word‑filer och kan trigga makron eller extern automation. Nedan lägger vi till en *command button* och sätter dess rubrik.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**När ska man använda en ActiveX‑knapp?**  
Om du distribuerar dokumentet inom en företagsmiljö som förlitar sig på VBA‑makron, kan en ActiveX‑knapp starta ett makro eller starta ett externt program. För ren HTML‑baserad interaktivitet, överväg att använda *content controls* med *Office.js* istället.

## Steg 5: Infoga en dold bild (t.ex. en logotyp) för varumärkesprofil eller senare skriptåtkomst

Dolda former visas inte i det utskrivna dokumentet men finns kvar i XML‑filen, vilket gör att du kan hämta dem programatiskt senare.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Steg 6: **Ladda markdown i ett Word‑dokument** samtidigt som understrykning bevaras

Aspose.Words kan importera Markdown direkt. Att aktivera `ImportUnderlineFormatting` säkerställer att markdown‑understrykningar (`<u>` eller `__text__`) blir Word‑understrykningar istället för vanlig text.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Edge case:** Om markdown‑filen innehåller tabeller konverteras de automatiskt till Word‑tabeller. Om du behöver anpassad tabellstil, applicera en `DocumentBuilder` efter insättningen.

## Steg 7: Signera dokumentet med XAdES‑EPES (valfritt säkerhetssteg)

Digitala signaturer garanterar dokumentets integritet. Följande kod signerar **skapa gruppform‑docx**‑filen med en XAdES‑EPES‑profil.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Säkerhetsnotering:** Håll certifikatlösenordet utanför källkontrollen. Använd miljövariabler eller ett säkert valv i produktion.

## Fullt körbart exempel

När alla steg sätts ihop får du ett enda, självständigt program. Spara filen som `Program.cs` och kör den från kommandoraden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

När programmet körs genereras `CompleteGroupShape.docx` som innehåller:

- En grupperad rektangel + ellips (kärnan i **skapa gruppform‑docx**)
- En ren‑text innehållskontroll med platshållartext
- En **infoga ActiveX‑kommandoknapp** med etiketten “Click Me”
- En dold logotypbild
- Markdown‑innehåll med bevarade understrykningar
- En XAdES‑EPES‑digital signatur (om certifikat tillhandahålls)

## Vanliga frågor och felsökning

| Fråga | Svar |
|---|---|
| **Fungerar ActiveX‑knappen i Word för macOS?** | macOS Word stödjer inte ActiveX‑kontroller. Knappen visas som en statisk bild. Använd innehållskontroller med Office.js för plattformsoberoende interaktivitet. |
| **Vad händer om markdown‑filen innehåller anpassad CSS?** | Aspose.Words ignorerar CSS; endast standard‑markdown‑syntax bearbetas. Konvertera CSS‑stylade element till Word‑stilar manuellt efter import. |
| **Kan jag lägga till fler former i samma grupp senare?** | Ja. Hämta `GroupShape` via dess namn eller index och anropa `AppendChild(newShape)`. Kom ihåg att spara dokumentet igen efter ändringar. |
| **Hur ändrar jag signaturalgoritmen?** | Sätt `signature.SignatureAlgorithm` innan du anropar `Sign`. Standard är SHA‑256, vilket uppfyller de flesta efterlevnadskrav. |
| **Är den dolda bilden synlig i Word‑gränssnittet?** | Nej, men den kan visas genom att aktivera *Show hidden text* i Word‑alternativen. Detta är användbart för att lagra metadata utan att störa layouten. |

## Nästa steg

Nu när du kan **skapa gruppform‑docx**, **infoga ActiveX‑kommandoknapp** och **ladda markdown i ett Word‑dokument**, kan du utforska:

- **Bädda in VBA‑makron** som reagerar på ActiveX‑knappens klick.
- **Applicera anpassade stilar** på de markdown‑genererade styckena.
- **Generera PDF‑filer** från samma dokument med `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automatisera batch‑behandling** av flera markdown‑filer till en samlad rapport.

Dessa tillägg låter dig bygga helt automatiserade dokument‑pipelines som kombinerar rik grafik, interaktiva kontroller och markdown‑baserad författning – allt från C#.

---

*Glad kodning! Om du gillade den här handledningen


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create markdown from word – Complete C# Guide](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}