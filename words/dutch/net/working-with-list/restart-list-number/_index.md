---
"description": "Leer hoe u lijstnummers in Word-documenten opnieuw kunt starten met Aspose.Words voor .NET. Deze gedetailleerde handleiding van 2000 woorden behandelt alles wat u moet weten, van installatie tot geavanceerde aanpassingen."
"linktitle": "Herstart lijstnummer"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Herstart lijstnummer"
"url": "/nl/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Herstart lijstnummer

## Invoering

Wil je de kunst van lijstmanipulatie in je Word-documenten onder de knie krijgen met Aspose.Words voor .NET? Dan ben je hier aan het juiste adres! In deze tutorial duiken we diep in het opnieuw starten van lijstnummers, een handige functie die je vaardigheden in documentautomatisering naar een hoger niveau tilt. Maak je klaar en laten we beginnen!

## Vereisten

Voordat we in de code duiken, controleren we of je alles hebt wat je nodig hebt:

1. Aspose.Words voor .NET: Je moet Aspose.Words voor .NET geïnstalleerd hebben. Als je het nog niet hebt geïnstalleerd, kun je het nu installeren. [download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Zorg dat u een geschikte ontwikkelomgeving hebt, zoals Visual Studio.
3. Basiskennis van C#: Met een basiskennis van C# kunt u de tutorial beter volgen.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Deze zijn cruciaal voor toegang tot de Aspose.Words-functies.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Laten we het proces nu opsplitsen in eenvoudig te volgen stappen. We behandelen alles, van het maken van een lijst tot het opnieuw nummeren ervan.

## Stap 1: Stel uw document en builder in

Voordat je met lijsten kunt beginnen, heb je een document en een DocumentBuilder nodig. De DocumentBuilder is dé tool om inhoud aan je document toe te voegen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Maak en pas uw eerste lijst aan

Vervolgens maken we een lijst op basis van een sjabloon en passen we de weergave ervan aan. In dit voorbeeld gebruiken we de Arabische getalnotatie met haakjes.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Hier hebben we de kleur van het lettertype op rood ingesteld en de tekst rechts uitgelijnd.

## Stap 3: Voeg items toe aan uw eerste lijst

Nu je lijst klaar is, is het tijd om wat items toe te voegen. De DocumentBuilder `ListFormat.List` eigenschap helpt bij het toepassen van de lijstopmaak op de tekst.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Stap 4: Lijstnummering opnieuw starten

Om de lijst opnieuw te gebruiken en de nummering opnieuw te starten, moet u een kopie van de originele lijst maken. Zo kunt u de nieuwe lijst zelfstandig wijzigen.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

In dit voorbeeld begint de nieuwe lijst bij nummer 10.

## Stap 5: Items toevoegen aan de nieuwe lijst

Voeg net als voorheen items toe aan je nieuwe lijst. Dit laat zien dat de lijst opnieuw begint bij het opgegeven nummer.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Stap 6: Sla uw document op

Sla ten slotte uw document op in de door u opgegeven directory.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusie

Het opnieuw beginnen van lijstnummers in Word-documenten met Aspose.Words voor .NET is eenvoudig en ongelooflijk handig. Of u nu rapporten genereert, gestructureerde documenten maakt of gewoon meer controle over uw lijsten nodig hebt, deze techniek biedt u de oplossing.

## Veelgestelde vragen

### Kan ik andere lijstsjablonen gebruiken naast NumberArabicParenthesis?

Absoluut! Aspose.Words biedt verschillende lijstsjablonen, zoals opsommingstekens, letters, Romeinse cijfers en meer. U kunt de sjabloon kiezen die het beste bij u past.

### Hoe verander ik het lijstniveau?

U kunt het lijstniveau wijzigen door de `ListLevels` eigendom. Bijvoorbeeld, `list1.ListLevels[1]` zou verwijzen naar het tweede niveau van de lijst.

### Kan ik de nummering bij elk nummer opnieuw starten?

Ja, u kunt het startnummer instellen op een willekeurig geheel getal met behulp van de `StartAt` Eigenschap van het lijstniveau.

### Is het mogelijk om verschillende opmaak te gebruiken voor verschillende lijstniveaus?

Inderdaad! Elk lijstniveau kan zijn eigen opmaakinstellingen hebben, zoals lettertype, uitlijning en nummering.

### Wat als ik wil doorgaan met de nummering van een eerdere lijst in plaats van opnieuw te beginnen?

Als u wilt doorgaan met nummeren, hoeft u geen kopie van de lijst te maken. U kunt gewoon items aan de oorspronkelijke lijst blijven toevoegen.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}