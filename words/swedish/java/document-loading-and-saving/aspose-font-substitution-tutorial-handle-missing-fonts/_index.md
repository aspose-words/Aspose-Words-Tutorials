---
category: general
date: 2026-05-04
description: Aspose-handledning om teckensnittssubstitution visar hur man hanterar
  saknade teckensnitt i Java med varningsåteruppringningar och LoadOptions för pålitlig
  dokumentladdning.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: sv
og_description: Aspose guide för teckensnittssubstitution förklarar hur du hanterar
  saknade teckensnitt i Java, fångar substitutionshändelser och ser till att dina
  dokument ser rätt ut.
og_title: Aspose-handledning för teckensnittssubstitution – Hantera saknade teckensnitt
tags:
- Aspose.Words
- Java
- Font Management
title: 'Aspose teckensnittssubstitution – Handledning: Hantera saknade teckensnitt'
url: /sv/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution handledning – Hantera saknade teckensnitt

Har du någonsin behövt en **aspose font substitution tutorial** eftersom en DOCX du laddar plötsligt ser felaktig ut? Du är inte ensam—saknade teckensnitt är en lurig källa till buggar som kan förvandla en perfekt formaterad rapport till ett rörigt mess. Den goda nyheten är att Aspose.Words ger dig ett rent sätt att **hantera saknade teckensnitt** innan de förstör din layout.

I den här guiden går vi igenom ett komplett, färdigt‑att‑köra Java‑exempel som fångar font‑substitution‑varningar, förklarar varför varje del är viktig, och visar hur du verifierar resultatet. I slutet vet du exakt hur du håller dina dokument skarpa även när de ursprungliga teckensnitten inte finns på maskinen.

## Vad du kommer att lära dig

- Hur man registrerar en anpassad `IWarningCallback` som lyssnar på `FONT_SUBSTITUTION`‑händelser.  
- Varför användning av `LoadOptions` är det rekommenderade tillvägagångssättet för pålitlig teckensnittshantering.  
- Sätt att testa lösningen med ett medvetet trasigt dokument.  
- Vanliga fallgropar (t.ex. att glömma att sätta callbacken) och snabba lösningar.  

**Förutsättningar**: Java 8+ installerat, en giltig Aspose.Words för Java‑licens (eller den fria utvärderingen), och en grundläggande IDE som IntelliJ eller Eclipse. Inga andra externa bibliotek behövs.

---

