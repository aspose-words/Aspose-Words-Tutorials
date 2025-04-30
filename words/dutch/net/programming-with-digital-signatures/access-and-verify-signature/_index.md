---
"description": "Krijg toegang tot en verifieer digitale handtekeningen in Word-documenten met Aspose.Words voor .NET met deze uitgebreide stapsgewijze handleiding. Zorg moeiteloos voor de authenticiteit van uw documenten."
"linktitle": "Toegang tot en verificatie van handtekening in Word-document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Toegang tot en verificatie van handtekening in Word-document"
"url": "/nl/net/programming-with-digital-signatures/access-and-verify-signature/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Toegang tot en verificatie van handtekening in Word-document

## Invoering

Hallo, mede-technologieliefhebbers! Heb je ooit een situatie meegemaakt waarin je digitale handtekeningen in een Word-document moest openen en verifiëren, maar geen idee had waar je moest beginnen? Dan heb je geluk! Vandaag duiken we in de wondere wereld van Aspose.Words voor .NET, een krachtige bibliotheek die het werken met Word-documenten een fluitje van een cent maakt. We leiden je stap voor stap door het proces, zodat je aan het einde van deze handleiding een professional bent in het verifiëren van digitale handtekeningen in Word-documenten. Laten we beginnen!

## Vereisten

Voordat we in de details duiken, zijn er een paar dingen die u moet regelen:

1. Visual Studio: Zorg ervoor dat Visual Studio op je computer is geïnstalleerd. Hier schrijf en voer je je code uit.
2. Aspose.Words voor .NET: Je moet Aspose.Words voor .NET geïnstalleerd hebben. Je kunt het downloaden. [hier](https://releases.aspose.com/words/net/)Vergeet niet om je gratis proefperiode aan te vragen [hier](https://releases.aspose.com/) als je dat nog niet gedaan hebt!
3. Een digitaal ondertekend Word-document: Zorg dat u een Word-document hebt dat al digitaal is ondertekend. Dit is het bestand waarmee u de handtekeningen gaat verifiëren.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Deze naamruimten stellen je in staat om de Aspose.Words-functies in je project te gebruiken.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

Oké, laten we dit opsplitsen in beheersbare stappen. Elke stap begeleidt je door een specifiek onderdeel van het proces. Klaar? Aan de slag!

## Stap 1: Stel uw project in

Voordat u een digitale handtekening kunt verifiëren, moet u uw project in Visual Studio instellen. Zo doet u dat:

### Een nieuw project maken

1. Visual Studio openen.
2. Klik op Een nieuw project maken.
3. Selecteer Console App (.NET Core) of Console App (.NET Framework), afhankelijk van uw voorkeur.
4. Klik op Volgende, geef uw project een naam en klik op Maken.

### Aspose.Words voor .NET installeren

1. Klik in Solution Explorer met de rechtermuisknop op uw projectnaam en selecteer NuGet-pakketten beheren.
2. Zoek in de NuGet Package Manager naar Aspose.Words.
3. Klik op Installeren om het aan uw project toe te voegen.

## Stap 2: Laad het digitaal ondertekende Word-document

Nu uw project is ingesteld, kunt u het digitaal ondertekende Word-document laden.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Digitally signed.docx");
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad naar uw documentmap. Dit codefragment initialiseert een nieuwe `Document` object en laadt uw ondertekende Word-document.

## Stap 3: Toegang tot de digitale handtekeningen

Nadat u uw document hebt geladen, is het tijd om toegang te krijgen tot de digitale handtekeningen.

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

Deze code doorloopt elke digitale handtekening in het document en print verschillende details over de handtekening. Laten we eens kijken wat elk onderdeel doet:

1. Handtekening gevonden: geeft aan dat er een handtekening is gevonden.
2. Is geldig: controleert of de handtekening geldig is.
3. Reden voor ondertekening: Geeft de reden voor ondertekening weer, indien beschikbaar.
4. Tijdstip van ondertekening: Geeft het tijdstempel weer waarop het document is ondertekend.
5. Onderwerpnaam: Haalt de onderwerpnaam op uit het certificaat.
6. Uitgeversnaam: Haalt de naam van de uitgever op uit het certificaat.

## Stap 4: Voer uw code uit

Zodra alles is ingesteld, is het tijd om uw code uit te voeren en de resultaten te bekijken.


1. Druk op F5 of klik op de Startknop in Visual Studio om uw programma uit te voeren.
2. Als uw document digitaal is ondertekend, worden de handtekeninggegevens in de console afgedrukt.

## Stap 5: Ga om met mogelijke fouten

Het is altijd een goed idee om mogelijke fouten af te handelen. Laten we wat basisfoutverwerking aan onze code toevoegen.

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

Hiermee worden eventuele uitzonderingen gedetecteerd en wordt een foutmelding weergegeven.

## Conclusie

En voilà! Je hebt met succes toegang gekregen tot en digitale handtekeningen geverifieerd in een Word-document met Aspose.Words voor .NET. Het is niet zo lastig als het lijkt, toch? Met deze stappen kun je vol vertrouwen digitale handtekeningen in je Word-documenten verwerken en de authenticiteit en integriteit ervan garanderen. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik Aspose.Words voor .NET gebruiken om digitale handtekeningen aan een Word-document toe te voegen?

Ja, u kunt Aspose.Words voor .NET gebruiken om digitale handtekeningen aan Word-documenten toe te voegen. De bibliotheek biedt uitgebreide functies voor zowel het toevoegen als verifiëren van digitale handtekeningen.

### Welke typen digitale handtekeningen kan Aspose.Words voor .NET verifiëren?

Aspose.Words voor .NET kan digitale handtekeningen verifiëren in DOCX-bestanden die gebruikmaken van X.509-certificaten.

### Is Aspose.Words voor .NET compatibel met alle versies van Microsoft Word?

Aspose.Words voor .NET ondersteunt alle versies van Microsoft Word-documenten, inclusief DOC, DOCX, RTF en meer.

### Hoe krijg ik een tijdelijke licentie voor Aspose.Words voor .NET?

U kunt een tijdelijke licentie voor Aspose.Words voor .NET verkrijgen via [hier](https://purchase.aspose.com/temporary-license/)Hiermee kunt u alle functies van de bibliotheek zonder beperkingen uitproberen.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

Gedetailleerde documentatie voor Aspose.Words voor .NET vindt u hier [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}