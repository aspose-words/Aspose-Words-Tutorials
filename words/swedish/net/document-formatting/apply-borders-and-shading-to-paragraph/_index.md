---
title: Tillämpa kanter och skuggning på stycke i Word-dokument
linktitle: Tillämpa kanter och skuggning på stycke i Word-dokument
second_title: Aspose.Words Document Processing API
description: Använd kanter och skuggning på stycken i Word-dokument med Aspose.Words för .NET. Följ vår steg-för-steg-guide för att förbättra din dokumentformatering.
weight: 10
url: /sv/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tillämpa kanter och skuggning på stycke i Word-dokument

## Introduktion

Hej, har du någonsin undrat hur du får dina Word-dokument att dyka upp med några snygga kanter och skuggningar? Nåväl, du är på rätt plats! Idag dyker vi in i Aspose.Words för .NET-världen för att förstärka våra stycken. Föreställ dig att ditt dokument ser lika elegant ut som en professionell designers arbete med bara några rader kod. Redo att börja? Låt oss gå!

## Förutsättningar

Innan vi kavlar upp ärmarna och dyker in i kodning, låt oss se till att vi har allt vi behöver. Här är din snabba checklista:

-  Aspose.Words för .NET: Du måste ha detta bibliotek installerat. Du kan ladda ner den från[Aspose hemsida](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan IDE som stöder .NET.
- Grundläggande kunskaper om C#: Precis tillräckligt för att förstå och justera kodavsnitten.
- En giltig licens: Antingen a[tillfällig licens](https://purchase.aspose.com/temporary-license/) eller en köpt från[Aspose](https://purchase.aspose.com/buy).

## Importera namnområden

Innan vi hoppar in i koden måste vi se till att vi har de nödvändiga namnrymden importerade till vårt projekt. Detta gör alla coola funktioner i Aspose.Words tillgängliga för oss.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Låt oss nu dela upp processen i små steg. Varje steg kommer att ha en rubrik och en detaljerad förklaring. Redo? Låt oss gå!

## Steg 1: Konfigurera din dokumentkatalog

Först och främst behöver vi en plats för att spara vårt vackert formaterade dokument. Låt oss ställa in sökvägen till din dokumentkatalog.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Den här katalogen är där ditt slutliga dokument kommer att sparas. Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen på din maskin.

## Steg 2: Skapa ett nytt dokument och DocumentBuilder

 Därefter måste vi skapa ett nytt dokument och ett`DocumentBuilder` objekt. De`DocumentBuilder` är vår trollstav som låter oss manipulera dokumentet.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 De`Document` objekt representerar hela vårt Word-dokument, och`DocumentBuilder` hjälper oss att lägga till och formatera innehåll.

## Steg 3: Definiera styckegränser

Låt oss nu lägga till några snygga ramar till vårt stycke. Vi kommer att definiera avståndet från texten och ställa in olika kantstilar.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Här sätter vi ett 20-punkters avstånd mellan texten och gränserna. Kanterna på alla sidor (vänster, höger, topp, botten) är inställda på dubbla linjer. Fancy, eller hur?

## Steg 4: Använd skuggning på stycket

Kanter är bra, men låt oss ta det upp ett snäpp med lite skuggning. Vi använder ett diagonalt korsmönster med en blandning av färger för att få vårt stycke att sticka ut.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

I det här steget applicerade vi en diagonal korsstruktur med ljus korall som bakgrundsfärg och ljus lax som förgrundsfärg. Det är som att klä din paragraf i märkeskläder!

## Steg 5: Lägg till text i stycket

Vad är ett stycke utan text? Låt oss lägga till en exempelmening för att se hur vår formatering fungerar.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Denna rad infogar vår text i dokumentet. Enkelt, men nu är det insvept i en snygg ram och skuggad bakgrund.

## Steg 6: Spara dokumentet

Äntligen är det dags att rädda vårt arbete. Låt oss spara dokumentet i den angivna katalogen med ett beskrivande namn.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 Detta sparar vårt dokument med namnet`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` i katalogen vi angav tidigare.

## Slutsats

Och där har du det! Med bara några rader kod har vi förvandlat ett enkelt stycke till ett visuellt tilltalande innehåll. Aspose.Words för .NET gör det otroligt enkelt att lägga till professionell formatering till dina dokument. Oavsett om du förbereder en rapport, ett brev eller vilket dokument som helst, kommer dessa knep hjälpa dig att göra ett bra intryck. Så fortsätt, prova det och se dina dokument komma till liv!

## FAQ's

### Kan jag använda olika linjestilar för varje kant?  
 Absolut! Aspose.Words för .NET låter dig anpassa varje kant individuellt. Ställ bara in`LineStyle` för varje kanttyp som visas i guiden.

### Vilka andra skuggningstexturer finns tillgängliga?  
 Det finns flera texturer du kan använda, till exempel solid, horisontell rand, vertikal rand och mer. Kontrollera[Aspose dokumentation](https://reference.aspose.com/words/net/) för en fullständig lista.

### Hur kan jag ändra kantfärgen?  
 Du kan ställa in kantfärgen med hjälp av`Color` egendom för varje gräns. Till exempel,`borders[BorderType.Left].Color = Color.Red;`.

### Är det möjligt att tillämpa ramar och skuggningar på en specifik del av texten?  
 Ja, du kan använda kanter och skuggning på specifika textserier med hjälp av`Run` objekt inom`DocumentBuilder`.

### Kan jag automatisera den här processen för flera stycken?  
Definitivt! Du kan gå igenom dina stycken och använda samma ramar och skugginställningar programmatiskt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
