---
"description": "Leer met deze handleiding hoe u bidirectionele (Bidi) markeringen toevoegt aan Word-documenten met Aspose.Words voor .NET. Zorg voor de juiste tekstrichting voor meertalige content."
"linktitle": "Bidi-markeringen toevoegen aan een Word-document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Bidi-markeringen toevoegen aan een Word-document"
"url": "/nl/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bidi-markeringen toevoegen aan een Word-document

## Invoering

In de wereld van documentverwerking kan bidirectionele (Bidi) tekst vaak lastig te beheren zijn. Dit geldt met name voor talen met verschillende tekstrichtingen, zoals Arabisch of Hebreeuws. Gelukkig maakt Aspose.Words voor .NET het gemakkelijk om met dergelijke situaties om te gaan. In deze tutorial laten we zien hoe je Bidi-markeringen aan een Word-document toevoegt met Aspose.Words voor .NET.

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat u het volgende heeft:

1. Aspose.Words voor .NET: Je moet Aspose.Words voor .NET geïnstalleerd hebben. Je kunt het downloaden van de [Aspose Downloads-pagina](https://releases.aspose.com/words/net/).
2. .NET Framework of .NET Core: Zorg ervoor dat u een compatibele .NET-omgeving hebt ingesteld om de voorbeelden uit te voeren.
3. Basiskennis van C#: Kennis van de programmeertaal C# en basisbewerkingen in .NET.

## Naamruimten importeren

Om te beginnen moet je de benodigde naamruimten importeren. Zo kun je ze in je project opnemen:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Laten we het proces van het toevoegen van Bidi-markeringen aan een Word-document in duidelijke stappen uitleggen. Elke stap leidt je door de code en het doel ervan.

## Stap 1: Stel uw document in

Begin met het maken van een nieuw exemplaar van de `Document` klasse en een `DocumentBuilder` om inhoud aan het document toe te voegen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Maak het document en voeg inhoud toe
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In deze stap initialiseert u een nieuw Word-document en stelt u een `DocumentBuilder` om het invoegen van inhoud te vergemakkelijken.

## Stap 2: Inhoud toevoegen aan uw document

Voeg vervolgens wat tekst toe aan je document. Hier voegen we tekst in verschillende talen toe om de Bidi-tekstverwerking te illustreren.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Hier voegen we eerst een standaard Engelse zin toe. Vervolgens activeren we Bidi-tekstopmaak voor de daaropvolgende tekst, die in het Hebreeuws en Arabisch is geschreven. Dit laat zien hoe je bidirectionele tekst kunt gebruiken.

## Stap 3: Configureer opslagopties voor Bidi-markeringen

Om ervoor te zorgen dat de Bidi-markeringen correct in het document worden opgeslagen, moet u de volgende instellingen configureren: `TxtSaveOptions` en schakel de `AddBidiMarks` optie.

```csharp
// Bidi-markeringen toevoegen
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

In deze stap maken we een exemplaar van `TxtSaveOptions` en stel de `AddBidiMarks` eigendom van `true`Hiermee wordt ervoor gezorgd dat de Bidi-markeringen worden meegenomen wanneer het document als tekstbestand wordt opgeslagen.

## Conclusie

Het toevoegen van Bidi-markeringen aan uw Word-documenten kan een cruciale stap zijn bij het werken met meertalige content met talen met verschillende tekstrichtingen. Met Aspose.Words voor .NET is dit proces eenvoudig en efficiënt. Door de bovenstaande stappen te volgen, kunt u ervoor zorgen dat uw documenten Bidi-tekst correct weergeven, wat de leesbaarheid en nauwkeurigheid verbetert.

## Veelgestelde vragen

### Wat zijn Bidi-merken en waarom zijn ze belangrijk?
Bidi-tekens zijn speciale tekens die worden gebruikt om de tekstrichting in documenten te bepalen. Ze zijn essentieel voor de correcte weergave van talen die van rechts naar links worden gelezen, zoals Arabisch en Hebreeuws.

### Kan ik Aspose.Words voor .NET gebruiken om andere soorten problemen met tekstrichting op te lossen?
Ja, Aspose.Words voor .NET biedt uitgebreide ondersteuning voor verschillende tekstrichtingen en opmaakbehoeften, inclusief talen die van rechts naar links en van links naar rechts worden geschreven.

### Is het mogelijk om Bidi-opmaak alleen op specifieke delen van een document toe te passen?
Ja, u kunt indien nodig Bidi-opmaak toepassen op specifieke alinea's of secties van uw document.

### In welke formaten kan ik het document met Bidi-markeringen opslaan?
In het voorbeeld wordt het document opgeslagen als tekstbestand. Aspose.Words ondersteunt echter ook het opslaan van documenten in verschillende formaten, met behoud van Bidi-markeringen.

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?
U kunt meer ontdekken over Aspose.Words voor .NET via de [Aspose-documentatie](https://reference.aspose.com/words/net/) en toegang krijgen tot de [Ondersteuningsforum](https://forum.aspose.com/c/words/8) voor extra hulp.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}