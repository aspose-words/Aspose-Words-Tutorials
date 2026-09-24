---
category: general
date: 2026-02-10
description: Hur man hanterar teckensnitt i Java med Aspose.Words. Lär dig varningar
  för teckensnittssubstitution, LoadOptions‑återanrop och hantering av saknade teckensnitt
  på några få steg.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: sv
og_description: Hur man hanterar typsnitt i Java med Aspose.Words. Denna guide visar
  steg‑för‑steg hur man hanterar typsnittssubstitution, varningsåteranrop och hantering
  av saknade typsnitt.
og_title: Hur du hanterar teckensnitt i Java – Fullständig Aspose.Words-handledning
tags:
- Java
- Aspose.Words
- Document Processing
title: Hur man hanterar teckensnitt i Java med Aspose.Words – Komplett guide
url: /sv/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man hanterar teckensnitt i Java – Komplett guide

Har du någonsin undrat **hur man hanterar teckensnitt** när ett Word‑dokument refererar till ett teckensnitt som inte är installerat på din server? Det är ett scenario som får många utvecklare att snubbla, särskilt när du automatiserar dokumentgenerering eller konvertering med Aspose.Words. Den goda nyheten? Du kan fånga varje teckensnittssubstitutions‑händelse och reagera på den—utan gissningar.

I den här handledningen går vi igenom ett verkligt exempel som visar **hur man hanterar teckensnitt** med Aspose.Words för Java. Vi kommer att ansluta en varnings‑callback, filtrera fram endast teckensnittssubstitutionsvarningar och skriva ut ett vänligt meddelande för varje saknat teckensnitt. I slutet kommer du att förstå varför detta är viktigt, hur du implementerar det på ett rent sätt och vad du kan förvänta dig när koden körs.

> **Vad du får:** en komplett, färdig‑att‑köra Java‑klass, en förklaring av varje rad, tips för produktionsanvändning och ett snabbt sätt att verifiera resultatet.

---

## Förutsättningar

- **Java 8** (eller nyare) installerat på din maskin.  
- **Aspose.Words for Java** JAR (den senaste versionen per 2026‑02, t.ex. `aspose-words-23.11.jar`).  
- Ett exempel‑dokument (`MissingFont.docx`) som refererar till ett teckensnitt du inte har installerat.  
- En utvecklingsmiljö (IntelliJ IDEA, Eclipse eller till och med en enkel textredigerare + kommandorad).

Inga ytterligare ramverk behövs—bara ren Java och Aspose.Words‑JAR‑filen.

