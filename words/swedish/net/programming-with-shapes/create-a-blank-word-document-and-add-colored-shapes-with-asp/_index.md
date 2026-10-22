---
category: general
date: 2026-09-21
description: Skapa ett tomt Word‑dokument med Aspose.Words, ange formens storlek,
  ange formens position, ange formens färg och spara docx‑filen i en enda genomgång.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: sv
lastmod: 2026-09-21
og_description: Skapa ett tomt Word‑dokument, ställ in formens storlek, ställ in formens
  position, ställ in formens färg och spara docx‑filen med Aspose.Words på några minuter.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Skapa ett tomt Word-dokument och lägg till färgade former – Aspose.Words‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Skapa ett tomt Word‑dokument och lägg till färgade former med Aspose.Words
url: /sv/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word‑dokument och lägg till färgade former med Aspose.Words

Om du behöver **skapa ett tomt Word‑dokument** programatiskt visar den här guiden hur du gör det med Aspose.Words. Du kommer att lära dig hur du **anger formens storlek**, **anger formens position**, **anger formens färg** och slutligen **sparar docx‑filen** utan att lämna din IDE.

Att arbeta med Word‑filer i C# innebär ofta att man jonglerar med lågnivå‑OpenXML‑anrop, men Aspose.Words döljer komplexiteten. I slutet av den här tutorialen har du en fullt funktionell `.docx` som innehåller en grupperad form bestående av två färgade rektanglar – perfekt för rapporter, certifikat eller anpassade mallar.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 eller nyare (installera via NuGet: `Install-Package Aspose.Words`)
- Grundläggande kunskap om C# och Visual Studio (eller någon annan C#‑redigerare)

Ingen befintlig Word‑fil krävs; tutorialen börjar med att **skapa ett tomt Word‑dokument** från grunden.

## Skapa ett tomt Word‑dokument med Aspose.Words

Det första steget är att instansiera ett `Document`‑objekt. Detta objekt representerar en tom Word‑fil i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` är tomt från början, vilket är exakt vad du behöver när du **skapar ett tomt Word‑dokument**. `builder` kommer senare att användas för att infoga gruppformen på den aktuella markörpositionen.

## Ange formens storlek och skapa en GroupShape

En `GroupShape` fungerar som en behållare som kan hålla flera enskilda former. Definiera först behållarens övergripande dimensioner.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Här **anger vi formens storlek** för själva gruppen (300 × 200). Samma egenskapsnamn (`Width`, `Height`) används för varje barnform, vilket ger dig fin‑granulär kontroll över varje element.

## Lägg till den första rektangeln och ange formens färg

Lägg nu till en rektangel i gruppen och ge den en bakgrundsfärg.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Egenskapen `FillColor` **anger formens färg**. Genom att använda `System.Drawing.Color` kan du välja vilket fördefinierat eller eget ARGB‑värde som helst.

## Lägg till en andra rektangel, ange dess storlek, position och färg

Den andra rektangeln visar hur du **anger formens position** relativt gruppen och hur du ändrar dess färg.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Eftersom gruppens bredd är 300 punkter får de två 120‑punkts‑rektanglarna plats med ett mellanrum på 30 punkter. Justera `Left` och `Top` om du behöver ett annat layout.

## Infoga GroupShape i dokumentet

När gruppen är fullt konfigurerad placerar du den på den aktuella markörpositionen.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` skriver formen direkt in i dokumentets kropp och bevarar den exakta **angivna formpositionen** du definierade tidigare.

## Spara docx‑filen

Det sista steget är att skriva dokumentet till disk. Detta demonstrerar **spara docx‑fil**‑operationen.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Efter att programmet har körts, öppna `GroupShape.docx` i Microsoft Word. Du bör se en tom sida med en grupperad form som innehåller två färgade rektanglar placerade sida‑vid‑sida.

### Förväntat resultat

- En enkelsidig `.docx`‑fil.
- Sidan innehåller en gruppform placerad 100 pt från vänster‑ och toppmarginalerna.
- Inuti gruppen sitter en ljusblå rektangel till vänster och en ljuskorall‑rektangel till höger, båda 120 × 80 pt.

## Fullt, körbart exempel

Nedan är hela programmet som du kan kopiera‑klistra in i en konsolapplikation. Inga ytterligare filer behövs.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När du kör detta program skapas exakt det dokument som beskrivits tidigare, och uppfyller alla fyra målen: **skapa tomt Word‑dokument**, **ange formens storlek**, **ange formens position**, **ange formens färg** och **spara docx‑fil**.

## Vanliga variationer och kantfall

| Scenario | Vad som ska ändras | Varför det är viktigt |
|----------|-------------------|-----------------------|
| **Olika formtyper** | Ersätt `ShapeType.Rectangle` med `ShapeType.Ellipse`, `ShapeType.Triangle` osv. | Gör det möjligt att bygga mer komplex grafik utan externa bilder. |
| **Dynamiska dimensioner** | Beräkna `Width` och `Height` från användarinmatning eller konfigurationsfiler. | Gör lösningen återanvändbar i flera dokumentmallar. |
| **Spara som PDF** | Anropa `document.Save("output.pdf", SaveFormat.Pdf);` | Om mottagarna behöver ett icke‑redigerbart format är PDF ett säkert val. |
| **Lägga till text i en form** | Skapa en `TextBox`‑form och sätt `TextBox.Text`. | Användbart för att skapa märkta märken eller pratbubblor. |
| **Flera grupper på en sida** | Upprepa steg 2‑5 med olika `Left`/`Top`‑värden. | Gör det möjligt att bygga instrumentpaneler eller flersektions‑layouter. |

### Proffstips

När du behöver justera former exakt, använd egenskapen `ShapeBase.WrapType = WrapType.Inline` innan du infogar gruppen. Detta får gruppen att bete sig som ett stycke och förhindrar oväntad textflöde runt den.

## Slutsats

Du vet nu hur du **skapar ett tomt Word‑dokument** med Aspose.Words, **anger formens storlek**, **anger formens position**, **anger formens färg** och **sparar docx‑filen**. Det kompletta exemplet visar ett rent, återanvändbart mönster för att lägga till grupperad grafik i alla Word‑automatiseringsprojekt.

Härifrån kan du utforska:

- Lägga till fler former eller bilder i samma `GroupShape` (**ange formens storlek**, **ange formens färg**‑variationer).
- Använda `ShapeBase.Rotation` för att rotera rektanglar för dekorativa effekter.
- Exportera samma dokument som PDF eller HTML för bredare distribution (**spara docx‑fil**‑alternativ).

Känn dig fri att experimentera med olika färger, storlekar och layoutlogik för att matcha dina specifika rapport‑ eller mallbehov. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande tutorialerna täcker nära besläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}