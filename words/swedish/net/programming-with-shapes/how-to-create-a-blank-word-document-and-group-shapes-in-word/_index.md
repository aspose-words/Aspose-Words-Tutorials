---
category: general
date: 2026-10-20
description: Lär dig hur du skapar ett tomt Word‑dokument, grupperar former i Word,
  anger fyllningsfärg för former och använder omslagstypen inline med ett komplett
  C#‑exempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: sv
lastmod: 2026-10-20
og_description: Skapa ett tomt Word‑dokument, gruppera former i Word och ställ in
  formens fyllningsfärg med omslagstypen inline med Aspose.Words och C#. Följ den
  kompletta handledningen.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Skapa ett tomt Word‑dokument och gruppera former i Word – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man skapar ett tomt Word‑dokument och grupperar former i Word med Aspose.Words
url: /sv/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett tomt Word-dokument och grupperar former i Word

Om du behöver **skapa ett tomt Word-dokument** som innehåller flera former som fungerar som en enhet, visar den här guiden exakt hur du gör. Du kommer att se hur du **grupperar former i Word**, sätter en forms fyllningsfärg och använder **wrap type inline**—allt med ett kort, körbart C#-program.

Handledningen går igenom varje kodrad, förklarar varför varje steg är viktigt och lyfter fram vanliga fallgropar. I slutet har du en .docx-fil som visar en rektangel och en textruta grupperade tillsammans, redo för vidare automatisering.

## Vad du kommer att lära dig

* Hur du initierar en tom Word-fil med Aspose.Words.
* Det korrekta sättet att skapa en **GroupShape** och lägga till underordnade former.
* Tekniker för **set shape fill color** och kontroll av positionering.
* Användning av **wrap type inline** så att gruppen beter sig som ett enda inline‑objekt.
* Hur du sparar och verifierar resultatet.

Ingen tidigare erfarenhet av Aspose.Words krävs, men du bör vara bekväm med grundläggande C#-syntax och ha Visual Studio (eller en annan IDE) installerad.

## Förutsättningar

| Krav | Orsak |
|------|-------|
| .NET 6.0 or later | Tillhandahåller runtime för C#‑projektet. |
| Aspose.Words for .NET (latest version) | Tillhandahåller `Document`, `DocumentBuilder` och shape‑klasserna som används i exemplet. |
| A writable folder path | `doc.Save`‑anropet behöver en giltig katalog för att skriva utdatafilen. |
| Basic C# knowledge | Gör det möjligt att följa koden och modifiera den för egna scenarier. |

Installera Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Steg 1: Skapa ett tomt Word-dokument

Den första operationen är att **skapa ett tomt Word-dokument**. Aspose.Words `Document`‑klass representerar en Word‑fil i minnet, och `DocumentBuilder` tillhandahåller ett bekvämt API för att redigera den.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt*: Att börja med ett tomt dokument garanterar att gruppformen du lägger till blir det enda innehållet, vilket gör verifieringen enkel.

## Steg 2: Definiera en gruppform med wrap type inline

En **GroupShape** fungerar som en behållare för andra former. Genom att sätta dess `WrapType` till `Inline` säkerställer du att gruppen beter sig som ett enda inline‑objekt i styckeflödet.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Varför detta är viktigt*: Användning av **wrap type inline** förhindrar att gruppen flyter bort från omgivande text, vilket är avgörande när du vill att gruppen ska röra sig som en enhet.

## Steg 3: Lägg till en rektangel och sätt formens fyllningsfärg

En rektangel är ett vanligt visuellt element. `Shape`‑konstruktorn tar en `ShapeType`; vi specificerar sedan dimensioner och fyllningsfärg.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Varför detta är viktigt*: `FillColor`‑egenskapen visar **set shape fill color** i praktiken, vilket ger rektangeln en ljusblå bakgrund som sticker ut i det färdiga dokumentet.

## Steg 4: Lägg till en textruta – hur man grupperar former effektivt

En textruta ger redigerbar text inom gruppen. Positionera den relativt gruppens koordinatsystem genom att justera `Top`‑egenskapen.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Varför detta är viktigt*: Detta steg svarar på **how to group shapes**—genom att lägga till varje underordnad form till samma `GroupShape`‑instans. `Top`‑offseten säkerställer att textrutan visas under rektangeln, vilket demonstrerar exakt layoutkontroll.

