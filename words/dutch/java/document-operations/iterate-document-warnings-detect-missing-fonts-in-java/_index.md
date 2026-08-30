---
category: general
date: 2026-04-28
description: Itereer documentwaarschuwingen in een Word‑bestand om ontbrekende lettertypen
  te detecteren, haal de namen van de ontbrekende lettertypen op en druk de details
  van de ontbrekende lettertypen af met Aspose.Words voor Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: nl
og_description: Itereer door documentwaarschuwingen om ontbrekende lettertypen te
  vinden, haal de namen van ontbrekende lettertypen op en print de details van ontbrekende
  lettertypen met een volledig Java‑voorbeeld.
og_title: 'Itereer documentwaarschuwingen: detecteer ontbrekende lettertypen in Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Itereer documentwaarschuwingen: Detecteer ontbrekende lettertypen in Java'
url: /nl/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Documentwaarschuwingen itereren – Ontbrekende lettertypen detecteren in Java

Heb je ooit **documentwaarschuwingen moeten itereren** bij het openen van een Word‑bestand en je afgevraagd welke lettertypen ontbreken? Je bent niet de enige. Ontbrekende lettertypen kunnen de uitstraling van een rapport verpesten, en zonder een manier om ze te vinden kun je een document leveren dat er totaal anders uitziet dan het origineel.  

In deze tutorial laten we je zien hoe je **ontbrekende lettertypen kunt detecteren** door een Word‑document te laden, de waarschuwingen te itereren, de namen van de ontbrekende lettertypen op te halen en uiteindelijk de informatie over de ontbrekende lettertypen af te drukken – alles met Aspose.Words for Java.  

We behandelen alles vanaf de allereerste regel code tot de verwachte console‑output, zodat je nu meteen een werkende oplossing kunt kopiëren‑plakken in je project. Geen extra documentatie nodig.

## Voorwaarden

- Java 8 of nieuwer geïnstalleerd.  
- Aspose.Words for Java‑bibliotheek (de nieuwste versie op 2026‑04‑28).  
- Een Word‑bestand dat mogelijk lettertypen bevat die niet op je machine zijn geïnstalleerd (bijv. `doc-with-missing-font.docx`).

Als je dit al hebt, prima – je bent klaar om **word document te laden** en te beginnen met itereren.

## Stap 1 – Word‑document laden met standaardopties

Voordat we **documentwaarschuwingen kunnen itereren**, moet het bestand in het geheugen worden geladen. Aspose.Words maakt dit mogelijk met één enkele constructor‑aanroep. Het gebruik van de standaard `LoadOptions` is meestal voldoende, maar we laten de expliciete creatie zien voor de duidelijkheid.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Waarom dit belangrijk is:**  
> Het laden van het document zorgt ervoor dat Aspose.Words het bestand scant op bronnen die het niet kan resolven, zoals lettertypen die lokaal niet geïnstalleerd zijn. Deze problemen worden opgeslagen als **waarschuwingen**, die we in de volgende stap **documentwaarschuwingen gaan itereren**.

## Stap 2 – Documentwaarschuwingen itereren om lettertype‑problemen te vinden

Nu volgt het hart van de oplossing: we lopen door elke waarschuwing die de bibliotheek heeft verzameld tijdens het laden. De `WarningInfo`‑objecten vertellen ons wat er mis ging, en we kunnen filteren op `FontSubstitutionWarning` om **ontbrekende lettertypen te detecteren**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro‑tip:** De `instanceof`‑controle zorgt ervoor dat we alleen waarschuwingen die met lettertypen te maken hebben afhandelen, en negeren we andere, zoals problemen met het laden van afbeeldingen. Dit maakt de lus efficiënt en houdt de output gericht op de lettertypen waarvoor je daadwerkelijk **ontbrekende lettertype‑informatie wilt ophalen**.

### Verwachte console‑output

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Als het document geen ontbrekende lettertypen bevat, eindigt de lus stilletjes – er is niets om **ontbrekend lettertype af te drukken**.

## Stap 3 – Waarom niet gewoon een uitzondering vangen?

Je vraagt je misschien af: “Waarom niet de `new Document(...)`‑aanroep in een try‑catch plaatsen en op een uitzondering zoeken?” Het antwoord is tweeledig:

1. **Gedetailleerde informatie:** Exceptions vertellen alleen dat er iets is mislukt. Waarschuwingen geven de exacte lettertype‑naam en de fallback die Aspose.Words heeft gekozen.  
2. **Niet‑fatale problemen:** Ontbrekende lettertypen zijn meestal niet‑fatale issues; het document wordt nog steeds geladen, maar de visuele nauwkeurigheid lijdt eronder. Door **documentwaarschuwingen te itereren** behoud je de mogelijkheid om de rest van het bestand te verwerken.

## Stap 4 – Voorbeeld uitbreiden: ontbrekende lettertypen verzamelen in een lijst

Soms heb je de ontbrekende lettertypen nodig voor verdere verwerking – bijvoorbeeld om ze in te sluiten of om een gebruiker via de UI te waarschuwen. Hier is een snelle aanpassing die de namen verzamelt in een `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Nu heb je een nette manier om **ontbrekende lettertype‑gegevens** programmatisch op te halen, die je kunt doorgeven aan een rapportagemodule of een wizard voor het installeren van lettertypen.

## Stap 5 – Praktische overwegingen

- **Meerdere substituties:** Eén ontbrekend lettertype kan in verschillende delen van het document door verschillende lettertypen worden vervangen. De waarschuwingslijst bevat elke gebeurtenis, dus je kunt dubbele vermeldingen van ontbrekende lettertypen zien.  
- **Prestaties:** Het laden van zeer grote documenten kan duizenden waarschuwingen genereren. Als je alleen geïnteresseerd bent in lettertypen, filter dan vroeg, zoals hierboven getoond, om de lus snel te houden.  
- **Cross‑platform lettertypen:** Op Linux is het standaard substitutie‑lettertype vaak *Liberation Sans*. Op Windows kan dit *Arial* zijn. Het kennen van de fallback helpt je beslissen of je aangepaste lettertypen mee moet leveren met je applicatie.

## Stap 6 – Visuele hulp

Hieronder zie je een screenshot van de console‑output (alt‑tekst bevat het primaire trefwoord voor SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt‑tekst:* *voorbeeld van documentwaarschuwingen die ontbrekende lettertypen en vervangingsdetails weergeven.*

## Conclusie

Je hebt zojuist geleerd hoe je **documentwaarschuwingen kunt itereren** in Aspose.Words for Java, **ontbrekende lettertypen kunt detecteren**, **word document veilig kunt laden**, **ontbrekende lettertype‑informatie kunt ophalen**, en **ontbrekende lettertypen kunt afdrukken** naar de console. De volledige code‑snippet werkt direct, en je kunt hem aanpassen om naar een bestand te loggen, een UI‑dialoog te tonen, of zelfs de ontbrekende lettertypen automatisch in te sluiten.

Vervolgens kun je onderzoeken hoe je **word document kunt laden** met aangepaste lettertype‑bronnen (bijv. een map met bedrijfslettertypen) of hoe je ontbrekende lettertypen direct in het bestand kunt insluiten om de lay‑out op verschillende machines te behouden. Beide onderwerpen bouwen logisch voort op wat we hier hebben behandeld.

Veel programmeerplezier, en moge je PDF‑bestanden er altijd precies zo uitzien als jij wilt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}