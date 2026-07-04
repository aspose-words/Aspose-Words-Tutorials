---
category: general
date: 2026-05-30
description: Registrera varningsåteruppringning i Java för att spåra saknade teckensnitt
  och anpassa dokumentladdning med Aspose.Words. Lär dig den fullständiga steg‑för‑steg‑lösningen.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: sv
og_description: Registrera varningsåteruppringning i Java för att spåra saknade teckensnitt
  och anpassa dokumentladdning. Komplett guide med kod och förklaringar.
og_title: Registrera varningscallback i Java – Spåra saknade typsnitt
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Registrera varningsåteranrop i Java – Spåra saknade teckensnitt
url: /sv/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrera varningsåteruppringning i Java – Spåra saknade teckensnitt

Har du någonsin funderat på hur du **spårar saknade teckensnitt** när du laddar ett Word-dokument med Aspose.Words för Java? Kanske har du sett de tysta teckensnittsersättningen och tänkt, “Vad hände med min layout?” Den goda nyheten är att du inte behöver gissa. Genom att **registrera en varningsåteruppringning** kan du fånga varje teckensnittsersättnings‑händelse i det ögonblick dokumentet läses, och du kan också **anpassa dokumentladdning** för att passa din pipeline.

> **What you’ll get:**  
> • Ett komplett Java‑program som använder Aspose.Words  
> • Steg‑för‑steg‑förklaringar av varje rad  
> • Tips för att hantera kantfall som krypterade filer eller stora batcher  
> • En snabb kontroll du kan köra på vilken `.docx`‑fil som helst

## Förutsättningar

Innan vi dyker ner, se till att du har:

- **Java 17** (eller någon nyare JDK) installerad och `JAVA_HOME` satt.  
- **Aspose.Words for Java** JAR på din classpath. Du kan hämta den senaste versionen från Maven Central‑arkivet:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Ett exempel‑Word‑dokument (`input.docx`) som du misstänker innehåller teckensnitt som inte är installerade på din maskin.  
- En IDE eller ett kommandorads‑byggverktyg (Maven/Gradle) som du är bekväm med.

Det är allt. Inga extra teckensnitt, inga extra tjänster – bara ren Java och Aspose.Words.

## Varför registrera en varningsåteruppringning?

Tänk på **varningsåteruppringningen** som en säkerhetskamera för din dokumentladdningsprocess. När Aspose.Words stöter på en saknad glyf kastar den inte ett undantag; den byter tyst till ett reservteckensnitt. Den tysta ersättningen kan förstöra din layout, särskilt i varumärkeskritiska PDF‑filer eller fakturor. Genom att registrera en återuppringning får du:

1. **Få insikt i realtid** – varje `FONT_SUBSTITUTION`‑varning levereras omedelbart.  
2. **Logga eller reagera** – du kan logga till en fil, utlösa en varning, eller till och med ersätta teckensnittet programatiskt.  
3. **Behålla ren output** – att veta vilka teckensnitt som saknas låter dig åtgärda källdokumentet innan publicering.

Kort sagt förvandlar återuppringningen ett dolt problem till ett synligt, vilket gör din dokumentpipeline mycket mer pålitlig.

## Steg 1 – Skapa `LoadOptions` för att anpassa hur dokumentet laddas

Det första vi gör är att instansiera `LoadOptions`. Detta objekt är porten för varje justering vid laddning du kan behöva, från lösenordshantering till vår **registrera varningsåteruppringning**‑funktion.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Varför inte bara anropa `new Document("file.docx")`? För utan `LoadOptions` förlorar du möjligheten att knyta in dig i laddnings‑händelserna. `LoadOptions` är den enda platsen där Aspose.Words låter dig **anpassa dokumentladdning**.

## Steg 2 – Registrera en varningsåteruppringning för att spåra saknade teckensnitt

Nu kommer stjärnan i showen: vi **registrerar en varningsåteruppringning** som implementerar `IWarningCallback`. Inuti `warning`‑metoden filtrerar vi på `WarningType.FONT_SUBSTITUTION` och skriver ut ett hjälpsamt meddelande.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Några saker att notera:

- **Varför `IWarningCallback`?** Det är det gränssnitt som Aspose.Words använder för alla varningstyper, vilket ger dig en enda ingångspunkt för många möjliga problem.  
- **Filtrering är avgörande** – utan `if`‑kontrollen skulle du se varningar om saknade bilder, föråldrade funktioner osv., vilket skulle fylla dina loggar.  
- **Trådsäkerhet** – återuppringningen körs på samma tråd som laddar dokumentet, så du kan säkert uppdatera delade strukturer om du senare vill samla resultat.

