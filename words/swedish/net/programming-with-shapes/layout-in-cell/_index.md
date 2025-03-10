---
title: Layout I Cell
linktitle: Layout I Cell
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in layouten i cellen med Aspose.Words för .NET med denna omfattande guide. Perfekt för utvecklare som vill anpassa Word-dokument.
weight: 10
url: /sv/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Layout I Cell

## Introduktion

Om du någonsin har velat finjustera layouten på dina tabellceller i Word-dokument programmatiskt, är du på rätt plats. Idag ska vi dyka in i hur man ställer in layouten i cellen med Aspose.Words för .NET. Vi går igenom ett praktiskt exempel och delar upp det steg för steg så att du enkelt kan följa med.

## Förutsättningar

Innan vi hoppar in i koden, låt oss se till att du har allt du behöver:

1.  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Om du inte har det kan du[ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Du behöver en utvecklingsmiljö med .NET. Visual Studio är ett utmärkt val om du letar efter rekommendationer.
3. Grundläggande kunskaper om C#: Även om jag kommer att förklara varje steg, kommer en grundläggande förståelse av C# att hjälpa dig att följa med enklare.
4.  Dokumentkatalog: Förbered en katalogsökväg där du ska spara dina dokument. Vi kommer att hänvisa till detta som`YOUR DOCUMENT DIRECTORY`.

## Importera namnområden

För att komma igång, se till att du importerar de nödvändiga namnrymden i ditt projekt:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Låt oss dela upp processen i hanterbara steg.

## Steg 1: Skapa ett nytt dokument

 Först skapar vi ett nytt Word-dokument och initierar ett`DocumentBuilder` objekt för att hjälpa oss att konstruera vårt innehåll.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Starta en tabell och ställ in radformat

Vi börjar konstruera en tabell och specificerar höjd- och höjdregeln för raderna.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Steg 3: Infoga celler och fylla med innehåll

Därefter slingrar vi för att infoga celler i tabellen. För var 7:e cell avslutar vi raden för att skapa en ny.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Steg 4: Lägg till en vattenstämpelform

 Låt oss nu lägga till en vattenstämpel till vårt dokument. Vi skapar en`Shape` objekt och ställ in dess egenskaper.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Visa formen utanför tabellcellen om den ska placeras i en cell.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Steg 5: Anpassa vattenstämpelns utseende

Vi kommer att anpassa vattenstämpelns utseende ytterligare genom att ställa in dess färg- och textegenskaper.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Steg 6: Infoga vattenstämpel i dokumentet

Vi hittar den sista körningen i dokumentet och infogar vattenstämpeln på den positionen.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Steg 7: Optimera dokument för Word 2010

För att säkerställa kompatibilitet kommer vi att optimera dokumentet för Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Steg 8: Spara dokumentet

Slutligen kommer vi att spara vårt dokument i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt skapat ett Word-dokument med en anpassad tabelllayout och lagt till en vattenstämpel med Aspose.Words för .NET. Denna handledning syftade till att ge en tydlig, steg-för-steg-guide som hjälper dig att förstå varje del av processen. Med dessa färdigheter kan du nu skapa mer sofistikerade och anpassade Word-dokument programmatiskt.

## FAQ's

### Kan jag använda ett annat teckensnitt för vattenstämpeltexten?
 Ja, du kan ändra teckensnittet genom att ställa in`watermark.TextPath.FontFamily` egenskap till önskat typsnitt.

### Hur justerar jag positionen för vattenstämpeln?
 Du kan ändra`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , och`VerticalAlignment` egenskaper för att justera vattenstämpelns position.

### Är det möjligt att använda en bild istället för text för vattenstämpeln?
 Absolut! Du kan skapa en`Shape` med typen`ShapeType.Image` och ställ in dess bild med hjälp av`ImageData.SetImage` metod.

### Kan jag skapa tabeller med olika radhöjder?
Ja, du kan ställa in olika höjder för varje rad genom att ändra`RowFormat.Height` egenskap innan du infogar celler i den raden.

### Hur tar jag bort en vattenstämpel från dokumentet?
 Du kan ta bort vattenstämpeln genom att lokalisera den i dokumentets formsamling och anropa den`Remove` metod.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
