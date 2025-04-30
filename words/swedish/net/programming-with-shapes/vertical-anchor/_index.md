---
"description": "Lär dig hur du ställer in vertikala ankarpositioner för textrutor i Word-dokument med Aspose.Words för .NET. Enkel steg-för-steg-guide ingår."
"linktitle": "Vertikalt ankare"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Vertikalt ankare"
"url": "/sv/net/programming-with-shapes/vertical-anchor/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vertikalt ankare

## Introduktion

Har du någonsin behövt kontrollera exakt var text visas i en textruta i ett Word-dokument? Kanske vill du att din text ska förankras högst upp, i mitten eller längst ner i textrutan? I så fall har du kommit rätt! I den här handledningen ska vi utforska hur man använder Aspose.Words för .NET för att ställa in det vertikala ankaret för textrutor i Word-dokument. Tänk på vertikal förankring som den trollstav som placerar din text exakt där du vill ha den i sin behållare. Redo att dyka in? Nu sätter vi igång!

## Förkunskapskrav

Innan vi går in på detaljerna kring vertikal förankring behöver du ha några saker på plats:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET-biblioteket installerat. Om du inte redan har det kan du göra det [ladda ner den här](https://releases.aspose.com/words/net/).
2. Visual Studio: Den här handledningen förutsätter att du använder Visual Studio eller en annan .NET IDE för kodning.
3. Grundläggande kunskaper i C#: Bekantskap med C# och .NET hjälper dig att följa med smidigt.

## Importera namnrymder

För att komma igång behöver du importera de nödvändiga namnrymderna i din C#-kod. Det är här du anger för din applikation var den hittar de klasser och metoder du ska använda. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Dessa namnrymder tillhandahåller de klasser du behöver för att arbeta med dokument och former.

## Steg 1: Initiera dokumentet

Först och främst behöver du skapa ett nytt Word-dokument. Tänk på detta som att du sätter upp din arbetsyta innan du börjar måla.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här, `Document` är din tomma duk, och `DocumentBuilder` är din pensel, så att du kan lägga till former och text.

## Steg 2: Infoga en textruteform

Nu ska vi lägga till en textruta i vårt dokument. Det är här din text kommer att finnas. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

I det här exemplet, `ShapeType.TextBox` anger den form du vill ha, och `200, 200` är textrutans bredd och höjd i punkter.

## Steg 3: Ställ in det vertikala ankaret

Det är här magin händer! Du kan ställa in den vertikala justeringen av texten i textrutan. Detta avgör om texten är förankrad i textrutans övre, mittersta eller nedre del.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

I det här fallet, `TextBoxAnchor.Bottom` säkerställer att texten förankras längst ner i textrutan. Om du vill att den ska vara centrerad eller justerad överst använder du `TextBoxAncheller.Center` or `TextBoxAnchor.Top`respektive.

## Steg 4: Lägg till text i textrutan

Nu är det dags att lägga till lite innehåll i din textruta. Tänk på det som att fylla i din arbetsyta med de sista detaljerna.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

Här, `MoveTo` säkerställer att texten infogas i textrutan, och `Write` lägger till den faktiska texten.

## Steg 5: Spara dokumentet

Det sista steget är att spara ditt dokument. Det är som att sätta din färdiga målning i en ram.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Slutsats

Och där har du det! Du har precis lärt dig hur du styr den vertikala justeringen av text i en textruta i ett Word-dokument med hjälp av Aspose.Words för .NET. Oavsett om du förankrar text högst upp, i mitten eller längst ner, ger den här funktionen dig exakt kontroll över dokumentets layout. Så nästa gång du behöver justera dokumentets textplacering vet du precis vad du ska göra!

## Vanliga frågor

### Vad är vertikal förankring i ett Word-dokument?
Vertikal förankring styr var texten placeras i en textruta, till exempel topp-, mitten- eller bottenjustering.

### Kan jag använda andra former förutom textrutor?
Ja, du kan använda vertikal förankring med andra former, även om textrutor är det vanligaste användningsfallet.

### Hur ändrar jag ankarpunkten efter att jag skapat textrutan?
Du kan ändra ankarpunkten genom att ställa in `VerticalAnchor` egenskapen på textboxformobjektet.

### Är det möjligt att förankra text i mitten av textrutan?
Absolut! Använd bara `TextBoxAnchor.Center` för att centrera texten vertikalt i textrutan.

### Var kan jag hitta mer information om Aspose.Words för .NET?
Kolla in [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/) för mer information och guider.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}