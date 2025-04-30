---
"description": "Lär dig steg för steg hur du använder sidhuvuden och sidfot i Aspose.Words för Java. Skapa professionella dokument utan ansträngning."
"linktitle": "Använda sidhuvuden och sidfot"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda sidhuvuden och sidfot i Aspose.Words för Java"
"url": "/sv/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda sidhuvuden och sidfot i Aspose.Words för Java


I den här omfattande guiden guidar vi dig genom processen att arbeta med sidhuvuden och sidfot i Aspose.Words för Java. Sidhuvuden och sidfot är viktiga element i dokumentformatering, och Aspose.Words erbjuder kraftfulla verktyg för att skapa och anpassa dem efter dina behov.

Låt oss nu gå in på vart och ett av dessa steg i detalj.

## 1. Introduktion till Aspose.Words

Aspose.Words är ett kraftfullt Java API som låter dig skapa, manipulera och rendera Word-dokument programmatiskt. Det erbjuder omfattande funktioner för dokumentformatering, inklusive sidhuvuden och sidfot.

## 2. Konfigurera din Java-miljö

Innan du börjar använda Aspose.Words, se till att din Java-utvecklingsmiljö är korrekt konfigurerad. Du hittar nödvändiga installationsanvisningar på dokumentationssidan för Aspose.Words: [Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/).

## 3. Skapa ett nytt dokument

För att arbeta med sidhuvuden och sidfot måste du skapa ett nytt dokument med Aspose.Words. Följande kod visar hur man gör detta:

```java
// Java-kod för att skapa ett nytt dokument
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Förstå sidinställningar

Sidinställningar är avgörande för att kontrollera dokumentets layout. Du kan ange olika egenskaper relaterade till sidhuvuden och sidfot med hjälp av `PageSetup` klass. Till exempel:

```java
// Konfigurera sidegenskaper
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Olika sidhuvud/sidfot på första sidan

Med Aspose.Words kan du ha olika sidhuvuden och sidfot för den första sidan i ditt dokument. `pageSetup.setDifferentFirstPageHeaderFooter(true);` för att aktivera den här funktionen.

## 6. Arbeta med rubriker

### 6.1. Lägga till text i rubriker

Du kan lägga till text i rubriker med hjälp av `DocumentBuilder`Här är ett exempel:

```java
// Lägga till text i rubriken på första sidan
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Infoga bilder i rubriker

För att infoga bilder i rubriker kan du använda `insertImage` metod. Här är ett exempel:

```java
// Infoga en bild i sidhuvudet
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Anpassa rubrikformat

Du kan anpassa rubrikstilar genom att ange olika egenskaper som teckensnitt, justering med mera, som visas i exemplen ovan.

## 7. Arbeta med sidfot

### 7.1. Lägga till text i sidfot

I likhet med sidhuvuden kan du lägga till text i sidfoten med hjälp av `DocumentBuilder`Här är ett exempel:

```java
// Lägga till text i den primära sidfoten
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Infoga text och fält efter behov
```

### 7.2. Infoga bilder i sidfot

För att infoga bilder i sidfoten, använd `insertImage` metod, precis som i rubriker.

### 7.3. Anpassa sidfotsstilar

Anpassa sidfotsstilar med hjälp av `DocumentBuilder`, ungefär som att anpassa rubriker.

## 8. Sidnumrering

Du kan inkludera sidnummer i dina sidhuvuden och sidfot med hjälp av fält som `PAGE` och `NUMPAGES`Dessa fält uppdateras automatiskt när du lägger till eller tar bort sidor.

## 9. Upphovsrättsinformation i sidfot

För att lägga till upphovsrättsinformation i dokumentets sidfot kan du använda en tabell med två celler, där den ena är justerad till vänster och den andra till höger, som visas i kodavsnittet.

## 10. Arbeta med flera sektioner

Med Aspose.Words kan du arbeta med flera avsnitt i ett dokument. Du kan ställa in olika sidinställningar och sidhuvuden/sidfot för varje avsnitt.

