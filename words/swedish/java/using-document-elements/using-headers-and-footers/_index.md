---
title: Använda sidhuvuden och sidfötter i Aspose.Words för Java
linktitle: Använda sidhuvuden och sidfötter
second_title: Aspose.Words Java Document Processing API
description: Lär dig steg-för-steg hur du använder sidhuvuden och sidfötter i Aspose.Words för Java. Skapa professionella dokument utan ansträngning.
weight: 16
url: /sv/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använda sidhuvuden och sidfötter i Aspose.Words för Java


I den här omfattande guiden går vi igenom processen att arbeta med sidhuvuden och sidfötter i Aspose.Words för Java. Sidhuvuden och sidfötter är viktiga element i dokumentformatering, och Aspose.Words tillhandahåller kraftfulla verktyg för att skapa och anpassa dem efter dina behov.

Låt oss nu dyka in i vart och ett av dessa steg i detalj.

## 1. Introduktion till Aspose.Words

Aspose.Words är ett kraftfullt Java API som låter dig skapa, manipulera och rendera Word-dokument programmatiskt. Den tillhandahåller omfattande funktioner för dokumentformatering, inklusive sidhuvuden och sidfötter.

## 2. Ställa in din Java-miljö

 Innan du börjar använda Aspose.Words, se till att din Java-utvecklingsmiljö är korrekt inställd. Du kan hitta de nödvändiga installationsinstruktionerna på Aspose.Words-dokumentationssidan:[Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/).

## 3. Skapa ett nytt dokument

För att arbeta med sidhuvuden och sidfötter måste du skapa ett nytt dokument med Aspose.Words. Följande kod visar hur du gör detta:

```java
// Java-kod för att skapa ett nytt dokument
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Förstå sidinställningar

 Sidinställning är avgörande för att styra layouten på ditt dokument. Du kan ange olika egenskaper relaterade till sidhuvuden och sidfötter med hjälp av`PageSetup` klass. Till exempel:

```java
// Ställa in sidegenskaper
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Annan sidhuvud/sidfot på första sidan

Aspose.Words låter dig ha olika sidhuvuden och sidfötter för första sidan i ditt dokument. Använda`pageSetup.setDifferentFirstPageHeaderFooter(true);` för att aktivera den här funktionen.

## 6. Arbeta med rubriker

### 6.1. Lägga till text i rubriker

 Du kan lägga till text i rubriker med hjälp av`DocumentBuilder`. Här är ett exempel:

```java
// Lägger till text i rubriken på första sidan
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Infoga bilder i rubriker

 För att infoga bilder i rubriker kan du använda`insertImage` metod. Här är ett exempel:

```java
// Infogar en bild i rubriken
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Anpassa rubrikstilar

Du kan anpassa rubrikstilar genom att ställa in olika egenskaper som typsnitt, justering och mer, som visas i exemplen ovan.

## 7. Arbeta med sidfötter

### 7.1. Lägga till text i sidfötter

 I likhet med sidhuvuden kan du lägga till text i sidfötter med hjälp av`DocumentBuilder`. Här är ett exempel:

```java
// Lägger till text i den primära sidfoten
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Infoga text och fält efter behov
```

### 7.2. Infoga bilder i sidfötter

 För att infoga bilder i sidfötter, använd`insertImage` metod, precis som i rubriker.

### 7.3. Anpassa sidfotsstilar

 Anpassa sidfotsstilar med hjälp av`DocumentBuilder`liknande att anpassa rubriker.

## 8. Sidnumrering

 Du kan inkludera sidnummer i sidhuvuden och sidfötter med fält som`PAGE` och`NUMPAGES`. Dessa fält uppdateras automatiskt när du lägger till eller tar bort sidor.

## 9. Upphovsrättsinformation i sidfötter

För att lägga till upphovsrättsinformation till dokumentets sidfot kan du använda en tabell med två celler, justera en till vänster och den andra till höger, som visas i kodavsnittet.

## 10. Arbeta med flera sektioner