![Diagram som visar hur man hanterar teckensnitt i Java med Aspose.Words](https://example.com/handle-fonts-diagram.png "diagram hur man hanterar teckensnitt")

*Bildtext: diagram hur man hanterar teckensnitt*

## Steg 1 – Ställ in en varnings‑callback (kärnan i **hur man hanterar teckensnitt**)

När Aspose.Words laddar ett dokument genererar det en serie `WarningInfo`‑objekt för allt som inte är perfekt. Genom att bifoga en `IWarningCallback` kan du fånga dessa varningar i realtid.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**Varför detta är viktigt:**  
Om du hoppar över callbacken byter Aspose.Words tyst ut saknade teckensnitt mot ett standardteckensnitt, och du får aldrig veta vilka teckensnitt som saknades. Genom att hantera varningen får du insyn och kan besluta om du vill bädda in ett reservteckensnitt, logga problemet eller till och med avbryta operationen.

---

## Steg 2 – Ladda dokumentet med de konfigurerade `LoadOptions`

Nu när callbacken är klar laddar vi helt enkelt dokumentet. `LoadOptions`‑instansen vi skapade ovan skickas direkt till `Document`‑konstruktorn.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**Vad du kan förvänta dig:**  
När `MissingFont.docx` refererar till t.ex. *Comic Sans MS* men servern bara har *Arial*, skriver callbacken ut något i stil med:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

Om dokumentet laddas utan saknade teckensnitt skrivs inget ut—precis vad du vill ha när **hur man hanterar teckensnitt** på ett smidigt sätt.

---

## Steg 3 – (Valfritt) Verifiera dokumentets teckensnittstabell

Ibland behöver du inspektera vilka teckensnitt dokumentet faktiskt använder efter inläsning. Aspose.Words gör det enkelt.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**När du ska använda detta:**  
Om du bygger en batch‑processor som måste rapportera saknade teckensnitt innan en PDF publiceras, ger utskrift av teckensnittstabellen en sista kontroll.

---

## Fullt, körbart exempel

När vi sätter ihop allt, här är den kompletta klassen du kan kopiera‑klistra in i `FontSubstitutionDemo.java` och köra:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Körning av koden:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

Du bör se substitueringsmeddelandena följt av den slutgiltiga teckensnittlistan.

---

## Vanliga frågor & kantfall

### Vad händer om jag själv behöver ersätta teckensnittet?

Varnings‑callbacken berättar bara *vad* som ersattes. Om du vill tvinga ett specifikt reservteckensnitt kan du använda `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

Nu kommer varje förekomst av “MissingFont” att ersättas med “Arial” innan dokumentet laddas.

### Fungerar detta när du sparar till PDF?

Absolut. Samma callback triggas under `document.save("out.pdf")` om PDF‑renderaren också behöver ersätta teckensnitt. Behåll samma `LoadOptions` eller bifoga en ny callback till `PdfSaveOptions`.

### Hur beter detta sig i en flertrådad miljö?

`LoadOptions` är **inte** trådsäker, så skapa en ny instans per tråd. Callbacken själv kan vara stateless (som visat) eller så kan du injicera en logger som är trådanpassad.

### Vad händer om det saknade teckensnittet är ett anpassat företags‑teckensnitt?

Du kommer vanligtvis att bädda in det teckensnittet i serverns teckensnittsmapp och peka Aspose.Words på den via `FontSettings.setFontsFolder("path/to/fonts", true)`. Callbacken kommer då sluta triggas för det teckensnittet eftersom det inte längre saknas.

---

## Proffstips för produktionsklar teckensnittshantering

- **Logga, inte bara `System.out.println`** – använd ett riktigt loggningsramverk (SLF4J, Log4j) så att du kan fånga varningar i ditt övervakningssystem.  
- **Cacha teckensnittssökningar** – om du bearbetar tusentals dokument, undvik att upprepade gånger skanna OS‑teckensnittskatalogen. Ladda teckensnitt en gång i en `FontSettings`‑instans och återanvänd den.  
- **Fail fast när kritiska teckensnitt saknas** – du kan kasta ett undantag i callbacken om ett specifikt teckensnitt är obligatoriskt för varumärkes‑efterlevnad.  
- **Testa med en variation av dokument** – inkludera PDF‑, DOCX‑ och DOC‑filer; varje format kan trigga olika varningstyper.  

---

## Slutsats

Vi har gått igenom **hur man hanterar teckensnitt** i Java med Aspose.Words från början till slut:

1. Anslut en `IWarningCallback` för att fånga teckensnittssubstitutionsvarningar.  
2. Ladda dokumentet med `LoadOptions` så att callbacken körs automatiskt.  
3. (Valfritt) Inspektera den slutgiltiga teckensnittlistan för att bekräfta resultatet.  

Genom att följa dessa steg får du full insyn i saknade teckensnitt, kan upprätthålla företagets teckensnittspolicyer och undvika tysta reservteckensnitt som kan förstöra utseendet på dina genererade PDF‑ eller Word‑filer.

Redo för nästa utmaning? Prova att byta ut callbacken för att logga *alla* varningar, experimentera med `FontSettings` för anpassade substitueringsregler, eller integrera denna logik i en Spring‑Boot‑mikrotjänst som bearbetar dokument i realtid.

Lycka till med kodandet, och må dina dokument alltid renderas med rätt teckensnitt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}