---
title: ASKField invoegen zonder Document Builder
linktitle: ASKField invoegen zonder Document Builder
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een ASK-veld invoegt zonder Document Builder te gebruiken in Aspose.Words voor .NET. Volg deze handleiding om uw Word-documenten dynamisch te verbeteren.
weight: 10
url: /nl/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ASKField invoegen zonder Document Builder

## Invoering

Wilt u documentautomatisering onder de knie krijgen met Aspose.Words voor .NET? Dan bent u hier aan het juiste adres! Vandaag laten we u zien hoe u een ASK-veld invoegt zonder een Document Builder te gebruiken. Dit is een handige functie als u wilt dat uw document gebruikers om specifieke invoer vraagt, waardoor uw Word-documenten interactiever en dynamischer worden. Laten we er dus induiken en uw documenten slimmer maken!

## Vereisten

Voordat we met code aan de slag gaan, moeten we eerst controleren of alles goed is ingesteld:

1.  Aspose.Words voor .NET: Zorg ervoor dat u deze bibliotheek hebt geïnstalleerd. Zo niet, dan kunt u deze downloaden van[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een geschikte IDE zoals Visual Studio.
3. .NET Framework: Zorg ervoor dat u .NET Framework hebt geïnstalleerd.

Geweldig! Nu we alles hebben ingesteld, kunnen we beginnen met het importeren van de benodigde naamruimten.

## Naamruimten importeren

Allereerst moeten we de Aspose.Words-naamruimte importeren om toegang te krijgen tot alle functies van Aspose.Words voor .NET. Dit is hoe u dat doet:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Stap 1: Maak een nieuw document

Voordat we een ASK-veld kunnen invoegen, hebben we een document nodig om mee te werken. Zo maakt u een nieuw document:

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Documentcreatie.
Document doc = new Document();
```

Met dit codefragment maken we een nieuw Word-document aan, waaraan we het ASK-veld gaan toevoegen.

## Stap 2: Toegang tot de alineaknoop

In een Word-document is de inhoud georganiseerd in nodes. We moeten toegang krijgen tot de eerste alinea-node waar we ons ASK-veld invoegen:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Met deze coderegel wordt de eerste alinea van het document opgehaald, zodat deze in het ASK-veld kan worden ingevoegd.

## Stap 3: Het ASK-veld invoegen

Laten we nu naar het hoofdevenement gaan: het invoegen van het ASK-veld. Dit veld vraagt de gebruiker om invoer wanneer het document wordt geopend.

```csharp
// Voeg het ASK-veld in.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Hier voegen we een ASK-veld toe aan de alinea. Simpel toch?

## Stap 4: Configureer het ASK-veld

We moeten een aantal eigenschappen instellen om te definiëren hoe het ASK-veld zich gedraagt. Laten we de bladwijzernaam, prompttekst, standaardrespons en mail merge-gedrag configureren:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: Een unieke identificatie voor het ASK-veld.
- PromptText: De tekst die de gebruiker om invoer vraagt.
- Standaardantwoord: het vooraf ingevulde antwoord dat de gebruiker kan wijzigen.
- PromptOnceOnMailMerge: bepaalt of de prompt slechts één keer wordt weergegeven tijdens een samenvoegbewerking.

## Stap 5: Werk het veld bij

Nadat u het ASK-veld hebt geconfigureerd, moeten we het bijwerken om ervoor te zorgen dat alle instellingen correct worden toegepast:

```csharp
field.Update();
```

Met deze opdracht zorgt u ervoor dat ons ASK-veld gereed is en correct is ingesteld in het document.

## Stap 6: Sla het document op

Laten we het document ten slotte opslaan in de door ons opgegeven directory:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Deze regel slaat het document op met het ingevoegde ASK-veld. En voilà: uw document is nu voorzien van een dynamisch ASK-veld!

## Conclusie

Gefeliciteerd! U hebt zojuist een ASK-veld toegevoegd aan een Word-document met Aspose.Words voor .NET zonder de Document Builder. Deze functie kan de gebruikersinteractie met uw documenten aanzienlijk verbeteren, waardoor ze flexibeler en gebruiksvriendelijker worden. Blijf experimenteren met verschillende velden en eigenschappen om het volledige potentieel van Aspose.Words te benutten. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is een ASK-veld in Aspose.Words?
Een ASK-veld in Aspose.Words is een veld dat de gebruiker om specifieke invoer vraagt wanneer het document wordt geopend, waardoor dynamische gegevensinvoer mogelijk is.

### Kan ik meerdere ASK-velden in één document gebruiken?
Ja, u kunt meerdere ASK-velden in een document invoegen, elk met unieke prompts en reacties.

###  Wat is het doel van de`PromptOnceOnMailMerge` property?
 De`PromptOnceOnMailMerge` Deze eigenschap bepaalt of de ASK-prompt slechts één keer tijdens een samenvoegbewerking wordt weergegeven, of elke keer.

### Moet ik het ASK-veld bijwerken nadat ik de eigenschappen heb ingesteld?
Ja, door het ASK-veld bij te werken, zorgt u ervoor dat alle eigenschappen correct worden toegepast en dat het veld functioneert zoals verwacht.

### Kan ik de prompttekst en het standaardantwoord aanpassen?
Absoluut! U kunt aangepaste prompttekst en standaardantwoorden instellen om het ASK-veld aan te passen aan uw specifieke behoeften.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
