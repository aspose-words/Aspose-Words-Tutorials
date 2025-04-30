---
"description": "Leer hoe u versleutelde Word-documenten ondertekent met Aspose.Words voor .NET met deze gedetailleerde, stapsgewijze handleiding. Perfect voor ontwikkelaars."
"linktitle": "Versleuteld Word-document ondertekenen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Versleuteld Word-document ondertekenen"
"url": "/nl/net/programming-with-digital-signatures/signing-encrypted-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Versleuteld Word-document ondertekenen

## Invoering

Heb je je ooit afgevraagd hoe je een versleuteld Word-document kunt ondertekenen? Vandaag leggen we je dit proces uit met behulp van Aspose.Words voor .NET. Maak je klaar voor een gedetailleerde, boeiende en leuke tutorial!

## Vereisten

Voordat we in de code duiken, controleren we of je alles hebt wat je nodig hebt:

1. Aspose.Words voor .NET: Downloaden en installeren vanaf [hier](https://releases.aspose.com/words/net/).
2. Visual Studio: Zorg ervoor dat u dit programma hebt geïnstalleerd.
3. Een geldig certificaat: u hebt een .pfx-certificaatbestand nodig.
4. Basiskennis van C#: Als u de basisbeginselen begrijpt, verloopt deze tutorial soepeler.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Deze zijn cruciaal voor toegang tot de Aspose.Words-functionaliteiten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

Laten we het proces nu opdelen in eenvoudige, beheersbare stappen.

## Stap 1: Uw project instellen

Allereerst moet u uw Visual Studio-project instellen. Open Visual Studio en maak een nieuwe C# Console Application. Geef deze een beschrijvende naam, zoals 'SignEncryptedWordDoc'.

## Stap 2: Aspose.Words toevoegen aan uw project

Vervolgens moeten we Aspose.Words aan je project toevoegen. Er zijn verschillende manieren om dit te doen, maar NuGet is het eenvoudigst. 

1. Open de NuGet Package Manager Console via Extra > NuGet Package Manager > Package Manager Console.
2. Voer de volgende opdracht uit:

```powershell
Install-Package Aspose.Words
```

## Stap 3: De documentenmap voorbereiden

Je hebt een map nodig om je Word-documenten en certificaten in op te slaan. Laten we er een aanmaken.

1. Maak een map aan op je computer. Voor het gemak noemen we deze "DocumentDirectory".
2. Plaats uw Word-document (bijv. "Document.docx") en uw .pfx-certificaat (bijv. "morzal.pfx") in deze map.

## Stap 4: De code schrijven

Laten we nu de code induiken. Open je `Program.cs` bestand en begin met het instellen van het pad naar uw documentmap en het initialiseren van de `SignOptions` met het decoderingswachtwoord.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## Stap 5: Het certificaat laden

Laad vervolgens uw certificaat met behulp van de `CertificateHolder` klasse. Hiervoor hebt u het pad naar uw .pfx-bestand en het wachtwoord van het certificaat nodig.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Stap 6: Het document ondertekenen

Gebruik ten slotte de `DigitalSignatureUtil.Sign` Methode om uw versleutelde Word-document te ondertekenen. Deze methode vereist het invoerbestand, het uitvoerbestand, de certificaathouder en de ondertekeningsopties.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## Stap 7: De code uitvoeren

Sla uw bestand op en voer het project uit. Als alles correct is ingesteld, ziet u uw ondertekende document in de opgegeven map.

## Conclusie

En voilà! Je hebt met succes een versleuteld Word-document ondertekend met Aspose.Words voor .NET. Met deze krachtige bibliotheek wordt digitaal ondertekenen een fluitje van een cent, zelfs voor versleutelde bestanden. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik een ander type certificaat gebruiken?
Ja, Aspose.Words ondersteunt verschillende certificaattypen, zolang ze maar het juiste formaat hebben.

### Is het mogelijk om meerdere documenten tegelijk te ondertekenen?
Absoluut! Je kunt door een verzameling documenten heen bladeren en elk document programmatisch ondertekenen.

### Wat als ik het decryptiewachtwoord vergeet?
Zonder het decryptiewachtwoord kunt u het document helaas niet ondertekenen.

### Kan ik een zichtbare handtekening aan het document toevoegen?
Ja, met Aspose.Words kunt u ook zichtbare digitale handtekeningen toevoegen.

### Is er een manier om de handtekening te verifiëren?
Ja, u kunt de `DigitalSignatureUtil.Verify` Methode om handtekeningen te verifiëren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}