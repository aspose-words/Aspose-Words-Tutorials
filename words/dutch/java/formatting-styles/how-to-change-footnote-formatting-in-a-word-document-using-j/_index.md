---
category: general
date: 2026-09-11
description: Leer hoe u de opmaak van voetnoten in Java met Aspose.Words kunt wijzigen.
  Deze gids legt uit hoe u een voetnoot bewerkt, de voetnootstijl bijwerkt en de voetnootscheiding
  aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: nl
lastmod: 2026-09-11
og_description: Wijzig de opmaak van voetnoten in Java met Aspose.Words. Volg deze
  volledige gids om voetnoten te bewerken, de voetnootstijl bij te werken en de voetnootscheiding
  aan te passen.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Voetnootopmaak wijzigen in Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Hoe de opmaak van voetnoten te wijzigen in een Word‑document met Java
url: /nl/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe de opmaak van voetnoten te wijzigen in een Word‑document met Java

Als je de **voetnootopmaak** in een Word‑document moet **wijzigen**, leidt deze tutorial je stap voor stap door het proces met behulp van Aspose.Words for Java. Of je nu een publicatie‑pipeline bouwt of gewoon de **hoe voetnoten te bewerken** uiterlijk programmatisch moet aanpassen, de onderstaande oplossing behandelt alles van het laden van het bestand tot het opslaan van de bijgewerkte versie.

Je leert hoe je de **voetnootstijl bijwerkt**, de voetnootscheiding vet maakt, en zelfs **eigenschappen van de voetnootscheiding** zoals lettergrootte of kleur **wijzigt**. De gids gaat ervan uit dat je basiskennis van Java hebt en een werkende Aspose.Words for Java‑licentie.

## Vereisten

* Java 17 of nieuwer geïnstalleerd.
* Aspose.Words for Java (versie 23.12 of later) toegevoegd aan de classpath van je project.
* Een Word‑document (`input.docx`) dat minstens één voetnoot bevat.
* Een IDE of build‑tool (Maven/Gradle) om de code te compileren en uit te voeren.

Als je niet zeker weet hoe je Aspose.Words aan een Maven‑project toevoegt, voeg dan de volgende afhankelijkheid toe in je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Voetnootopmaak wijzigen met Aspose.Words for Java

De kern van de oplossing is een kort Java‑programma dat een document laadt, de alinea van de voetnootscheiding benadert, de opmaak wijzigt en het resultaat opslaat. De code is volledig zelfstandig, zodat je deze kunt kopiëren naar een nieuwe klasse en direct kunt uitvoeren.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Waarom elke stap belangrijk is

* **Het laden van het document** (`new Document`) creëert een in‑memory representatie die Aspose.Words kan manipuleren.  
* **Het ophalen van de voetnootscheiding** (`getFootnoteSeparator`) geeft je directe toegang tot de alinea die voetnoten van de hoofdtekst scheidt. Dit is het element dat je moet targeten wanneer je de **voetnootopmaak wilt wijzigen**.  
* **Het formatteren van de run** (`setBold`, `setItalic`, `setSize`, `setColor`) toont hoe je de eigenschappen van de **voetnootscheiding** kunt **wijzigen**. Je kunt hier extra lettertype‑attributen toevoegen, zoals onderstrepen of markeren, om de weergave volledig te beheersen.  
* **Het opslaan van het document** schrijft de wijzigingen terug naar de schijf, waardoor een nieuw bestand (`output.docx`) ontstaat dat de bijgewerkte voetnootstijl weergeeft.

> **Pro tip:** Als je bron‑document een aangepaste voetnootscheiding gebruikt die meerdere runs bevat (bijv. een combinatie van symbolen), doorloop dan `footnoteSeparator.getRuns()` en pas dezelfde `Font`‑instellingen toe op elke run voor consistente opmaak.

## Hoe de voetnootscheiding programmatisch te bewerken

Soms moet je niet alleen de scheiding bewerken, maar ook de tekst van de voetnoot zelf. Met dezelfde API kun je elke voetnoot benaderen, de alinea‑opmaak aanpassen of de nummeringsstijl wijzigen.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

De bovenstaande code laat zien **hoe je voetnoot‑inhoud** kunt bewerken nadat je de **voetnootopmaak** van de scheiding al hebt **gewijzigd**. Door te itereren over `doc.getFootnotes()` zorg je ervoor dat elke voetnoot dezelfde stijl overneemt, wat essentieel is voor een professioneel uitziend document.

## Voetnootstijl bijwerken voor een consistente documentuiterlijk

Als je liever met stijlen werkt in plaats van individuele runs, stelt Aspose.Words je in staat een `Style`‑object te maken of te wijzigen en dit vervolgens toe te passen op voetnoten en de scheiding. Deze aanpak is handig wanneer je de **voetnootstijl wilt bijwerken** in veel documenten.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Het gebruik van een toegewijde stijl maakt toekomstig onderhoud eenvoudiger—wijzig de stijl één keer, en elke voetnoot en scheiding wordt automatisch bijgewerkt. Deze techniek is de aanbevolen manier om de **voetnootstijl bij te werken** in grootschalige publicatieworkflows.

## De voetnootscheiding aanpassen aan je branding

Merkrichtlijnen bepalen soms dat de voetnootscheiding een specifiek teken moet gebruiken (bijv. een sterretje) of een aangepaste lijn. Aspose.Words maakt het mogelijk om de standaard scheidingsinhoud volledig te vervangen.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

De bovenstaande code **wijzigt de voetnootscheiding** door eventuele bestaande runs te wissen en een nieuwe run in te voegen met de gewenste tekst en opmaak. Je kunt ook Unicode‑tekens gebruiken zoals `\u2022` (bullet) of `\u2014` (em dash) om het exacte visuele effect te bereiken dat je merk vereist.

## Verwacht resultaat

Na het uitvoeren van het programma:

* De voetnootscheiding in `output.docx` verschijnt **vet**, **cursief**, 10 pt, en grijs (of welke kleur je ook hebt ingesteld).  
* Alle voetnoot‑alinea's nemen de door jou gedefinieerde stijl over, waardoor een uniform uiterlijk door het hele document ontstaat.  
* Als je de scheidingstekst hebt vervangen, is de nieuwe aangepaste lijn precies zichtbaar waar de oorspronkelijke lijn stond.

Open het resulterende bestand in Microsoft Word of LibreOffice Writer om de wijzigingen te verifiëren. Je zou de bijgewerkte scheiding direct boven de eerste voetnoot moeten zien, en de voetnoottekst moet de eventuele stijlwijzigingen die je hebt toegepast weergeven.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` veroorzaakt een uitzondering | Sommige documenten hebben een lege scheidingsalinea. | Voeg een defensieve controle toe en maak een run aan als er geen bestaat (zie het code‑voorbeeld). |
| Lettertype‑wijzigingen zijn niet zichtbaar | Het document gebruikt een thema dat directe opmaak overschrijft. | Stel `font.setThemeFont(null)` in of pas een aangepaste stijl toe in plaats van directe opmaak. |
| Opgeslagen bestand weerspiegelt geen wijzigingen | Het originele bestand is nog geopend in Word, waardoor het uitvoerpad vergrendeld is. | Sluit alle exemplaren van het bestand voordat je het programma uitvoert, of

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Woorden verwerken met voetnoot en eindnoot](/words/english/net/working-with-footnote-and-endnote/)
- [Voetnoot‑ en eindnoot‑positie instellen](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Hoe Aspose.Words versie‑info weer te geven in Java: Een uitgebreide gids](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}