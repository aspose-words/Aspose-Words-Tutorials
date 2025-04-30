---
"description": "Leer hoe u een tekstwatermerk met specifieke opties toevoegt aan uw Word-documenten met Aspose.Words voor .NET. Pas eenvoudig het lettertype, de grootte, de kleur en de lay-out aan."
"linktitle": "Voeg tekstwatermerk toe met specifieke opties"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Voeg tekstwatermerk toe met specifieke opties"
"url": "/nl/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg tekstwatermerk toe met specifieke opties

## Invoering

Watermerken kunnen een stijlvolle en functionele toevoeging zijn aan je Word-documenten, van het markeren van documenten als vertrouwelijk tot het toevoegen van een persoonlijk tintje. In deze tutorial laten we zien hoe je een tekstwatermerk toevoegt aan een Word-document met Aspose.Words voor .NET. We gaan dieper in op de specifieke opties die je kunt configureren, zoals lettertype, lettergrootte, kleur en lay-out. Aan het einde kun je het watermerk van je document aanpassen aan je exacte behoeften. Dus pak je code-editor en laten we aan de slag gaan!

## Vereisten

Voordat we beginnen, zorg ervoor dat je het volgende hebt geregeld:

1. Aspose.Words voor .NET-bibliotheek: Je hebt de Aspose.Words-bibliotheek nodig. Als je dat nog niet hebt gedaan, kun je deze downloaden van de [Aspose.Words Downloadlink](https://releases.aspose.com/words/net/).
2. Basiskennis van C#: In deze tutorial gebruiken we C# als programmeertaal. Een basiskennis van de C#-syntaxis is nuttig.
3. .NET-ontwikkelomgeving: zorg ervoor dat u een ontwikkelomgeving hebt ingesteld (zoals Visual Studio) waarin u uw .NET-toepassingen kunt maken en uitvoeren.

## Naamruimten importeren

Om met Aspose.Words te kunnen werken, moet je de benodigde naamruimten in je project opnemen. Dit is wat je moet importeren:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Stap 1: Stel uw document in

Eerst moet je het document laden waarmee je wilt werken. Voor deze tutorial gebruiken we een voorbeelddocument genaamd `Document.docx`Zorg ervoor dat dit document in de door u opgegeven directory staat.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

In deze stap definieert u de map waarin uw document zich bevindt en laadt u het in een exemplaar van de `Document` klas.

## Stap 2: Watermerkopties configureren

Configureer vervolgens de opties voor je tekstwatermerk. Je kunt verschillende aspecten aanpassen, zoals lettertype, lettergrootte, kleur en lay-out. Laten we deze opties instellen.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Dit is wat elke optie doet:
- `FontFamily`: Hiermee geeft u het lettertype van de watermerktekst op.
- `FontSize`Hiermee stelt u de grootte van de watermerktekst in.
- `Color`: Definieert de kleur van de watermerktekst.
- `Layout`: Bepaalt de oriëntatie van het watermerk (horizontaal of diagonaal).
- `IsSemitrasparent`: Hiermee stelt u in of het watermerk semi-transparant is.

## Stap 3: Voeg de watermerktekst toe

Pas nu het watermerk toe op uw document met behulp van de eerder geconfigureerde opties. In deze stap stelt u de watermerktekst in op 'Test' en past u de door u gedefinieerde opties toe.

```csharp
doc.Watermark.SetText("Test", options);
```

Met deze regel code wordt het watermerk met de tekst 'Test' aan het document toegevoegd, waarbij de opgegeven opties worden toegepast.

## Stap 4: Sla het document op

Sla ten slotte het document op met het nieuwe watermerk. U kunt het opslaan onder een nieuwe naam om te voorkomen dat het originele document wordt overschreven.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Met dit codefragment wordt het gewijzigde document in dezelfde map opgeslagen, onder een nieuwe bestandsnaam.

## Conclusie

Het toevoegen van een tekstwatermerk aan uw Word-documenten met Aspose.Words voor .NET is een eenvoudig proces dat u kunt opsplitsen in overzichtelijke stappen. Door deze tutorial te volgen, hebt u geleerd hoe u verschillende watermerkopties kunt configureren, zoals lettertype, grootte, kleur, lay-out en transparantie. Met deze vaardigheden kunt u uw documenten nu aanpassen aan uw behoeften of essentiële informatie toevoegen, zoals vertrouwelijkheid of branding.

Als u vragen heeft of verdere hulp nodig heeft, kunt u gerust de [Aspose.Words-documentatie](https://reference.aspose.com/words/net/) of bezoek de [Aspose Ondersteuningsforum](https://forum.aspose.com/c/words/8) voor meer hulp.

## Veelgestelde vragen

### Kan ik verschillende lettertypen gebruiken voor het watermerk?

Ja, u kunt elk lettertype kiezen dat op uw systeem is geïnstalleerd door de `FontFamily` eigendom in de `TextWatermarkOptions`.

### Hoe verander ik de kleur van het watermerk?

U kunt de kleur van het watermerk wijzigen door de `Color` eigendom in de `TextWatermarkOptions` aan welke dan ook `System.Drawing.Color` waarde.

### Is het mogelijk om meerdere watermerken aan een document toe te voegen?

Aspose.Words ondersteunt het toevoegen van één watermerk tegelijk. Om meerdere watermerken toe te voegen, moet u ze achtereenvolgens maken en toepassen.

### Kan ik de positie van het watermerk aanpassen?

De `WatermarkLayout` De eigenschap bepaalt de oriëntatie, maar nauwkeurige positioneringsaanpassingen worden niet direct ondersteund. Mogelijk moet u andere technieken gebruiken voor een exacte plaatsing.

### Wat als ik een semi-transparant watermerk nodig heb?

Stel de `IsSemitrasparent` eigendom van `true` om uw watermerk semi-transparant te maken.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}