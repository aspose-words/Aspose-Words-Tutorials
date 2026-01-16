---
date: 2026-01-16
description: Leer hoe u spelfouten in Word kunt markeren met Aspose.Words voor Java,
  en ontdek hoe u tekens per regel kunt instellen, weergaveopties kunt aanpassen en
  stijlen kunt opschonen.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Spelfouten markeren in Word met Aspose.Words Java
url: /nl/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documentopties en -instellingen gebruiken in Aspose.Words voor Java

## Introductie tot het gebruik van documentopties en -instellingen in Aspose.Words voor Java

## Snelle antwoorden
- **Hoe kan ik spelfouten in Word markeren?** Gebruik `setShowSpellingErrors(true)` op het `Document`-object.  
- **Kan ik ook grammaticale fouten weergeven?** Ja—roep `setShowGrammaticalErrors(true)` aan.  
- **Welke methode stelt het aantal tekens per regel in?** `getPageSetup().setCharactersPerLine(int)`.  
- **Welke API optimaliseert voor een specifieke Word‑versie?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Is er een manier om ongebruikte stijlen op te schonen?** Gebruik `CleanupOptions` met `setUnusedStyles(true)` en roep `doc.cleanup(options)` aan.

## Hoe spelfouten in Word markeren?

Aspose.Words maakt het eenvoudig om markering van spelfouten in te schakelen. Wanneer het document wordt geopend in Microsoft Word, verschijnen verkeerd gespelde woorden met de bekende rode onderstreping, waardoor eindgebruikers problemen direct opmerken.

## Hoe het aantal tekens per regel instellen

Het aantal tekens per regel regelen is essentieel voor vaste‑breedte lay-outs (bijv. code‑lijsten of legacy‑formulieren). De `PageSetup`‑klasse biedt `setCharactersPerLine(int)`, waarmee u deze waarde nauwkeurig kunt definiëren.

## Hoe grammaticale fouten weergeven

Naast spelfouten kunt u ook de weergave van grammaticale fouten inschakelen. Dit is nuttig bij het opstellen van inhoud die moet voldoen aan stijlgidsen of bij het bouwen van proeflees‑tools.

## Optimizing Documents for Compatibility

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Een belangrijk aspect van documentbeheer is het waarborgen van compatibiliteit met verschillende versies van Microsoft Word. Aspose.Words for Java biedt een eenvoudige manier om documenten te optimaliseren voor specifieke Word‑versies. In het bovenstaande voorbeeld optimaliseren we een document voor Word 2016, waardoor naadloze compatibiliteit wordt gegarandeerd.

## Identifying Grammatical and Spelling Errors

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

Nauwkeurigheid is van het grootste belang bij het werken met documenten. Aspose.Words for Java stelt u in staat om grammaticale en spelfouten in uw documenten te markeren, waardoor proeflezen en bewerken efficiënter wordt.

## Cleaning Up Unused Styles and Lists

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

Het efficiënt beheren van documentstijlen en lijsten is essentieel voor het behouden van consistentie. Aspose.Words for Java maakt het mogelijk om ongebruikte stijlen en lijsten op te schonen, waardoor een gestroomlijnde en georganiseerde documentstructuur ontstaat.

## Removing Duplicate Styles

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

Duplicaatstijlen kunnen leiden tot verwarring en inconsistentie in uw documenten. Met Aspose.Words for Java kunt u eenvoudig duplicaatstijlen verwijderen, waardoor de duidelijkheid en samenhang van het document behouden blijven.

## Customizing Document Viewing Options

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

Het aanpassen van de weergave‑ervaring van uw documenten is cruciaal. Aspose.Words for Java stelt u in staat om verschillende weergave‑opties in te stellen, zoals paginalay-out en zoompercentage, om de leesbaarheid van het document te verbeteren.

## Configuring Document Page Setup

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

Een nauwkeurige paginainstelling is cruciaal voor documentopmaak. Aspose.Words for Java stelt u in staat om lay-outmodi, **tekens per regel** en regels per pagina in te stellen, zodat uw documenten er visueel aantrekkelijk uitzien.

## Setting Editing Languages

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

Bewerkings­talen spelen een belangrijke rol bij documentverwerking. Met Aspose.Words for Java kunt u bewerkings­talen instellen en aanpassen aan de linguïstische behoeften van uw document.

## Conclusion

In deze gids hebben we de verschillende documentopties en -instellingen van Aspose.Words voor Java onderzocht. Van optimalisatie en foutweergave tot stijl‑opschoning en weergave‑opties, biedt deze krachtige bibliotheek uitgebreide mogelijkheden voor het beheren en aanpassen van uw documenten.

## FAQ's

### Hoe optimaliseer ik een document voor een specifieke Word‑versie?

Om een document te optimaliseren voor een specifieke Word‑versie, gebruikt u de `optimizeFor`‑methode en geeft u de gewenste versie op. Bijvoorbeeld, om te optimaliseren voor Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Hoe kan ik grammaticale en spelfouten in een document markeren?

U kunt de weergave van grammaticale en spelfouten in een document inschakelen met de volgende code:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Wat is het doel van het opschonen van ongebruikte stijlen en lijsten?

Het opschonen van ongebruikte stijlen en lijsten helpt een schone en georganiseerde documentstructuur te behouden. Het verwijdert onnodige rommel, waardoor de leesbaarheid en consistentie van het document verbeteren.

### Hoe kan ik duplicaatstijlen uit een document verwijderen?

Om duplicaatstijlen uit een document te verwijderen, gebruikt u de `cleanup`‑methode met de `duplicateStyle`‑optie ingesteld op `true`. Hier is een voorbeeld:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Hoe pas ik de weergave‑opties van een document aan?

U kunt de weergave‑opties van een document aanpassen met de `ViewOptions`‑klasse. Bijvoorbeeld, om het weergavetype in te stellen op paginalay-out en in te zoomen op 50 %:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Extra tips & veelvoorkomende valkuilen

- **Schakel zowel spelling‑ als grammaticacontrole in** wanneer u uitgebreide proeflezen nodig heeft. Het vergeten van een van de vlaggen (`setShowGrammaticalErrors` of `setShowSpellingErrors`) kan ertoe leiden dat fouten onopgemerkt blijven.
- **Bij het instellen van tekens per regel**, onthoud dat de waarde interacteert met het gekozen lettertype en de paginamarges. Test met de daadwerkelijke documentlay-out om onverwachte regeleinden te voorkomen.
- **Opschoningsbewerkingen zijn onomkeerbaar** op het originele bestand. Werk altijd met een kopie of gebruik versiebeheer om de oorspronkelijke opmaak te behouden.
- **Voorkeuren voor bewerkingstalen** beïnvloeden het gedrag van de spellingscontrole. Als u zich richt op meertalige documenten, voeg dan alle relevante talen toe aan `LanguagePreferences`.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}