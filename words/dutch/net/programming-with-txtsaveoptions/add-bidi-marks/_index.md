---
title: Bidi-markeringen toevoegen aan Word-document
linktitle: Bidi-markeringen toevoegen aan Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u bidirectionele (Bidi) markeringen toevoegt in Word-documenten met Aspose.Words voor .NET met deze gids. Zorg voor de juiste tekstrichting voor meertalige content.
weight: 10
url: /nl/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bidi-markeringen toevoegen aan Word-document

## Invoering

In de wereld van documentverwerking kan bidirectionele (Bidi) tekst vaak lastig te beheren zijn. Dit geldt met name voor talen met verschillende tekstrichtingen, zoals Arabisch of Hebreeuws. Gelukkig maakt Aspose.Words voor .NET het gemakkelijk om dergelijke scenario's te verwerken. In deze tutorial laten we zien hoe u Bidi-markeringen toevoegt aan een Word-document met behulp van Aspose.Words voor .NET.

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat u het volgende heeft:

1. Aspose.Words voor .NET: U moet Aspose.Words voor .NET geïnstalleerd hebben. U kunt het downloaden van de[Aspose Downloads-pagina](https://releases.aspose.com/words/net/).
2. .NET Framework of .NET Core: Zorg ervoor dat u een compatibele .NET-omgeving hebt ingesteld om de voorbeelden uit te voeren.
3. Basiskennis van C#: Kennis van de programmeertaal C# en basisbewerkingen in .NET.

## Naamruimten importeren

Om te beginnen moet u de benodigde namespaces importeren. Zo kunt u ze in uw project opnemen:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Laten we het proces van het toevoegen van Bidi-markeringen in een Word-document opsplitsen in duidelijke stappen. Elke stap leidt u door de code en het doel ervan.

## Stap 1: Stel uw document in

 Begin met het maken van een nieuw exemplaar van de`Document` klasse en een`DocumentBuilder` om inhoud aan het document toe te voegen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Maak het document en voeg inhoud toe
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In deze stap initialiseert u een nieuw Word-document en stelt u een`DocumentBuilder` om het invoegen van inhoud te vergemakkelijken.

## Stap 2: Voeg inhoud toe aan uw document

Voeg vervolgens wat tekst toe aan uw document. Hier voegen we tekst toe in verschillende talen om Bidi-tekstverwerking te illustreren.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Hier voegen we eerst een standaard Engelse zin toe. Vervolgens schakelen we Bidi-tekstopmaak in voor de daaropvolgende tekst, die in het Hebreeuws en Arabisch is geschreven. Dit laat zien hoe u bidirectionele tekst kunt opnemen.

## Stap 3: Configureer opslagopties voor Bidi-markeringen

 Om ervoor te zorgen dat de Bidi-markeringen correct in het document worden opgeslagen, moet u de volgende instellingen configureren:`TxtSaveOptions` en schakel de`AddBidiMarks` optie.

```csharp
// Bidi-markeringen toevoegen
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 In deze stap maken we een instantie van`TxtSaveOptions` en stel de`AddBidiMarks`eigendom van`true`Hiermee wordt ervoor gezorgd dat de Bidi-markeringen worden meegenomen wanneer het document als tekstbestand wordt opgeslagen.

## Conclusie

Het toevoegen van Bidi-markeringen aan uw Word-documenten kan een cruciale stap zijn bij het werken met meertalige content die talen met verschillende tekstrichtingen bevat. Met Aspose.Words voor .NET is dit proces eenvoudig en efficiënt. Door de hierboven beschreven stappen te volgen, kunt u ervoor zorgen dat uw documenten Bidi-tekst correct weergeven, wat de leesbaarheid en nauwkeurigheid verbetert.

## Veelgestelde vragen

### Wat zijn Bidi-merken en waarom zijn ze belangrijk?
Bidi-tekens zijn speciale tekens die worden gebruikt om de richting van tekst in documenten te bepalen. Ze zijn essentieel voor het correct weergeven van talen die van rechts naar links worden gelezen, zoals Arabisch en Hebreeuws.

### Kan ik Aspose.Words voor .NET gebruiken om andere soorten problemen met tekstrichting op te lossen?
Ja, Aspose.Words voor .NET biedt uitgebreide ondersteuning voor verschillende tekstrichtingen en opmaakbehoeften, inclusief talen die van rechts naar links en van links naar rechts worden geschreven.

### Is het mogelijk om Bidi-opmaak alleen op specifieke delen van een document toe te passen?
Ja, u kunt indien nodig Bidi-opmaak toepassen op specifieke paragrafen of secties van uw document.

### In welke formaten kan ik het document met Bidi-markeringen opslaan?
In het gegeven voorbeeld wordt het document opgeslagen als een tekstbestand. Aspose.Words ondersteunt echter ook het opslaan van documenten in verschillende formaten, waarbij Bidi-markeringen behouden blijven.

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?
 U kunt meer te weten komen over Aspose.Words voor .NET via de[Aspose-documentatie](https://reference.aspose.com/words/net/) en toegang krijgen tot de[Ondersteuningsforum](https://forum.aspose.com/c/words/8) voor extra hulp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
