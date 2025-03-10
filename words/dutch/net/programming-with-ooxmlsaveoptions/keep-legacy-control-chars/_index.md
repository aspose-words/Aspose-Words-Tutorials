---
title: Behoud oude controletekens
linktitle: Behoud oude controletekens
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u oude besturingstekens in Word-documenten kunt behouden met Aspose.Words voor .NET met deze stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Behoud oude controletekens

## Invoering

Bent u ooit in de war geraakt door die vreemde, onzichtbare controletekens in uw Word-documenten? Het zijn net kleine, verborgen gremlins die de opmaak en functionaliteit kunnen verstoren. Gelukkig biedt Aspose.Words voor .NET een handige functie om deze oude controletekens intact te houden bij het opslaan van documenten. In deze tutorial duiken we diep in hoe u deze controletekens kunt beheren met Aspose.Words voor .NET. We leggen het stap voor stap uit, zodat u onderweg elk detail begrijpt. Klaar om te beginnen? Laten we erin duiken!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1.  Aspose.Words voor .NET: Downloaden en installeren vanaf[hier](https://releases.aspose.com/words/net/).
2.  Een geldige Aspose-licentie: U kunt een tijdelijke licentie verkrijgen[hier](https://purchase.aspose.com/temporary-license/).
3. Ontwikkelomgeving: Visual Studio of een andere IDE die .NET ondersteunt.
4. Basiskennis van C#: Kennis van de programmeertaal C# is nuttig.

## Naamruimten importeren

Voordat u uw code schrijft, moet u de benodigde namespaces importeren. Voeg de volgende regels toe aan het begin van uw C#-bestand:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Uw project instellen

Eerst moet u uw project instellen in Visual Studio (of uw favoriete IDE). 

1. Maak een nieuw C#-project: open Visual Studio en maak een nieuw C# Console Application-project.
2. Installeer Aspose.Words voor .NET: Gebruik NuGet Package Manager om Aspose.Words voor .NET te installeren. Klik met de rechtermuisknop op uw project in Solution Explorer, selecteer 'Manage NuGet Packages', zoek naar 'Aspose.Words' en installeer het.

## Stap 2: Laad uw document

Vervolgens laadt u het Word-document dat de oude besturingstekens bevat.

1. Geef het documentpad op: Stel het pad naar uw documentmap in.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2.  Laad het document: Gebruik de`Document` klasse om uw document te laden.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Stap 3: Configureer opslagopties

Nu gaan we de opslagopties configureren om de oude besturingstekens intact te houden.

1.  Opties voor opslaan maken: Initialiseer een exemplaar van`OoxmlSaveOptions` en stel de`KeepLegacyControlChars`eigendom van`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Stap 4: Sla het document op

Sla ten slotte het document op met de geconfigureerde opslagopties.

1.  Sla het document op: Gebruik de`Save` methode van de`Document` klasse om het document op te slaan met de opgegeven opslagopties.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je ervoor zorgen dat je oude controletekens behouden blijven wanneer je met Word-documenten werkt in Aspose.Words voor .NET. Deze functie kan een levensredder zijn, vooral bij het werken met complexe documenten waarbij controletekens een cruciale rol spelen. 

## Veelgestelde vragen

### Wat zijn legacy-controlekarakters?

Oude controletekens zijn niet-afdrukbare tekens die in oudere documenten worden gebruikt om de opmaak en lay-out te bepalen.

### Kan ik deze besturingskarakters verwijderen in plaats van ze te behouden?

Ja, u kunt Aspose.Words voor .NET gebruiken om deze tekens indien nodig te verwijderen of te vervangen.

### Is deze functie beschikbaar in alle versies van Aspose.Words voor .NET?

Deze functie is beschikbaar in recente versies. Zorg ervoor dat u de nieuwste versie gebruikt om toegang te krijgen tot alle functionaliteiten.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?

 Ja, u hebt een geldige licentie nodig. U kunt een tijdelijke licentie krijgen voor evaluatiedoeleinden[hier](https://purchase.aspose.com/temporary-license/).

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

 Gedetailleerde documentatie vindt u hier[hier](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
