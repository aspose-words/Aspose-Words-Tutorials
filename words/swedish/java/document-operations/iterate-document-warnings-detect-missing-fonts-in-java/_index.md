---
category: general
date: 2026-04-28
description: Iterera dokumentvarningar i en Word‑fil för att upptäcka saknade teckensnitt,
  hämta namn på de saknade teckensnitten och skriva ut detaljer om de saknade teckensnitten
  med Aspose.Words för Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: sv
og_description: Iterera dokumentvarningar för att hitta saknade typsnitt, hämta namn
  på saknade typsnitt och skriva ut detaljer om saknade typsnitt med ett komplett
  Java‑exempel.
og_title: 'Iterera dokumentvarningar: Upptäck saknade teckensnitt i Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterera dokumentvarningar: Upptäck saknade teckensnitt i Java'
url: /sv/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Iterera dokumentvarningar – Upptäck saknade teckensnitt i Java

Har du någonsin behövt **iterera dokumentvarningar** när du öppnar en Word‑fil och undrat vilka teckensnitt som saknas? Du är inte ensam. Saknade teckensnitt kan förstöra utseendet på en rapport, och utan ett sätt att upptäcka dem kan du leverera ett dokument som ser helt annorlunda ut än originalet.  

I den här handledningen visar vi hur du **upptäcker saknade teckensnitt** genom att ladda ett Word‑dokument, iterera dess varningar, hämta namnen på de saknade teckensnitten och slutligen skriva ut informationen – allt med Aspose.Words för Java.  

Vi går igenom allt från den allra första kodraden till det förväntade konsolutdata, så att du kan kopiera‑klistra in en fungerande lösning i ditt projekt direkt nu. Inga extra dokument behövs.

## Förutsättningar

- Java 8 eller nyare installerat.
- Aspose.Words för Java‑bibliotek (senaste versionen per 2026‑04‑28).
- En Word‑fil som eventuellt innehåller teckensnitt som inte är installerade på din maskin (t.ex. `doc-with-missing-font.docx`).

Om du redan har detta, bra – du är redo att **ladda word‑dokument** och börja iterera.

## Steg 1 – Ladda Word‑dokument med standardalternativ

Innan vi kan **iterera dokumentvarningar** måste filen laddas in i minnet. Aspose.Words låter dig göra detta med ett enda konstruktörsanrop. Att använda standard‑`LoadOptions` räcker oftast, men vi visar den explicita skapelsen för tydlighetens skull.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Varför detta är viktigt:**  
> När dokumentet laddas skannar Aspose.Words filen efter resurser som den inte kan lösa, exempelvis teckensnitt som inte är installerade lokalt. Dessa problem lagras som **varningar**, som vi kommer att **iterera dokumentvarningar** över i nästa steg.

## Steg 2 – Iterera dokumentvarningar för att hitta teckensnittsproblem

Nu kommer hjärtat i lösningen: vi loopar igenom varje varning som biblioteket samlade in under laddningen. `WarningInfo`‑objekten berättar vad som gick fel, och vi kan filtrera på `FontSubstitutionWarning` för att **upptäcka saknade teckensnitt**.

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

> **Proffstips:** `instanceof`‑kontrollen säkerställer att vi bara hanterar teckensnittsrelaterade varningar och ignorerar andra, som bild‑laddningsproblem. Detta gör loopen effektiv och håller utskriften fokuserad på de teckensnitt du faktiskt behöver **hämta saknat teckensnitt**‑information för.

### Förväntat konsolutdata

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Om dokumentet inte innehåller några saknade teckensnitt avslutas loopen tyst – inget att **skriva ut saknat teckensnitt**.

## Steg 3 – Varför inte bara fånga ett undantag?

Du kanske undrar: “Varför inte omsluta `new Document(...)`‑anropet med en try‑catch och leta efter ett undantag?” Svaret är tvådelat:

1. **Detaljerad information:** Undantag berättar bara att något misslyckades. Varningar ger dig exakt teckensnittsnamn och den reserv som Aspose.Words valde.
2. **Icke‑fatala problem:** Saknade teckensnitt är vanligtvis icke‑fatala; dokumentet laddas fortfarande, men den visuella integriteten äventyras. Genom att **iterera dokumentvarningar** behåller du möjligheten att bearbeta resten av filen.

## Steg 4 – Utöka exemplet: Samla saknade teckensnitt i en lista

Ibland behöver du de saknade teckensnitten för vidare bearbetning – kanske för att bädda in dem eller för att varna en användare via UI. Här är en snabb justering som samlar namnen i ett `Set<String>`.

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

Nu har du ett rent sätt att **hämta saknat teckensnitt**‑data programatiskt, som du kan föra in i en rapporteringsmodul eller en teckensnitt‑installationsguide.

## Steg 5 – Praktiska överväganden

- **Flera ersättningar:** Ett enda saknat teckensnitt kan ersättas av olika teckensnitt i olika delar av dokumentet. Varningslistan kommer att innehålla varje förekomst, så du kan se dubbletter av saknade‑teckensnitt‑poster.
- **Prestanda:** Att ladda mycket stora dokument kan generera tusentals varningar. Om du bara bryr dig om teckensnitt, filtrera tidigt som visat för att hålla loopen snabb.
- **Plattformsoberoende teckensnitt:** På Linux är standard‑ersättningsteckensnittet ofta *Liberation Sans*. På Windows kan det vara *Arial*. Att känna till reservteckensnittet hjälper dig avgöra om du behöver leverera egna teckensnitt med din applikation.

## Steg 6 – Visuell hjälp

Nedan är en skärmdump av konsolutdata (alt‑text inkluderar huvudnyckelordet för SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt‑text:* *iterate document warnings‑exempel som visar namn på saknade teckensnitt och ersättningsdetaljer.*

## Slutsats

Du har precis lärt dig hur du **itererar dokumentvarningar** i Aspose.Words för Java, **upptäcker saknade teckensnitt**, **laddar word‑dokument** på ett säkert sätt, **hämtar saknat teckensnitt**‑information och **skriver ut saknat teckensnitt**‑detaljer till konsolen. Den kompletta kodsnutten körs som den är, och du kan anpassa den för att logga till en fil, visa en UI‑dialog eller till och med automatiskt bädda in de saknade teckensnitten.

Nästa steg kan vara att utforska hur du **laddar word‑dokument** med anpassade teckensnittskällor (t.ex. genom att lägga till en mapp med företagets teckensnitt) eller hur du bäddar in saknade teckensnitt direkt i filen för att bevara layouten på alla maskiner. Båda ämnena bygger naturligt på det vi gått igenom här.

Lycka till med kodningen, och må dina PDF‑filer alltid se exakt ut som du tänkt dig!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}