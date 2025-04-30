---
"description": "Leer hoe je afgeschermde code en infostrings toevoegt aan Word-documenten met Aspose.Words voor .NET. Inclusief stapsgewijze handleiding. Verbeter je vaardigheden in documentopmaak."
"linktitle": "Omheinde code"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Omheinde code"
"url": "/nl/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Omheinde code

## Invoering

Hallo, mede-programmeur! Vandaag duiken we in de wereld van Aspose.Words voor .NET om de kunst van het toevoegen van afgeschermde code en afgeschermde code met infostrings aan je Word-documenten onder de knie te krijgen. Stel je je Word-document voor als een canvas, en jij, de kunstenaar, staat op het punt om te schilderen met de precisie van een ervaren ontwikkelaar. Met Aspose.Words krijg je de kracht om je documenten programmatisch te verbeteren met gestructureerde, geformatteerde codeblokken, waardoor je technische documenten schitteren met professionaliteit en helderheid.

## Vereisten

Voordat we met de tutorial beginnen, willen we ervoor zorgen dat je alles hebt wat je nodig hebt:

- Basiskennis van C#: Met een algemene kennis van C# kunt u de concepten snel begrijpen.
- Aspose.Words voor .NET: Je moet Aspose.Words voor .NET geïnstalleerd hebben. Als je het nog niet hebt, download het dan. [hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere C# IDE waar u vertrouwd mee bent.

## Naamruimten importeren

Allereerst moet je de benodigde naamruimten importeren. Dit is vergelijkbaar met het verzamelen van al je tools voordat je aan een project begint.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Laten we het proces nu stap voor stap uitleggen.

## Stap 1: Uw project instellen

Voordat we mooie, opgemaakte codeblokken in ons Word-document kunnen maken, moeten we een nieuw project in Visual Studio instellen.

1. Een nieuw project maken: open Visual Studio en maak een nieuwe C# Console-toepassing.
2. Aspose.Words toevoegen Referentie: Installeer Aspose.Words via NuGet Package Manager. U kunt dit doen door met de rechtermuisknop op uw project in Solution Explorer te klikken, 'NuGet-pakketten beheren' te selecteren en te zoeken naar Aspose.Words.

## Stap 2: Initialiseer de DocumentBuilder

Nu uw project is ingesteld, kunnen we de DocumentBuilder initialiseren. Dit is het belangrijkste hulpmiddel voor het toevoegen van inhoud aan het Word-document.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Stap 3: Een stijl voor Fenced Code creëren

Om afgeschermde code toe te voegen, moeten we eerst een stijl creëren. Zie dit als het instellen van het thema voor ons codeblok.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Stap 4: Voeg omheinde code toe aan het document

Nu de stijl klaar is, kunnen we een omheind codeblok aan het document toevoegen.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Stap 5: Maak een stijl voor Fenced Code met een infostring

Soms wil je misschien de programmeertaal specificeren of extra informatie aan je codeblok toevoegen. Laten we daar een stijl voor maken.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Stap 6: Voeg een omheinde code met een infostring toe aan het document

Laten we nu een omheind codeblok toevoegen met een infostring om aan te geven dat het C#-code is.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Conclusie

Gefeliciteerd! Je hebt zojuist afgeschermde codeblokken en afgeschermde code met infostrings toegevoegd aan je Word-documenten met Aspose.Words voor .NET. Dit is slechts het topje van de ijsberg. Met Aspose.Words kun je je documentverwerking automatiseren en naar een hoger niveau tillen. Blijf ontdekken en veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, bewerken en converteren.

### Kan ik Aspose.Words gebruiken met andere programmeertalen?
Aspose.Words ondersteunt voornamelijk .NET-talen, maar er zijn versies beschikbaar voor Java, Python en andere talen.

### Is Aspose.Words gratis te gebruiken?
Aspose.Words is een commercieel product, maar u kunt een gratis proefversie downloaden [hier](https://releases.aspose.com/) om de functies ervan te verkennen.

### Hoe kan ik ondersteuning krijgen voor Aspose.Words?
U kunt ondersteuning krijgen van de Aspose-community en ontwikkelaars [hier](https://forum.aspose.com/c/words/8).

### Welke andere functies biedt Aspose.Words?
Aspose.Words biedt een breed scala aan functies, waaronder documentconversie, op sjablonen gebaseerde documentgeneratie, rapportage en nog veel meer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}