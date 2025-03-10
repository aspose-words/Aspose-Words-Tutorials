---
title: Inhoudsopgave Generatie
linktitle: Inhoudsopgave Generatie
second_title: Aspose.Words Java Documentverwerkings-API
description: Leer hoe u een dynamische inhoudsopgave maakt met Aspose.Words voor Java. Leer TOC-generatie met stapsgewijze begeleiding en broncodevoorbeelden.
weight: 14
url: /nl/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhoudsopgave Generatie

## Invoering

Heb je ooit moeite gehad met het maken van een dynamische en professioneel ogende inhoudsopgave (TOC) in je Word-documenten? Zoek niet verder! Met Aspose.Words voor Java kun je het hele proces automatiseren, wat tijd bespaart en nauwkeurigheid garandeert. Of je nu een uitgebreid rapport of een academisch artikel schrijft, deze tutorial leidt je door het programmatisch genereren van een TOC met Java. Klaar om erin te duiken? Laten we beginnen!

## Vereisten

Voordat we beginnen met coderen, moet u ervoor zorgen dat u het volgende heeft:

1.  Java Development Kit (JDK): Geïnstalleerd op uw systeem. U kunt het downloaden van[Website van Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words voor Java-bibliotheek: Download de nieuwste versie van de[vrijgavepagina](https://releases.aspose.com/words/java/).
3. Geïntegreerde ontwikkelomgeving (IDE): zoals IntelliJ IDEA, Eclipse of NetBeans.
4.  Aspose Tijdelijke Licentie: Om evaluatiebeperkingen te vermijden, verkrijg een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/).

## Pakketten importeren

Om Aspose.Words voor Java effectief te gebruiken, moet u ervoor zorgen dat u de vereiste klassen importeert. Dit zijn de imports:

```java
import com.aspose.words.*;
```

Volg deze stappen om een dynamische inhoudsopgave in uw Word-document te genereren.

## Stap 1: Initialiseer het document en DocumentBuilder

 De eerste stap is het maken van een nieuw document en het gebruiken van de`DocumentBuilder` klasse om het te manipuleren.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Geeft het Word-document weer.
- `DocumentBuilder`: Een hulpklasse waarmee u het document eenvoudig kunt manipuleren.

## Stap 2: Voeg de inhoudsopgave in

Laten we nu de inhoudsopgave aan het begin van het document invoegen.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Voegt een TOC-veld in. De parameters specificeren:
  - `\o "1-3"`: Voeg koppen van niveau 1 tot en met 3 toe.
  - `\h`: Maak hyperlinks naar de items.
  - `\z`: Onderdruk paginanummers voor webdocumenten.
  - `\u`: Stijlen voor hyperlinks behouden.
- `insertBreak`: Voegt een pagina-einde toe na de inhoudsopgave.

## Stap 3: Voeg koppen toe om de inhoudsopgave te vullen

Om de inhoudsopgave te vullen, moet u alinea's met koptekststijlen toevoegen.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Stelt de alineastijl in op een specifiek kopniveau (bijv.`HEADING_1`, `HEADING_2`).
- `writeln`: Voegt tekst toe aan het document met de opgegeven stijl.

## Stap 4: Geneste koppen toevoegen

Om de inhoudsopgaveniveaus te illustreren, kunt u geneste koppen gebruiken.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Voeg koppen van diepere niveaus toe om de hiërarchie in de inhoudsopgave weer te geven.

## Stap 5: TOC-velden bijwerken

Het inhoudsopgaveveld moet worden bijgewerkt om de nieuwste koppen weer te geven.


```java
doc.updateFields();
```

- `updateFields`: Vernieuwt alle velden in het document en zorgt ervoor dat de inhoudsopgave de toegevoegde koppen weerspiegelt.

## Stap 6: Sla het document op

Sla het document ten slotte op in het door u gewenste formaat.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exporteert het document naar een`.docx` bestand. U kunt andere formaten opgeven, zoals`.pdf` of`.txt` indien nodig.

## Conclusie

Gefeliciteerd! U hebt met succes een dynamische inhoudsopgave gemaakt in een Word-document met Aspose.Words voor Java. Met slechts een paar regels code hebt u een taak geautomatiseerd die anders uren zou duren. Dus, wat nu? Experimenteer met verschillende kopstijlen en -formaten om uw inhoudsopgave aan te passen aan specifieke behoeften.

## Veelgestelde vragen

### Kan ik de inhoudsopgave verder aanpassen?
Absoluut! U kunt TOC-parameters aanpassen, zoals het opnemen van paginanummers, het uitlijnen van tekst of het gebruiken van aangepaste koptekststijlen.

### Is een licentie verplicht voor Aspose.Words voor Java?
 Ja, voor volledige functionaliteit is een licentie vereist. U kunt beginnen met een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/).

### Kan ik een inhoudsopgave genereren voor een bestaand document?
 Ja! Laad het document in een`Document` object en volg dezelfde stappen om de inhoudsopgave in te voegen en bij te werken.

### Werkt dit voor PDF-exporten?
 Ja, de inhoudsopgave verschijnt in de PDF als u het document opslaat in`.pdf` formaat.

### Waar kan ik meer documentatie vinden?
 Bekijk de[Aspose.Words voor Java-documentatie](https://reference.aspose.com/words/java/) voor meer voorbeelden en details.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