Det kodsnutten **registrerar varningsåteruppringningen**, och från och med nu kommer varje saknad‑teckensnitt‑händelse att skrivas till `stdout`. Detta är kärnan i **spåra saknade teckensnitt**.

## Steg 3 – Ladda dokumentet med de konfigurerade `LoadOptions`

Med återuppringningen på plats laddar vi äntligen filen. Om dokumentet refererar till ett teckensnitt du inte har, triggas återuppringningen innan dokumentobjektet är helt konstruerat.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Byt ut `YOUR_DIRECTORY` mot den faktiska sökvägen på din maskin. `Document`‑konstruktorn läser filen, applicerar eventuellt lösenord (om du har angett ett i `loadOptions`), och utlöser varningsåteruppringningen för varje saknat teckensnitt. Du kommer att se output liknande:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Den raden bevisar att du framgångsrikt **spårat saknade teckensnitt**.

## Steg 4 – Fortsätt bearbeta dokumentet (valfritt)

I detta skede kan du manipulera dokumentet hur du vill – ersätta text, infoga bilder eller till och med programatiskt byta de ersatta teckensnitten. Återuppringningen har redan gett dig en lista på problematiska teckensnitt, så du kan till exempel bädda in ett reservteckensnitt:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Känn dig fri att hoppa över detta block om du bara behöver **spåra saknade teckensnitt**. Nyckeln är att du nu har informationen du behöver för att fatta ett välgrundat beslut.

## Steg 5 – Spara det bearbetade dokumentet

Till sist persisterar vi dokumentet. Du kan skriva över originalet, spara till en ny plats eller exportera till PDF – allt utan att förlora varningsdata du fångade tidigare.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Att köra hela klassen kommer att producera konsolutdata för varje saknat teckensnitt och en ny fil kallad `processed.docx` i samma mapp.

## Komplett fungerande exempel

Nedan är den fullständiga Java‑klassen som du kan kopiera‑klistra in i din IDE. Den innehåller allt vi har diskuterat, plus en liten `main`‑metod‑wrapper.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Förväntad output

När du kör programmet mot ett dokument som använder ett teckensnitt som inte är installerat på ditt system, kommer du att se något liknande:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Om dokumentet **inte innehåller några saknade teckensnitt**, förblir konsolen tyst tills den sista raden “Document saved successfully.” – exakt vad du förväntar dig av en väl‑beteende **registrera varningsåteruppringning**‑implementation.

## Pro‑tips & vanliga fallgropar

- **Flera återuppringningar?** Aspose.Words tillåter bara en varningshanterare. Om du behöver logga både till en fil och till konsolen, implementera en sammansatt återuppringning som vidarebefordrar varningen till flera destinationer.  
- **Stora batcher** – när du bearbetar hundratals filer, överväg att återanvända en enda `LoadOptions`‑instans; att skapa en per fil ger onödig overhead.  
- **Krypterade dokument** – sätt lösenordet på `LoadOptions` innan du laddar, annars får du ett `IncorrectPasswordException` innan återuppringningen någonsin triggas.  
- **Prestanda** – återuppringningen körs synkront. Om du loggar till en fjärrtjänst, buffra meddelandena och skriv ut dem efter att laddningen är klar för att undvika I/O‑flaskhalsar.  
- **Teckensnittsfallback** – du kan också tillhandahålla en egen `FontSource`‑samling om du har proprietära teckensnitt som du vill att Aspose.Words ska överväga innan den faller tillbaka på systemteckensnitt.

## Slutsats

Du har just lärt dig hur du **registrerar varningsåteruppringning** i Java, effektivt **spårar saknade teckensnitt**, och **anpassar dokumentladdning** med Aspose.Words. Lösningen är självständig, körs med en enda `main`‑metod, och ger dig omedelbar insyn i varje teckensnittsersättning som annars skulle gå obemärkt förbi.

Nästa steg? Prova att utöka återuppringningen så att den skriver varningar till en CSV‑fil för revisionsändamål, eller kombinera den med en batch‑processor som automatiskt bäddar in saknade teckensnitt. Du kan också utforska andra varningstyper som `IMAGE_SUBSTITUTION` eller `DEPRECATED_FEATURE` – samma mönster gäller.

Lycka till med kodningen, och må dina dokument alltid renderas exakt som du avsett!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")

## Vad bör du lära dig härnäst?

- [Varningsåteruppringning i Word-dokument](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Anpassa temafärger och teckensnitt i Aspose.Words Java: En omfattande guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Spåra ändringar i Word-dokument med Aspose.Words Java: En komplett guide till dokumentrevisioner](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}