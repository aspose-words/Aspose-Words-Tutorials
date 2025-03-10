---
title: Herstart lijstnummer
linktitle: Herstart lijstnummer
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u lijstnummers in Word-documenten opnieuw kunt starten met Aspose.Words voor .NET. Deze gedetailleerde gids van 2000 woorden behandelt alles wat u moet weten, van installatie tot geavanceerde aanpassing.
weight: 10
url: /nl/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Herstart lijstnummer

## Invoering

Wilt u de kunst van lijstmanipulatie in uw Word-documenten onder de knie krijgen met Aspose.Words voor .NET? Dan bent u hier aan het juiste adres! In deze tutorial duiken we diep in het opnieuw starten van lijstnummers, een handige functie die uw vaardigheden in documentautomatisering naar een hoger niveau tilt. Gespen vast en laten we beginnen!

## Vereisten

Voordat we met de code beginnen, controleren we eerst of je alles hebt wat je nodig hebt:

1.  Aspose.Words voor .NET: U moet Aspose.Words voor .NET geïnstalleerd hebben. Als u het nog niet hebt geïnstalleerd, kunt u[download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Zorg dat u over een geschikte ontwikkelomgeving beschikt, zoals Visual Studio.
3. Basiskennis van C#: Een basiskennis van C# helpt u de tutorial te volgen.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Deze zijn cruciaal voor toegang tot de Aspose.Words-functies.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Laten we het proces nu opsplitsen in gemakkelijk te volgen stappen. We behandelen alles van het maken van een lijst tot het opnieuw nummeren ervan.

## Stap 1: Stel uw document en builder in

Voordat u kunt beginnen met het bewerken van lijsten, hebt u een document en een DocumentBuilder nodig. De DocumentBuilder is uw go-to tool voor het toevoegen van content aan uw document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Maak en pas uw eerste lijst aan

Vervolgens maken we een lijst op basis van een sjabloon en passen we het uiterlijk ervan aan. In dit voorbeeld gebruiken we het Arabische getalformaat met haakjes.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Hier hebben we de kleur van het lettertype op rood ingesteld en de tekst rechts uitgelijnd.

## Stap 3: Voeg items toe aan uw eerste lijst

 Nu uw lijst gereed is, is het tijd om wat items toe te voegen. De DocumentBuilder's`ListFormat.List` eigenschap helpt bij het toepassen van de lijstopmaak op de tekst.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Stap 4: Herstart lijstnummering

Om de lijst opnieuw te gebruiken en de nummering opnieuw te starten, moet u een kopie van de originele lijst maken. Hiermee kunt u de nieuwe lijst onafhankelijk wijzigen.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

In dit voorbeeld begint de nieuwe lijst bij nummer 10.

## Stap 5: Items toevoegen aan de nieuwe lijst

Voeg net als voorheen items toe aan uw nieuwe lijst. Dit laat zien dat de lijst opnieuw start bij het opgegeven nummer.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Stap 6: Sla uw document op

Sla ten slotte uw document op in de door u opgegeven map.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusie

Het opnieuw starten van lijstnummers in Word-documenten met Aspose.Words voor .NET is eenvoudig en ongelooflijk handig. Of u nu rapporten genereert, gestructureerde documenten maakt of gewoon meer controle over uw lijsten nodig hebt, deze techniek is wat u zoekt.

## Veelgestelde vragen

### Kan ik andere lijstsjablonen gebruiken dan NumberArabicParenthesis?

Absoluut! Aspose.Words biedt verschillende lijstsjablonen, zoals opsommingstekens, letters, Romeinse cijfers en meer. U kunt degene kiezen die het beste bij uw behoeften past.

### Hoe verander ik het lijstniveau?

 U kunt het lijstniveau wijzigen door de`ListLevels` eigendom. Bijvoorbeeld,`list1.ListLevels[1]` zou verwijzen naar het tweede niveau van de lijst.

### Kan ik bij elk nummer opnieuw nummeren?

 Ja, u kunt het startnummer instellen op een willekeurig geheel getal met behulp van de`StartAt` Eigenschap van het lijstniveau.

### Is het mogelijk om verschillende opmaak te gebruiken voor verschillende lijstniveaus?

Inderdaad! Elk lijstniveau kan zijn eigen opmaakinstellingen hebben, zoals lettertype, uitlijning en nummeringsstijl.

### Wat als ik wil doorgaan met de nummering van een vorige lijst in plaats van opnieuw te beginnen?

Als u wilt doorgaan met nummeren, hoeft u geen kopie van de lijst te maken. Blijf gewoon items toevoegen aan de originele lijst.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
