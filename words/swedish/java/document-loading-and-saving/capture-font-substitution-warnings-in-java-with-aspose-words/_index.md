---
category: general
date: 2026-06-27
description: Lär dig hur du fångar varningar för teckensnittssubstitution i Java med
  Aspose.Words. Denna steg‑för‑steg‑handledning täcker också varnings‑callback‑funktioner
  och användning av LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: sv
og_description: Fånga varningar om teckensnittssubstitution i Java med Aspose.Words.
  Följ den här guiden för att konfigurera varningsåteruppringningar, använda LoadOptions
  och hantera saknade teckensnitt.
og_title: Fånga varningar om teckensnittssubstitution i Java – Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Fånga varningar om teckensnittssubstitution i Java med Aspose.Words – Komplett
  guide
url: /sv/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fånga varningar om teckensnittssubstitution i Java med Aspose.Words – Komplett guide

Har du någonsin behövt **fånga varningar om teckensnittssubstitution** när du laddar en DOCX som använder exotiska teckensnitt? Du är inte ensam. I många verkliga projekt—tänk automatiska rapportgeneratorer eller batch‑dokumentkonverterare—utlöser saknade teckensnitt tysta substitutioner som kan förstöra layoutens noggrannhet.  

Lyckligtvis erbjuder Aspose.Words ett enkelt sätt att lyssna på dessa varningar. I den här handledningen går vi igenom hur du konfigurerar **LoadOptions**, kopplar en **Aspose.Words varnings‑callback**, och skriver ut varje *teckensnittssubstitution*‑meddelande till konsolen. I slutet vet du exakt när ett teckensnitt har bytts ut och hur du kan reagera programmässigt.

> **Vad du får:** ett fullt körbart Java‑exempel, en förklaring av *varför* varje del är viktig, samt tips för att hantera kantfall som anpassade teckensnittskataloger.

## Förutsättningar och vad du behöver

Innan vi dyker ner, se till att du har:

- Java 8 eller nyare installerat (koden fungerar även med Java 11+).
- Den senaste Aspose.Words for Java JAR (ladda ner från den officiella webbplatsen eller Maven Central).
- En DOCX‑fil som refererar till teckensnitt som inte är installerade på din maskin (t.ex. en *font‑rich.docx* som du kan hitta i Aspose‑demopaketet).
- En bra IDE (IntelliJ IDEA, Eclipse eller till och med VS Code med Java‑tillägg).

Inga externa bibliotek utöver Aspose.Words krävs, och exemplet körs i en enkel `main`‑metod.

## Steg 1: Ställ in LoadOptions – Ingångspunkten för anpassad laddning

`LoadOptions` är Aspose.Words konfigurationsbehållare som talar om för biblioteket *hur* ett dokument ska läsas. Som standard ersätter det tyst saknade teckensnitt, men du kan ändra det beteendet med en varnings‑callback.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Varför detta är viktigt:** Utan `LoadOptions` laddas dokumentet tyst, och du förlorar insyn i saknade teckensnitt. Genom att skapa en instans får du en krok för varningssystemet.

## Steg 2: Definiera en varnings‑callback för att *fånga varningar om teckensnittssubstitution*

