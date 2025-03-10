---
title: Infoga Ole-objekt i Word med Ole-paketet
linktitle: Infoga Ole-objekt i Word med Ole-paketet
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar OLE-objekt i Word-dokument med Aspose.Words för .NET. Följ vår detaljerade steg-för-steg-guide för att bädda in filer sömlöst.
weight: 10
url: /sv/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga Ole-objekt i Word med Ole-paketet

## Introduktion

Om du någonsin har velat bädda in en fil i ett Word-dokument har du kommit rätt. Oavsett om det är en ZIP-fil, ett Excel-ark eller någon annan filtyp, kan det vara otroligt användbart att bädda in den direkt i ditt Word-dokument. Tänk på det som att ha ett hemligt fack i ditt dokument där du kan förvara alla möjliga skatter. Och idag ska vi gå igenom hur man gör detta med Aspose.Words för .NET. Är du redo att bli en Word-guide? Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner det från[här](https://releases.aspose.com/words/net/).
2. En utvecklingsmiljö: Visual Studio eller någon annan .NET-utvecklingsmiljö.
3. Grundläggande förståelse för C#: Du behöver inte vara expert, men att känna till din väg runt C# kommer att hjälpa.
4. En dokumentkatalog: En mapp där du kan lagra och hämta dokument.

## Importera namnområden

Först till kvarn, låt oss få ordning på våra namnutrymmen. Du måste inkludera följande namnrymder i ditt projekt:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Låt oss dela upp detta i lagom stora steg, så det är lätt att följa med.

## Steg 1: Konfigurera ditt dokument

Föreställ dig att du är en konstnär med en tom duk. Först behöver vi vår tomma duk, som är vårt Word-dokument. Så här ställer du in det:

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Den här koden initierar ett nytt Word-dokument och skapar en DocumentBuilder, som vi kommer att använda för att infoga innehåll i vårt dokument.

## Steg 2: Läs ditt Ole-objekt

Låt oss sedan läsa filen du vill bädda in. Se det här som att plocka upp skatten du vill gömma i ditt hemliga fack:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Den här raden läser alla byte från din ZIP-fil och lagrar dem i en byte-array.

## Steg 3: Sätt in Ole-objektet

Nu kommer den magiska delen. Vi ska bädda in filen i vårt Word-dokument:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Här skapar vi en minnesström från byte-arrayen och använder`InsertOleObject` metod för att bädda in den i dokumentet. Vi anger också filnamnet och visningsnamnet för det inbäddade objektet.

## Steg 4: Spara ditt dokument

Till sist, låt oss rädda vårt mästerverk:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Detta sparar dokumentet med din inbäddade fil i den angivna katalogen.

## Slutsats

Och där har du det! Du har framgångsrikt bäddat in ett OLE-objekt i ett Word-dokument med Aspose.Words för .NET. Det är som att lägga till en dold pärla i ditt dokument som kan avslöjas när som helst. Denna teknik kan vara otroligt användbar för en mängd olika applikationer, från teknisk dokumentation till dynamiska rapporter. 

## FAQ's

### Kan jag bädda in andra filtyper med den här metoden?
Ja, du kan bädda in olika filtyper som Excel-ark, PDF-filer och bilder.

### Behöver jag en licens för Aspose.Words?
 Ja, du behöver en giltig licens. Du kan få en[tillfällig licens](https://purchase.aspose.com/temporary-license/) för utvärdering.

### Hur kan jag anpassa visningsnamnet för OLE-objektet?
 Du kan ställa in`DisplayName` egendom av`OlePackage` för att anpassa den.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words stöder både .NET Framework och .NET Core.

### Kan jag redigera det inbäddade OLE-objektet i Word-dokumentet?
Nej, du kan inte redigera OLE-objektet direkt i Word. Du måste öppna den i dess ursprungliga applikation.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