## Steg 5: Infoga den färdiga gruppformen i dokumentet

Nu när gruppen innehåller båda underordnade former, infogar du den på den aktuella builder‑positionen.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Varför detta är viktigt*: Att infoga gruppen som en enda nod garanterar att Word behandlar rektangeln och textrutan som ett logiskt objekt, vilket bevarar deras relativa positioner under redigering.

## Steg 6: Spara dokumentet och verifiera resultatet

Slutligen skriver du dokumentet till disk. Ersätt `YOUR_DIRECTORY` med en riktig sökväg på din maskin.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

När du öppnar `GroupShape.docx` i Microsoft Word bör du se en ljusblå rektangel med en textruta märkt “Grouped text” placerad direkt under den. Att markera någon av formerna kommer att markera hela gruppen, vilket bekräftar att **group shapes in Word** fungerar som avsett.

### Förväntat resultat

* En .docx-fil som innehåller ett enda stycke.
* Inuti stycket, en inline‑grupp som ser ut som ett enda sammansatt objekt.
* Rektangeln är fylld med ljusblått, och textrutan visar “Grouped text”.

![Skärmdump av det genererade Word-dokumentet](grouped_shapes.png){.center width=600 alt="Skärmdump av ett tomt Word-dokument med grupperad rektangel och textruta skapad med Aspose.Words"}

## Vanliga frågor och hantering av kantfall

### Vad händer om jag behöver att gruppen flyter istället för att vara inline?

Ersätt `WrapType.Inline` med `WrapType.TopBottom` (eller något annat `WrapType`‑enum‑värde). Flytande grupper kan positioneras oberoende av styckeflödet, men de förlorar den automatiska inline‑justeringen.

### Kan jag lägga till fler former, såsom cirklar eller bilder?

Ja. Skapa ytterligare `Shape`‑objekt med `ShapeType.Ellipse` eller `ShapeType.Image`, konfigurera deras egenskaper och anropa `group.AppendChild(newShape)`. Gruppen kommer automatiskt att expandera för att rymma de nya gränserna om du uppdaterar `group.Bounds` därefter.

### Hur ändrar jag gruppens totala storlek efter att ha lagt till barnformer?

Justera `group.Bounds` efter att alla barnformer har lagts till, eller beräkna föreningen av barnens gränser programatiskt. Detta säkerställer att gruppens träff‑testområde matchar det visuella innehållet.

### Vad händer om målmappen inte finns?

Aspose.Words kastar ett `DirectoryNotFoundException`. Skapa katalogen först:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Fungerar detta med .NET Framework istället för .NET Core?

Alla API:er som används (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) finns i .NET Framework‑versionen av Aspose.Words, så samma kod fungerar oförändrad.

## Pro‑tips

* **Prestandatips** – Återanvänd en enda `DocumentBuilder`‑instans när du infogar många grupper; att skapa en ny builder per grupp ger extra overhead.
* **Visuell konsistens** – Sätt `rectangle.StrokeColor` så att den matchar `FillColor` för ett sömlöst utseende, eller sätt `rectangle.LineWidth = 0` för att dölja kanten.
* **Felsökning** – Anropa `doc.UpdatePageLayout()` innan du sparar om du modifierar många former; detta tvingar Word att omräkna layouten och kan förhindra oväntad beskärning.

## Slutsats

Du vet nu hur du **skapar ett tomt Word-dokument**, **grupperar former i Word**, **sätter formens fyllningsfärg** och använder **wrap type inline** med Aspose.Words för .NET. Det kompletta exemplet demonstrerar den standardmetod som används för att bygga sammansatta grafikobjekt som beter sig som ett enda objekt i Word.

Härifrån kan du utforska:

* Att lägga till ytterligare former såsom bilder eller diagram.
* Att experimentera med olika `WrapType`‑värden för flytande grupper.
* Att automatisera batch‑generering av grupperade diagram i flera dokument.

Känn dig fri att anpassa koden till dina egna automationsscenarier, och dela dina resultat i kommentarerna!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}