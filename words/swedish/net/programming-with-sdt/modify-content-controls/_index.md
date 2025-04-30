---
"description": "Lär dig hur du ändrar strukturerade dokumenttaggar i Word med Aspose.Words för .NET. Uppdatera text, rullgardinsmenyer och bilder steg för steg."
"linktitle": "Ändra innehållskontroller"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ändra innehållskontroller"
"url": "/sv/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ändra innehållskontroller

## Introduktion

Om du någonsin har arbetat med Word-dokument och behövt ändra strukturerade innehållskontroller – som vanlig text, listrutor eller bilder – med Aspose.Words för .NET, har du kommit rätt! Structured Document Tags (SDT) är kraftfulla verktyg som gör dokumentautomation enklare och mer flexibel. I den här handledningen går vi in på hur du kan ändra dessa SDT för att passa dina behov. Oavsett om du uppdaterar text, ändrar listruteval eller byter ut bilder, kommer den här guiden att guida dig genom processen steg för steg.

## Förkunskapskrav

Innan vi går in på detaljerna kring att modifiera innehållskontroller, se till att du har följande:

1. Aspose.Words för .NET installerat: Se till att du har Aspose.Words-biblioteket installerat. Om inte kan du [ladda ner den här](https://releases.aspose.com/words/net/).

2. Grundläggande kunskaper i C#: Den här handledningen förutsätter att du är bekant med grundläggande C#-programmeringskoncept.

3. En .NET-utvecklingsmiljö: Du bör ha en IDE som Visual Studio konfigurerad för att köra .NET-applikationer.

4. Ett exempeldokument: Vi kommer att använda ett exempeldokument i Word med olika typer av SDT:er. Du kan använda det från exemplet eller skapa ditt eget.

5. Åtkomst till Aspose-dokumentation: För mer detaljerad information, se [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/).

## Importera namnrymder

För att börja arbeta med Aspose.Words behöver du importera relevanta namnrymder till ditt C#-projekt. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Dessa namnrymder ger dig tillgång till de klasser och metoder som krävs för att manipulera strukturerade dokumenttaggar i dina Word-dokument.

## Steg 1: Konfigurera din dokumentsökväg

Innan du gör några ändringar måste du ange sökvägen till dokumentet. Ersätt `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument är lagrat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Steg 2: Loopa igenom strukturerade dokumenttaggar

För att ändra SDT:er måste du först loopa igenom alla SDT:er i dokumentet. Detta görs med hjälp av `GetChildNodes` metod för att hämta alla noder av typen `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Ändra SDT:er baserat på deras typ
}
```

## Steg 3: Ändra SDT:er i vanlig text

Om SDT:n är av vanlig texttyp kan du ersätta dess innehåll. Först, rensa befintligt innehåll och lägg sedan till ny text.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Förklaring: Här, `RemoveAllChildren()` rensar det befintliga innehållet i SDT:n. Vi skapar sedan en ny `Paragraph` och `Run` objekt för att infoga den nya texten.

## Steg 4: Ändra SDT:er i rullgardinslistan

För SDT:er i rullgardinsmenyn kan du ändra det valda objektet genom att öppna `ListItems` samling. Här väljer vi det tredje objektet i listan.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Förklaring: Detta kodavsnitt väljer objektet vid index 2 (tredje objektet) från rullgardinsmenyn. Justera indexet baserat på dina behov.

## Steg 5: Ändra bild-SDT:er

För att uppdatera en bild inom en bild-SDT kan du ersätta den befintliga bilden med en ny.

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

Förklaring: Denna kod kontrollerar om formen innehåller en bild och ersätter den sedan med en ny bild som finns på `ImagesDir`.

## Steg 6: Spara ditt modifierade dokument

När du har gjort alla nödvändiga ändringar, spara det ändrade dokumentet med ett nytt namn för att behålla originaldokumentet intakt.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Förklaring: Detta sparar dokumentet med ett nytt filnamn så att du enkelt kan skilja det från originalet.

## Slutsats

Att ändra innehållskontroller i ett Word-dokument med Aspose.Words för .NET är enkelt när du väl förstår stegen. Oavsett om du uppdaterar text, ändrar rullgardinsmenyer eller byter bilder, tillhandahåller Aspose.Words ett robust API för dessa uppgifter. Genom att följa den här handledningen kan du effektivt hantera och anpassa dokumentets strukturerade innehållskontroller, vilket gör dina dokument mer dynamiska och anpassade efter dina behov.

## Vanliga frågor

1. Vad är en strukturerad dokumenttagg (SDT)?

SDT:er är element i Word-dokument som hjälper till att hantera och formatera dokumentinnehåll, som textrutor, listrutor eller bilder.

2. Hur kan jag lägga till ett nytt rullgardinsmenyobjekt i en SDT?

För att lägga till ett nytt objekt, använd `ListItems` egenskap och lägg till en ny `SdtListItem` till samlingen.

3. Kan jag använda Aspose.Words för att ta bort SDT:er från ett dokument?

Ja, du kan ta bort SDT:er genom att komma åt dokumentets noder och ta bort önskad SDT.

4. Hur hanterar jag SDT:er som är kapslade i andra element?

Använd `GetChildNodes` metod med lämpliga parametrar för att komma åt kapslade SDT:er.

5. Vad ska jag göra om den SDT jag behöver ändra inte syns i dokumentet?

Se till att SDT:n inte är dold eller skyddad. Kontrollera dokumentinställningarna och se till att din kod är korrekt riktad mot SDT-typen.


### Exempel på källkod för att ändra innehållskontroller med Aspose.Words för .NET 

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

Det var allt! Du har framgångsrikt modifierat olika typer av innehållskontroller i ditt Word-dokument med hjälp av Aspose.Words för .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}