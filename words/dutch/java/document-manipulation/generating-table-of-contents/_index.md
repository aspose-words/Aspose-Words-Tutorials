---
date: 2026-01-03
description: Leer hoe u paginanummers kunt aanpassen bij het invoegen van een inhoudsopgave
  met Aspose.Words voor Java. Pas TOC‑stijlen aan en maak moeiteloos documenten.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Paginanummers aanpassen & inhoudsopgave genereren met Aspose.Words voor Java
url: /nl/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Paginanummers aanpassen & een inhoudsopgave genereren in Aspose.Words voor Java

In deze tutorial ontdek je hoe je **paginanummers kunt aanpassen** en **een inhoudsopgave** (TOC) kunt invoegen met Aspose.Words voor Java. Een goed gestructureerde TOC maakt lange documenten gemakkelijk navigeerbaar, en het verfijnen van de uitlijning van paginanummers geeft je lezers een professionele ervaring. We lopen stap voor stap door het maken van een document, het aanpassen van TOC‑stijlen en het finetunen van tab‑stops zodat de paginanummers precies daar staan waar je ze wilt.

## Snelle antwoorden
- **Wat betekent “paginanummers aanpassen”?** Het wijzigen van de tab‑stops die de paginanummers in een TOC uitlijnen.  
- **Kan ik automatisch een inhoudsopgave invoegen?** Ja – gebruik de `FieldToc`‑klasse.  
- **Heb ik een licentie nodig om de code uit te voeren?** Een gratis proefversie werkt voor ontwikkeling; een licentie is vereist voor productie.  
- **Welke Aspose‑versie wordt ondersteund?** De voorbeelden werken met de nieuwste release van Aspose.Words voor Java.  
- **Is het mogelijk om TOC‑stijlen aan te passen?** Absoluut – je kunt lettertypen, vetgedruktheid en meer wijzigen.

## Wat is een inhoudsopgave in Aspose.Words?
Een TOC is een veld dat het document scant op kopstijlen (bijv. Heading 1, Heading 2) en een lijst met items en paginanummers genereert. Aspose.Words stelt je in staat dit veld programmatisch in te voegen en de weergave volledig te controleren.

## Waarom paginanummers in een TOC aanpassen?
Het aanpassen van de tab‑stops geeft je precieze controle over waar de paginanummers verschijnen, wat essentieel is voor:

- Het behouden van een nette, kolom‑uitgelijnde lay‑out.  
- Het volgen van bedrijfs‑styleguidelines.  
- Het verbeteren van de leesbaarheid in zowel gedrukte als digitale documenten.

## Vereisten
- Aspose.Words voor Java toegevoegd aan je project (Maven/Gradle).  
- Basiskennis van Java‑syntaxis.  

## Stapsgewijze handleiding

### Stap 1: Een nieuw document maken
Maak eerst een leeg `Document`‑object aan dat je inhoud en TOC zal bevatten.

```java
Document doc = new Document();
```

### Stap 2: TOC‑stijlen aanpassen
Je kunt het uiterlijk van elk TOC‑niveau wijzigen. In dit voorbeeld maken we de eerste‑niveau‑items vet, wat een veelvoorkomende opmaakvraag is.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Stap 3: Inhoud aan je document toevoegen
Voeg koppen in (bijv. `Heading1`, `Heading2`) en gewone alinea’s toe. Het TOC‑veld zal later deze koppen automatisch oppikken. *(Code weggelaten voor beknoptheid – de focus ligt op TOC‑generatie.)*

### Stap 4: Het TOC‑veld invoegen
Plaats de TOC waar je wilt – meestal aan het begin van het document.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Stap 5: Het document opslaan
Sla het document op schijf op. Je kunt elk ondersteund formaat kiezen, zoals DOCX, PDF of HTML.

```java
doc.save("your_output_path_here");
```

## Tab‑stops aanpassen in TOC (paginanummers aanpassen)
Als de standaard tab‑stop de paginanummers niet op de gewenste plek uitlijnt, kun je door alle TOC‑alinea’s itereren en hun tab‑posities wijzigen.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nu tonen de TOC‑items paginanummers precies waar je ze wilt, waardoor je document er gepolijst uitziet.

## Veelvoorkomende problemen & tips
- **Ontbrekende koppen in TOC:** Zorg ervoor dat je koppen ingebouwde stijlen gebruiken (`Heading1`, `Heading2`, enz.) of koppel aangepaste stijlen aan TOC‑niveaus.  
- **Tab‑stop niet toegepast:** Controleer of de alinea daadwerkelijk tot een TOC‑stijl behoort (`TOC_1`‑`TOC_9`).  
- **Prestaties bij grote documenten:** Roep `doc.updateFields()` aan na het invoegen van de TOC om de items in één keer te vernieuwen.

## Veelgestelde vragen

**V: Hoe wijzig ik de opmaak van TOC‑items?**  
A: Gebruik `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` waarbij *X* het niveau is (1‑9) en pas het lettertype, de kleur of alinea‑instellingen aan.

**V: Hoe kan ik meer niveaus aan mijn TOC toevoegen?**  
A: Pas de `FieldToc`‑switch `\o "1-3"` (bijvoorbeeld) aan om extra kopniveaus op te nemen, en werk vervolgens de overeenkomstige `TOC_X`‑stijlen bij.

**V: Kan ik de tab‑stopposities voor specifieke TOC‑items wijzigen?**  
A: Ja – itereer door de alinea’s zoals getoond in de sectie “Tab‑stops aanpassen” en wijzig elke tab‑stop afzonderlijk.

**V: Is het mogelijk om een TOC te genereren in PDF‑output?**  
A: Absoluut. Sla het document op als PDF (`doc.save("output.pdf")`) nadat de TOC is gegenereerd; het veld wordt automatisch gerenderd.

**V: Moet ik `updateFields()` handmatig aanroepen?**  
A: Wanneer je een `FieldToc` invoegt, werkt Aspose.Words deze bij bij het opslaan, maar het aanroepen van `doc.updateFields()` geeft directe resultaten voor debugging.

## Conclusie
Je hebt geleerd hoe je **paginanummers kunt aanpassen**, **een inhoudsopgave kunt invoegen** en **TOC‑stijlen kunt aanpassen** met Aspose.Words voor Java. Deze technieken stellen je in staat schone, navigeerbare en professioneel opgemaakte documenten te maken die aan elke publicatiestandaard voldoen.

---  

**Laatst bijgewerkt:** 2026-01-03  
**Getest met:** Aspose.Words voor Java (nieuwste release)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}