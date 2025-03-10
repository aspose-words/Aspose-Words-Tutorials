---
title: Randen en arcering toepassen op alinea's in Word-document
linktitle: Randen en arcering toepassen op alinea's in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Pas randen en arcering toe op alinea's in Word-documenten met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding om de opmaak van uw document te verbeteren.
weight: 10
url: /nl/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Randen en arcering toepassen op alinea's in Word-document

## Invoering

Hallo, heb je je ooit afgevraagd hoe je je Word-documenten kunt laten opvallen met wat mooie randen en schaduwen? Nou, dan ben je hier aan het juiste adres! Vandaag duiken we in de wereld van Aspose.Words voor .NET om onze paragrafen op te vrolijken. Stel je voor dat je document er net zo strak uitziet als het werk van een professionele ontwerper met slechts een paar regels code. Klaar om te beginnen? Laten we beginnen!

## Vereisten

Voordat we onze mouwen opstropen en in de codering duiken, moeten we ervoor zorgen dat we alles hebben wat we nodig hebben. Hier is je snelle checklist:

-  Aspose.Words voor .NET: Deze bibliotheek moet geïnstalleerd zijn. U kunt deze downloaden van de[Aspose-website](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere IDE die .NET ondersteunt.
- Basiskennis van C#: Net genoeg om de codefragmenten te begrijpen en aan te passen.
- Een geldige licentie: ofwel een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) of een gekochte van[Aspose](https://purchase.aspose.com/buy).

## Naamruimten importeren

Voordat we in de code duiken, moeten we ervoor zorgen dat we de benodigde namespaces in ons project hebben geïmporteerd. Dit maakt alle coole features van Aspose.Words voor ons toegankelijk.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Laten we het proces nu opsplitsen in kleine stapjes. Elke stap heeft een kop en een gedetailleerde uitleg. Klaar? Laten we gaan!

## Stap 1: Stel uw documentenmap in

Allereerst hebben we een plek nodig om ons prachtig opgemaakte document op te slaan. Laten we het pad naar uw documentdirectory instellen.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 In deze directory wordt uw definitieve document opgeslagen. Vervangen`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad op uw machine.

## Stap 2: Maak een nieuw document en DocumentBuilder

 Vervolgens moeten we een nieuw document maken en een`DocumentBuilder` voorwerp. Het`DocumentBuilder` is onze toverstaf waarmee we het document kunnen manipuleren.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 De`Document` object vertegenwoordigt ons hele Word-document en de`DocumentBuilder` helpt ons inhoud toe te voegen en op te maken.

## Stap 3: Definieer alinearanden

Laten we nu wat stijlvolle randen aan onze alinea toevoegen. We definiëren de afstand tot de tekst en stellen verschillende randstijlen in.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Hier stellen we een afstand van 20 punten in tussen de tekst en de randen. De randen aan alle kanten (links, rechts, boven, onder) worden ingesteld op dubbele lijnen. Mooi, toch?

## Stap 4: Schaduw toepassen op de alinea

Randen zijn geweldig, maar laten we het nog een tandje hoger tillen met wat schaduw. We gebruiken een diagonaal kruispatroon met een mix van kleuren om onze alinea te laten opvallen.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

In deze stap hebben we een diagonale kruistextuur toegepast met licht koraal als achtergrondkleur en licht zalm als voorgrondkleur. Het is alsof je je alinea in designerkleding kleedt!

## Stap 5: Voeg tekst toe aan de alinea

Wat is een alinea zonder tekst? Laten we een voorbeeldzin toevoegen om onze opmaak in actie te zien.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Deze regel voegt onze tekst in het document in. Simpel, maar nu is het verpakt in een stijlvol frame en een gearceerde achtergrond.

## Stap 6: Sla het document op

Ten slotte is het tijd om ons werk op te slaan. Laten we het document opslaan in de opgegeven directory met een beschrijvende naam.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 Dit slaat ons document op met de naam`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` in de directory die we eerder hebben opgegeven.

## Conclusie

En daar heb je het! Met slechts een paar regels code hebben we een simpele alinea getransformeerd in een visueel aantrekkelijk stukje content. Aspose.Words voor .NET maakt het ongelooflijk eenvoudig om professioneel ogende opmaak toe te voegen aan je documenten. Of je nu een rapport, een brief of een ander document voorbereidt, deze trucs helpen je om een geweldige indruk te maken. Dus ga je gang, probeer het uit en zie je documenten tot leven komen!

## Veelgestelde vragen

### Kan ik voor elke rand een andere lijnstijl gebruiken?  
 Absoluut! Met Aspose.Words voor .NET kunt u elke rand individueel aanpassen. Stel gewoon de`LineStyle` voor elk randtype zoals aangegeven in de gids.

### Welke andere schaduwtexturen zijn beschikbaar?  
 Er zijn verschillende texturen die u kunt gebruiken, zoals effen, horizontale strepen, verticale strepen en meer. Bekijk de[Aspose-documentatie](https://reference.aspose.com/words/net/) voor een volledige lijst.

### Hoe kan ik de randkleur veranderen?  
 U kunt de randkleur instellen met behulp van de`Color` eigenschap voor elke grens. Bijvoorbeeld,`borders[BorderType.Left].Color = Color.Red;`.

### Is het mogelijk om randen en schaduw toe te passen op een specifiek deel van de tekst?  
 Ja, u kunt randen en schaduwen toepassen op specifieke tekstgedeelten met behulp van de`Run` object binnen de`DocumentBuilder`.

### Kan ik dit proces automatiseren voor meerdere alinea's?  
Zeker! Je kunt door je alinea's heen lussen en dezelfde randen en schaduwinstellingen programmatisch toepassen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
