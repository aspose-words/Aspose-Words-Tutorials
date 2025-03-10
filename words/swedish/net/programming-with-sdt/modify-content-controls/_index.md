---
title: Ändra innehållskontroller
linktitle: Ändra innehållskontroller
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ändrar strukturerade dokumenttaggar i Word med Aspose.Words för .NET. Uppdatera text, rullgardinsmenyer och bilder steg för steg.
weight: 10
url: /sv/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ändra innehållskontroller

## Introduktion

Om du någonsin har arbetat med Word-dokument och behövt ändra strukturerade innehållskontroller – som vanlig text, rullgardinslistor eller bilder – med Aspose.Words för .NET, är du på rätt plats! Structured Document Tags (SDT) är kraftfulla verktyg som gör dokumentautomatisering enklare och mer flexibel. I den här handledningen kommer vi att dyka ner i hur du kan ändra dessa SDT för att passa dina behov. Oavsett om du uppdaterar text, ändrar rullgardinsval eller byter ut bilder, kommer den här guiden att leda dig genom processen steg-för-steg.

## Förutsättningar

Innan vi går in i det snåriga med att ändra innehållskontroller, se till att du har följande:

1.  Aspose.Words för .NET installerat: Se till att du har Aspose.Words-biblioteket installerat. Om inte, kan du[ladda ner den här](https://releases.aspose.com/words/net/).

2. Grundläggande kunskaper om C#: Denna handledning förutsätter att du är bekant med grundläggande C#-programmeringskoncept.

3. En .NET-utvecklingsmiljö: Du bör ha en IDE som Visual Studio inställd för att köra .NET-applikationer.

4. Ett exempeldokument: Vi kommer att använda ett exempel på Word-dokument med olika typer av SDT. Du kan använda den från exemplet eller skapa din egen.

5.  Tillgång till Aspose-dokumentation: För mer detaljerad information, kolla in[Aspose.Words dokumentation](https://reference.aspose.com/words/net/).

## Importera namnområden

För att börja arbeta med Aspose.Words måste du importera de relevanta namnområdena till ditt C#-projekt. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Dessa namnrymder ger dig tillgång till de klasser och metoder som krävs för att manipulera strukturerade dokumenttaggar i dina Word-dokument.

## Steg 1: Ställ in din dokumentsökväg

 Innan du gör några ändringar måste du ange sökvägen till ditt dokument. Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument är lagrat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Steg 2: Gå igenom strukturerade dokumenttaggar

 För att ändra SDT:er måste du först gå igenom alla SDT:er i dokumentet. Detta görs med hjälp av`GetChildNodes` metod för att få alla noder av typ`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Ändra SDT baserat på deras typ
}
```

## Steg 3: Ändra SDT:er för vanlig text

Om SDT är en vanlig texttyp kan du ersätta dess innehåll. Rensa först befintligt innehåll och lägg sedan till ny text.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Förklaring: Här,`RemoveAllChildren()`rensar det befintliga innehållet i SDT. Vi skapar sedan en ny`Paragraph` och`Run` objekt för att infoga den nya texten.

## Steg 4: Ändra SDT:er i rullgardinsmenyn

 För SDT:er i rullgardinsmenyn kan du ändra det valda objektet genom att gå till`ListItems` samling. Här väljer vi det tredje objektet i listan.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Förklaring: Det här kodavsnittet väljer objektet i index 2 (tredje objektet) från rullgardinsmenyn. Justera indexet utifrån dina behov.

## Steg 5: Ändra bild-SDT

För att uppdatera en bild i en bild-SDT kan du ersätta den befintliga bilden med en ny.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Förklaring: Den här koden kontrollerar om formen innehåller en bild och ersätter den sedan med en ny bild som finns på`ImagesDir`.

## Steg 6: Spara ditt ändrade dokument

När du har gjort alla nödvändiga ändringar, spara det ändrade dokumentet med ett nytt namn för att behålla ditt ursprungliga dokument intakt.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Förklaring: Detta sparar dokumentet med ett nytt filnamn så att du enkelt kan skilja det från originalet.

## Slutsats

Att ändra innehållskontroller i ett Word-dokument med Aspose.Words för .NET är enkelt när du förstår stegen. Oavsett om du uppdaterar text, ändrar rullgardinsval eller byter bilder, tillhandahåller Aspose.Words ett robust API för dessa uppgifter. Genom att följa denna handledning kan du effektivt hantera och anpassa dokumentets strukturerade innehållskontroller, vilket gör dina dokument mer dynamiska och skräddarsydda efter dina behov.

## Vanliga frågor

1. Vad är en SDT (Structured Document Tag)?

SDT:er är element i Word-dokument som hjälper till att hantera och formatera dokumentinnehåll, som textrutor, rullgardinslistor eller bilder.

2. Hur kan jag lägga till ett nytt rullgardinsobjekt till en SDT?

 För att lägga till ett nytt objekt, använd`ListItems` egendom och bifoga en ny`SdtListItem` till samlingen.

3. Kan jag använda Aspose.Words för att ta bort SDT från ett dokument?

Ja, du kan ta bort SDT genom att komma åt dokumentets noder och ta bort önskad SDT.

4. Hur hanterar jag SDT:er som är kapslade i andra element?

 Använd`GetChildNodes` metod med lämpliga parametrar för att komma åt kapslade SDT:er.

5. Vad ska jag göra om SDT jag behöver ändra inte syns i dokumentet?

Se till att SDT inte är dold eller skyddad. Kontrollera dokumentinställningarna och se till att din kod är korrekt inriktad på SDT-typen.


### Exempel på källkod för Ändra innehållskontroller med Aspose.Words för .NET 

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Det är det! Du har framgångsrikt modifierat olika typer av innehållskontroller i ditt Word-dokument med Aspose.Words för .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
