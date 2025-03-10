---
title: Kopteksten en voetteksten ontkoppelen
linktitle: Kopteksten en voetteksten ontkoppelen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u kop- en voetteksten in Word-documenten kunt ontkoppelen met Aspose.Words voor .NET. Volg onze gedetailleerde, stapsgewijze handleiding om documentmanipulatie onder de knie te krijgen.
weight: 10
url: /nl/net/join-and-append-documents/unlink-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kopteksten en voetteksten ontkoppelen

## Invoering

In de wereld van documentverwerking kan het soms een uitdaging zijn om headers en footers consistent te houden. Of u nu documenten samenvoegt of gewoon verschillende headers en footers voor verschillende secties wilt, het is essentieel om te weten hoe u ze kunt ontkoppelen. Vandaag duiken we in hoe u dit kunt bereiken met Aspose.Words voor .NET. We leggen het stap voor stap uit, zodat u het gemakkelijk kunt volgen. Klaar om documentmanipulatie onder de knie te krijgen? Laten we beginnen!

## Vereisten

Voordat we in de details duiken, zijn er een paar dingen die je nodig hebt:

-  Aspose.Words voor .NET-bibliotheek: U kunt het downloaden van de[Aspose releases pagina](https://releases.aspose.com/words/net/).
- .NET Framework: Zorg ervoor dat u een compatibel .NET Framework hebt geïnstalleerd.
- IDE: Visual Studio of een andere .NET-compatibele geïntegreerde ontwikkelomgeving.
- Basiskennis van C#: U hebt een basiskennis van de programmeertaal C# nodig.

## Naamruimten importeren

Om te beginnen, zorg ervoor dat u de benodigde namespaces in uw project importeert. Dit zal u in staat stellen om toegang te krijgen tot de Aspose.Words bibliotheek en de functies ervan.

```csharp
using Aspose.Words;
```

Laten we het proces opsplitsen in hanteerbare stappen om u te helpen kop- en voetteksten in uw Word-documenten te ontkoppelen.

## Stap 1: Stel uw project in

Eerst moet u uw projectomgeving instellen. Open uw IDE en maak een nieuw .NET-project. Voeg een verwijzing toe naar de Aspose.Words-bibliotheek die u eerder hebt gedownload.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Laad het brondocument

Vervolgens moet u het brondocument laden dat u wilt wijzigen. De headers en footers van dit document zijn niet gekoppeld.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Stap 3: Laad het bestemmingsdocument

Laad nu het doeldocument waaraan u het brondocument wilt toevoegen, nadat u de kop- en voetteksten hebt ontkoppeld.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Stap 4: Kopteksten en voetteksten ontkoppelen

 Deze stap is cruciaal. Om de kop- en voetteksten van het brondocument los te koppelen van die van het doeldocument, gebruikt u de`LinkToPrevious` methode. Deze methode zorgt ervoor dat de kop- en voetteksten niet worden overgedragen naar het bijgevoegde document.

```csharp
// Koppel de kop- en voetteksten in het brondocument los om dit te stoppen
//door de kop- en voetteksten van het doeldocument voort te zetten.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Stap 5: Voeg het bron document toe

 Nadat u de kop- en voetteksten hebt losgekoppeld, kunt u het brondocument aan het doeldocument toevoegen. Gebruik de`AppendDocument` methode en stel de importformaatmodus in op`KeepSourceFormatting` om de oorspronkelijke opmaak van het brondocument te behouden.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Stap 6: Sla het definitieve document op

Sla ten slotte het nieuw gemaakte document op. Dit document zal de inhoud van het brondocument aan het doeldocument toevoegen, met de kop- en voetteksten ontkoppeld.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Conclusie

En daar heb je het! Door deze stappen te volgen, heb je de kop- en voetteksten in je brondocument succesvol losgekoppeld en toegevoegd aan je doeldocument met behulp van Aspose.Words voor .NET. Deze techniek kan met name handig zijn als je werkt met complexe documenten die verschillende kop- en voetteksten voor verschillende secties nodig hebben. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?  
Aspose.Words voor .NET is een krachtige bibliotheek voor het werken met Word-documenten in .NET-applicaties. Hiermee kunnen ontwikkelaars programmatisch documenten maken, wijzigen, converteren en afdrukken.

### Kan ik kop- en voetteksten alleen voor specifieke secties loskoppelen?  
 Ja, u kunt kop- en voetteksten voor specifieke secties loskoppelen door naar de`HeadersFooters` eigenschap van de gewenste sectie en het gebruik van de`LinkToPrevious` methode.

### Is het mogelijk om de originele opmaak van het brondocument te behouden?  
 Ja, gebruik bij het toevoegen van het bron document de`ImportFormatMode.KeepSourceFormatting` optie om de originele opmaak te behouden.

### Kan ik Aspose.Words voor .NET gebruiken met andere .NET-talen dan C#?  
Absoluut! Aspose.Words voor .NET kan worden gebruikt met elke .NET-taal, inclusief VB.NET en F#.

### Waar kan ik meer documentatie en ondersteuning vinden voor Aspose.Words voor .NET?  
 Uitgebreide documentatie vindt u op de[Aspose.Words voor .NET-documentatiepagina](https://reference.aspose.com/words/net/) , en ondersteuning is beschikbaar op de[Aspose-forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
