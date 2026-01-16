---
date: 2026-01-16
description: Lär dig hur du markerar stavfel i Word med Aspose.Words för Java, och
  upptäck hur du ställer in tecken per rad, anpassar visningsalternativ och rensar
  upp stilar.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Markera stavfel i Word med Aspose.Words Java
url: /sv/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda dokumentalternativ och inställningar i Aspose.Words för Java

## Introduktion till att använda dokumentalternativ och inställningar i Aspose.Words för Java

I den här omfattande guiden kommer du att lära dig **hur du markerar stavfel i Word** med Aspose.Words för Java samtidigt som du behärskar relaterade inställningar såsom visningsalternativ, sidlayout och stilrensning. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer exemplen nedan att hjälpa dig skapa robusta, felmedvetna dokument som fungerar i alla Word‑versioner.

## Snabba svar
- **Hur kan jag markera stavfel i Word?** Använd `setShowSpellingErrors(true)` på `Document`‑objektet.  
- **Kan jag också visa grammatiska fel?** Ja—anropa `setShowGrammaticalErrors(true)`.  
- **Vilken metod sätter tecken per rad?** `getPageSetup().setCharactersPerLine(int)`.  
- **Vilket API optimerar för en specifik Word‑version?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Finns det ett sätt att rensa oanvända stilar?** Använd `CleanupOptions` med `setUnusedStyles(true)` och anropa `doc.cleanup(options)`.

## Hur man markerar stavfel i Word?

Aspose.Words gör det enkelt att slå på markering av stavfel. När dokumentet öppnas i Microsoft Word visas felstavade ord med den välkända röda understreckningen, vilket hjälper slutanvändare att snabbt upptäcka problem.

## Hur man ställer in tecken per rad

Att kontrollera antalet tecken per rad är avgörande för layout med fast bredd (t.ex. kodlistor eller äldre formulär). Klassen `PageSetup` erbjuder `setCharactersPerLine(int)` som låter dig definiera detta värde exakt.

## Hur man visar grammatiska fel

Utöver stavning kan du också aktivera visning av grammatiska fel. Detta är användbart när du skriver innehåll som måste följa stilguider eller när du bygger korrekturverktyg.

## Optimera dokument för kompatibilitet

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

En viktig aspekt av dokumenthantering är att säkerställa kompatibilitet med olika versioner av Microsoft Word. Aspose.Words för Java erbjuder ett enkelt sätt att optimera dokument för specifika Word‑versioner. I exemplet ovan optimerar vi ett dokument för Word 2016, vilket garanterar sömlös kompatibilitet.

## Identifiera grammatiska och stavfel

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Noggrannhet är av största vikt när man arbetar med dokument. Aspose.Words för Java gör det möjligt att markera både grammatiska och stavfel i dina dokument, vilket gör korrekturläsning och redigering mer effektiv.

## Rensa oanvända stilar och listor

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Effektiv hantering av dokumentstilar och listor är nödvändig för att bibehålla dokumentkonsistens. Aspose.Words för Java låter dig rensa oanvända stilar och listor, vilket säkerställer en strömlinjeformad och organiserad dokumentstruktur.

## Ta bort duplicerade stilar

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Duplicerade stilar kan leda till förvirring och inkonsekvens i dina dokument. Med Aspose.Words för Java kan du enkelt ta bort duplicerade stilar och därmed behålla dokumentets tydlighet och sammanhang.

## Anpassa visningsalternativ för dokument

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Att skräddarsy hur dokumentet visas är avgörande. Aspose.Words för Java låter dig ställa in olika visningsalternativ, såsom sidlayout och zoomprocent, för att förbättra läsbarheten.

## Konfigurera sidinställningar för dokument

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Exakta sidinställningar är viktiga för dokumentformatering. Aspose.Words för Java ger dig möjlighet att ange layoutlägen, **tecken per rad** och rader per sida, så att dina dokument blir visuellt tilltalande.

## Ställa in redigeringsspråk

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Redigeringsspråk spelar en viktig roll i dokumentbehandling. Med Aspose.Words för Java kan du ange och anpassa redigeringsspråk för att passa ditt dokuments språkliga behov.

## Slutsats

I den här guiden har vi gått igenom de olika dokumentalternativen och inställningarna som finns i Aspose.Words för Java. Från optimering och felvisning till stilrensning och visningsalternativ, erbjuder detta kraftfulla bibliotek omfattande möjligheter för att hantera och anpassa dina dokument.

## Vanliga frågor

### Hur optimerar jag ett dokument för en specifik Word‑version?

För att optimera ett dokument för en specifik Word‑version, använd metoden `optimizeFor` och ange önskad version. Till exempel, för att optimera för Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Hur kan jag markera grammatiska och stavfel i ett dokument?

Du kan aktivera visning av grammatiska och stavfel i ett dokument med följande kod:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Vad är syftet med att rensa oanvända stilar och listor?

Att rensa oanvända stilar och listor hjälper till att upprätthålla en ren och organiserad dokumentstruktur. Det tar bort onödig skräpförvaring, vilket förbättrar dokumentets läsbarhet och konsekvens.

### Hur kan jag ta bort duplicerade stilar från ett dokument?

För att ta bort duplicerade stilar från ett dokument, använd `cleanup`‑metoden med alternativet `duplicateStyle` satt till `true`. Här är ett exempel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Hur anpassar jag visningsalternativen för ett dokument?

Du kan anpassa dokumentets visningsalternativ med klassen `ViewOptions`. Till exempel, för att sätta vystyper till sidlayout och zoom till 50 %:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Ytterligare tips & vanliga fallgropar

- **Aktivera både stavnings‑ och grammatikkontroller** när du behöver en heltäckande korrekturläsning. Att glömma någon av flaggorna (`setShowGrammaticalErrors` eller `setShowSpellingErrors`) kan leda till att fel förbises.  
- **När du ställer in tecken per rad**, kom ihåg att värdet samverkar med det valda teckensnittet och sidmarginalerna. Testa med den faktiska dokumentlayouten för att undvika oväntade radbrytningar.  
- **Rensningsoperationer är oåterkalleliga** på originalfilen. Arbeta alltid på en kopia eller använd versionskontroll för att bevara den ursprungliga formateringen.  
- **Inställningar för redigeringsspråk** påverkar stavningskontrollen. Om du riktar dig mot flerspråkiga dokument, lägg till alla relevanta språk i `LanguagePreferences`.

---

**Senast uppdaterad:** 2026-01-16  
**Testat med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}