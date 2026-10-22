---
category: general
date: 2026-08-07
description: Hoe voetnoten te bewerken in Java met Aspose.Words – een aangepaste streep
  toevoegen, de voetnootlijn wijzigen en alinea‑uitlijning instellen voor gepolijste
  documenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: nl
lastmod: 2026-08-07
og_description: Hoe bewerk je een voetnoot in Java met Aspose.Words. Leer hoe je een
  aangepast streepje toevoegt, de voetnootlijn wijzigt en de alinea‑uitlijning in
  slechts een paar stappen instelt.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Hoe voetnoot bewerken in Java – streepje toevoegen, regel wijzigen, uitlijning
  instellen
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Hoe bewerk je een voetnoot in Java met Aspose.Words
url: /nl/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe voetnoot bewerken in Java met Aspose.Words

Als je **hoe voetnoot te bewerken** in een Word‑document met Java nodig hebt, laat deze gids de volledige workflow zien. Je leert een aangepaste streep toe te voegen, de voetnootlijn te wijzigen en de alinea‑uitlijning in te stellen zodat de voetnootscheiding er professioneel uitziet.

Het bewerken van voetnoten is een veelvoorkomende eis bij het opstellen van juridische contracten, academische papers of marketingbrochures. De onderstaande stappen behandelen alles wat je nodig hebt – van het laden van het document tot het opslaan van het uiteindelijke bestand – zonder extra tools.

## Voorvereisten

Voordat je begint, zorg dat je het volgende hebt:

* Java 17 of nieuwer geïnstalleerd.
* Aspose.Words for Java (nieuwste versie) toegevoegd aan de classpath van je project.
* Een DOCX‑bestand (`input.docx`) dat minstens één voetnoot bevat.

Deze items garanderen dat de code zonder runtime‑fouten draait.

## Hoe voetnootscheiding en -lijn bewerken

De voetnootscheiding is de alinea die verschijnt tussen de hoofdtekst en de lijst met voetnoten. Het wijzigen van het uiterlijk verbetert de leesbaarheid en past bij de huisstijl.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Waarom elke regel belangrijk is

1. **Document laden** – `new Document(...)` leest het DOCX‑bestand in het geheugen, waardoor je toegang krijgt tot al zijn knooppunten.
2. **De scheiding ophalen** – `getFootnoteSeparator()` retourneert de speciale alinea die Aspose.Words als de voetnootlijn beschouwt. Dit object is de enige plek waar je de scheiding veilig kunt aanpassen.
3. **Alinea‑uitlijning instellen** – `setAlignment(ParagraphAlignment.CENTER)` wijzigt de uitlijning van de lijn. Het trefwoord *set paragraph alignment* wordt direct op de scheiding toegepast, waardoor een gecentreerde streep ontstaat.
4. **Een aangepaste streep toevoegen** – Door bestaande runs te wissen en een nieuwe `Run` met het em‑dash‑teken (`—`) toe te voegen, bereik je het *add custom dash*-effect terwijl je ook *change footnote line* naar de gewenste stijl wijzigt.
5. **Document opslaan** – `doc.save(...)` schrijft de wijzigingen terug naar de schijf, waardoor een uitvoerbestand ontstaat dat alle aanpassingen weerspiegelt.

## Aangepaste streep toevoegen aan de voetnootscheiding

De code in **Stap 4** demonstreert de *add custom dash*-techniek. Je kunt het em‑dash vervangen door een willekeurige tekenreeks, zoals `"***"` of `"---"`, om aan de visuele taal van je document te voldoen.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Het gebruik van een aangepaste streep is vooral handig wanneer de standaard dunne lijn niet voldoet aan de merkrichtlijnen.

## Stijl van de voetnootlijn wijzigen

Als je een doorlopende lijn in plaats van een streep wilt, kun je een Unicode‑teken voor box‑drawing of een herhaalde onderstreping invoegen.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

De *change footnote line*-stap werkt op dezelfde manier, ongeacht welk teken je kiest, omdat de scheidingsalinea simpelweg de tekst die hij bevat weergeeft.

## Alinea‑uitlijning instellen voor voetnootscheiding

De *set paragraph alignment*-bewerking is niet beperkt tot centreren. Je kunt links, rechts of uitvullen uitlijnen volgens je lay-outbehoeften.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

De scheiding naar rechts uitlijnen kan nuttig zijn voor documenten die rechts uitgelijnde voetnoten gebruiken, zoals tweetalige publicaties.

## Volledig, uitvoerbaar voorbeeld

Hieronder vind je het complete programma dat alle concepten combineert – een document laden, de voetnootscheiding bewerken, een aangepaste streep toevoegen, de lijnstijl wijzigen en de uitlijning instellen.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Verwacht resultaat:** Het `output.docx`‑bestand bevat een gecentreerde em‑dash waar vroeger de dunne lijn stond. Alle voetnoten blijven ongewijzigd en de lay-out van het document weerspiegelt de nieuwe scheidingsstijl.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Reden | Oplossing |
|----------|-------|-----------|
| Scheiding niet gevonden | Document heeft geen voetnoten of gebruikt een aangepaste voetnootstijl | Zorg ervoor dat het bron‑DOCX minstens één voetnoot bevat voordat `getFootnoteSeparator()` wordt aangeroepen |
| Aangepaste streep niet zichtbaar | Lettertype ondersteunt het gekozen teken niet | Gebruik een Unicode‑teken dat wordt ondersteund door het standaardlettertype van het document, of embed een compatibel lettertype |
| Uitlijning lijkt onveranderd | Alinea‑opmaak wordt later in de code overschreven | Pas uitlijning **na** eventuele andere opmaak‑aanroepen toe die deze kunnen resetten |

Door deze punten aan te pakken voorkom je runtime‑fouten en garandeer je dat het *how to edit footnote*-proces betrouwbaar werkt.

## Volgende stappen

Nu je weet **hoe voetnoot te bewerken** elementen, kun je gerelateerde taken verkennen:

* **Aangepaste voetnootreferentiestijl toevoegen** – wijzig `FootnoteReference`‑knooppunten om nummering of symbolen te veranderen.
* **Programma­matig nieuwe voetnoten invoegen** – gebruik `DocumentBuilder.insertFootnote()` voor dynamische inhoud.
* **Voorwaardelijke opmaak toepassen** – wijzig de weergave van voetnoten op basis van alinea‑stijl of inhoudslengte.

Elk van deze uitbreidingen bouwt voort op dezelfde API‑interface die je gebruikte voor *add custom dash*, *change footnote line* en *set paragraph alignment*.

---

*Happy coding! Als de tutorial je heeft geholpen de voetnootbewerking onder de knie te krijgen, deel hem dan met je team of lever een pull‑request in om het voorbeeld verder te verbeteren.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies te beheersen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Voetnoot- en eindnootpositie instellen](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hoe LoadOptions in te stellen in Aspose.Words voor Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}