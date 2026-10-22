---
category: general
date: 2026-06-20
description: Hoe je een callback instelt in Aspose.Words Java om ontbrekende lettertypen
  te detecteren en het laden van documenten aan te passen. Leer stap voor stap hoe
  je waarschuwingen voor lettertypevervanging afhandelt.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: nl
og_description: hoe je een callback instelt in Aspose.Words Java om ontbrekende lettertypen
  te detecteren, substituties af te handelen en het laden van documenten aan te passen.
  Complete gids met code.
og_title: hoe callback instellen – Ontbrekende lettertypen detecteren in Aspose.Words
  Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Hoe een callback instellen in Aspose.Words Java – Detecteer en verwerk ontbrekende
  lettertypen
url: /nl/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hoe stel je een callback in Aspose.Words Java – Detecteer en verwerk ontbrekende lettertypen

Heb je je ooit afgevraagd **hoe je een callback instelt** in Aspose.Words Java zodat je ontbrekende lettertypen kunt opsporen voordat ze je PDF of DOCX verpesten? Je bent niet de enige. Waarschuwingen over ontbrekende lettertypen kunnen stilletjes de lay-out corrumperen, en zonder een juiste warning‑callback merk je het misschien pas op wanneer het uiteindelijke document er niet goed uitziet.  

In deze tutorial lopen we een volledig, kant‑klaar voorbeeld door dat **ontbrekende lettertypen detecteert**, **ontbrekende lettertypen verwerkt** op een elegante manier, en je laat zien hoe je **documentladen kunt aanpassen** met een warning‑callback. Aan het einde heb je een zelfstandige Java‑klasse die je in elk project kunt plaatsen—geen extra documentatie zoeken nodig.

## Wat je nodig hebt

- Java 8 of nieuwer (de code werkt ook met Java 11+)  
- Aspose.Words for Java‑bibliotheek (versie 23.9 of later)  
- Een DOCX‑bestand dat verwijst naar een lettertype dat je niet geïnstalleerd hebt (bijv. een aangepast bedrijfslettertype)  

Als je Aspose.Words nog niet aan je Maven‑project hebt toegevoegd, voeg dan simpelweg het volgende toe:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Dat is alles—geen extra plug‑ins, geen native afhankelijkheden.

## Stap 1: Begrijp het WarningCallback‑mechanisme

De **warning callback** is de manier waarop Aspose.Words je waarschuwt wanneer er iets onverwachts gebeurt tijdens het laden of opslaan van een document. Door `IWarningCallback` te implementeren krijg je volledige controle over wat wordt gelogd, genegeerd, of zelfs omgezet in een uitzondering.

> **Waarom dit belangrijk is:**  
> Wanneer een lettertype ontbreekt, vervangt Aspose het door een fallback‑lettertype. Het visuele resultaat kan drastisch verschillen, vooral bij sterk merk‑gerichte PDF’s. Door `WarningType.FONT_SUBSTITUTION` op te vangen, kun je de exacte lettertype‑naam loggen, beslissen of je moet afbreken, of je eigen aangepaste lettertype programmatisch substitueren.

## Stap 2: Maak een LoadOptions‑instantie

`LoadOptions` is het startpunt voor het aanpassen van het laden van documenten. Je koppelt de callback aan dit object voordat je het bestand daadwerkelijk laadt.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Op dit moment is `loadOptions` slechts een eenvoudige container—er gebeurt nog niets. De echte magie begint wanneer we de callback aansluiten.

## Stap 3: Implementeer en koppel de callback

Hieronder staat een compacte anonieme klasse die `IWarningCallback` implementeert. Hij print een vriendelijke regel naar de console telkens wanneer een lettertype‑substitutie plaatsvindt.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro tip:** Als je **ontbrekende lettertypen wilt verwerken** door een vervanging te bieden, kun je ook `FontSettings` op de `LoadOptions` instellen en ontbrekende lettertypen naar een bekende fallback mappen.

## Stap 4: Laad het document met je aangepaste opties

