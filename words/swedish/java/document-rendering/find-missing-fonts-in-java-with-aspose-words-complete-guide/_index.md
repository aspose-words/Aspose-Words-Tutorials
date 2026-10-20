---
category: general
date: 2026-06-08
description: Hitta saknade teckensnitt snabbt med Aspose.Words för Java. Lär dig att
  diagnostisera varningar om teckensnittssubstitution och åtgärda problem med saknade
  teckensnitt på bara några steg.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: sv
og_description: Hitta saknade teckensnitt i dina DOCX‑filer med Aspose.Words för Java.
  Denna handledning visar hur du aktiverar diagnostik, läser FontSubstitutionWarning‑händelser
  och visar original‑ och ersatta teckensnittsnamn.
og_title: Hitta saknade teckensnitt i Java – Aspose.Words steg för steg
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: Hitta saknade teckensnitt i Java med Aspose.Words – Komplett guide
url: /sv/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hitta saknade teckensnitt i Java med Aspose.Words – Komplett guide

Har du någonsin undrat hur man **hittar saknade teckensnitt** i ett Word‑dokument innan det förstör layouten? Du är inte ensam—utvecklare stöter ständigt på tysta teckensnittssubstitutioner som förstör PDF‑filer eller utskrivna rapporter. Den goda nyheten är att Aspose.Words för Java ger dig ett inbyggt diagnostik‑API som gör det enkelt att upptäcka dessa saknade teckensnitt.

I den här handledningen går vi igenom ett verkligt exempel som laddar en DOCX, aktiverar varningsinsamling och skriver ut varje *FontSubstitutionWarning* du behöver känna till. I slutet kan du logga det ursprungliga teckensnittets namn, det reservteckensnitt som Aspose valde och besluta om du själv ska bädda in det saknade teckensnittet.

## Vad du behöver

Innan vi dyker ner, se till att du har:

* **Aspose.Words for Java** (senaste 23.x‑versionen) på din classpath.  
* En Java 8+ utvecklingsmiljö (valfri IDE, Maven/Gradle fungerar bra).  
* Ett exempel‑DOCX som medvetet refererar till ett teckensnitt som inte är installerat på din maskin—vi kallar det `MissingFonts.docx`.

Det är allt. Inga extra bibliotek, ingen komplex konfiguration, bara ren Java och Aspose.

