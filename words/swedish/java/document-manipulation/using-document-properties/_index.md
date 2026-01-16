---
date: 2026-01-16
description: Lär dig hur du konverterar tum till punkter, läser dokumentmetadata i
  Java, lägger till anpassade egenskaper i Java och ställer in sidmarginaler i Java
  med Aspose.Words för Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Konvertera tum till punkter – Använda dokumentegenskaper i Aspose.Words för
  Java
url: /sv/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera tum till punkter – Använda dokumentegenskaper i Aspose.Words för Java

I den här handledningen kommer du att upptäcka hur du **konverterar tum till punkter** när du ställer in sidmarginaler, läser dokumentmetadata i Java, lägger till anpassade egenskaper i Java och arbetar med inbyggda dokumentegenskaper med Aspose.Words för Java. Oavsett om du genererar rapporter, fakturor eller juridiska dokument ger behärskning av dessa tekniker dig finjusterad kontroll över utseendet och metadata i dina Word-filer.

## Snabba svar
- **Hur konverterar jag tum till punkter?** Använd `ConvertUtil.inchToPoint(value)` från Aspose.Words.
- **Kan jag läsa dokumentmetadata i Java?** Ja – anropa `doc.getBuiltInDocumentProperties()` eller `doc.getCustomDocumentProperties()`.
- **Hur lägger jag till en anpassad egenskap i Java?** Använd `doc.getCustomDocumentProperties().add(name, value)`.
- **Vilken metod sätter sidmarginaler i punkter?** `PageSetup.setTopMargin`, `setBottomMargin` osv. accepterar punktvärden.
- **Stöds länka till ett bokmärke?** Ja – använd `addLinkToContent` på samlingen av anpassade egenskaper.

## Introduktion till dokumentegenskaper

Dokumentegenskaper är en viktig del av alla Word-filer. De lagrar information såsom titel, författare, ämne, nyckelord och eventuell anpassad metadata du behöver för efterföljande bearbetning. I Aspose.Words för Java kan du manipulera både inbyggda och anpassade dokumentegenskaper, och du kan också kontrollera layoutdetaljer som marginaler genom att konvertera mätenheter (t.ex. **konvertera tum till punkter**).

## Vad är “konvertera tum till punkter”?

I Word uttrycks layoutmått i punkter (1 punkt = 1/72 tum). Att konvertera tum till punkter låter dig definiera marginaler, indrag och avstånd med välbekanta imperiella enheter medan API:et arbetar med punkter internt.

## Varför hantera dokumentmetadata i Java?

Att bädda in metadata gör det enklare att söka, kategorisera och automatisera arbetsflöden. Till exempel kan du märka ett avtal med en “Authorized”-flagga eller lagra ett revisionsnummer för revisionsspår. Att läsa och skriva denna information programatiskt säkerställer konsistens över stora dokumentbatchar.

## Förutsättningar
- Java 17+ (eller kompatibel JDK)
- Aspose.Words för Java-biblioteket tillagt i ditt projekt (Maven/Gradle)
- En exempel `.docx`-fil (t.ex. `Properties.docx`) placerad i en åtkomlig katalog

## Steg‑för‑steg‑guide

### Enumerera inbyggda dokumentegenskaper
Nedan är ett enkelt test som öppnar ett dokument och skriver ut alla inbyggda egenskaper såsom Title, Author och Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Proffstips:** Använd detta kodstycke för att verifiera att din metadata har skrivits korrekt under tidigare steg.

### Lägga till anpassade dokumentegenskaper (add custom properties java)
Anpassade egenskaper låter dig lagra vilken datatyp du behöver—boolean, string, datum, nummer osv.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Varför detta är viktigt:** Att lägga till en flagga som **Authorized** kan driva efterföljande godkännandeflöden utan att ändra dokumentets innehåll.

