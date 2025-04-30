---
"description": "Leer hoe u een Word-document ondertekent met Aspose.Words voor .NET met deze stapsgewijze handleiding. Beveilig uw documenten eenvoudig."
"linktitle": "Onderteken Word-document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Onderteken Word-document"
"url": "/nl/net/programming-with-digital-signatures/sign-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Onderteken Word-document

## Invoering

In de digitale wereld van vandaag is het beveiligen van uw documenten belangrijker dan ooit. Digitale handtekeningen bieden een manier om de authenticiteit en integriteit van uw documenten te garanderen. Wilt u een Word-document programmatisch ondertekenen met Aspose.Words voor .NET? Dan bent u hier aan het juiste adres. Deze handleiding leidt u stap voor stap door het hele proces, op een eenvoudige en boeiende manier.

## Vereisten

Voordat u de code induikt, moet u een aantal zaken regelen:

1. Aspose.Words voor .NET: Zorg ervoor dat u de nieuwste versie van Aspose.Words voor .NET hebt geïnstalleerd. U kunt deze downloaden. [hier](https://releases.aspose.com/words/net/).
2. .NET-omgeving: Zorg ervoor dat u een .NET-ontwikkelomgeving hebt ingesteld (bijvoorbeeld Visual Studio).
3. Digitaal certificaat: verkrijg een digitaal certificaat (bijvoorbeeld een .pfx-bestand) voor het ondertekenen van documenten.
4. Te ondertekenen document: Zorg dat u een Word-document bij de hand hebt dat u wilt ondertekenen.

## Naamruimten importeren

Allereerst moet u de benodigde naamruimten importeren. Voeg de volgende using-richtlijnen toe aan uw project:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Security.Cryptography.X509Certificates;
```

Laten we het proces nu opdelen in beheersbare stappen.

## Stap 1: Het digitale certificaat laden

De eerste stap is het laden van het digitale certificaat uit het bestand. Dit certificaat wordt gebruikt om het document te ondertekenen.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Laad het digitale certificaat.
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

### Uitleg

- `dataDir`:Dit is de map waar uw certificaat en documenten worden opgeslagen.
- `CertificateHolder.Create`: Deze methode laadt het certificaat vanaf het opgegeven pad. Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw directory, en `"morzal.pfx"` met de naam van uw certificaatbestand. De `"aw"` is het wachtwoord voor het certificaat.

## Stap 2: Laad het Word-document

Laad vervolgens het Word-document dat u wilt ondertekenen.

```csharp
// Laad het te ondertekenen document.
Document doc = new Document(dataDir + "Digitally signed.docx");
```

### Uitleg

- `Document`Deze klasse vertegenwoordigt het Word-document. Vervangen `"Digitally signed.docx"` met de naam van uw document.

## Stap 3: Onderteken het document

Gebruik nu de `DigitalSignatureUtil.Sign` Methode om het document te ondertekenen.

```csharp
// Onderteken het document.
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx", dataDir + "Document.Signed.docx", certHolder);
```

### Uitleg

- `DigitalSignatureUtil.Sign`: Deze methode ondertekent het document met behulp van het geladen certificaat. De eerste parameter is het pad naar het originele document, de tweede is het pad naar het ondertekende document en de derde is de certificaathouder.

## Stap 4: Sla het ondertekende document op

Sla ten slotte het ondertekende document op de opgegeven locatie op.

```csharp
// Sla het ondertekende document op.
doc.Save(dataDir + "Document.Signed.docx");
```

### Uitleg

- `doc.Save`: Deze methode slaat het ondertekende document op. Vervangen `"Document.Signed.docx"` met de gewenste naam van uw ondertekende document.

## Conclusie

En voilà! Je hebt met succes een Word-document ondertekend met Aspose.Words voor .NET. Door deze eenvoudige stappen te volgen, kun je ervoor zorgen dat je documenten veilig worden ondertekend en geverifieerd. Vergeet niet dat digitale handtekeningen een krachtig hulpmiddel zijn om de integriteit van je documenten te beschermen, dus maak er gebruik van wanneer nodig.

## Veelgestelde vragen

### Wat is een digitale handtekening?
Een digitale handtekening is een elektronische vorm van een handtekening waarmee de identiteit van de ondertekenaar kan worden geverifieerd en kan worden gecontroleerd of het document niet is gewijzigd.

### Waarom heb ik een digitaal certificaat nodig?
Een digitaal certificaat is nodig om een digitale handtekening te creëren. Het bevat een publieke sleutel en de identiteit van de certificaathouder, waarmee de handtekening kan worden geverifieerd.

### Kan ik elk .pfx-bestand gebruiken voor ondertekening?
Ja, zolang het .pfx-bestand een geldig digitaal certificaat bevat en u over het wachtwoord beschikt om er toegang toe te krijgen.

### Is Aspose.Words voor .NET gratis te gebruiken?
Aspose.Words voor .NET is een commerciële bibliotheek. U kunt een gratis proefversie downloaden. [hier](https://releases.aspose.com/), maar u moet een licentie aanschaffen voor volledige functionaliteit. U kunt het kopen [hier](https://purchase.aspose.com/buy).

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?
U kunt uitgebreide documentatie vinden [hier](https://reference.aspose.com/words/net/) en ondersteuning [hier](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}