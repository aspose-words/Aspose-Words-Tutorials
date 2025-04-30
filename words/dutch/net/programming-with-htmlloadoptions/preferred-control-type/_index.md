---
"description": "Leer hoe u een invoervak in een Word-document invoegt met Aspose.Words voor .NET. Volg deze stapsgewijze handleiding voor naadloze integratie van HTML-inhoud."
"linktitle": "Voorkeursbesturingstype in Word-document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Voorkeursbesturingstype in Word-document"
"url": "/nl/net/programming-with-htmlloadoptions/preferred-control-type/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voorkeursbesturingstype in Word-document

## Invoering

We duiken in een interessante tutorial over het werken met HTML-laadopties in Aspose.Words voor .NET, met specifieke aandacht voor het instellen van het gewenste besturingselementtype bij het invoegen van een invoervak in een Word-document. Deze stapsgewijze handleiding helpt je te begrijpen hoe je HTML-inhoud in je Word-documenten effectief kunt bewerken en weergeven met Aspose.Words voor .NET.

## Vereisten

Voordat we met de code aan de slag gaan, zijn er een paar dingen die je moet regelen:

1. Aspose.Words voor .NET: Zorg ervoor dat u de Aspose.Words voor .NET-bibliotheek hebt geïnstalleerd. U kunt deze downloaden van de [website](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: U moet een ontwikkelomgeving instellen, zoals Visual Studio.
3. Basiskennis van C#: Een basiskennis van C#-programmering is noodzakelijk om deze tutorial te kunnen volgen.
4. HTML-inhoud: basiskennis van HTML is nuttig omdat we in dit voorbeeld met HTML-inhoud werken.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren om aan de slag te gaan:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Laten we het voorbeeld nu opsplitsen in meerdere stappen, zodat het duidelijker en begrijpelijker wordt.

## Stap 1: Stel uw HTML-inhoud in

Eerst moeten we de HTML-inhoud definiëren die we in het Word-document willen invoegen. Dit is het HTML-fragment dat we gaan gebruiken:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

Deze HTML bevat een eenvoudige keuzelijst met twee opties. We laden deze HTML in een Word-document en specificeren hoe deze moet worden weergegeven.

## Stap 2: Definieer de documentmap

Geef vervolgens de map op waar uw Word-document moet worden opgeslagen. Dit helpt bij het ordenen van uw bestanden en zorgt ervoor dat het padbeheer overzichtelijk blijft.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad waar u uw Word-document wilt opslaan.

## Stap 3: HTML-laadopties configureren

Hier configureren we de HTML-laadopties, met speciale aandacht voor de `PreferredControlType` eigenschap. Hiermee bepaalt u hoe de keuzelijst met invoervak in het Word-document wordt weergegeven.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

Door het instellen `PreferredControlType` naar `HtmlControlType.StructuredDocumentTag`zorgen we ervoor dat de keuzelijst wordt weergegeven als een gestructureerde documenttag (SDT) in het Word-document.

## Stap 4: Laad de HTML-inhoud in het document

Met behulp van de geconfigureerde laadopties laden we de HTML-inhoud in een nieuw Word-document.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Hier converteren we de HTML-string naar een byte-array en laden deze via een geheugenstroom in het document. Dit zorgt ervoor dat de HTML-inhoud correct wordt geïnterpreteerd en weergegeven door Aspose.Words.

## Stap 5: Sla het document op

Sla het document ten slotte op in de opgegeven directory in DOCX-formaat.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

Hiermee wordt het Word-document met het gerenderde keuzelijstbesturingselement op de opgegeven locatie opgeslagen.

## Conclusie

En voilà! We hebben met succes een invoervak in een Word-document ingevoegd met Aspose.Words voor .NET, waarbij we gebruik hebben gemaakt van de HTML-laadopties. Deze stapsgewijze handleiding helpt u het proces te begrijpen en toe te passen op uw projecten. Of u nu de documentcreatie automatiseert of HTML-inhoud bewerkt, Aspose.Words voor .NET biedt krachtige tools om uw doelen te bereiken.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor documentmanipulatie waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, bewerken, converteren en weergeven.

### Kan ik andere HTML-besturingselementen gebruiken met Aspose.Words voor .NET?
Ja, Aspose.Words voor .NET ondersteunt verschillende typen HTML-besturingselementen. U kunt aanpassen hoe verschillende besturingselementen in het Word-document worden weergegeven.

### Hoe verwerk ik complexe HTML-inhoud in Aspose.Words voor .NET?
Aspose.Words voor .NET biedt uitgebreide ondersteuning voor HTML, inclusief complexe elementen. Zorg ervoor dat u de `HtmlLoadOptions` op de juiste manier met uw specifieke HTML-inhoud omgaan.

### Waar kan ik meer voorbeelden en documentatie vinden?
Gedetailleerde documentatie en voorbeelden vindt u op de [Aspose.Words voor .NET-documentatiepagina](https://reference.aspose.com/words/net/).

### Is er een gratis proefversie beschikbaar voor Aspose.Words voor .NET?
Ja, u kunt een gratis proefversie downloaden van de [Aspose-website](https://releases.aspose.com/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}