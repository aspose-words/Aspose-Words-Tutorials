---
"description": "Leer hoe u een handtekeningregel in een Word-document maakt en digitaal ondertekent met Aspose.Words voor .NET met deze stapsgewijze tutorial. Perfect voor documentautomatisering."
"linktitle": "Een nieuwe handtekeningregel maken en ondertekenen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Een nieuwe handtekeningregel maken en ondertekenen"
"url": "/nl/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Een nieuwe handtekeningregel maken en ondertekenen

## Invoering

Hallo! Je hebt een Word-document en moet een handtekeningregel toevoegen en het vervolgens digitaal ondertekenen. Klinkt lastig? Helemaal niet! Dankzij Aspose.Words voor .NET kun je dit naadloos realiseren met slechts een paar regels code. In deze tutorial leiden we je door het hele proces, van het instellen van je omgeving tot het opslaan van je document met een glimmende nieuwe handtekening. Klaar? Laten we beginnen!

## Vereisten

Voordat we in de code duiken, controleren we of je alles hebt wat je nodig hebt:
1. Aspose.Words voor .NET - Je kunt [download het hier](https://releases.aspose.com/words/net/).
2. Een .NET-ontwikkelomgeving - Visual Studio wordt sterk aanbevolen.
3. Een document ondertekenen - Maak een eenvoudig Word-document of gebruik een bestaand document.
4. Een certificaatbestand - Dit is nodig voor digitale handtekeningen. U kunt een `.pfx` bestand.
5. Afbeeldingen voor handtekeningregel - Optioneel, een afbeeldingsbestand voor de handtekening.

## Naamruimten importeren

Eerst moeten we de benodigde naamruimten importeren. Deze stap is cruciaal omdat het de omgeving instelt voor het gebruik van Aspose.Words-functionaliteiten.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Stap 1: De documentenmap instellen

Elk project heeft een goede start nodig. Laten we het pad naar uw documentmap instellen. Dit is waar uw documenten worden opgeslagen en opgehaald.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Een nieuw document maken

Laten we nu een nieuw Word-document maken met Aspose.Words. Dit wordt ons canvas waar we de handtekeningregel toevoegen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: De handtekeningregel invoegen

Dit is waar de magie gebeurt. We voegen een handtekeningregel toe aan ons document met behulp van de `DocumentBuilder` klas.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Stap 4: Het document opslaan met de handtekeningregel

Zodra de handtekeningregel is geplaatst, moeten we het document opslaan. Dit is een tussenstap voordat we het ondertekenen.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Stap 5: Ondertekeningsopties instellen

Laten we nu de opties voor het ondertekenen van het document instellen. Dit omvat het specificeren van de handtekeningregel-ID en de te gebruiken afbeelding.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Stap 6: Het certificaat laden

Voor digitale handtekeningen is een certificaat vereist. Hier laden we het certificaatbestand dat gebruikt zal worden om het document te ondertekenen.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Stap 7: Het document ondertekenen

Dit is de laatste stap. We gebruiken de `DigitalSignatureUtil` klasse om het document te ondertekenen. Het ondertekende document wordt opgeslagen onder een nieuwe naam.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusie

En voilà! Met deze stappen heb je succesvol een nieuw Word-document gemaakt, een handtekeningregel toegevoegd en het digitaal ondertekend met Aspose.Words voor .NET. Het is een krachtige tool die documentautomatisering een fluitje van een cent maakt. Of je nu te maken hebt met contracten, overeenkomsten of andere formele documenten, deze methode zorgt ervoor dat ze veilig worden ondertekend en geverifieerd.

## Veelgestelde vragen

### Kan ik andere afbeeldingformaten gebruiken voor de handtekeningregel?
Ja, u kunt verschillende afbeeldingformaten gebruiken, zoals PNG, JPG, BMP, enz.

### Is het nodig om een `.pfx` bestand voor het certificaat?
Ja, een `.pfx` bestand is een veelgebruikt formaat voor het opslaan van cryptografische informatie, zoals certificaten en persoonlijke sleutels.

### Kan ik meerdere handtekeningregels in één document toevoegen?
Absoluut! U kunt meerdere handtekeningregels invoegen door de invoegstap voor elke handtekening te herhalen.

### Wat als ik geen digitaal certificaat heb?
moet een digitaal certificaat aanvragen bij een vertrouwde certificeringsinstantie of er zelf een genereren met behulp van hulpmiddelen als OpenSSL.

### Hoe verifieer ik de digitale handtekening in het document?
U kunt het ondertekende document openen in Word en naar de handtekeningdetails gaan om de authenticiteit en integriteit van de handtekening te verifiëren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}