---
category: general
date: 2026-06-20
description: hur man ställer in en återuppringning i Aspose.Words Java för att upptäcka
  saknade teckensnitt och anpassa dokumentladdning. Lär dig steg‑för‑steg hur du hanterar
  varningar om teckensnittssubstitution.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: sv
og_description: hur man ställer in en återuppringning i Aspose.Words Java för att
  upptäcka saknade teckensnitt, hantera ersättningar och anpassa dokumentladdning.
  Komplett guide med kod.
og_title: hur man ställer in callback – Upptäck saknade teckensnitt i Aspose.Words
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
title: Hur man ställer in återanrop i Aspose.Words Java – Upptäck och hantera saknade
  teckensnitt
url: /sv/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man ställer in callback i Aspose.Words Java – Upptäck och hantera saknade teckensnitt

Har du någonsin funderat **hur man ställer in callback** i Aspose.Words Java så att du kan upptäcka saknade teckensnitt innan de förstör din PDF eller DOCX? Du är inte ensam. Varningar om saknade teckensnitt kan tyst förstöra layouten, och utan en korrekt varnings‑callback kanske du aldrig märker det förrän det färdiga dokumentet ser felaktigt ut.

I den här handledningen går vi igenom ett komplett, färdigt‑att‑köra exempel som **upptäcker saknade teckensnitt**, **hanterar saknade teckensnitt** på ett smidigt sätt och visar hur du **anpassar dokumentladdning** med en varnings‑callback. I slutet har du en självständig Java‑klass som du kan släppa in i vilket projekt som helst – utan extra dokumentationssökning.

## Vad du behöver

- Java 8 eller nyare (koden fungerar även med Java 11+)  
- Aspose.Words for Java‑biblioteket (version 23.9 eller senare)  
- En DOCX‑fil som refererar till ett teckensnitt du inte har installerat (t.ex. ett eget företags‑teckensnitt)  

Om du ännu inte har lagt till Aspose.Words i ditt Maven‑projekt, inkludera bara:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Det är allt – inga extra plugins, inga inhemska beroenden.

## Steg 1: Förstå WarningCallback‑mekanismen

**Varnings‑callback** är Aspose.Words sätt att varna dig när något oväntat händer under laddning eller sparning av ett dokument. Genom att implementera `IWarningCallback` får du full kontroll över vad som loggas, ignoreras eller till och med omvandlas till ett undantag.

> **Varför detta är viktigt:**  
> När ett teckensnitt saknas ersätter Aspose det med ett reservteckensnitt. Det visuella resultatet kan bli dramatiskt annorlunda, särskilt för PDF‑filer med stark varumärkesprofil. Genom att fånga `WarningType.FONT_SUBSTITUTION` kan du logga det exakta teckensnittsnamnet, besluta om du ska avbryta, eller ersätta med ditt eget anpassade teckensnitt programatiskt.

## Steg 2: Skapa en LoadOptions‑instans

`LoadOptions` är ingångspunkten för att anpassa dokumentladdning. Du kommer att fästa callback‑en på detta objekt innan du faktiskt laddar filen.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Vid detta tillfälle är `loadOptions` bara en enkel behållare – inget händer ännu. Den verkliga magin börjar när vi kopplar in callback‑en.

## Steg 3: Implementera och fäst callback‑en

Nedan finns en kompakt anonym klass som implementerar `IWarningCallback`. Den skriver en vänlig rad till konsolen varje gång en teckensnittsersättning sker.

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

> **Proffstips:** Om du vill **hantera saknade teckensnitt** genom att tillhandahålla en ersättning kan du också sätta `FontSettings` på `LoadOptions` och mappa saknade teckensnitt till ett känt reservteckensnitt.

## Steg 4: Ladda dokumentet med dina anpassade alternativ

Nu när callback‑en är ansluten, ladda dokumentet. Om filen refererar till ett teckensnitt du inte har, kommer du att se varningen skrivas ut.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

När du kör programmet kan konsolen visa:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Den raden bevisar att du framgångsrikt **upptäckt saknade teckensnitt** och nu är i en position att **hantera saknade teckensnitt** på det sätt du föredrar.

## Steg 5: Valfritt – Ersätt saknade teckensnitt med ett känt teckensnitt

Om du föredrar att automatiskt ersätta alla saknade teckensnitt med t.ex. `Times New Roman` kan du lägga till ett `FontSettings`‑objekt:

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

Nu laddas dokumentet, och varje referens till `MyCustomFont` byts tyst ut mot `Times New Roman`. Konsolen kommer fortfarande att meddela vad som ersattes, så du hålls informerad.

## Fullt fungerande exempel

Nedan är en enda Java‑klass som innehåller alla stegen ovan. Kopiera‑klistra in den i din IDE, justera `docPath` och kör.

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

**Förväntad output**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Du har nu ett reproducerbart sätt att **upptäcka saknade teckensnitt**, **hantera saknade teckensnitt** och **anpassa dokumentladdning** – allt genom att lära dig **hur man ställer in callback** korrekt.

## Vanliga frågor

### Vad händer om jag vill att programmet ska sluta ladda när ett teckensnitt saknas?

Kasta ett undantag i `warning`‑metoden:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Fångstblocket längst ner kommer att fånga det, och du kan bestämma hur du loggar eller varnar användaren.

### Fungerar detta för PDF‑filer som genereras från DOCX?

Absolut. Callback‑en triggas under **laddnings**‑fasen, vilket är identiskt för alla utdataformat (`save` till PDF, DOCX, HTML osv.). Så länge du laddar källdokumentet med samma `LoadOptions` kommer du att fånga saknade teckensnitt innan de påverkar den slutliga PDF‑filen.

### Kan jag fånga andra varningstyper (t.ex. bildkonvertering)?

Ja – `WarningInfo.getWarningType()` kan jämföras med andra enum‑värden som `WarningType.IMAGE_CONVERSION`. Lägg bara till fler `if`‑grenar i callback‑en.

### Finns det någon prestandapåverkan?

Obetydlig. Callback‑en körs synkront under laddning, och de extra kontrollerna är lätta. Om du laddar tusentals dokument kan du vilja inaktivera varningar i produktion genom att sätta `loadOptions.setWarningCallback(null);`.

## Visuell översikt

![exempel på hur man ställer in callback i Aspose.Words Java](https://example.com/images/callback-diagram.png "hur man ställer in callback")

*Diagrammet illustrerar flödet: `LoadOptions` → `IWarningCallback` → Dokumentladdning → Hantering av teckensnittsersättning.*

## Sammanfattning

Vi har gått igenom **hur man ställer in callback** i Aspose.Words Java, demonstrerat **upptäckt av saknade teckensnitt**, visat praktiska sätt att **hantera saknade teckensnitt** och förklarat hur man **anpassar dokumentladdning** med `LoadOptions`.  

Beväpnad med denna kunskap kan du nu skydda dina dokumentflöden mot tysta teckensnittssubstitutioner, behålla varumärkesidentiteten och ge dina användare tydlig återkoppling när något går fel.

### Vad blir nästa steg?

- Utforska **teckensnittsersättningstabeller** för massmappning av många saknade teckensnitt.  
- Kombinera denna callback med **dokumentvalidering** för att upprätthålla stilguider.  
- Prova **anpassade varnings‑callbacks** som skriver till en loggfil eller ett övervakningssystem istället för `System.out`.  

Känn dig fri att experimentera, och låt oss veta hur du anpassade callback‑en för dina egna projekt. Lycka till med kodningen!

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man ställer in LoadOptions i Aspose.Words för Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hur man fångar teckensnitt i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}