Aspose.Words låter dig arbeta med flera avsnitt i ett dokument. Du kan ställa in olika sidinställningar och sidhuvuden/sidfötter för varje avsnitt.

## 11. Landskapsorientering

Du kan ändra orienteringen för specifika avsnitt till liggande läge om det behövs.

## 12. Kopiera sidhuvuden/sidfötter från tidigare avsnitt

Att kopiera sidhuvuden och sidfötter från tidigare avsnitt kan spara tid när du skapar komplexa dokument.

## 13. Spara ditt dokument

När du har skapat och anpassat ditt dokument, glöm inte att spara det med hjälp av`doc.save()` metod.

## Komplett källkod
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Ange om vi vill att sidhuvuden/sidfötter på första sidan ska skilja sig från andra sidor.
        // Du kan också använda egenskapen PageSetup.OddAndEvenPagesHeaderFooter för att ange
        // olika sidhuvuden/sidfötter för udda och jämna sidor.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Infoga en positionerad bild i det övre/vänstra hörnet av rubriken.
        // Avståndet från sidans övre/vänsterkant är satt till 10 punkter.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Vi använder en tabell med två celler för att göra en del av texten på raden (med sidnumrering).
        // Att justeras till vänster och den andra delen av texten (med upphovsrätt) ska justeras till höger.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Den använder PAGE- och NUMPAGES-fälten för att automatiskt beräkna det aktuella sidnumret och många sidor.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Gör en sidbrytning för att skapa en andra sida där de primära sidhuvuden/sidfötterna kommer att synas.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Det här avsnittet behöver inte en annan sidhuvud/sidfot på första sidan vi behöver bara en titelsida i dokumentet,
        //och sidhuvudet/sidfoten för den här sidan har redan definierats i föregående avsnitt.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Det här avsnittet visar sidhuvuden/sidfötter från föregående avsnitt
        // anrop som standard currentSection.HeadersFooters.LinkToPrevious(false) för att avbryta denna sidbredd
        // är annorlunda för det nya avsnittet, och därför måste vi ställa in olika cellbredder för en sidfotstabell.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Om vi vill använda den redan befintliga sidhuvud/sidfotsuppsättningen för detta avsnitt.
        // Men med några mindre ändringar kan det vara lämpligt att kopiera sidhuvuden/sidfötter
        // från föregående avsnitt och tillämpa nödvändiga ändringar där vi vill ha dem.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Källkod för metoden copyHeadersFootersFromPreviousSection
```java
    /// <sammanfattning>
    /// Kloner och kopierar sidhuvuden/sidfötter bildar föregående avsnitt till det angivna avsnittet.
    /// </summary>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Slutsats

den här handledningen har vi täckt grunderna för att arbeta med sidhuvuden och sidfötter i Aspose.Words för Java. Du har lärt dig hur du skapar, anpassar och formaterar sidhuvuden och sidfötter, såväl som andra viktiga dokumentformateringstekniker.

 För ytterligare detaljer och avancerade funktioner, se[Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/).

## Vanliga frågor

### 1. Hur kan jag lägga till sidnummer i mitt dokuments sidfot?
 Du kan lägga till sidnummer genom att infoga`PAGE` fältet i sidfoten med Aspose.Words.

### 2. Är Aspose.Words kompatibel med Java utvecklingsmiljöer?
Ja, Aspose.Words ger stöd för Java-utveckling. Se till att du har nödvändiga inställningar på plats.

### 3. Kan jag anpassa typsnittet och stilen för sidhuvuden och sidfötter?
Absolut, du kan anpassa typsnitt, justering och andra stilar för att göra dina sidhuvuden och sidfötter visuellt tilltalande.

### 4. Är det möjligt att ha olika rubriker för udda och jämna sidor?
 Ja, du kan använda`PageSetup.OddAndEvenPagesHeaderFooter` för att ange olika rubriker för udda och jämna sidor.

### 5. Hur kommer jag igång med Aspose.Words för Java?
 För att börja, besök[Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/) för omfattande vägledning om hur du använder API.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
