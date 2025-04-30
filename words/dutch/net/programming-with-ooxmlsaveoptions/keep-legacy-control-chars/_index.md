---
"description": "Leer hoe u oude besturingstekens in Word-documenten kunt behouden met Aspose.Words voor .NET met behulp van deze stapsgewijze handleiding."
"linktitle": "Behoud oude controletekens"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Behoud oude controletekens"
"url": "/nl/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Behoud oude controletekens

## Invoering

Heb je je ooit verbaasd over die vreemde, onzichtbare controletekens in je Word-documenten? Het zijn net kleine, verborgen gremlins die de opmaak en functionaliteit kunnen verstoren. Gelukkig biedt Aspose.Words voor .NET een handige functie om deze oude controletekens intact te houden bij het opslaan van documenten. In deze tutorial gaan we dieper in op hoe je deze controletekens kunt beheren met Aspose.Words voor .NET. We leggen het stap voor stap uit, zodat je elk detail begrijpt. Klaar om te beginnen? Laten we beginnen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. Aspose.Words voor .NET: Downloaden en installeren vanaf [hier](https://releases.aspose.com/words/net/).
2. Een geldige Aspose-licentie: U kunt een tijdelijke licentie verkrijgen [hier](https://purchase.aspose.com/temporary-license/).
3. Ontwikkelomgeving: Visual Studio of een andere IDE die .NET ondersteunt.
4. Basiskennis van C#: Kennis van de programmeertaal C# is nuttig.

## Naamruimten importeren

Voordat u uw code schrijft, moet u de benodigde naamruimten importeren. Voeg de volgende regels toe bovenaan uw C#-bestand:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Uw project instellen

Eerst moet u uw project instellen in Visual Studio (of uw favoriete IDE). 

1. Een nieuw C#-project maken: open Visual Studio en maak een nieuw C# Console Application-project.
2. Installeer Aspose.Words voor .NET: Gebruik NuGet Package Manager om Aspose.Words voor .NET te installeren. Klik met de rechtermuisknop op uw project in Solution Explorer, selecteer 'NuGet-pakketten beheren', zoek naar 'Aspose.Words' en installeer het.

## Stap 2: Laad uw document

Vervolgens laadt u het Word-document dat de oude besturingstekens bevat.

1. Geef het documentpad op: stel het pad in naar uw documentmap.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Laad het document: Gebruik de `Document` klasse om uw document te laden.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Stap 3: Opties voor opslaan configureren

Laten we nu de opslagopties configureren om de oude besturingscodes intact te houden.

1. Opties voor opslaan maken: Initialiseer een instantie van `OoxmlSaveOptions` en stel de `KeepLegacyControlChars` eigendom van `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Stap 4: Sla het document op

Sla ten slotte het document op met de geconfigureerde opslagopties.

1. Sla het document op: Gebruik de `Save` methode van de `Document` klasse om het document op te slaan met de opgegeven opslagopties.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusie

En voilà! Door deze stappen te volgen, zorgt u ervoor dat uw oude controletekens behouden blijven wanneer u met Word-documenten werkt in Aspose.Words voor .NET. Deze functie kan een uitkomst zijn, vooral bij complexe documenten waarbij controletekens een cruciale rol spelen. 

## Veelgestelde vragen

### Wat zijn legacy-controlekarakters?

Oude controlekarakters zijn niet-afdrukbare tekens die in oudere documenten worden gebruikt om de opmaak en lay-out te bepalen.

### Kan ik deze controlekarakters verwijderen in plaats van ze te behouden?

Ja, u kunt Aspose.Words voor .NET gebruiken om deze tekens indien nodig te verwijderen of te vervangen.

### Is deze functie beschikbaar in alle versies van Aspose.Words voor .NET?

Deze functie is beschikbaar in recente versies. Zorg ervoor dat u de nieuwste versie gebruikt om toegang te krijgen tot alle functionaliteiten.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?

Ja, u heeft een geldige vergunning nodig. U kunt een tijdelijke vergunning aanvragen voor evaluatiedoeleinden. [hier](https://purchase.aspose.com/temporary-license/).

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

Gedetailleerde documentatie vindt u hier [hier](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}