## 11. Liggande orientering

Du kan ändra orienteringen för specifika avsnitt till liggande läge om det behövs.

## 12. Kopiera sidhuvuden/sidfot från föregående avsnitt

Att kopiera sidhuvuden och sidfot från tidigare avsnitt kan spara tid när du skapar komplexa dokument.

## 13. Spara ditt dokument

När du har skapat och anpassat ditt dokument, glöm inte att spara det med hjälp av `doc.save()` metod.

## Komplett källkod
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Ange om vi vill att sidhuvuden/sidfoten på den första sidan ska skilja sig från andra sidor.
        // Du kan också använda egenskapen PageSetup.OddAndEvenPagesHeaderFooter för att ange
        // olika sidhuvuden/sidfot för udda och jämna sidor.
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
        // Infoga en placerad bild i sidhuvudets övre/vänstra hörn.
        // Avståndet från sidans övre/vänstra kanter är inställt på 10 punkter.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Vi använder en tabell med två celler för att skapa en del av texten på raden (med sidnumrering).
        // Ska vänsterjusteras och den andra delen av texten (med upphovsrätt) högerjusteras.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Den använder fälten PAGE och NUMPAGES för att automatiskt beräkna det aktuella sidnumret och antalet sidor.
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
        // Gör en sidbrytning för att skapa en andra sida där de primära sidhuvudena/sidfötterna kommer att synas.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Det här avsnittet behöver inte ett separat sidhuvud/sidfot på första sidan, vi behöver bara en titelsida i dokumentet.
        // och sidhuvudet/sidfoten för den här sidan har redan definierats i föregående avsnitt.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Det här avsnittet visar sidhuvuden/sidfot från föregående avsnitt
        // som standard anropas currentSection.HeadersFooters.LinkToPrevious(false) för att avbryta denna sidbredd
        // är annorlunda för det nya avsnittet, och därför behöver vi ange olika cellbredder för en sidfotstabell.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Om vi vill använda den redan befintliga uppsättningen sidhuvud/sidfot för det här avsnittet.
        // Men med några mindre ändringar kan det vara lämpligt att kopiera sidhuvuden/sidfot
        // från föregående avsnitt och tillämpa nödvändiga ändringar där vi vill ha dem.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Källkod för copyHeadersFootersFromPreviousSection-metoden
```java
    /// <sammanfattning>
    //Klonar och kopierar sidhuvuden/sidfot från föregående avsnitt till det angivna avsnittet.
    /// </sammanfattning>
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

I den här handledningen har vi gått igenom grunderna i att arbeta med sidhuvuden och sidfot i Aspose.Words för Java. Du har lärt dig hur du skapar, anpassar och formaterar sidhuvuden och sidfot, samt andra viktiga formateringstekniker för dokument.

För mer information och avancerade funktioner, se [Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/).

## Vanliga frågor

### 1. Hur kan jag lägga till sidnummer i mitt dokuments sidfot?
Du kan lägga till sidnummer genom att infoga `PAGE` fält i sidfoten med hjälp av Aspose.Words.

### 2. Är Aspose.Words kompatibelt med Java-utvecklingsmiljöer?
Ja, Aspose.Words erbjuder stöd för Java-utveckling. Se till att du har nödvändiga inställningar på plats.

### 3. Kan jag anpassa teckensnitt och stil för sidhuvuden och sidfot?
Absolut, du kan anpassa teckensnitt, justering och andra stilar för att göra dina sidhuvuden och sidfot visuellt tilltalande.

### 4. Är det möjligt att ha olika rubriker för udda och jämna sidor?
Ja, du kan använda `PageSetup.OddAndEvenPagesHeaderFooter` att ange olika rubriker för udda och jämna sidor.

### 5. Hur kommer jag igång med Aspose.Words för Java?
För att börja, besök [Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/) för omfattande vägledning om hur man använder API:et.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}