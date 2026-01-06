---
date: 2026-01-06
description: Leer hoe u voetteksten uit Word‑documenten kunt verwijderen met Aspose.Words
  voor Java, plus hoe u sectie‑einden, pagina‑einden en meer kunt verwijderen.
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Hoe voetteksten uit Word-documenten te verwijderen met Aspose.Words voor Java
url: /nl/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe voetregels uit Word‑documenten te verwijderen met Aspose.Words voor Java

## Introductie tot Aspose.Words voor Java

In deze tutorial ontdek je **hoe je voetregels uit Word**‑bestanden programmatically kunt verwijderen met Aspose.Words voor Java. Of je nu gegenereerde rapporten wilt opschonen, vertrouwelijke informatie wilt verwijderen, of simpelweg een sjabloon wilt opruimen, deze gids leidt je door de meest voorkomende scenario’s voor het verwijderen van inhoud — paginawissels, sectiewissels, voetregels en inhoudsopgaven. Laten we beginnen!

## Snelle antwoorden
- **Kan ik voetregels verwijderen zonder andere inhoud te beïnvloeden?** Ja, de API laat je alleen voetregel‑knopen targeten.
- **Heb ik een licentie nodig om deze voorbeelden uit te voeren?** Een gratis proefversie werkt voor ontwikkeling; een licentie is vereist voor productie.
- **Welke Word‑formaten worden ondersteund?** DOC, DOCX, DOCM en OOXML‑gebaseerde formaten.
- **Is de code compatibel met Java 8 en hoger?** Absoluut, de bibliotheek is Java‑compatibel vanaf versie 8 en hoger.
- **Hoe verwijder ik sectiewissels?** Zie de sectie “Hoe sectiewissels te verwijderen” hieronder.

## Wat betekent “voetregels uit Word verwijderen”?

Het verwijderen van voetregels uit een Word‑document betekent het verwijderen van de `HeaderFooter`‑knopen die onderaan elke pagina verschijnen. Deze bewerking is gebruikelijk wanneer je een schone lay‑out alleen met een koptekst wilt maken of wanneer voetregels gevoelige gegevens bevatten die niet gedeeld mogen worden.

## Waarom Aspose.Words voor Java voor deze taak gebruiken?

Aspose.Words biedt een hoog‑niveau objectmodel dat de complexiteit van het DOCX‑bestandsformaat abstraheert. Je kunt alinea’s, runs, secties en voetregels manipuleren met een paar regels Java‑code, zonder dat Microsoft Word op de server geïnstalleerd hoeft te zijn.

## Vereisten
- Java Development Kit (JDK) 8 of nieuwer.
- Aspose.Words voor Java‑bibliotheek (download van de Aspose‑website).
- Een voorbeeld‑Word‑document (`Document.docx`) geplaatst in een bekende map.

## Paginawissels verwijderen

Paginawissels bepalen de paginering maar moeten soms worden verwijderd. Het volgende fragment scant elke alinea, wist de `PageBreakBefore`‑vlag en verwijdert eventuele expliciete paginawissel‑tekens.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*Pro tip:* Voer dit uit vóór het verwijderen van voetregels als je een één‑pagina‑lay‑out wilt.

## Hoe sectiewissels te verwijderen

Sectiewissels splitsen een document in onafhankelijke secties, elk met eigen kop‑ en voetteksten en pagina‑instellingen. Om secties te combineren en effectief **sectiewissels te verwijderen**, doorloop je de secties in omgekeerde volgorde, voeg je de inhoud van elke eerdere sectie toe aan de laatste, en verwijder je vervolgens de nu lege sectie.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

Deze aanpak behoudt alle inhoud terwijl de structurele onderbreking wordt geëlimineerd.

## Voetregels verwijderen (Primair doel: voetregels uit Word verwijderen)

Voetregels bevatten vaak paginanummers, datums of vertrouwelijke notities. De onderstaande code verwijdert **alle voetregel‑typen** — eerste pagina, primair en zelfs even‑pagina’s — uit elke sectie.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

Na het uitvoeren van dit fragment zal het resulterende document **geen voetregels** meer hebben, waarmee het primaire doel “voetregels uit Word verwijderen” is bereikt.

## Inhoudsopgave verwijderen

Een inhoudsopgave (TOC) wordt opgeslagen als een veld. Om deze te verwijderen, zoek je het TOC‑veld op basis van zijn index en verwijder je het bijbehorende knooppunt.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(De `removeTableOfContents`‑methode maakt deel uit van de Aspose.Words‑voorbeelden en verwijdert het opgegeven TOC‑knooppunt.)*

## Veelvoorkomende problemen & foutopsporing

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| Voetregels verschijnen nog steeds na het uitvoeren van de code | Document bevat **header/footer**‑paren die niet worden benaderd (bijv. ontbrekende `FOOTER_FIRST`) | Loop door alle `HeaderFooterType`‑waarden of controleer op `null` vóór het aanroepen van `remove()`. |
| Paginalay‑out verandert onverwacht na het verwijderen van sectiewissels | Sectiespecifieke pagina‑instellingen (marges, oriëntatie) zijn verloren gegaan | Kopieer de sectie‑instellingen naar de doel‑sectie vóór verwijdering. |
| `ControlChar.PAGE_BREAK` niet verwijderd | Het document gebruikt **sectiewissels** in plaats van paginawissel‑tekens | Gebruik eerst de methode “Hoe sectiewissels te verwijderen”. |

## Veelgestelde vragen

**V: Kan ik alleen specifieke voetregels verwijderen (bijv. alleen de eerste‑pagina‑voetregel)?**  
A: Ja. Haal de voetregel op op basis van zijn type (`FOOTER_FIRST`) en roep `remove()` alleen aan op dat exemplaar.

**V: Hoe verwijder ik sectiewissels zonder de inhoud te combineren?**  
A: Je kunt een `Section`‑knooppunt direct verwijderen als je de inhoud niet hoeft te behouden, maar wees je ervan bewust dat eventuele kop‑/voetteksten die aan die sectie zijn gekoppeld ook verloren gaan.

**V: Is het mogelijk om programmatically te detecteren of een document een TOC bevat voordat je probeert deze te verwijderen?**  
A: Gebruik `doc.getRange().getFields()` en controleer op velden van het type `FieldType.FIELD_TABLE_OF_CONTENTS`.

**V: Ondersteunt Aspose.Words het verwijderen van voetregels uit versleutelde Word‑bestanden?**  
A: Ja, open het document gewoon met het wachtwoord: `new Document(path, new LoadOptions(password))`.

**V: Heeft het verwijderen van voetregels invloed op de paginering van het document?**  
A: Het verwijderen van voetregels verandert de paginanummers niet, tenzij de voetregel zelf een paginanummer‑veld bevat. Als je de paginanummers opnieuw moet nummeren, werk dan de paginanummer‑velden bij.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **voetregels uit Word**‑documenten te verwijderen met Aspose.Words voor Java, inclusief gerelateerde taken zoals het verwijderen van paginawissels, **hoe sectiewissels te verwijderen**, en het strippen van inhoudsopgaven. Door deze fragmenten te gebruiken kun je schone, professionele documenten produceren die zijn afgestemd op de eisen van jouw applicatie.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Laatst bijgewerkt:** 2026-01-06  
**Getest met:** Aspose.Words voor Java 24.12  
**Auteur:** Aspose  

---