Nu de callback is gekoppeld, laad je het document. Als het bestand verwijst naar een lettertype dat je niet hebt, zie je de waarschuwing geprint.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Wanneer je het programma uitvoert, kan de console het volgende tonen:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Die regel bewijst dat je succesvol **ontbrekende lettertypen hebt gedetecteerd** en nu in staat bent om **ontbrekende lettertypen** naar eigen inzicht te **verwerken**.

## Stap 5: Optioneel – Vervang ontbrekende lettertypen door een bekend lettertype

Als je liever elk ontbrekend lettertype automatisch vervangt door bijvoorbeeld `Times New Roman`, kun je een `FontSettings`‑object toevoegen:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Nu laadt het document, en elke verwijzing naar `MyCustomFont` wordt stilletjes vervangen door `Times New Roman`. De console zal nog steeds aangeven wat er vervangen is, zodat je op de hoogte blijft.

## Volledig werkend voorbeeld

Hieronder staat een enkele Java‑klasse die alle bovenstaande stappen combineert. Kopieer‑en‑plak deze in je IDE, pas `docPath` aan, en voer uit.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Verwachte output**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Je hebt nu een reproduceerbare manier om **ontbrekende lettertypen te detecteren**, **ontbrekende lettertypen te verwerken**, en **documentladen aan te passen**—alles door correct te leren **hoe je een callback instelt**.

## Veelgestelde vragen

### Wat als ik wil dat het programma stopt met laden wanneer een lettertype ontbreekt?

Gooi een uitzondering in de `warning`‑methode:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Het catch‑blok onderaan zal dit opvangen, en je kunt bepalen hoe je het logt of de gebruiker waarschuwt.

### Werkt dit voor PDF’s die gegenereerd zijn vanuit DOCX?

Absoluut. De callback wordt geactiveerd tijdens de **load‑fase**, die identiek is voor alle uitvoerformaten (`save` naar PDF, DOCX, HTML, enz.). Zolang je het bron‑document laadt met dezelfde `LoadOptions`, vang je ontbrekende lettertypen op voordat ze de uiteindelijke PDF beïnvloeden.

### Kan ik andere waarschuwings‑types opvangen (bijv. afbeeldingconversie)?

Ja—`WarningInfo.getWarningType()` kan worden vergeleken met andere enums zoals `WarningType.IMAGE_CONVERSION`. Voeg gewoon meer `if`‑takken toe in de callback.

### Heeft dit invloed op de prestaties?

Negentig. De callback draait synchroon tijdens het laden, en de extra controles zijn lichtgewicht. Als je duizenden documenten laadt, wil je waarschuwingen in productie misschien uitschakelen door `loadOptions.setWarningCallback(null);` in te stellen.

## Visueel overzicht

![voorbeeld van hoe een callback in te stellen in Aspose.Words Java](https://example.com/images/callback-diagram.png "voorbeeld van hoe een callback in te stellen in Aspose.Words Java")

*Het diagram illustreert de stroom: `LoadOptions` → `IWarningCallback` → Document laden → Verwerking van lettertype‑substitutie.*

## Samenvatting

We hebben **hoe je een callback instelt** in Aspose.Words Java behandeld, **ontbrekende lettertypen gedetecteerd**, praktische manieren getoond om **ontbrekende lettertypen te verwerken**, en uitgelegd hoe je **documentladen kunt aanpassen** met `LoadOptions`.  

Met deze kennis kun je nu je document‑pijplijnen beschermen tegen stille lettertype‑vervangingen, de branding behouden, en je gebruikers duidelijke feedback geven wanneer er iets misgaat.

### Wat is het volgende?

- Verken **font substitution‑tabellen** voor bulk‑mapping van veel ontbrekende lettertypen.  
- Combineer deze callback met **documentvalidatie** om stijl‑richtlijnen af te dwingen.  
- Probeer **aangepaste warning‑callbacks** die naar een log‑bestand of een bewakingssysteem schrijven in plaats van `System.out`.  

Voel je vrij om te experimenteren, en laat ons weten hoe je de callback voor je eigen projecten hebt aangepast. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe LoadOptions in te stellen in Aspose.Words voor Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Hoe lettertypen te detecteren in Aspose.Words – Waarschuwingen & instellingen verwerken](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hoe lettertypen vast te leggen in Aspose.Words – Complete gids](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}