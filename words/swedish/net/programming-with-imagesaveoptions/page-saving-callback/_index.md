---
"description": "Lär dig att spara varje sida i ett Word-dokument som en separat PNG-bild med Aspose.Words för .NET med vår detaljerade steg-för-steg-guide."
"linktitle": "Återuppringning av sida"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Återuppringning av sida"
"url": "/sv/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Återuppringning av sida

## Introduktion

Hej! Har du någonsin känt behov av att spara varje sida i ett Word-dokument som separata bilder? Kanske vill du dela upp en stor rapport i lättförståeliga bilder, eller kanske behöver du skapa miniatyrbilder för en förhandsgranskning. Oavsett anledning gör Aspose.Words för .NET den här uppgiften till en barnlek. I den här guiden guidar vi dig genom processen att konfigurera en återuppringning för att spara varje sida i ett dokument som en individuell PNG-bild. Nu kör vi igång!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner och installera det från [här](https://releases.aspose.com/words/net/).
2. Visual Studio: Alla versioner borde fungera, men jag kommer att använda Visual Studio 2019 för den här guiden.
3. Grundläggande kunskaper i C#: Du behöver grundläggande förståelse för C# för att kunna följa med.

## Importera namnrymder

Först måste vi importera de nödvändiga namnrymderna. Detta hjälper oss att komma åt de nödvändiga klasserna och metoderna utan att behöva skriva hela namnrymden varje gång.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera din dokumentkatalog

Okej, låt oss börja med att definiera sökvägen till din dokumentkatalog. Det är här ditt Word-indatadokument finns och där utdatabilderna kommer att sparas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda ditt dokument

Härnäst laddar vi dokumentet du vill bearbeta. Se till att ditt dokument ("Rendering.docx") finns i den angivna katalogen.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera alternativ för att spara bilder

Vi behöver konfigurera alternativen för att spara bilder. I det här fallet sparar vi sidorna som PNG-filer.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

Här, `PageSet` anger sidintervallet som ska sparas, och `PageSavingCallback` pekar på vår anpassade callback-klass.

## Steg 4: Implementera återanropet för att spara sidan

Nu ska vi implementera callback-klassen som hanterar hur varje sida sparas.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

Den här klassen implementerar `IPageSavingCallback` gränssnittet, och inom `PageSaving` Metoden definierar vi namngivningsmönstret för varje sparad sida.

## Steg 5: Spara dokumentet som bilder

Slutligen sparar vi dokumentet med de konfigurerade alternativen.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Slutsats

Och där har du det! Du har framgångsrikt konfigurerat en återanropsfunktion för att spara varje sida i ett Word-dokument som en separat PNG-bild med hjälp av Aspose.Words för .NET. Den här tekniken är otroligt användbar för olika applikationer, från att skapa sidförhandsvisningar till att generera enskilda sidbilder för rapporter. 

Lycka till med kodningen!

## Vanliga frågor

### Kan jag spara sidor i andra format än PNG?  
Ja, du kan spara sidor i olika format som JPEG, BMP och TIFF genom att ändra `SaveFormat` i `ImageSaveOptions`.

### Vad händer om jag bara vill spara specifika sidor?  
Du kan ange vilka sidor du vill spara genom att justera `PageSet` parameter i `ImageSaveOptions`.

### Är det möjligt att anpassa bildkvaliteten?  
Absolut! Du kan ställa in egenskaper som `ImageSaveOptions.JpegQuality` för att kontrollera kvaliteten på utdatabilderna.

### Hur kan jag hantera stora dokument effektivt?  
För stora dokument, överväg att bearbeta sidor i omgångar för att hantera minnesanvändningen effektivt.

### Var kan jag hitta mer information om Aspose.Words för .NET?  
Kolla in [dokumentation](https://reference.aspose.com/words/net/) för omfattande guider och exempel.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}