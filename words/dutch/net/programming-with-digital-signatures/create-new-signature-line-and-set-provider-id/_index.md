---
"description": "Leer hoe u een nieuwe handtekeningregel maakt en de provider-ID instelt in Word-documenten met Aspose.Words voor .NET. Stapsgewijze handleiding."
"linktitle": "Nieuwe handtekeningregel maken en provider-ID instellen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Nieuwe handtekeningregel maken en provider-ID instellen"
"url": "/nl/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nieuwe handtekeningregel maken en provider-ID instellen

## Invoering

Hallo, technologiefanaten! Heb je je ooit afgevraagd hoe je programmatisch een handtekeningregel aan je Word-documenten kunt toevoegen? Vandaag duiken we erin met Aspose.Words voor .NET. Deze handleiding leidt je door elke stap, waardoor het een fluitje van een cent wordt om een nieuwe handtekeningregel te maken en de provider-ID in je Word-documenten in te stellen. Of je nu documentverwerking wilt automatiseren of gewoon je workflow wilt stroomlijnen, deze tutorial helpt je op weg.

## Vereisten

Voordat we aan de slag gaan, moeten we eerst controleren of we alles hebben wat we nodig hebben:

1. Aspose.Words voor .NET: Als je het nog niet hebt gedaan, download het dan [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere C#-ontwikkelomgeving.
3. .NET Framework: Zorg ervoor dat u .NET Framework hebt geïnstalleerd.
4. PFX-certificaat: Voor het ondertekenen van documenten hebt u een PFX-certificaat nodig. U kunt dit verkrijgen bij een vertrouwde certificeringsinstantie.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten in uw C#-project importeren:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Oké, laten we tot de kern van de zaak komen. Hier is een gedetailleerde beschrijving van elke stap voor het aanmaken van een nieuwe handtekeningregel en het instellen van de provider-ID.

## Stap 1: Een nieuw document maken

Om te beginnen moeten we een nieuw Word-document aanmaken. Dit wordt het canvas voor onze handtekening.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In dit fragment initialiseren we een nieuwe `Document` en een `DocumentBuilder`. De `DocumentBuilder` helpt ons elementen aan ons document toe te voegen.

## Stap 2: Definieer de opties voor de handtekeningregel

Vervolgens definiëren we de opties voor onze handtekeningregel. Dit omvat de naam, functie, e-mailadres en andere gegevens van de ondertekenaar.

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

Met deze opties personaliseert u de handtekeningregel, waardoor deze duidelijk en professioneel oogt.

## Stap 3: De handtekeningregel invoegen

Nu we onze opties hebben ingesteld, kunnen we de handtekeningregel in het document invoegen.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Hier, de `InsertSignatureLine` methode voegt de handtekeningregel toe en wij wijzen er een unieke provider-ID aan toe.

## Stap 4: Sla het document op

Nadat u de handtekeningregel hebt ingevoegd, slaat u het document op.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Hiermee wordt uw document opgeslagen met de nieuw toegevoegde handtekeningregel.

## Stap 5: Ondertekeningsopties instellen

Nu moeten we de opties voor het ondertekenen van het document instellen. Dit omvat de handtekeningregel-ID, provider-ID, opmerkingen en het tijdstip van ondertekening.

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

Om het document te ondertekenen, gebruiken we een PFX-certificaat. Laten we er een certificaathouder voor aanmaken.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Zorg ervoor dat u vervangt `"morzal.pfx"` met uw daadwerkelijke certificaatbestand en `"aw"` met uw certificaatwachtwoord.

## Stap 7: Onderteken het document

Ten slotte ondertekenen we het document met behulp van het hulpprogramma voor digitale handtekeningen.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Hiermee wordt het document ondertekend en opgeslagen als een nieuw bestand.

## Conclusie

En voilà! Je hebt met succes een nieuwe handtekeningregel aangemaakt en de provider-ID ingesteld in een Word-document met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het ongelooflijk eenvoudig om documentverwerkingstaken te beheren en te automatiseren. Probeer het eens uit en ontdek hoe het je workflow kan stroomlijnen.

## Veelgestelde vragen

### Kan ik het uiterlijk van de handtekeningregel aanpassen?
Absoluut! Je kunt verschillende opties aanpassen in de `SignatureLineOptions` die bij uw behoeften passen.

### Wat als ik geen PFX-certificaat heb?
Je hebt er een nodig van een vertrouwde certificeringsinstantie. Het is essentieel voor het digitaal ondertekenen van documenten.

### Kan ik meerdere handtekeningregels aan een document toevoegen?
Ja, u kunt zoveel handtekeningregels toevoegen als nodig is door het invoegproces te herhalen met verschillende opties.

### Is Aspose.Words voor .NET compatibel met .NET Core?
Ja, Aspose.Words voor .NET ondersteunt .NET Core, waardoor het veelzijdig is voor verschillende ontwikkelomgevingen.

### Hoe veilig zijn digitale handtekeningen?
Digitale handtekeningen die met Aspose.Words zijn gemaakt, zijn zeer veilig, mits u een geldig en vertrouwd certificaat gebruikt.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}