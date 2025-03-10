---
title: Toegang tot en verificatie van handtekening in Word-document
linktitle: Toegang tot en verificatie van handtekening in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Krijg toegang tot en verifieer digitale handtekeningen in Word-documenten met Aspose.Words voor .NET met deze uitgebreide stapsgewijze handleiding. Zorg moeiteloos voor authenticiteit van documenten.
weight: 10
url: /nl/net/programming-with-digital-signatures/access-and-verify-signature/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Toegang tot en verificatie van handtekening in Word-document

## Invoering

Hallo, mede-tech-enthousiastelingen! Heb je ooit in een situatie gezeten waarin je digitale handtekeningen in een Word-document moest openen en verifiëren, maar geen idee had waar je moest beginnen? Nou, dan heb je geluk! Vandaag duiken we in de wondere wereld van Aspose.Words voor .NET, een krachtige bibliotheek die het verwerken van Word-documenten een fluitje van een cent maakt. We leiden je stap voor stap door het proces, zodat je aan het einde van deze gids een pro bent in het verifiëren van digitale handtekeningen in Word-documenten. Laten we beginnen!

## Vereisten

Voordat we in de details duiken, zijn er een paar dingen die u moet regelen:

1. Visual Studio: Zorg ervoor dat Visual Studio op uw machine is geïnstalleerd. Dit is waar u uw code schrijft en uitvoert.
2.  Aspose.Words voor .NET: U moet Aspose.Words voor .NET geïnstalleerd hebben. U kunt het downloaden[hier](https://releases.aspose.com/words/net/) Vergeet niet om je gratis proefperiode te krijgen[hier](https://releases.aspose.com/) als je dat nog niet gedaan hebt!
3. Een digitaal ondertekend Word-document: Heb een Word-document dat al digitaal is ondertekend. Dit is het bestand waarmee u gaat werken om de handtekeningen te verifiëren.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Deze namespaces stellen u in staat om de Aspose.Words-functies in uw project te gebruiken.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

Oké, laten we dit opsplitsen in beheersbare stappen. Elke stap zal je door een specifiek deel van het proces leiden. Klaar? Laten we gaan!

## Stap 1: Stel uw project in

Voordat u een digitale handtekening kunt verifiëren, moet u uw project in Visual Studio instellen. Dit doet u als volgt:

### Een nieuw project maken

1. Open Visual Studio.
2. Klik op Nieuw project maken.
3. Selecteer Console-app (.NET Core) of Console-app (.NET Framework), afhankelijk van uw voorkeur.
4. Klik op Volgende, geef uw project een naam en klik op Maken.

### Installeer Aspose.Words voor .NET

1. Klik in Solution Explorer met de rechtermuisknop op de naam van uw project en selecteer NuGet-pakketten beheren.
2. Zoek in de NuGet Package Manager naar Aspose.Words.
3. Klik op Installeren om het aan uw project toe te voegen.

## Stap 2: Laad het digitaal ondertekende Word-document

Nu uw project is ingesteld, kunt u het digitaal ondertekende Word-document laden.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Digitally signed.docx");
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw documentdirectory. Dit codefragment initialiseert een nieuwe`Document` object en laadt uw ondertekende Word-document.

## Stap 3: Toegang tot de digitale handtekeningen

Zodra uw document is geladen, is het tijd om toegang te krijgen tot de digitale handtekeningen.

```csharp
foreach (DigitalSignature signature in doc.DigitalSignatures)
{
    Console.WriteLine("* Signature Found *");
    Console.WriteLine("Is valid: " + signature.IsValid);
    Console.WriteLine("Reason for signing: " + signature.Comments); 
    Console.WriteLine("Time of signing: " + signature.SignTime);
    Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
    Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
    Console.WriteLine();
}
```

Deze code loopt door elke digitale handtekening in het document en print verschillende details over de handtekening. Laten we eens kijken wat elk onderdeel doet:

1. Handtekening gevonden: geeft aan dat er een handtekening is gevonden.
2. Is geldig: controleert of de handtekening geldig is.
3. Reden voor ondertekening: Geeft de reden voor ondertekening weer, indien beschikbaar.
4. Tijdstip van ondertekening: Geeft het tijdstempel weer waarop het document is ondertekend.
5. Onderwerpnaam: Haalt de onderwerpnaam op uit het certificaat.
6. Uitgeversnaam: Haalt de uitgeversnaam op uit het certificaat.

## Stap 4: Voer uw code uit

Zodra alles is ingesteld, is het tijd om uw code uit te voeren en de resultaten te bekijken.


1. Druk op F5 of klik op de Start-knop in Visual Studio om uw programma uit te voeren.
2. Als uw document digitaal is ondertekend, worden de handtekeninggegevens in de console afgedrukt.

## Stap 5: Ga om met mogelijke fouten

Het is altijd een goed idee om mogelijke fouten die kunnen optreden, af te handelen. Laten we wat basisfoutafhandeling aan onze code toevoegen.

```csharp
try
{
    // Het pad naar de documentenmap.
    string dataDir = "YOUR DOCUMENT DIRECTORY";
    Document doc = new Document(dataDir + "Digitally signed.docx");

    foreach (DigitalSignature signature in doc.DigitalSignatures)
    {
        Console.WriteLine("* Signature Found *");
        Console.WriteLine("Is valid: " + signature.IsValid);
        Console.WriteLine("Reason for signing: " + signature.Comments); 
        Console.WriteLine("Time of signing: " + signature.SignTime);
        Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
        Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
        Console.WriteLine();
    }
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

Hiermee worden eventuele uitzonderingen onderschept en wordt een foutmelding weergegeven.

## Conclusie

En daar heb je het! Je hebt met succes toegang gekregen tot en digitale handtekeningen geverifieerd in een Word-document met Aspose.Words voor .NET. Het is niet zo ontmoedigend als het lijkt, toch? Met deze stappen kun je vol vertrouwen digitale handtekeningen verwerken in je Word-documenten, en hun authenticiteit en integriteit garanderen. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik Aspose.Words voor .NET gebruiken om digitale handtekeningen aan een Word-document toe te voegen?

Ja, u kunt Aspose.Words voor .NET gebruiken om digitale handtekeningen toe te voegen aan Word-documenten. De bibliotheek biedt uitgebreide functies voor zowel het toevoegen als verifiëren van digitale handtekeningen.

### Welke typen digitale handtekeningen kan Aspose.Words voor .NET verifiëren?

Aspose.Words voor .NET kan digitale handtekeningen verifiëren in DOCX-bestanden die gebruikmaken van X.509-certificaten.

### Is Aspose.Words voor .NET compatibel met alle versies van Microsoft Word?

Aspose.Words voor .NET ondersteunt alle versies van Microsoft Word-documenten, waaronder DOC, DOCX, RTF en meer.

### Hoe krijg ik een tijdelijke licentie voor Aspose.Words voor .NET?

 U kunt een tijdelijke licentie voor Aspose.Words voor .NET verkrijgen via[hier](https://purchase.aspose.com/temporary-license/)Hiermee kunt u de volledige functionaliteit van de bibliotheek uitproberen zonder enige beperking.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

 Gedetailleerde documentatie voor Aspose.Words voor .NET vindt u hier[hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
