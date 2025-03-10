---
title: Sidspara återuppringning
linktitle: Sidspara återuppringning
second_title: Aspose.Words Document Processing API
description: Lär dig att spara varje sida i ett Word-dokument som en separat PNG-bild med Aspose.Words för .NET med vår detaljerade steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sidspara återuppringning

## Introduktion

Hej där! Har du någonsin känt behovet av att spara varje sida i ett Word-dokument som separata bilder? Kanske vill du dela upp en stor rapport i lättsmälta bilder, eller så kanske du behöver skapa miniatyrer för en förhandsvisning. Oavsett din anledning, att använda Aspose.Words för .NET gör den här uppgiften till en lek. I den här guiden går vi igenom processen för att ställa in en sidsparande återuppringning för att spara varje sida i ett dokument som en individuell PNG-bild. Låt oss dyka direkt in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner och installera det från[här](https://releases.aspose.com/words/net/).
2. Visual Studio: Alla versioner borde fungera, men jag kommer att använda Visual Studio 2019 för den här guiden.
3. Grundläggande kunskaper i C#: Du behöver en grundläggande förståelse för C# för att följa med.

## Importera namnområden

Först måste vi importera de nödvändiga namnrymden. Detta hjälper oss att komma åt de klasser och metoder som krävs utan att skriva hela namnutrymmet varje gång.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera din dokumentkatalog

Okej, låt oss börja med att definiera sökvägen till din dokumentkatalog. Det är här ditt inmatade Word-dokument finns och där de utgående bilderna kommer att sparas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda ditt dokument

Därefter laddar vi dokumentet du vill bearbeta. Se till att ditt dokument ("Rendering.docx") finns i den angivna katalogen.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera bildsparalternativ

Vi måste konfigurera alternativen för att spara bilder. I det här fallet sparar vi sidorna som PNG-filer.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Här,`PageSet` anger intervallet av sidor som ska sparas, och`PageSavingCallback` pekar på vår anpassade återuppringningsklass.

## Steg 4: Implementera sidsparande återuppringning

Låt oss nu implementera callback-klassen som hanterar hur varje sida sparas.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Denna klass implementerar`IPageSavingCallback` gränssnitt och inom`PageSaving` metoden definierar vi namngivningsmönstret för varje sparad sida.

## Steg 5: Spara dokumentet som bilder

Slutligen sparar vi dokumentet med de konfigurerade alternativen.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Slutsats

Och där har du det! Du har framgångsrikt ställt in en sidsparande återuppringning för att spara varje sida i ett Word-dokument som en separat PNG-bild med Aspose.Words för .NET. Den här tekniken är otroligt användbar för olika applikationer, från att skapa sidförhandsvisningar till att generera individuella sidbilder för rapporter. 

Glad kodning!

## FAQ's

### Kan jag spara sidor i andra format än PNG?  
 Ja, du kan spara sidor i olika format som JPEG, BMP och TIFF genom att ändra`SaveFormat` i`ImageSaveOptions`.

### Vad händer om jag bara vill spara specifika sidor?  
 Du kan ange vilka sidor du vill spara genom att justera`PageSet` parameter in`ImageSaveOptions`.

### Är det möjligt att anpassa bildkvaliteten?  
 Absolut! Du kan ställa in egenskaper som`ImageSaveOptions.JpegQuality` för att kontrollera kvaliteten på de utgående bilderna.

### Hur kan jag hantera stora dokument effektivt?  
För stora dokument, överväg att bearbeta sidor i omgångar för att hantera minnesanvändningen effektivt.

### Var kan jag hitta mer information om Aspose.Words för .NET?  
 Kolla in[dokumentation](https://reference.aspose.com/words/net/) för omfattande guider och exempel.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
