---
"description": "Leer hoe je de tekstrichting in een document in Word instelt met Aspose.Words voor .NET met deze stapsgewijze handleiding. Perfect voor talen die van rechts naar links worden geschreven."
"linktitle": "Documenttekstrichting"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Documenttekstrichting"
"url": "/nl/net/programming-with-txtloadoptions/document-text-direction/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documenttekstrichting

## Invoering

Bij het werken met Word-documenten, met name documenten met meerdere talen of speciale opmaakbehoeften, kan het instellen van de tekstrichting cruciaal zijn. Bij talen die van rechts naar links worden geschreven, zoals Hebreeuws of Arabisch, moet u de tekstrichting mogelijk aanpassen. In deze handleiding leggen we uit hoe u de tekstrichting van een document instelt met Aspose.Words voor .NET. 

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat u het volgende heeft:

- Aspose.Words voor .NET-bibliotheek: Zorg ervoor dat u Aspose.Words voor .NET hebt geïnstalleerd. U kunt het downloaden van de [Aspose-website](https://releases.aspose.com/words/net/).
- Visual Studio: een ontwikkelomgeving voor het schrijven en uitvoeren van C#-code.
- Basiskennis van C#: Kennis van C#-programmering is nuttig omdat we code gaan schrijven.

## Naamruimten importeren

Om te beginnen moet je de benodigde naamruimten voor het werken met Aspose.Words in je project importeren. Zo doe je dat:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

Deze naamruimten bieden toegang tot de klassen en methoden die nodig zijn om Word-documenten te bewerken.

## Stap 1: Definieer het pad naar uw documentmap

Stel eerst het pad in naar de locatie van uw document. Dit is cruciaal voor het correct laden en opslaan van bestanden.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad waar uw document is opgeslagen.

## Stap 2: TxtLoadOptions maken met documentrichtinginstelling

Vervolgens moet u een exemplaar maken van `TxtLoadOptions` en zet zijn `DocumentDirection` eigenschap. Deze vertelt Aspose.Words hoe de tekstrichting in het document moet worden behandeld.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

In dit voorbeeld gebruiken we `DocumentDirection.Auto` om Aspose.Words automatisch de richting te laten bepalen op basis van de inhoud.

## Stap 3: Het document laden

Laad nu het document met behulp van de `Document` klasse en de eerder gedefinieerde `loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

Hier, `"Hebrew text.txt"` is de naam van uw tekstbestand. Zorg ervoor dat dit bestand in de opgegeven directory staat.

## Stap 4: Toegang krijgen tot en controleren van de bidirectionele opmaak van de alinea

Om te bevestigen dat de tekstrichting correct is ingesteld, gaat u naar de eerste alinea van het document en controleert u de bidirectionele opmaak.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

Deze stap is handig om fouten op te sporen en te controleren of de tekstrichting van het document zoals verwacht is toegepast.

## Stap 5: Sla het document op met de nieuwe instellingen

Sla ten slotte het document op om de wijzigingen toe te passen en te behouden.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

Hier, `"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` is de naam van het uitvoerbestand. Zorg ervoor dat u een naam kiest die de aangebrachte wijzigingen weerspiegelt.

## Conclusie

Het instellen van de tekstrichting in Word-documenten is een eenvoudig proces met Aspose.Words voor .NET. Door deze stappen te volgen, kunt u eenvoudig configureren hoe uw document tekst van rechts naar links of van links naar rechts verwerkt. Of u nu met meertalige documenten werkt of de tekstrichting voor specifieke talen wilt opmaken, Aspose.Words biedt een robuuste oplossing die aan uw behoeften voldoet.

## Veelgestelde vragen

### Wat is de `DocumentDirection` Waarvoor wordt het onroerend goed gebruikt?

De `DocumentDirection` eigendom in `TxtLoadOptions` bepaalt de tekstrichting voor het document. Het kan worden ingesteld op `DocumentDirection.Auto`, `DocumentDirection.LeftToRight`, of `DocumentDirection.RightToLeft`.

### Kan ik de tekstrichting voor specifieke alinea's instellen in plaats van voor het hele document?

Ja, u kunt de tekstrichting voor specifieke alinea's instellen met behulp van de `ParagraphFormat.Bidi` eigendom, maar de `TxtLoadOptions.DocumentDirection` Met deze eigenschap wordt de standaardrichting voor het hele document ingesteld.

### Welke bestandsindelingen worden ondersteund voor het laden met `TxtLoadOptions`?

`TxtLoadOptions` wordt voornamelijk gebruikt voor het laden van tekstbestanden (.txt). Voor andere bestandsformaten worden verschillende klassen gebruikt, zoals `DocLoadOptions` of `DocxLoadOptions`.

### Hoe kan ik documenten met gemengde tekstrichtingen verwerken?

Voor documenten met gemengde tekstrichtingen moet u de opmaak mogelijk per alinea aanpassen. Gebruik de `ParagraphFormat.Bidi` eigenschap om de richting van elke alinea indien nodig aan te passen.

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?

Voor meer details, bekijk de [Aspose.Words voor .NET-documentatie](https://reference.aspose.com/words/net/)U kunt ook aanvullende bronnen bekijken, zoals [Downloadlink](https://releases.aspose.com/words/net/), [Kopen](https://purchase.aspose.com/buy), [Gratis proefperiode](https://releases.aspose.com/), [Tijdelijke licentie](https://purchase.aspose.com/temporary-license/), En [Steun](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}