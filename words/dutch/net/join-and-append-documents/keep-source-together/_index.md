---
"description": "Leer hoe u kunt voorkomen dat tabellen over pagina's worden verdeeld met Aspose.Words voor .NET met deze stapsgewijze handleiding. Zorg voor nette, professioneel ogende Word-documenten."
"linktitle": "Houd de tafel bij elkaar"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Houd de tafel bij elkaar"
"url": "/nl/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Houd de tafel bij elkaar

## Invoering

Tabellen zijn een essentieel onderdeel van veel Word-documenten, maar soms kan het gebeuren dat je tabel over twee pagina's wordt verdeeld. Dit kan de flow van je document verstoren en de leesbaarheid ervan beïnvloeden. Zou het niet handig zijn als er een manier was om de hele tabel op één pagina te houden? Nou, met Aspose.Words voor .NET is er een eenvoudige oplossing voor dit probleem! In deze tutorial laten we zien hoe je kunt voorkomen dat tabellen over pagina's worden verdeeld, zodat je document er netjes en professioneel uitziet.

## Vereisten

Voordat we met de tutorial beginnen, willen we ervoor zorgen dat je alles hebt wat je nodig hebt om de tutorial soepel te kunnen volgen.

### Aspose.Words voor .NET-bibliotheek

Allereerst moet je Aspose.Words voor .NET geïnstalleerd hebben. Dit is de krachtige bibliotheek waarmee je programmatisch met Word-documenten kunt werken.

- [Download Aspose.Words voor .NET](https://releases.aspose.com/words/net/)

### Ontwikkelomgeving

U moet een ontwikkelomgeving hebben ingesteld om C#-code uit te voeren, zoals:

- Visual Studio (elke recente versie)
- .NET Framework 2.0 of hoger

### Een Word-document met een tabel

Je hebt een Word-document nodig met een tabel. In deze tutorial werken we met een voorbeelddocument genaamd `"Table spanning two pages.docx"`Dit bestand bevat een tabel die momenteel twee pagina's beslaat.

### Tijdelijke licentie (optioneel)

Hoewel Aspose.Words een gratis proefversie heeft, wilt u misschien een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/) om het volledige potentieel van de bibliotheek te ontsluiten.

## Pakketten importeren

Voordat we code schrijven, moeten we de benodigde naamruimten importeren voor het werken met Aspose.Words voor .NET. Voeg de volgende imports bovenaan je codebestand toe:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Deze naamruimten geven u toegang tot klassen zoals `Document`, `Table`, `Cell`en andere die we in deze tutorial zullen gebruiken.

## Stap 1: Het document laden

Het eerste wat we moeten doen is het Word-document laden dat de tabel bevat. Hiervoor gebruiken we de `Document` klasse van Aspose.Words. Met deze klasse kunt u Word-bestanden programmatisch openen en bewerken.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

In dit codefragment specificeren we de locatie van ons document. Vervangen `"YOUR DOCUMENTS DIRECTORY"` met de daadwerkelijke map waarin uw document is opgeslagen.

## Stap 2: Toegang tot de tabel

Zodra het document is geladen, is de volgende stap het openen van de tabel die we bij elkaar willen houden. In dit voorbeeld gaan we ervan uit dat de tabel de eerste tabel in het document is.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Deze regel code vindt de eerste tabel in het document. `GetChild` methode haalt een specifiek type knooppunt op, wat in dit geval is `NodeType.Table`. De `0` geeft aan dat we de eerste tabel willen, en de `true` Met de vlag wordt ervoor gezorgd dat we recursief door alle onderliggende knooppunten zoeken.

## Stap 3: Door tabelcellen heen lussen

Nu moeten we door elke cel in de tabel heen lussen. Omdat een tabel meerdere rijen bevat en elke rij meerdere cellen bevat, itereren we door elke cel om ervoor te zorgen dat deze niet over meerdere pagina's wordt verdeeld.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Hier, `GetChildNodes` haalt alle cellen in de tabel op en we doorlopen ze allemaal. De `EnsureMinimum()` Deze methode zorgt ervoor dat elke cel ten minste één alinea bevat. Een lege cel kan namelijk later voor problemen zorgen.

## Stap 4: KeepWithNext-eigenschap instellen

Om te voorkomen dat de tabel over pagina's heen wordt verdeeld, moeten we de `KeepWithNext` Eigenschap voor elke alinea in de tabel. Deze eigenschap zorgt ervoor dat de alinea bij de volgende alinea blijft, waardoor pagina-einden tussen alinea's effectief worden voorkomen.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Deze lus controleert elke alinea in elke cel. De voorwaarde zorgt ervoor dat we de `KeepWithNext` eigenschap toe aan de laatste alinea in de laatste rij. Anders zou de eigenschap geen effect hebben, aangezien er geen volgende alinea is.

## Stap 5: Sla het document op

Ten slotte, na het aanbrengen van de `KeepWithNext` eigenschap, moeten we het gewijzigde document opslaan.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Deze regel slaat het bijgewerkte document op onder een nieuwe naam, waarbij het oorspronkelijke bestand behouden blijft. U kunt het resulterende bestand nu openen en zien dat de tabel niet langer over twee pagina's is verdeeld!

## Conclusie

En voilà! Door deze eenvoudige stappen te volgen, voorkom je eenvoudig dat tabellen over pagina's in Word-documenten worden verdeeld met Aspose.Words voor .NET. Of je nu werkt aan rapporten, contracten of andere documenten, het intact houden van tabellen zorgt voor een meer gepolijste, professionele uitstraling.

Het mooie van Aspose.Words is de flexibiliteit en het gebruiksgemak, waardoor u Word-documenten programmatisch kunt bewerken zonder dat u Microsoft Word op uw computer hoeft te installeren. Nu u de basis kent voor het bijhouden van tabellen, kunt u de andere functies van de bibliotheek verkennen om uw documentverwerkingsvaardigheden naar een hoger niveau te tillen!

## Veelgestelde vragen

### Waarom wordt mijn tabel nog steeds op meerdere pagina's weergegeven nadat ik deze code heb gebruikt?

Als uw tafel nog steeds kapot gaat, zorg er dan voor dat u de `KeepWithNext` eigenschap correct is ingesteld. Controleer nogmaals of alle alinea's, behalve de laatste in elke cel, deze eigenschap hebben ingesteld.

### Kan ik alleen bepaalde rijen bij elkaar houden?

Ja, u kunt de `KeepWithNext` eigenschap aan specifieke rijen of alinea's in de tabel toe om te bepalen welke onderdelen bij elkaar moeten blijven.

### Werkt deze methode met grote tabellen?

Bij zeer grote tabellen kan Word deze nog steeds over meerdere pagina's verdelen als er niet genoeg ruimte is om de hele tabel op één pagina te plaatsen. Overweeg de opmaak of marges van uw tabel aan te passen om grotere tabellen te kunnen plaatsen.

### Kan ik deze methode gebruiken met andere documentformaten?

Ja! Aspose.Words voor .NET ondersteunt veel formaten, zoals DOC, DOCX, PDF en andere. Dezelfde methode werkt voor alle formaten die tabellen ondersteunen.

### Is Aspose.Words voor .NET een gratis bibliotheek?

Aspose.Words voor .NET biedt een gratis proefperiode, maar voor volledige toegang tot alle functies moet u een licentie aanschaffen. U kunt de licentieopties bekijken op de [Aspose-aankooppagina](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}