---
title: Document invoegen met Builder
linktitle: Document invoegen met Builder
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u twee Word-documenten samenvoegt met Aspose.Words voor .NET. Stapsgewijze handleiding voor het invoegen van een document met DocumentBuilder en het behouden van opmaak.
weight: 10
url: /nl/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document invoegen met Builder

## Invoering

Dus, je hebt twee Word-documenten en je wilt ze samenvoegen tot één. Je denkt misschien: "Is er een eenvoudige manier om dit programmatisch te doen?" Absoluut! Vandaag ga ik je door het proces leiden van het invoegen van één document in een ander met behulp van de Aspose.Words voor .NET-bibliotheek. Deze methode is superhandig, vooral als je met grote documenten werkt of het proces wilt automatiseren. Laten we er meteen induiken!

## Vereisten

Voordat we beginnen, willen we er zeker van zijn dat u alles heeft wat u nodig hebt:

1.  Aspose.Words voor .NET: Als u dat nog niet hebt gedaan, kunt u het hier downloaden[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u Visual Studio of een andere geschikte IDE hebt geïnstalleerd.
3. Basiskennis van C#: Een beetje vertrouwdheid met C# is handig.

## Naamruimten importeren

Allereerst moet u de benodigde naamruimten importeren om toegang te krijgen tot de Aspose.Words-bibliotheekfunctionaliteiten. Dit is hoe u dat kunt doen:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nu we aan de voorwaarden hebben voldaan, gaan we het proces stap voor stap uitleggen.

## Stap 1: Uw documentenmap instellen

Voordat we beginnen met coderen, moet u het pad naar uw documentdirectory instellen. Dit is waar uw bron- en bestemmingsdocumenten worden opgeslagen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad waar uw documenten zich bevinden. Dit zal het programma helpen uw bestanden gemakkelijk te vinden.

## Stap 2: De bron- en doeldocumenten laden

Vervolgens moeten we de documenten laden waarmee we willen werken. In dit voorbeeld hebben we een brondocument en een bestemmingsdocument.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

 Hier gebruiken we de`Document` klasse uit de Aspose.Words-bibliotheek om onze documenten te laden. Zorg ervoor dat de bestandsnamen overeenkomen met die in uw directory.

## Stap 3: Een DocumentBuilder-object maken

 De`DocumentBuilder` class is een krachtige tool in de Aspose.Words-bibliotheek. Hiermee kunnen we door het document navigeren en het manipuleren.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

 In deze stap hebben we een`DocumentBuilder` object voor ons bestemmingsdocument. Dit zal ons helpen om inhoud in het document in te voegen.

## Stap 4: Naar het einde van het document gaan

We moeten de buildercursor naar het einde van het doeldocument verplaatsen voordat we het brondocument invoegen.

```csharp
builder.MoveToDocumentEnd();
```

Hiermee wordt ervoor gezorgd dat het brondocument aan het einde van het doeldocument wordt ingevoegd.

## Stap 5: Een pagina-einde invoegen

Om het overzichtelijk te houden, voegen we een pagina-einde toe voordat we het brondocument invoegen. Dit zal de inhoud van het brondocument op een nieuwe pagina starten.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Met een pagina-einde zorgt u ervoor dat de inhoud van het brondocument op een nieuwe pagina begint, waardoor het samengevoegde document er professioneel uitziet.

## Stap 6: Het brondocument invoegen

Nu komt het spannende gedeelte: het daadwerkelijke invoegen van het brondocument in het doeldocument.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

 Met behulp van de`InsertDocument` methode, kunnen we het volledige brondocument in het doeldocument invoegen. De`ImportFormatMode.KeepSourceFormatting` zorgt ervoor dat de opmaak van het brondocument behouden blijft.

## Stap 7: Het samengevoegde document opslaan

Laten we ten slotte het samengevoegde document opslaan. Dit zal de bron- en bestemmingsdocumenten in één bestand combineren.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Door het document op te slaan, voltooien we het proces van het samenvoegen van de twee documenten. Uw nieuwe document is nu klaar en opgeslagen in de opgegeven directory.

## Conclusie

En daar heb je het! Je hebt succesvol één document in een ander document ingevoegd met Aspose.Words voor .NET. Deze methode is niet alleen efficiënt, maar behoudt ook de opmaak van beide documenten, wat zorgt voor een naadloze samenvoeging. Of je nu aan een eenmalig project werkt of de documentverwerking wilt automatiseren, Aspose.Words voor .NET heeft alles wat je nodig hebt.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?  
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, bewerken, converteren en manipuleren.

### Kan ik de opmaak van het brondocument behouden?  
 Ja, door gebruik te maken van`ImportFormatMode.KeepSourceFormatting`, blijft de opmaak van het brondocument behouden wanneer het in het doeldocument wordt ingevoegd.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?  
 Ja, Aspose.Words voor .NET vereist een licentie voor volledige functionaliteit. U kunt een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) voor evaluatie.

### Kan ik dit proces automatiseren?  
Absoluut! De beschreven methode kan worden opgenomen in grotere applicaties om documentverwerkingstaken te automatiseren.

### Waar kan ik meer informatie en ondersteuning vinden?  
 Voor meer informatie kunt u de[documentatie](https://reference.aspose.com/words/net/) , of bezoek de[ondersteuningsforum](https://forum.aspose.com/c/words/8) voor hulp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