Aspose.Words skickar varningshändelser via `IWarningCallback`‑gränssnittet. Implementera det inline (eller som en separat klass) och filtrera på `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Förklaring:**  
- `info.getWarningType()` anger varningens kategori.  
- `WarningType.FONT_SUBSTITUTION` är enum‑värdet vi är intresserade av.  
- `info.getDescription()` innehåller ett mänskligt läsbart meddelande, t.ex. *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Genom att skriva ut beskrivningen **fångar du varningar om teckensnittssubstitution** i realtid.

## Steg 3: Ladda dokumentet med de konfigurerade LoadOptions

Nu när callbacken är på plats, ladda din DOCX. Varnings‑callbacken avfyras automatiskt under parsning.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Byt ut `YOUR_DIRECTORY` mot den faktiska sökvägen till din testfil. När `Document`‑konstruktorn körs, utlöser varje saknat teckensnitt den tidigare definierade callbacken, och du ser substitutionsmeddelandena i konsolen.

## Steg 4: Verifiera det laddade dokumentet (valfritt men hjälpsamt)

Efter laddning kanske du vill bekräfta dokumentets integritet—sidantal, textutdrag osv. Detta steg krävs inte för att fånga varningar, men det hjälper dig att se effekten av substitutioner.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Om ett teckensnitt har substituerats kan layouten förändras något; att kontrollera sidantalet kan avslöja sådana förändringar.

## Steg 5: Avancerat – Hantera substituerade teckensnitt programmässigt

Ibland vill du inte bara logga varningen—du kan behöva bädda in ett reservteckensnitt eller justera stil. Nedan är ett snabbt mönster du kan använda.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Genom att peka Aspose.Words mot en mapp som innehåller de ursprungliga teckensnitten kan du *förhindra* substitution helt och hållet. Om mappen saknas fångar varnings‑callbacken fortfarande händelsen, vilket ger dig en reservstrategi.

## Fullständigt fungerande exempel

När allt sätts ihop, här är det kompletta, färdiga programmet:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Förväntad konsolutskrift** (när ett saknat teckensnitt påträffas):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Om alla teckensnitt finns kvar, förblir callbacken tyst—inget skrivs ut, vilket är precis vad du kan förvänta dig.

## Vanliga fallgropar & pro‑tips

| Fallgropar | Varför det händer | Lösning |
|------------|-------------------|---------|
| **Callbacken avfyras aldrig** | Du glömde att fästa callbacken till `LoadOptions` **eller** använde standardkonstruktorn för `Document` utan att skicka `loadOptions`. | Anropa alltid `loadOptions.setWarningCallback(...)` **och** använd överlagringen `new Document(path, loadOptions)`. |
| **För många varningar skräpar ner loggen** | Stora dokument med många saknade teckensnitt genererar en varning per substitution. | Filtrera ytterligare genom att kontrollera `info.getDescription()` för specifika teckensnittsnamn, eller samla varningar i en lista för senare bearbetning. |
| **Substituerade teckensnitt påverkar layouten** | Reservteckensnittet kan ha andra mått (storlek, avstånd). | Tillhandahåll en anpassad teckensnittsmapp (se Steg 5) eller justera dokumentets stil efter laddning. |
| **Körning på en huvudlös server** | Standardreservteckensnittet kan förlita sig på systemteckensnitt som inte är installerade på servern. | Leverera de nödvändiga teckensnitten med din applikation och peka `FontSettings` till den mappen. |

## Vanliga frågor

**Q: Fungerar detta med PDF eller andra format?**  
A: Ja. Varnings‑callbacken är format‑agnostisk; den avfyras för alla dokumenttyper som Aspose.Words laddar (DOC, DOCX, RTF, HTML osv.). Den enda skillnaden är vilka varningar som kan visas.

**Q: Kan jag fånga andra varningstyper, som varningar om *bildupplösning*?**  
A: Absolut. Inuti `warning`‑metoden kan du inspektera `info.getWarningType()` för andra enum‑värden såsom `WarningType.IMAGE_RESOLUTION`. Hantera dem därefter.

**Q: Vad händer om jag behöver listan över substituerade teckensnitt efter att dokumentet har laddats?**  
A: Spara varje `info.getDescription()` i en `List<String>` i callbacken. Efter laddning har du en samling som du kan logga, skicka till en övervakningstjänst eller använda för att starta en teckensnitts‑nedladdningsrutin.

## Slutsats

Du vet nu **hur du fångar varningar om teckensnittssubstitution** i Java med Aspose.Words, varför varje del av pusslet är viktig, och hur du kan utöka lösningen för verkliga scenarier. Genom att utnyttja `LoadOptions`, en `Aspose.Words warning callback` och valfri `FontSettings` får du full insyn i saknade teckensnitt och kan hålla dina dokumentkonverterings‑pipelines pålitliga.

Redo för nästa steg? Prova att ersätta `System.out.println` med en logger som SLF4J, eller integrera varningslistan i ett UI som varnar användare innan de slutför en batch‑konvertering. Du kan också utforska **Aspose.Words warning callback** för andra varningstyper, såsom *ej stödda funktioner* eller *varningar om högupplösta bilder*.

Lycka till med kodandet, och må dina PDF‑filer aldrig drabbas av oväntade teckensnittssubstitutioner igen! 

![Skärmbild som visar konsolutdata för fångade varningar om teckensnittssubstitution](image-placeholder.png "fånga varningar om teckensnittssubstitution")


## Vad du bör lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Aktivera varningar om teckensnittssubstitution i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Hur man ställer in LoadOptions i Aspose.Words för Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Hur man skapar PDF‑dokument med Aspose.Words för Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}