---
category: general
date: 2026-10-07
description: Lär dig hur du lägger till en innehållskontroll i ett Word‑dokument med
  Aspose.Words. Den här guiden förklarar också hur du skapar en innehållskontroll
  för ett anställd‑ID‑fält.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: sv
lastmod: 2026-10-07
og_description: Lägg till en innehållskontroll i ett Word‑dokument med Aspose.Words.
  Följ den här kompletta handledningen för att lära dig hur du skapar en innehållskontroll
  och lägger till ett fält för anställdas ID.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: Lägg till ett innehållskontrollord i Word med Aspose.Words – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: Hur man lägger till en innehållskontroll i ett Word‑dokument med Aspose.Words
url: /sv/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här lägger du till content control word i ett Word-dokument med Aspose.Words

Om du behöver **add content control word** till en Word‑fil, visar den här handledningen exakt hur du gör det med Aspose.Words för .NET‑biblioteket. Oavsett om du bygger ett formulärliknande dokument eller automatiserar datainmatning, kommer du att lära dig **how to create content control** som fångar en anställds ID i ett enda steg.

I den här guiden kommer du att:

* Skapa ett tomt Word‑dokument programatiskt.  
* Infoga en plain‑text Structured Document Tag (SDT) som fungerar som en content control.  
* Fyll i kontrollen med ett anställd-ID och spara filen.  

De enda förutsättningarna är en aktuell version av .NET (4.6+ rekommenderas) och en Aspose.Words‑licens (eller gratis provversion). Inga extra NuGet‑paket krävs utöver `Aspose.Words`.

## Lägg till content control word med Aspose.Words

Det första stora steget är att skapa själva content control. I Aspose.Words representeras en **content control** av klassen `StructuredDocumentTag`. Genom att lägga till en SDT i dokumentet lägger du i praktiken **add content control word** som kan redigeras senare i Microsoft Word eller bearbetas programatiskt.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt*: `DocumentBuilder` ger dig ett markör‑liknande gränssnitt som låter dig infoga noder (paragrafer, tabeller, SDT‑er osv.) på den aktuella positionen. Att börja med ett tomt dokument säkerställer att content control visas exakt där du avser.

## Så skapar du content control för ett anställd-ID‑fält

Nästa steg är att konfigurera SDT‑en så att den fungerar som en plain‑text content control som ska hålla anställdens identifierare. `Title`‑egenskapen är vad Word visar i **Properties**‑panelen, medan `PlaceholderName` ger en ledtråd till användaren.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*Varför detta är viktigt*: Att sätta `Title` till **EmployeeID** gör kontrollen själv‑beskrivande, vilket är användbart när du senare extraherar värden med `StructuredDocumentTag.GetText()`. Placeholder‑texten förbättrar slutanvändarupplevelsen genom att ange det förväntade formatet.

### Lägg till anställd-id‑fältet i content control

Infoga nu SDT‑en i dokumentet på builderns aktuella plats och skriv det förvalda anställdnumret.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*Varför detta är viktigt*: `InsertNode` placerar SDT‑en i dokumentträdet. Den efterföljande `Writeln` skriver innehåll **inside** kontrollen eftersom builderns markör fortfarande är inom SDT‑noden. Om du hade anropat `Writeln` innan du infogade SDT‑en, skulle texten ha hamnat utanför kontrollen.

## Spara dokumentet och verifiera content control

Till sist sparas dokumentet till disk. Den sparade `.docx`‑filen kommer att innehålla content control som du kan öppna i Microsoft Word för att se placeholder‑texten och det förvalda anställd‑ID‑t.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*Varför detta är viktigt*: Att använda en absolut eller relativ sökväg låter dig kontrollera var filen hamnar. Aspose.Words skriver automatiskt de nödvändiga XML‑delarna för content control, så inga extra steg krävs.

### Snabba verifieringssteg

1. Öppna `EmployeeForm.docx` i Word.  
2. Klicka på den grå rutan som säger **Enter ID** – den ska ersättas av **12345**.  
3. Öppna fliken **Developer** → **Design Mode** för att se kontrollens egenskaper (Title = *EmployeeID*).

Om kontrollen inte visas, dubbelkolla att du använder Aspose.Words ≥ 23.10; tidigare versioner hade en annan konstruktor‑signatur för `StructuredDocumentTag`.

## Valfria varianter och kantfall

| Scenario | Hur du anpassar koden |
|----------|-----------------------|
| **Use a rich‑text control** instead of plain‑text | Change `SdtType.PlainText` to `SdtType.RichText`. |
| **Add the control to an existing document** | Läs in filen med `new Document("Existing.docx")` och placera buildern vid önskat bokmärke innan du infogar SDT‑en. |
| **Lock the content control so users cannot edit the value** | Ställ in `sdt.LockContentControl = true;` efter att du skapat SDT‑en. |
| **Apply a custom tag for later extraction** | Använd `sdt.Tag = "EmpIdTag";` och hämta den senare med `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **Set a repeating content control (multiple IDs)** | Skapa SDT‑en i en tabellrad och duplicera raden efter behov. |

**Pro tip**: Dispose alltid `Document`‑objektet (eller omslut det i ett `using`‑block) när du arbetar i en långvarig tjänst för att snabbt frigöra inhemska resurser.

## Slutsats

Du vet nu hur du **add content control word** till ett Word‑dokument med Aspose.Words, hur du **how to create content control** som fångar en anställds identifierare, och hur du **add employee id field** programatiskt. Genom att följa stegen ovan kan du bädda in strukturerade, redigerbara fält i vilket genererat dokument som helst, vilket gör det enkelt att samla in eller visa data i ett konsekvent format.

Nästa steg är att utforska relaterade ämnen såsom **binding content controls to XML data**, **creating repeating content controls for tables**, eller **using the Aspose.Words API to extract values from filled‑in controls**. Dessa tillägg låter dig bygga fullständiga, datadrivna Word‑formulär utan att någonsin öppna filen manuellt. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}