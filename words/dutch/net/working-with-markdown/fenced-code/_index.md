---
title: Omheinde code
linktitle: Omheinde code
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u omheinde code en infostrings toevoegt aan Word-documenten met Aspose.Words voor .NET. Inclusief stapsgewijze handleiding. Verbeter uw vaardigheden in het opmaken van documenten.
weight: 10
url: /nl/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Omheinde code

## Invoering

Hallo, mede-programmeur! Vandaag duiken we in de wereld van Aspose.Words voor .NET om de kunst van het toevoegen van fenced code en fenced code met info strings aan uw Word-documenten onder de knie te krijgen. Stel u uw Word-document voor als een canvas en u, de kunstenaar, staat op het punt om te schilderen met de precisie van een doorgewinterde ontwikkelaar. Met Aspose.Words krijgt u de kracht om uw documenten programmatisch te verbeteren met gestructureerde, geformatteerde codeblokken, waardoor uw technische documenten schitteren met professionaliteit en helderheid.

## Vereisten

Voordat we met de tutorial beginnen, willen we ervoor zorgen dat je alles hebt wat je nodig hebt:

- Basiskennis van C#: Een algemene kennis van C# helpt u de concepten snel te begrijpen.
-  Aspose.Words voor .NET: U moet Aspose.Words voor .NET geïnstalleerd hebben. Als u het nog niet hebt, download het dan[hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere C# IDE waar u vertrouwd mee bent.

## Naamruimten importeren

Allereerst moet u de benodigde namespaces importeren. Dit is alsof u al uw tools verzamelt voordat u een project start.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Laten we het proces nu stap voor stap uitleggen.

## Stap 1: Uw project instellen

Voordat we mooie, opgemaakte codeblokken in ons Word-document kunnen maken, moeten we een nieuw project in Visual Studio instellen.

1. Een nieuw project maken: open Visual Studio en maak een nieuwe C# Console-toepassing.
2. Voeg Aspose.Words toe Referentie: Installeer Aspose.Words via NuGet Package Manager. U kunt dit doen door met de rechtermuisknop op uw project in Solution Explorer te klikken, "Manage NuGet Packages" te selecteren en te zoeken naar Aspose.Words.

## Stap 2: Initialiseer de DocumentBuilder

Nu uw project is ingesteld, kunnen we de DocumentBuilder initialiseren. Dit is het belangrijkste hulpmiddel voor het toevoegen van inhoud aan het Word-document.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Stap 3: Creëer een stijl voor Fenced Code

Om afgeschermde code toe te voegen, moeten we eerst een stijl maken. Zie dit als het instellen van het thema voor ons codeblok.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Stap 4: Voeg omheinde code toe aan het document

Nu de stijl gereed is, kunnen we een omheind codeblok aan het document toevoegen.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Stap 5: Maak een stijl voor Fenced Code met infostring

Soms wilt u misschien de programmeertaal specificeren of extra informatie toevoegen aan uw codeblok. Laten we daar een stijl voor maken.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Stap 6: Voeg omheinde code met infostring toe aan het document

Laten we nu een omheind codeblok toevoegen met een infostring om aan te geven dat het C#-code is.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Conclusie

Gefeliciteerd! U hebt zojuist afgeschermde codeblokken en afgeschermde code met infostrings toegevoegd aan uw Word-documenten met Aspose.Words voor .NET. Dit is slechts het topje van de ijsberg. Met Aspose.Words kunt u uw documentverwerking automatiseren en verbeteren tot nieuwe hoogten. Blijf ontdekken en veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, bewerken en converteren.

### Kan ik Aspose.Words gebruiken met andere programmeertalen?
Aspose.Words ondersteunt voornamelijk .NET-talen, maar er zijn versies beschikbaar voor Java, Python en andere talen.

### Is Aspose.Words gratis te gebruiken?
 Aspose.Words is een commercieel product, maar u kunt een gratis proefversie downloaden[hier](https://releases.aspose.com/)om de kenmerken ervan te verkennen.

### Hoe kan ik ondersteuning krijgen voor Aspose.Words?
 U kunt ondersteuning krijgen van de Aspose-community en ontwikkelaars[hier](https://forum.aspose.com/c/words/8).

### Welke andere functies biedt Aspose.Words?
Aspose.Words biedt een breed scala aan functies, waaronder documentconversie, sjabloongebaseerde documentgeneratie, rapportage en nog veel meer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