### Ta bort en anpassad egenskap
Om en egenskap inte längre behövs kan du radera den på ett rent sätt.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Konfigurera en länk till innehåll (bokmärkeslänkning)
Du kan skapa ett bokmärke och sedan lägga till en anpassad egenskap som pekar på det bokmärket, vilket möjliggör dynamiska korsreferenser.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Konvertera mellan måttenheter (set page margins java)
Här är där huvudnyckelordet glänser. Vi sätter marginaler i tum och sedan **konverterar tum till punkter** med `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Obs:** `ConvertUtil` erbjuder också `pointToInch`, `mmToPoint` osv. för flexibel layouthantering.

### Använda kontrolltecken (read document metadata java)
Kontrolltecken hjälper dig att rensa upp textströmmar. Detta exempel ersätter ett vagnretur (`\r`) med Windows radbrytningsekvensen (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Vanliga problem & lösningar

| Problem | Orsak | Lösning |
|-------|-------|-----|
| Marginalerna ser felaktiga ut efter konvertering | Fel enhet används (t.ex. cm istället för tum) | Verifiera att du anropar `ConvertUtil.inchToPoint` för tumvärden |
| Anpassad egenskap visas inte | Egenskapen lades till efter att dokumentet sparats | Anropa `doc.save(...)` efter att egenskaper lagts till |
| Bokmärkeslänk trasig | Stavfel i bokmärkesnamnet | Säkerställ att bokmärkesnamnet matchar exakt i `addLinkToContent` |

## Vanliga frågor

### Hur får jag åtkomst till inbyggda dokumentegenskaper?

För att få åtkomst till inbyggda dokumentegenskaper i Aspose.Words för Java kan du använda metoden `getBuiltInDocumentProperties` på `Document`-objektet. Denna metod returnerar en samling av inbyggda egenskaper som du kan iterera igenom.

### Kan jag lägga till anpassade dokumentegenskaper i ett dokument?

Ja, du kan lägga till anpassade dokumentegenskaper i ett dokument med hjälp av samlingen `CustomDocumentProperties`. Du kan definiera anpassade egenskaper med olika datatyper, inklusive strängar, boolean, datum och numeriska värden.

### Hur kan jag ta bort en specifik anpassad dokumentegenskap?

För att ta bort en specifik anpassad dokumentegenskap kan du använda `remove`-metoden på samlingen `CustomDocumentProperties` och skicka namnet på egenskapen du vill ta bort som parameter.

### Vad är syftet med att länka till innehåll inom ett dokument?

Att länka till innehåll inom ett dokument gör det möjligt att skapa dynamiska referenser till specifika delar av dokumentet. Detta kan vara användbart för att skapa interaktiva dokument eller korsreferenser mellan sektioner.

### Hur kan jag konvertera mellan olika måttenheter i Aspose.Words för Java?

Du kan konvertera mellan olika måttenheter i Aspose.Words för Java genom att använda klassen `ConvertUtil`. Den erbjuder metoder för att konvertera enheter såsom tum till punkter, punkter till centimeter och mer.

## Vanliga frågor och svar

**Q: Hur läser jag dokumentmetadata Java utan att ladda hela filen?**  
A: Använd `DocumentInfo` för att hämta kärnegenskaper utan att helt ladda dokumentets innehåll.

**Q: Kan jag programatiskt ställa in sidmarginaler i Java för befintliga dokument?**  
A: Ja—öppna dokumentet, ändra `PageSetup`-marginaler (konvertera tum till punkter om det behövs) och spara.

**Q: Är det möjligt att exportera anpassade egenskaper till PDF-metadata?**  
A: Vid sparande till PDF mappar Aspose.Words automatiskt anpassade dokumentegenskaper till PDF:s anpassade metadata.

**Q: Påverkar kontrolltecken PDF-konverteringen?**  
A: De bevaras under konverteringen; dock kan du vilja normalisera radslut för konsekvens.

**Q: Vilken version av Aspose.Words krävs för `ConvertUtil`?**  
A: `ConvertUtil` har funnits sedan Aspose.Words 16.5; alla nyare versioner stöder den.

## Slutsats

Genom att behärska **konvertera tum till punkter**, läsa dokumentmetadata i Java och lägga till anpassade egenskaper i Java får du full kontroll över både den visuella layouten och den dolda datan i dina Word-filer. Dessa möjligheter ger dig möjlighet att bygga automatiserade dokumentpipeline, upprätthålla efterlevnad och skapa rikt formaterade rapporter — allt med Aspose.Words för Java.

---

**Senast uppdaterad:** 2026-01-16  
**Testad med:** Aspose.Words for Java 24.11  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}