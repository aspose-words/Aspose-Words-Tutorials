---
title: Vertikalt ankare
linktitle: Vertikalt ankare
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in vertikala ankarpositioner för textrutor i Word-dokument med Aspose.Words för .NET. Enkel steg-för-steg guide ingår.
weight: 10
url: /sv/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vertikalt ankare

## Introduktion

Har du någonsin behövt kontrollera exakt var text visas i en textruta i ett Word-dokument? Kanske vill du att din text ska förankras högst upp, i mitten eller längst ner i textrutan? I så fall är du på rätt plats! I den här handledningen kommer vi att undersöka hur man använder Aspose.Words för .NET för att ställa in den vertikala ankaret för textrutor i Word-dokument. Tänk på vertikal förankring som trollstaven som placerar din text exakt där du vill ha den i dess behållare. Redo att dyka i? Låt oss komma igång!

## Förutsättningar

Innan vi dyker in i muttrarna och bultarna för vertikal förankring måste du ha några saker på plats:

1.  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Om du inte har det än så kan du[ladda ner den här](https://releases.aspose.com/words/net/).
2. Visual Studio: Denna handledning förutsätter att du använder Visual Studio eller en annan .NET IDE för kodning.
3. Grundläggande kunskaper i C#: Bekantskap med C# och .NET hjälper dig att följa med smidigt.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden i din C#-kod. Det är här du talar om för din applikation var du kan hitta klasserna och metoderna du kommer att använda. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Dessa namnrymder ger de klasser du behöver för att arbeta med dokument och former.

## Steg 1: Initiera dokumentet

Först och främst måste du skapa ett nytt Word-dokument. Se detta som att sätta upp din duk innan du börjar måla.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Här,`Document` är din tomma duk, och`DocumentBuilder` är din målarpensel, så att du kan lägga till former och text.

## Steg 2: Infoga en textrutaform

Låt oss nu lägga till en textruta i vårt dokument. Det är här din text kommer att leva. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 I det här exemplet,`ShapeType.TextBox` anger vilken form du vill ha, och`200, 200` är textrutans bredd och höjd i punkter.

## Steg 3: Ställ in det vertikala ankaret

Här händer magin! Du kan ställa in den vertikala justeringen av texten i textrutan. Detta avgör om texten är förankrad till toppen, mitten eller botten av textrutan.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 I det här fallet,`TextBoxAnchor.Bottom`säkerställer att texten förankras längst ner i textrutan. Om du ville ha den centrerad eller i linje med toppen skulle du använda`TextBoxAnchor.Center` eller`TextBoxAnchor.Top`, respektive.

## Steg 4: Lägg till text i textrutan

Nu är det dags att lägga till lite innehåll i din textruta. Se det som att du fyller i din duk med sista handen.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Här,`MoveTo` ser till att texten infogas i textrutan, och`Write` lägger till själva texten.

## Steg 5: Spara dokumentet

Det sista steget är att spara ditt dokument. Det här är som att sätta in din färdiga målning i en ram.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Slutsats

Och där har du det! Du har precis lärt dig hur du styr den vertikala justeringen av text i en textruta i ett Word-dokument med Aspose.Words för .NET. Oavsett om du förankrar text till toppen, mitten eller botten, ger den här funktionen dig exakt kontroll över dokumentets layout. Så nästa gång du behöver justera dokumentets textplacering vet du precis vad du ska göra!

## FAQ's

### Vad är vertikal förankring i ett Word-dokument?
Vertikal förankring styr var texten placeras i en textruta, till exempel topp-, mitt- eller bottenjustering.

### Kan jag använda andra former än textrutor?
Ja, du kan använda vertikal förankring med andra former, även om textrutor är det vanligaste användningsfallet.

### Hur ändrar jag ankarpunkten efter att jag skapat textrutan?
 Du kan ändra ankarpunkten genom att ställa in`VerticalAnchor` egenskapen på textbox-formobjektet.

### Är det möjligt att förankra text i mitten av textrutan?
 Absolut! Använd bara`TextBoxAnchor.Center` för att centrera texten vertikalt i textrutan.

### Var kan jag hitta mer information om Aspose.Words för .NET?
 Kolla in[Aspose.Words dokumentation](https://reference.aspose.com/words/net/) för mer information och guider.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
