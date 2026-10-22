---
category: general
date: 2026-07-20
description: Verander eenvoudig de voetnootafstand in DOCX‑bestanden. Leer hoe je
  de afstand instelt, de voetnootscheiding aanpast en de regelafstand van alinea’s
  instelt met Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: nl
lastmod: 2026-07-20
og_description: Verander snel de voetnootafstand in DOCX‑bestanden. Deze gids laat
  zien hoe je de afstand instelt, de voetnootscheiding aanpast en de regelafstand
  van alinea’s in Java aanpast.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Voetnootafstand wijzigen in DOCX – Stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Voetnootafstand wijzigen in DOCX – Complete gids
url: /nl/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Voetnootafstand wijzigen in DOCX – Complete gids

Heb je ooit moeten **voetnootafstand wijzigen** in een Word‑document, maar wist je niet waar je moest beginnen? Je bent niet de enige. Of je nu een scriptie perfectioneert of een contract aanpast, het precies goed krijgen van die voetnootseparator kan een groot verschil maken.  

In deze tutorial lopen we stap voor stap door **hoe je de afstand instelt**, de voetnootseparator aanpast, en **de alinealijnafstand instelt** met behulp van Java‑gebaseerde bibliotheken. Aan het einde heb je een kant‑klaar voorbeeld dat je in elk project kunt gebruiken.

## Wat je nodig hebt

- Java 17 of nieuwer (de code maakt gebruik van de moderne taalfeatures)
- Maven of Gradle voor afhankelijkheidsbeheer
- Een DOCX‑bestand met minstens één voetnoot (of je kunt er zelf één handmatig maken)
- De **Aspose.Words for Java**‑bibliotheek (of een compatibele API; we gebruiken Aspose in het voorbeeld)

Dat is alles—geen zware frameworks, alleen plain Java en één bibliotheek.

![Change footnote spacing in DOCX example](/images/footnote-spacing.png){alt="Voorbeeld van voetnootafstand wijzigen in DOCX"}

## Stap 1: Het DOCX‑document laden (Voetnootafstand wijzigen)

Het eerste wat je moet doen is het Word‑bestand openen. Dit levert een `Document`‑object op dat je kunt manipuleren.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Waarom dit belangrijk is*: Het laden van het document is het startpunt voor **voetnootafstand wijzigen**. Zonder een `Document`‑instantie kun je de voetnootseparator of enige alinea‑formaten niet bereiken.

## Stap 2: De voetnootseparator ophalen en aanpassen (Voetnootseparator aanpassen)

Een voetnootseparator is een verborgen alinea die tussen de hoofdtekst en de voetnootlijst zit. Om de regelafstand ervan te wijzigen, moet je die alinea ophalen en het formaat aanpassen.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Hoe dit het probleem oplost

- **De voetnootseparator ophalen** – dit is het onderdeel dat je daadwerkelijk wilt aanpassen, wat voldoet aan de *voetnootseparator aanpassen* eis.
- **Regelafstand instellen** – `setLineSpacing(12.0)` beantwoordt direct *hoe je de afstand instelt* voor die verborgen alinea.
- **Afhandeling van randgevallen** – als het document om welke reden dan ook geen separator heeft, maken we er direct één aan, waardoor een `NullPointerException` wordt voorkomen.

## Stap 3: De wijziging verifiëren en opslaan (Alinealijnafstand instellen)

Nadat je de separator hebt aangepast, wil je zeker weten dat de wijziging is doorgevoerd. Het openen van het opgeslagen bestand in Word toont de nieuwe afstand, maar je kunt het ook programmatically controleren.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Voeg een aanroep toe aan `verifySpacing(doc);` direct vóór `doc.save(...)` in `main`. Wanneer je het programma uitvoert, zou je moeten zien:

```
Current footnote separator line spacing: 12.0
```

Dat bevestigt dat de **regelafstand wijzigen docx**‑operatie geslaagd is.

## Veelvoorkomende valkuilen & pro‑tips

- **Valkuil**: Het gebruik van `setLineSpacing` met een waarde die eruitziet als “12”, maar wordt geïnterpreteerd als “12 pt” versus “12 regels”. Aspose verwacht punten, dus 12 betekent 12 pt. Voor dubbele regelafstand gebruik `24.0`.
- **Pro‑tip**: Als je een consistente weergave wilt over alle voetnoottypen (separator, voortzettingsseparator, enz.), herhaal dan dezelfde stappen voor `doc.getFootnoteContinuationSeparator()` en `doc.getFootnoteContinuationNotice()`.
- **Valkuil**: Vergeten om `save()` aan te roepen na aanpassingen. Het document in het geheugen verandert, maar het bestand op schijf blijft hetzelfde.
- **Pro‑tip**: Combineer afstandsaanpassingen met stijl‑updates (`ParagraphStyle`) voor een volledig gepolijste voetnootsectie.

## Volledig werkend voorbeeld (Alle stappen in één bestand)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Kopieer de bovenstaande code naar een nieuwe Java‑klasse, voeg de Aspose.Words Maven‑dependency toe, en voer het uit. Je `output.docx` zal nu de regelafstand van de voetnootseparator hebben ingesteld op **12 pt**, waardoor je effectief **voetnootafstand wijzigt**.

### Maven‑dependency

Voeg dit fragment toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Als je de voorkeur geeft aan Gradle, is het equivalent:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Conclusie

Je hebt zojuist geleerd hoe je **voetnootafstand wijzigt** in een DOCX‑bestand met Java. Door het document te laden, de **voetnootseparator** op te halen en **alinea‑lijnafstand in te stellen**, krijg je precieze controle over de weergave van voetnoten.  

Vanaf hier kun je gerelateerde aanpassingen verkennen, zoals het wijzigen van de voetnoot‑tekststijl, het toevoegen van aangepaste separators, of zelfs het automatiseren van bulk‑updates over meerdere documenten.  

Heb je meer vragen over **voetnootseparator aanpassen** of andere Word‑automatiseringstaken? Laat een reactie achter, en happy coding!

## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Asian alinea‑spatiëring en inspringingen wijzigen in Word‑document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Asian alinea‑spatiëring en inspringingen wijzigen](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Asian alinea‑spatiëring en inspringingen wijzigen](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}