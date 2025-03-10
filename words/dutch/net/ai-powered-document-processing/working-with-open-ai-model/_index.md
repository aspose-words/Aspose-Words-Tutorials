---
title: Werken met een open AI-model
linktitle: Werken met een open AI-model
second_title: Aspose.Words API voor documentverwerking
description: Ontgrendel efficiënte documentsamenvatting met Aspose.Words voor .NET met de krachtige modellen van OpenAI. Duik nu in deze uitgebreide gids.
weight: 10
url: /nl/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Werken met een open AI-model

## Invoering

In de digitale wereld van vandaag is content koning. Of u nu een student, een zakelijke professional of een fervent schrijver bent, het vermogen om documenten efficiënt te manipuleren, samen te vatten en te genereren is van onschatbare waarde. Dit is waar de Aspose.Words voor .NET-bibliotheek in het spel komt, waarmee u documenten als een professional kunt beheren. In deze uitgebreide tutorial duiken we in hoe u Aspose.Words in combinatie met OpenAI-modellen kunt gebruiken om documenten effectief samen te vatten. Klaar om uw potentieel voor documentbeheer te ontsluiten? Laten we beginnen!

## Vereisten

Voordat we de mouwen opstropen en in de code duiken, zijn er een paar essentiële zaken die je moet regelen:

### .NET-framework
Zorg ervoor dat u een versie van het .NET Framework gebruikt die compatibel is met Aspose.Words. Over het algemeen zou .NET 5.0 en hoger perfect moeten werken.

### Aspose.Words voor .NET-bibliotheek
 Je moet de Aspose.Words-bibliotheek downloaden en installeren. Je kunt het ophalen van[deze link](https://releases.aspose.com/words/net/).

### OpenAI API-sleutel
Om OpenAI's taalmodellen voor documentsamenvatting te integreren, hebt u een API-sleutel nodig. U kunt deze krijgen door u aan te melden op het OpenAI-platform en uw sleutel op te halen uit uw accountinstellingen.

### IDE voor ontwikkeling
Voor het ontwikkelen van .NET-toepassingen is het ideaal om een Integrated Development Environment (IDE) zoals Visual Studio in te stellen.

### Basiskennis programmeren
Een basiskennis van C# en objectgeoriënteerd programmeren helpt u de concepten gemakkelijker te begrijpen.

## Pakketten importeren

Nu we alles op een rijtje hebben, kunnen we onze pakketten importeren. Open je Visual Studio-project en voeg de benodigde bibliotheken toe. Zo doe je dat:

### Aspose.Words-pakket toevoegen

U kunt het Aspose.Words-pakket toevoegen via NuGet Package Manager. Dit is hoe u dat doet:
- Ga naar Extra -> NuGet Package Manager -> NuGet-pakketten beheren voor oplossing.
- Zoek naar "Aspose.Words" en klik op Installeren.

### Systeemomgeving toevoegen

 Zorg ervoor dat u de`System`naamruimte voor het verwerken van omgevingsvariabelen:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Voeg Aspose.Words toe

Neem vervolgens de Aspose.Words-naamruimte op in uw C#-bestand:
```csharp
using Aspose.Words;
```

### OpenAI-bibliotheek toevoegen

Als u een bibliotheek gebruikt om te interfacen met OpenAI (zoals een REST-client), zorg er dan voor dat u die ook opneemt. Mogelijk moet u deze toevoegen via NuGet, op dezelfde manier als wij Aspose.Words toevoegden.

Nu we onze omgeving hebben voorbereid en de benodigde pakketten hebben geïmporteerd, gaan we het proces voor het samenvatten van documenten stap voor stap doornemen.

## Stap 1: Definieer uw documentmappen

Voordat u met uw documenten kunt gaan experimenteren, moet u de mappen instellen waar uw documenten en artefacten worden opgeslagen:

```csharp
// Uw documentenmap
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Uw artefacten directory
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Dit maakt uw code beter beheersbaar, omdat u de paden indien nodig eenvoudig kunt wijzigen.`MyDir` is waar uw invoerdocumenten worden opgeslagen, terwijl`ArtifactsDir` is waar u gegenereerde samenvattingen opslaat.

## Stap 2: Laad uw documenten

Vervolgens laadt u de documenten die u wilt samenvatten. Dit is eenvoudig met Aspose.Woorden:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Zorg ervoor dat de namen van uw documenten overeenkomen met de namen die u wilt gebruiken. Anders ontstaan er fouten!

## Stap 3: Ontvang uw API-sleutel

Nu uw documenten zijn geladen, is het tijd om uw OpenAI API-sleutel op te halen. U haalt deze op uit omgevingsvariabelen om deze veilig te houden:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Het is essentieel om uw API-sleutel veilig te beheren om ongeautoriseerde gebruikers buiten de deur te houden.

## Stap 4: Maak een OpenAI-modelinstantie

Met uw API-sleutel bij de hand kunt u nu een instantie van het OpenAI-model maken. Voor het samenvatten van documenten gebruiken we het Gpt4OMini-model:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Met deze stap beschikt u over de denkkracht die nodig is om uw documenten samen te vatten, zodat u toegang krijgt tot AI-gestuurde samenvattingen.

## Stap 5: Vat een enkel document samen

Laten we eerst het eerste document samenvatten. Dit is waar de magie gebeurt:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Hier gebruiken we de`Summarize` methode van het model. De`SummaryLength.Short`parameter geeft aan dat we een korte samenvatting willen — perfect voor een snel overzicht!

## Stap 6: Meerdere documenten samenvatten

Ambitieus? Je kunt meerdere documenten tegelijk samenvatten. Kijk eens hoe makkelijk het is:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Deze functie is vooral handig voor het vergelijken van meerdere bestanden. Misschien bereidt u zich voor op een vergadering en hebt u bondige aantekeningen nodig van meerdere lange rapporten. Dit is uw nieuwe beste vriend!

## Conclusie

Documenten samenvatten met Aspose.Words voor .NET en OpenAI is niet alleen een nuttige vaardigheid; het is ook heel krachtig. Door deze gids te volgen, hebt u lange, ingewikkelde tekst omgezet in bondige samenvattingen, waarmee u tijd en moeite bespaart. Of u nu duidelijkheid voor klanten wilt creëren of u wilt voorbereiden op die belangrijke presentatie, u hebt nu de tools om het efficiënt te doen.

Waar wacht u nog op? Duik vol vertrouwen in uw documenten en laat de technologie het zware werk doen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?  
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch documenten kunnen maken, bewerken en converteren.

### Heb ik een API-sleutel nodig voor OpenAI?  
Ja, u moet over een geldige OpenAI API-sleutel beschikken om toegang te krijgen tot de samenvattingsmogelijkheden met behulp van hun modellen.

### Kan ik meerdere documenten tegelijk samenvatten?  
Absoluut! U kunt meerdere documenten samenvatten in één gesprek, wat ideaal is voor uitgebreide rapporten.

### Hoe installeer ik Aspose.Words?  
U kunt het installeren via NuGet Package Manager in Visual Studio door te zoeken naar 'Aspose.Words'.

### Is er een gratis proefversie voor Aspose.Words?  
 Ja, u kunt een gratis proefversie van Aspose.Words krijgen via hun[website](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
