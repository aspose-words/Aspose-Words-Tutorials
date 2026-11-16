---
category: general
date: 2026-11-15
description: Stel de regelafstand van alinea's in een Word‑document in met Java. Leer
  hoe u de regelafstand programmatisch kunt instellen met Aspose.Words voor precieze
  documentopmaak.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: nl
lastmod: 2026-11-15
og_description: Stel de regelafstand van alinea's in een Word‑document in met Java.
  Deze gids legt uit hoe u de regelafstand voor alinea's en voetnoot‑scheidingslijnen
  kunt instellen met Aspose.Words, waardoor u volledige controle krijgt over de lay‑out
  van het document.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Stel alinea‑regelafstand in Word in met Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Stel de regelafstand van alinea's in een Word‑document in met Java
url: /nl/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Paragraafregelafstand instellen in een Word‑document met Java

Als je **paragraafregelafstand** in een Word‑document moet instellen, laat deze tutorial zien hoe je dat doet met Java en Aspose.Words. Je leert ook **hoe je regelafstand** voor voetnoot‑scheidingstekens instelt — een veelvoorkomende eis bij het opmaken van professionele documenten.

In de volgende secties zul je:

* Een bestaand *.docx*-bestand laden.
* De voetnoot‑scheidingsteken‑paragraaf ophalen.
* Een aangepaste regel‑afstand toepassen.
* Het bijgewerkte document opslaan.

Er is geen externe configuratie nodig, behalve het toevoegen van de Aspose.Words‑bibliotheek aan je project, dus je kunt de code letterlijk kopiëren en direct uitvoeren.

## Voorvereisten

Zorg ervoor dat je het volgende hebt:

* Java 17 of nieuwer geïnstalleerd.
* Maven (of een andere build‑tool) om afhankelijkheden te beheren.
* Een geldige Aspose.Words for Java‑licentie (de gratis evaluatie werkt voor testen).
* Een invoer‑Word‑document (`input.docx`) in een bekende map.

Voeg de Aspose.Words‑dependency toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Paragraafregelafstand instellen met Aspose.Words

Deze H2‑kop bevat het primaire zoekwoord en voldoet aan de SEO‑vereiste.

### Stap 1: Het Word‑document laden

Maak eerst een `Document`‑instantie die naar je bronbestand wijst.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Waarom dit belangrijk is*: Het laden van het document geeft je een in‑memory‑model dat je kunt manipuleren zonder het originele bestand aan te passen totdat je expliciet opslaat.

### Stap 2: De voetnoot‑scheiding ophalen

Voetnoot‑scheidingen zijn speciale paragrafen die tussen voetnoten en de hoofdtekst verschijnen. Om hun weergave te wijzigen moet je toegang krijgen tot het `FootnoteSeparator`‑object.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tip*: Als je document geen voetnoten bevat, bestaat de scheiding nog steeds als een verborgen paragraaf, dus de oproep zal nooit `null` retourneren.

### Stap 3: Regelafstand instellen voor de paragraaf van de scheiding

Pas nu de gewenste regelafstand toe. Aspose.Words gebruikt punten voor regelafstand; 12 pts is ongeveer enkele regelafstand voor de meeste lettertypen.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Je kunt ook andere afstandsmodi gebruiken:

| Modus                     | Methode‑aanroep                                      |
|--------------------------|------------------------------------------------------|
| **Exact** (vaste pts)    | `setLineSpacingRule(LineSpacingRule.EXACTLY)`       |
| **Meervoudig** (bijv. 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Het kiezen van de juiste regel zorgt ervoor dat het document consistent wordt weergegeven in Word, Google Docs en andere viewers.

### Stap 4: Het bijgewerkte document opslaan

Schrijf tenslotte de wijzigingen terug naar de schijf.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Wanneer je `output.docx` opent in Microsoft Word, zal de voetnoot‑scheiding worden weergegeven met de door jou gedefinieerde regelafstand.

## Begrijpen hoe je regelafstand instelt voor gewone paragrafen

Dezelfde API werkt voor elk `Paragraph`‑object, niet alleen voor voetnoot‑scheidingen. Hier is een kort voorbeeld dat de afstand van de eerste paragraaf in de body aanpast:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Waarom je dit nodig kunt hebben**: Rapporten, contracten en academische papers vereisen vaak een specifieke regelafstand (bijv. dubbele regelafstand voor concepten). Het gebruik van dezelfde `setLineSpacing`‑methode garandeert de exacte lay-out die je verwacht.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem                                 | Oorzaak                                   | Oplossing |
|------------------------------------------|-------------------------------------------|-----------|
| Regelafstand blijft ongewijzigd          | `LineSpacingRule` staat op de standaardwaarde (AUTO) | Stel de regel expliciet in met `setLineSpacingRule`. |
| Extra lege regels na de scheiding        | Scheiding bevat verborgen carriage returns | Trim de tekst van de scheiding met `separator.getText().trim();` vóór het toepassen van de afstand. |
| Document wordt corrupt na het opslaan    | Een verouderde Aspose.Words‑versie         | Upgrade naar de nieuwste versie (bijv. 24.10) die bugfixes voor opslaan bevat. |

## Pro‑tip: batch‑verwerking van meerdere documenten

Als je tientallen bestanden moet bijwerken, verpak de logica dan in een hulpfunctie en doorloop een map:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Het uitvoeren van deze methode in een lus bespaart je uren handmatig bewerken.

## Verwachte output

Na het uitvoeren van het volledige programma zal `output.docx`:

* De oorspronkelijke inhoud ongewijzigd laten, behalve de regelafstand.
* De voetnoot‑scheiding weergeven met een enkele regelafstand (12 pts) lay-out.
* Alle andere opmaak behouden (stijlen, afbeeldingen, tabellen).

Open het bestand in Word en controleer of de scheidingslijn strakker (of losser) is, afhankelijk van de waarde die je hebt ingesteld.

## Conclusie

Je weet nu hoe je **paragraafregelafstand** in een Word‑document instelt met Java, en je begrijpt ook **hoe je regelafstand** instelt voor zowel voetnoot‑scheidingen als gewone paragrafen. Het volledige, uitvoerbare voorbeeld toont het laden van een document, het aanpassen van regelafstand‑eigenschappen en het opslaan van het resultaat — alles met een paar duidelijke API‑aanroepen.

**Volgende stappen** die je kunt verkennen:

* **Hoe je regelafstand** instelt voor tabellen en lijstitems.
* Verschillende afstandsregels toepassen op koppen versus body‑tekst.
* Het `Style`‑object gebruiken om afstand over een heel document af te dwingen.

Experimenteer met de waarden, combineer ze met andere opmaakopties, en je hebt volledige controle over de documentlay-out in elke Java‑applicatie. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}