![Diagram för att hitta saknade teckensnitt](https://example.com/find-missing-fonts.png "Diagram för att hitta saknade teckensnitt")

*Bilden ovan illustrerar flödet: load → diagnostics → warnings → output.*

## Steg 1: Förbered LoadOptions och specificera dokumentformatet

Det första vi gör är att skapa ett **LoadOptions**‑objekt. Detta talar om för Aspose.Words hur den inkommande filen ska tolkas och, viktigast av allt, möjliggör insamling av *document warnings*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*Varför använda LoadOptions?*  
Utan det laddar Aspose fortfarande filen men kan hoppa över viss diagnostisk data. Genom att explicit ange formatet garanterar du konsekvent varningsgenerering, särskilt när du hanterar äldre eller korrupta filer.

## Steg 2: Läs in dokumentet med diagnostik aktiverad

Nu läser vi faktiskt in filen. `Document`‑konstruktorn startar automatiskt insamling av varningar, vilka senare kommer att inkludera eventuella **FontSubstitutionWarning**‑instanser.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **Proffstips:** Om du använder Maven, lägg till Aspose.Words‑beroendet i din `pom.xml`. På så sätt hämtas JAR‑filen automatiskt och du slipper hantera classpath manuellt.

## Steg 3: Skanna dokumentvarningarna för teckensnittssubstitutionshändelser

Aspose lagrar varje varning i en samling som du kan iterera över. Vi filtrerar på `FontSubstitutionWarning`‑objekt eftersom de specifikt indikerar ett saknat teckensnitt som har ersatts.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*Vad händer här?*  
`doc.getWarnings()` returnerar en `List<WarningInfo>`. Genom att kontrollera `instanceof FontSubstitutionWarning` isolerar vi bara de teckensnittsrelaterade posterna och ignorerar andra varningar som “unsupported feature” eller “image conversion”.

## Steg 4: Skriv ut original‑ och ersatta teckensnittsnamn

Till sist skriver vi ut både det saknade (ursprungliga) teckensnittets namn och det teckensnitt som Aspose valde som ersättning. Denna utskrift är perfekt för loggning eller för att mata in i en bygg‑pipeline‑kontroll.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### Förväntad konsolutskrift

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

Om du inte ser någon utskrift betyder det att **inga saknade teckensnitt upptäcktes**—ditt dokument innehåller redan teckensnitt som finns på maskinen som kör koden.

## Steg 5: Hantera kantfall och vanliga fallgropar

### Saknat teckensnitt men ingen varning

Ibland är ett teckensnitt inbäddat i DOCX, men inbäddningen är korrupt. Aspose kommer fortfarande att ge en `FontSubstitutionWarning` eftersom den inte kan rendera texten. För att särskilja, kontrollera `fsWarning.isFontEmbedded()` (tillgängligt i nyare versioner).

### Flera substitutioner för samma teckensnitt

Ett enskilt saknat teckensnitt kan ersättas flera gånger under olika körningar om fallback‑hierarkin förändras (t.ex. först försöker Arial, sedan faller tillbaka till Helvetica). Behåll en `Set<String>` av `getOriginalFontName()` för att deduplicera om du bara behöver en lista med unika saknade teckensnitt.

### Prestandaöverväganden

Att ladda mycket stora DOCX‑filer (hundratals MB) samtidigt som varningar samlas in kan lägga till extra belastning. Om du bara behöver teckensnittsd diagnostik, sätt `loadOptions.setValidateStructure(false)` för att hoppa över djup validering. Detta snabbar upp processen utan att påverka varningsgenereringen.

## Bonus: Automatisera teckensnittsinfogning

När du vet vilka teckensnitt som saknas kan du programatiskt bädda in dem:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

Infogning säkerställer att den slutgiltiga PDF‑en eller sparade DOCX‑en renderas exakt som avsett på vilken maskin som helst—inga fler överraskande fallback‑val.

## Sammanfattning: Så hittar du saknade teckensnitt med Aspose.Words

- **Create LoadOptions** and set the load format.  
- **Load the document** while Aspose captures warnings.  
- **Iterate over `doc.getWarnings()`**, filtering for `FontSubstitutionWarning`.  
- **Print** `getOriginalFontName()` and `getSubstitutedFontName()` to see which fonts are missing.  
- **Optional:** deduplicate, check embedding status, or automatically embed the missing fonts.

Detta är den kompletta lösningen för att **hitta saknade teckensnitt** i en Java‑applikation med Aspose.Words. Du har nu ett pålitligt sätt att fånga teckensnittsproblem tidigt, hålla dina PDF‑er konsekventa och undvika obehagliga överraskningar i produktion.

## Vad du kan utforska härnäst?

* **Embedding fonts** automatically (see the bonus snippet).  
* **Generating a PDF** after fixing fonts to verify the visual output.  
* **Using Aspose.Words’ FontSettings** to define a custom fallback chain.  
* **Running the same diagnostics on DOC, RTF, or HTML** files—just change `LoadFormat` accordingly.

Känn dig fri att experimentera med olika dokumenttyper och teckensnittsfamiljer. Om du stöter på problem, lämna en kommentar nedan eller kolla Asposes officiella Java‑API‑dokumentation för djupare anpassning.

Happy coding, and may your documents always render with the fonts you intended!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Använda teckensnitt i Aspose.Words för Java](/words/english/java/using-document-elements/using-fonts/)
- [Fånga varningar för teckensnittssubstitution i Java med Aspose.Words – Komplett guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}