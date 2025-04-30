---
"description": "Leer hoe je de lay-out van een cel instelt met Aspose.Words voor .NET met deze uitgebreide handleiding. Perfect voor ontwikkelaars die Word-documenten willen aanpassen."
"linktitle": "Lay-out in cel"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Lay-out in cel"
"url": "/nl/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lay-out in cel

## Invoering

Als je ooit de lay-out van je tabelcellen in Word-documenten programmatisch hebt willen verfijnen, ben je hier aan het juiste adres. Vandaag duiken we in hoe je de lay-out in cellen instelt met Aspose.Words voor .NET. We nemen een praktisch voorbeeld door en leggen het stap voor stap uit, zodat je het gemakkelijk kunt volgen.

## Vereisten

Voordat we in de code duiken, controleren we of je alles hebt wat je nodig hebt:

1. Aspose.Words voor .NET: Zorg ervoor dat de Aspose.Words voor .NET-bibliotheek is geïnstalleerd. Zo niet, dan kunt u... [download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Je hebt een ontwikkelomgeving nodig die is ingesteld met .NET. Visual Studio is een goede keuze als je op zoek bent naar aanbevelingen.
3. Basiskennis van C#: Ik leg elke stap uit, maar een basiskennis van C# helpt u het proces gemakkelijker te volgen.
4. Documentmap: Maak een map aan waar u uw documenten wilt opslaan. We noemen dit 'Document Directory'. `YOUR DOCUMENT DIRECTORY`.

## Naamruimten importeren

Om te beginnen moet u ervoor zorgen dat u de benodigde naamruimten in uw project importeert:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Laten we het proces opdelen in hanteerbare stappen.

## Stap 1: Een nieuw document maken

Eerst maken we een nieuw Word-document en initialiseren we een `DocumentBuilder` object om ons te helpen onze inhoud te construeren.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Start een tabel en stel de rijopmaak in

We beginnen met het maken van een tabel en specificeren de hoogte en hoogteregel voor de rijen.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Stap 3: Cellen invoegen en vullen met inhoud

Vervolgens maken we een lus om cellen in de tabel in te voegen. Voor elke 7 cellen sluiten we de rij af om een nieuwe te maken.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Stap 4: Voeg een watermerkvorm toe

Laten we nu een watermerk aan ons document toevoegen. We maken een `Shape` object en stel de eigenschappen ervan in.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Geef de vorm buiten de tabelcel weer als deze in een cel wordt geplaatst.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Stap 5: Pas het uiterlijk van het watermerk aan

We passen het uiterlijk van het watermerk verder aan door de kleur en de teksteigenschappen in te stellen.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Stap 6: Watermerk in document invoegen

We zoeken de laatste run in het document en voegen het watermerk op die positie in.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Stap 7: Document optimaliseren voor Word 2010

Om compatibiliteit te garanderen, optimaliseren we het document voor Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Stap 8: Sla het document op

Ten slotte slaan we ons document op in de opgegeven directory.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Conclusie

En voilà! Je hebt met succes een Word-document gemaakt met een aangepaste tabelindeling en een watermerk toegevoegd met Aspose.Words voor .NET. Deze tutorial was bedoeld om je een duidelijke, stapsgewijze handleiding te bieden die je helpt elk onderdeel van het proces te begrijpen. Met deze vaardigheden kun je nu programmatisch geavanceerdere en aangepaste Word-documenten maken.

## Veelgestelde vragen

### Kan ik een ander lettertype gebruiken voor de watermerktekst?
Ja, u kunt het lettertype wijzigen door de `watermark.TextPath.FontFamily` eigenschap aan het gewenste lettertype.

### Hoe pas ik de positie van het watermerk aan?
U kunt de `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, En `VerticalAlignment` Eigenschappen om de positie van het watermerk aan te passen.

### Is het mogelijk om in plaats van tekst een afbeelding te gebruiken voor het watermerk?
Absoluut! Je kunt een `Shape` met het type `ShapeType.Image` en stel zijn afbeelding in met behulp van de `ImageData.SetImage` methode.

### Kan ik tabellen met verschillende rijhoogten maken?
Ja, u kunt voor elke rij verschillende hoogtes instellen door de `RowFormat.Height` eigenschap voordat u cellen in die rij invoegt.

### Hoe verwijder ik een watermerk uit een document?
U kunt het watermerk verwijderen door het in de vormenverzameling van het document te zoeken en de `Remove` methode.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}