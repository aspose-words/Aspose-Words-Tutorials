---
category: general
date: 2026-10-04
description: Voetnootscheiding bewerken in Java met Aspose.Words – leer hoe je de
  voetnootscheiding wijzigt en een aangepast scheidingstekenwoord toevoegt aan Word‑documenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: nl
lastmod: 2026-10-04
og_description: Bewerk de voetnootseparator in Java met Aspose.Words. Deze tutorial
  laat zien hoe je de voetnootseparator wijzigt en een aangepast scheidingsteken invoegt.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Voetnootseparator bewerken in Java – volledige Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: Hoe de voetnootscheiding te bewerken in Java met Aspose.Words
url: /nl/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe voetnootseparator te bewerken in Java met Aspose.Words

Als je de **voetnootseparator** in een Word‑document moet **bewerken**, laat deze gids je precies zien hoe dat in Java kan. Of je nu de **voetnootseparator** wilt wijzigen naar een streepje, een ster, of een **aangepast separator‑woord**, de onderstaande stappen behandelen alles wat je nodig hebt.

Je leert hoe je een `.docx`‑bestand laadt, de speciale separator‑sectie ophaalt, de inhoud wijzigt en het resultaat opslaat. Geen externe scripts of handmatige bewerkingen nodig – alles gebeurt programmatisch met de Aspose.Words for Java‑bibliotheek.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

- Java 17 of hoger geïnstalleerd.
- Maven of Gradle om afhankelijkheden te beheren (het voorbeeld gebruikt Maven).
- Een geldige Aspose.Words for Java‑licentie (of een gratis evaluatiesleutel).
- Een Word‑document dat al voetnoten bevat (de separator bestaat alleen wanneer er voetnoten aanwezig zijn).

## Aspose.Words aan je project toevoegen

Als je Maven gebruikt, voeg dan de volgende afhankelijkheid toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Voor Gradle, voeg toe:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Stap 1: Laad het document dat voetnoten bevat

De eerste stap is het openen van het Word‑bestand dat je wilt aanpassen. Aspose.Words leest het bestand in een `Document`‑object, waarmee je volledige toegang krijgt tot alle delen van het document, inclusief voetnootseparators.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**Waarom dit belangrijk is:** Het laden van het document creëert een in‑memory‑representatie, zodat je veilig elk knooppunt kunt wijzigen zonder het originele bestand aan te raken totdat je expliciet opslaat.

## Stap 2: Haal de voetnootseparator‑sectie op

Word slaat de voetnootseparator op als een speciaal `Separator`‑knooppunt. Aspose.Words biedt de `getFootnoteSeparator()`‑methode om deze direct te verkrijgen.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Pro‑tip:** Het separator‑knooppunt bestaat alleen als het document al minstens één voetnoot heeft. Als je een document zonder voetnoten probeert te bewerken, retourneert `getFootnoteSeparator()` `null`; controleer daarom altijd op deze situatie.

## Stap 3: Voeg een aangepast separator‑woord toe

Nu kun je het uiterlijk van de separator wijzigen. In dit voorbeeld vervangen we de standaardlijn door een em‑dash (`—`). Je kunt in plaats daarvan elk **aangepast separator‑woord** invoegen, zoals `"NOTE:"` of `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### Wat de code doet

1. **`clearChildren()`** verwijdert eventuele bestaande runs, zodat de separator alleen de door jou opgegeven tekst bevat.
2. **`new Run(document, "—")`** maakt een tekstknooppunt aan met de gewenste separator. Het `Run`‑object respecteert de stijl van het document, zodat de separator de opmaak van de oorspronkelijke voetnootseparator erft.
3. **`appendChild(customRun)`** voegt de nieuwe run toe aan de separator‑paragraaf.

Je kunt ook opmaak toepassen op de run, bijvoorbeeld:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Stap 4: Sla het gewijzigde document op

Na het bewerken van de separator schrijf je het document terug naar de schijf. Kies een nieuwe bestandsnaam om het originele bestand onaangeroerd te laten.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**Resultaatverificatie:** Open `ModifiedNotes.docx` in Microsoft Word. De voetnootseparator zou nu de aangepaste streep (of welk woord je ook hebt gekozen) moeten tonen in plaats van de standaardlijn.

## Meerdere voetnootseparators verwerken

Word ondersteunt drie speciale separator‑typen:

| Separator type | Method |
|----------------|--------|
| Footnote separator | `getFootnoteSeparator()` |
| Footnote continuation separator | `getFootnoteContinuationSeparator()` |
| Footnote separator for the first page | `getFootnoteSeparatorForFirstPage()` |

Als je ze allemaal wilt bewerken, herhaal dan **Stap 2** en **Stap 3** voor elke methode. Voorbeeld:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Issue | Cause | Fix |
|-------|-------|-----|
| No separator appears after saving | Document had no footnotes → separator node is `null` | Add at least one footnote before editing, or create a dummy footnote programmatically. |
| Separator shows extra spaces | Existing runs were not cleared | Call `clearChildren()` before appending the new run. |
| Formatting looks different | Run inherits style from the original separator | Explicitly set font properties on the `Run` if you need a specific appearance. |

## Volledig werkend voorbeeld

Alle onderdelen samengevoegd, hier is een zelfstandige Java‑klasse die je kunt kopiëren, compileren en uitvoeren:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

Voer het programma uit en open vervolgens `ModifiedNotes.docx` om te bevestigen dat de separator is bijgewerkt.

## Conclusie

Je weet nu hoe je de **voetnootseparator** in een Word‑document kunt **bewerken** met Java en Aspose.Words. De tutorial besprak het laden van een document, het ophalen van het speciale separator‑knooppunt, het invoegen van een **aangepast separator‑woord**, en het opslaan van het resultaat. Door deze stappen te volgen kun je ook de **voetnootseparator** voor voortzettings‑secties of eerste‑pagina‑voetnoten **wijzigen**.

Vervolgens kun je verkennen:

- Verschillende separators toevoegen voor eerste‑pagina‑voetnoten (`getFootnoteSeparatorForFirstPage()`).
- Programma­matig voetnoten aanmaken wanneer er geen bestaan.
- Aspose.Words gebruiken om voetnoottekst te stylen (lettertypen, kleuren, inspringing).

Voel je vrij om met andere tekens of woorden te experimenteren om ze aan te laten sluiten bij de branding van je document. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Documentstijlseparator invoegen in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Paragraafstijlseparator ophalen in Word‑document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Hoe Word‑documenten te laden met Aspose.Words Java: uitgebreide gids](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}