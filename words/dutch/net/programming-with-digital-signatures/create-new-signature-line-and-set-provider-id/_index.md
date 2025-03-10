---
title: Nieuwe handtekeningregel maken en provider-ID instellen
linktitle: Nieuwe handtekeningregel maken en provider-ID instellen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een nieuwe handtekeningregel maakt en de provider-ID instelt in Word-documenten met Aspose.Words voor .NET. Stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nieuwe handtekeningregel maken en provider-ID instellen

## Invoering

Hallo, tech-enthousiastelingen! Heb je je ooit afgevraagd hoe je een handtekeningregel programmatisch kunt toevoegen aan je Word-documenten? Nou, vandaag duiken we erin met Aspose.Words voor .NET. Deze gids leidt je door elke stap, waardoor het heel eenvoudig wordt om een nieuwe handtekeningregel te maken en de provider-ID in te stellen in je Word-documenten. Of je nu documentverwerking automatiseert of gewoon je workflow wilt stroomlijnen, deze tutorial helpt je verder.

## Vereisten

Voordat we onze handen vuil maken, moeten we eerst controleren of we alles hebben wat we nodig hebben:

1.  Aspose.Words voor .NET: Als u het nog niet hebt gedaan, download het dan[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere C#-ontwikkelomgeving.
3. .NET Framework: Zorg ervoor dat u .NET Framework hebt geïnstalleerd.
4. PFX-certificaat: Voor het ondertekenen van documenten hebt u een PFX-certificaat nodig. U kunt er een krijgen van een vertrouwde certificeringsinstantie.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten in uw C#-project importeren:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Oké, laten we tot de kern van de zaak komen. Hier is een gedetailleerde uiteenzetting van elke stap om een nieuwe handtekeningregel te maken en de provider-ID in te stellen.

## Stap 1: Maak een nieuw document

Om te beginnen moeten we een nieuw Word-document maken. Dit wordt het canvas voor onze handtekeningregel.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In dit fragment initialiseren we een nieuwe`Document` en een`DocumentBuilder` . De`DocumentBuilder` helpt ons elementen aan ons document toe te voegen.

## Stap 2: Definieer de opties voor de handtekeningregel

Vervolgens definiëren we de opties voor onze handtekeningregel. Dit omvat de naam, titel, e-mail en andere details van de ondertekenaar.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Met deze opties personaliseert u de handtekeningregel, waardoor deze duidelijk en professioneel overkomt.

## Stap 3: Voeg de handtekeningregel in

Nu we de opties hebben ingesteld, kunnen we de handtekeningregel in het document invoegen.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Hier, de`InsertSignatureLine` De methode voegt de handtekeningregel toe en wij wijzen er een unieke provider-ID aan toe.

## Stap 4: Sla het document op

Nadat u de handtekeningregel hebt ingevoegd, slaat u het document op.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Hiermee wordt uw document opgeslagen met de nieuw toegevoegde handtekeningregel.

## Stap 5: Ondertekeningsopties instellen

Nu moeten we de opties voor het ondertekenen van het document instellen. Dit omvat de handtekeningregel-ID, provider-ID, opmerkingen en de ondertekeningstijd.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Met deze opties weet u zeker dat het document met de juiste gegevens wordt ondertekend.

## Stap 6: Certificaathouder aanmaken

Om het document te ondertekenen, gebruiken we een PFX-certificaat. Laten we er een certificaathouder voor maken.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Zorg ervoor dat u vervangt`"morzal.pfx"` met uw werkelijke certificaatbestand en`"aw"` met uw certificaatwachtwoord.

## Stap 7: Onderteken het document

Ten slotte ondertekenen we het document met behulp van het hulpprogramma voor digitale handtekeningen.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Hiermee wordt het document ondertekend en opgeslagen als een nieuw bestand.

## Conclusie

En daar heb je het! Je hebt met succes een nieuwe handtekeningregel gemaakt en de provider-ID ingesteld in een Word-document met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het ongelooflijk eenvoudig om documentverwerkingstaken te beheren en automatiseren. Probeer het eens uit en zie hoe het je workflow kan stroomlijnen.

## Veelgestelde vragen

### Kan ik het uiterlijk van de handtekeningregel aanpassen?
 Absoluut! Je kunt verschillende opties aanpassen in de`SignatureLineOptions`afgestemd op uw behoeften.

### Wat als ik geen PFX-certificaat heb?
U moet er een verkrijgen van een vertrouwde certificeringsinstantie. Het is essentieel voor het digitaal ondertekenen van documenten.

### Kan ik meerdere handtekeningregels aan een document toevoegen?
Ja, u kunt zoveel handtekeningregels toevoegen als nodig is door het invoegproces te herhalen met verschillende opties.

### Is Aspose.Words voor .NET compatibel met .NET Core?
Ja, Aspose.Words voor .NET ondersteunt .NET Core, waardoor het veelzijdig is voor verschillende ontwikkelomgevingen.

### Hoe veilig zijn digitale handtekeningen?
Digitale handtekeningen die met Aspose.Words zijn gemaakt, zijn uiterst veilig, mits u een geldig en vertrouwd certificaat gebruikt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