![Aspose font substitution tutorial diagram](https://example.com/images/font-substitution-diagram.png "Aspose font substitution tutorial diagram")

## Steg 1 – Definiera en varnings‑callback för att fånga substitutioner  

Det första Aspose.Words gör när den inte kan hitta ett begärt teckensnitt är att avfyra en `WarningInfo`‑händelse. Genom att implementera `IWarningCallback` kan du logga, visa eller till och med avbryta inläsningen om du föredrar.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Varför detta är viktigt** – Utan en callback skulle du aldrig veta att Aspose bytte *Arial* mot *Liberation Sans* (eller vilken reserv som helst). Den tysta bytet kan orsaka layoutförändringar, särskilt i tabeller eller flerkolumnslayouter.

---

## Steg 2 – Anslut callbacken till `LoadOptions`

`LoadOptions` är den centrala hubben för allt som påverkar hur ett dokument läses. Genom att ansluta callbacken här garanterar du att **alla** dokument som läses med dessa alternativ utlöser din varningslogik.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Tips** – Om du planerar att läsa in flera dokument i en batch, återanvänd samma `LoadOptions`‑instans. Det sparar objekt‑skapande overhead och håller din loggning konsekvent.

---

## Steg 3 – Läs in ett dokument som kan behöva teckensnittssubstitution  

Nu läser vi faktiskt en fil som vi vet saknar ett teckensnitt. Ersätt `YOUR_DIRECTORY` med mappen som innehåller dina testfiler.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

När laddaren stöter på en glyf som inte kan renderas, skriver callbacken från **Steg 1** ett vänligt meddelande till konsolen. Till exempel:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Edge case** – Om dokumentet innehåller *inbäddade* teckensnitt kommer Aspose att använda dem först och hoppa över varningen. Det är förväntat beteende; du ser bara varningar för faktiskt saknade teckensnitt.

---

## Steg 4 – Spara dokumentet (nu med substituerade teckensnitt)

Efter att inläsningen är klar har Aspose redan bytt de saknade teckensnitten internt. Att spara dokumentet bevarar substitutionen, så utdata ser exakt ut som du såg i konsolen.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Öppna `loaded.docx` i Word eller LibreOffice så ser du att layouten är oförändrad, även om det ursprungliga teckensnittet inte är installerat på din maskin.

---

## Steg 5 – Verifiera resultatet programatiskt (valfritt)

Om du vill vara extra säker på att inga oväntade substitutioner smög igenom kan du fråga dokumentets teckensnittstabell efter inläsning.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

Utdata bör innehålla reservteckensnittet (t.ex. *Arial*) istället för det saknade. Detta är praktiskt för automatiserade pipelines där du behöver en garanti att den slutgiltiga PDF‑ eller DOCX‑filen uppfyller varumärkeskraven.

---

## Pro‑tips & vanliga fallgropar

- **Pro‑tips:** Sätt `loadOptions.setFontSettings(new FontSettings())` om du behöver peka Aspose på en anpassad teckensnittsmapp innan inläsning. Detta minskar antalet substitutioner.  
- **Se upp för:** Att glömma att anropa `setWarningCallback`. Koden körs fortfarande, men du missar de viktiga diagnostikmeddelandena.  
- **Prestanda‑notering:** Att läsa in stora dokument med många saknade teckensnitt kan generera många varningar. Överväg att begränsa utskriften eller skriva till en loggfil istället för `System.out`.  
- **Vad om du behöver avbryta vid substitution?** Ersätt anropet `System.out.println` med `throw new RuntimeException(info.getDescription())` i callbacken. Det tvingar inläsningen att misslyckas, vilket är användbart för strikta efterlevnadsscenarier.

---

## Vanliga frågor

**Q: Fungerar detta med PDF‑ eller bildformat?**  
A: Varnings‑callbacken är specifik för inläsningsfasen av Word‑bearbetningsformat (`.docx`, `.doc`, `.rtf`, etc.). PDF‑rendering använder en annan pipeline, men du kan fortfarande fånga teckensnitt‑relaterade varningar via `PdfLoadOptions`.

**Q: Kan jag ersätta ett specifikt teckensnitt med ett annat jag väljer?**  
A: Ja. Skapa ett `FontSettings`‑objekt, anropa `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")`, och tilldela det till `loadOptions.setFontSettings(fontSettings)`.

**Q: Är callbacken trådsäker?**  
A: Standardimplementeringen är inte synkroniserad. Om du läser in dokument parallellt, se till att din callback‑implementation hanterar samtidiga åtkomster (t.ex. med `ConcurrentLinkedQueue` för loggning).

---

## Slutsats

Du har nu en komplett **aspose font substitution tutorial** som visar hur du **hanterar saknade teckensnitt** på ett elegant sätt i Java. Genom att definiera en anpassad `IWarningCallback`, ansluta den till `LoadOptions` och spara dokumentet behåller du enhetlig output oavsett vilka teckensnitt som är installerade på värdmaskinen.  

Härifrån kan du utforska:

- Anpassade teckensnittssubstitutionstabeller för varumärkes‑kompatibla ersättningar.  
- Integrera varningsloggaren med SLF4J eller Log4j för produktions‑klassade diagnostik.  
- Utöka callbacken för att samla statistik över en batch av dokument.

Ge det ett försök, justera reservteckensnitten, och låt dina dokument förbli vackra även när de ursprungliga teckensnitten försvinner. Lycka till med kodningen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}