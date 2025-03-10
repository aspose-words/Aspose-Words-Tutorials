---
title: Verplaatsen naar kopteksten en voetteksten in Word-document
linktitle: Verplaatsen naar kopteksten en voetteksten in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u naar headers en footers in een Word-document gaat met Aspose.Words voor .NET met onze stapsgewijze handleiding. Verbeter uw vaardigheden in het maken van documenten.
weight: 10
url: /nl/net/add-content-using-documentbuilder/move-to-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verplaatsen naar kopteksten en voetteksten in Word-document

## Invoering

Als het gaat om het programmatisch maken en beheren van Word-documenten, is Aspose.Words voor .NET een krachtige tool die u veel tijd en moeite kan besparen. In dit artikel onderzoeken we hoe u naar kopteksten en voetteksten in een Word-document kunt gaan met Aspose.Words voor .NET. Deze functie is essentieel wanneer u specifieke inhoud aan de koptekst- of voettekstsecties van uw document moet toevoegen. Of u nu een rapport, een factuur of een ander document maakt dat een professionele aanpak vereist, het is cruciaal om te weten hoe u kopteksten en voetteksten kunt manipuleren.

## Vereisten

Voordat we in de code duiken, controleren we of alles is ingesteld:

1. **Aspose.Words for .NET** : Zorg ervoor dat u de Aspose.Words voor .NET-bibliotheek hebt. U kunt deze downloaden van de[Aspose releases pagina](https://releases.aspose.com/words/net/).
2. **Development Environment**U hebt een ontwikkelomgeving nodig, zoals Visual Studio.
3. **Basic Knowledge of C#**:Als u de basisbeginselen van C#-programmering begrijpt, kunt u de cursus beter volgen.

## Naamruimten importeren

Om te beginnen moet u de benodigde naamruimten importeren. Deze stap is cruciaal voor toegang tot de klassen en methoden die worden geleverd door Aspose.Words voor .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System;
```

Laten we het proces opsplitsen in simpele stappen. Elke stap wordt duidelijk uitgelegd om u te helpen begrijpen wat de code doet en waarom.

## Stap 1: Initialiseer het document

De eerste stap is het initialiseren van een nieuw document en een DocumentBuilder-object. Met de DocumentBuilder-klasse kunt u het document construeren en manipuleren.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In deze stap maakt u een nieuw exemplaar van de`Document` klasse en de`DocumentBuilder` klasse. De`dataDir` variabele wordt gebruikt om de map op te geven waar u het document wilt opslaan.

## Stap 2: Pagina-instelling configureren

Vervolgens moeten we opgeven dat de kop- en voetteksten voor de eerste, even en oneven pagina's verschillend moeten zijn.

```csharp
//Geef aan dat u wilt dat kop- en voetteksten voor de eerste, even en oneven pagina's verschillend zijn.
builder.PageSetup.DifferentFirstPageHeaderFooter = true;
builder.PageSetup.OddAndEvenPagesHeaderFooter = true;
```

Met deze instellingen kunt u unieke kop- en voetteksten voor verschillende soorten pagina's maken.

## Stap 3: Ga naar de koptekst/voettekst en voeg inhoud toe

Laten we nu naar de kop- en voettekstsecties gaan en wat inhoud toevoegen.

```csharp
// Maak de headers.
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.Write("Header for the first page");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderEven);
builder.Write("Header for even pages");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);
builder.Write("Header for all other pages");
```

 In deze stap gebruiken we de`MoveToHeaderFooter` methode om naar de gewenste header- of footersectie te navigeren. De`Write` Vervolgens wordt de methode gebruikt om tekst aan deze secties toe te voegen.

## Stap 4: Inhoud toevoegen aan de documentbody

Om de kop- en voetteksten te demonstreren, voegen we wat inhoud toe aan de hoofdtekst van het document en maken we een aantal pagina's.

```csharp
// Maak twee pagina's in het document.
builder.MoveToSection(0);
builder.Writeln("Page1");
builder.InsertBreak(BreakType.PageBreak);
builder.Writeln("Page2");
```

Hier voegen we tekst toe aan het document en voegen we een pagina-einde in om een tweede pagina te maken.

## Stap 5: Sla het document op

Sla het document ten slotte op in de opgegeven map.

```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx");
```

Met deze regel code wordt het document opgeslagen met de naam 'AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx' in de opgegeven map.

## Conclusie

 Door deze stappen te volgen, kunt u eenvoudig headers en footers in een Word-document bewerken met Aspose.Words voor .NET. Deze tutorial behandelde de basis, maar Aspose.Words biedt een breed scala aan functionaliteiten voor complexere documentmanipulaties. Aarzel niet om de[documentatie](https://reference.aspose.com/words/net/) voor meer geavanceerde functies.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, wijzigen en converteren met behulp van C#.

### Kan ik afbeeldingen toevoegen aan kop- en voetteksten?
 Ja, u kunt afbeeldingen toevoegen aan kop- en voetteksten met behulp van de`DocumentBuilder.InsertImage` methode.

### Is het mogelijk om voor elke sectie een andere kop- en voettekst te gebruiken?
 Absoluut! U kunt unieke headers en footers voor elke sectie hebben door verschillende`HeaderFooterType` voor elke sectie.

### Hoe maak ik complexere lay-outs in kop- en voetteksten?
kunt tabellen, afbeeldingen en diverse opmaakopties van Aspose.Words gebruiken om complexe lay-outs te maken.

### Waar kan ik meer voorbeelden en tutorials vinden?
 Bekijk de[documentatie](https://reference.aspose.com/words/net/) en de[ondersteuningsforum](https://forum.aspose.com/c/words/8) voor meer voorbeelden en ondersteuning van de community.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
