---
date: '2026-04-02'
description: Lär dig hur du skapar nästlade bokmärken, anger bokmärkesnivåer i dispositionen
  och sparar Word‑dokument som PDF‑filer med Aspose.Words för Java.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Skapa nästlade bokmärken och ange konturnivåer i PDF-filer med Aspose.Words
  för Java
url: /sv/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa nästlade bokmärken och ange konturnivåer i PDF‑filer med Aspose.Words för Java

## Introduktion
Har du problem med att hantera bokmärken när du konverterar Word‑dokument till PDF‑filer? **Den här handledningen visar hur du skapar nästlade bokmärken**, konfigurerar deras konturnivåer och sparar resultatet som en ren, navigerbar PDF med Aspose.Words för Java. I slutet av guiden har du en professionellt utseende PDF där läsarna kan hoppa direkt till de avsnitt de behöver.

**Vad du kommer att lära dig**
- Installera Aspose.Words för Java i ditt projekt  
- **Skapa nästlade bokmärken** i ett Word‑dokument  
- **Hur man anger bokmärkens** konturnivåer för tydlig hierarki  
- **Spara Word‑PDF‑bokmärken** med korrekt struktur  

### Snabba svar
- **Vilken är den primära klassen för att bygga dokument?** `DocumentBuilder`  
- **Vilken metod lägger till en bokmärkeskonturnivå?** `BookmarksOutlineLevels.add()`  
- **Behöver jag en licens för att exportera PDF‑filer?** En licens krävs för produktion; en gratis provperiod fungerar för utvärdering.  
- **Kan jag nästla bokmärken godtyckligt djupt?** Ja, men håll hierarkin läsbar för slutanvändarna.  
- **Vilken version av Aspose.Words krävs?** Version 25.3 eller senare.

## Vad är “skapa nästlade bokmärken”?
Nästlade bokmärken är bokmärken som placeras inuti andra bokmärken och bildar en förälder‑barn‑hierarki. I en PDF visas de som expanderbara objekt i bokmärkespanelen, vilket låter läsarna fälla ihop eller expandera avsnitt efter behov.

## Varför ange bokmärkeskonturnivåer?
Konturnivåer definierar den visuella nästlingsordningen i PDF‑filens bokmärkespanel. Korrekt nivåer förbättrar navigeringen, särskilt i långa juridiska avtal, tekniska rapporter eller e‑böcker där användare snabbt måste hitta information.

## Förutsättningar
- **Bibliotek och beroenden**: Aspose.Words för Java (version 25.3 eller senare).  
- **Miljö**: JDK 8+ och en IDE som IntelliJ IDEA eller Eclipse.  
- **Kunskap**: Grundläggande Java, Maven‑ eller Gradle‑kunskap.

### Installera Aspose.Words
Lägg till biblioteket i ditt projekt med Maven eller Gradle.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Licensanskaffning
Aspose.Words är en kommersiell produkt, men du kan börja med en gratis provperiod.

1. **Free Trial** – Ladda ner från [Aspose's release page](https://releases.aspose.com/words/java/) för att testa full funktionalitet.  
2. **Temporary License** – Ansök på [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) om du behöver en korttidsnyckel.  
3. **Purchase** – Köp en permanent licens via [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

Initiera licensfilen i din kod innan du använder några Aspose‑API:er för att låsa upp alla funktioner.

## Implementeringsguide

### Hur man skapar nästlade bokmärken i ett Word‑dokument
Vi kommer att bygga ett enkelt dokument och lägga till tre bokmärken, varav ett innehåller ett annat bokmärke.

#### Steg 1: Initiera dokumentet och byggaren
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### Steg 2: Infoga det första (föräldra) bokmärket
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Steg 3: Nästla ett andra bokmärke inuti det första
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Steg 4: Stäng det yttre bokmärket
```java
builder.endBookmark("Bookmark 1");
```

#### Steg 5: Lägg till ett oberoende tredje bokmärke
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Hur man anger bokmärkeskonturnivåer för PDF‑export
Nu kommer vi att konfigurera konturhierarkin som kommer att visas i den slutliga PDF‑filen.

#### Steg 1: Förbered `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Steg 2: Tilldela konturnivåer till varje bokmärke
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Steg 3: Spara dokumentet som en PDF med de konfigurerade bokmärkena
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Vanliga problem och lösningar
- **Missing bookmarks** – Verifiera att varje `startBookmark` har ett matchande `endBookmark`.  
- **Incorrect hierarchy** – Dubbelkolla de nivånummer du tilldelar; ett lägre nummer betyder en högre (förälder) nivå.  
- **License not applied** – Om bokmärken försvinner, se till att licensfilen laddas innan någon dokumentbehandling.  

## Praktiska tillämpningar
1. **Legal contracts** – Hoppa snabbt till klausuler, underklausuler och bilagor.  
2. **Technical reports** – Navigera avsnitt, tabeller och figurer utan att scrolla.  
3. **E‑learning material** – Låt studenter expandera kapitel och fälla ihop exempel efter behov.

## Prestandatips
- Ta bort oanvända avsnitt eller bilder innan du sparar för att hålla PDF‑filens storlek liten.  
- För mycket stora dokument, anropa `doc.cleanup()` eller bearbeta filen i delar för att minska minnesbelastningen.

## Vanliga frågor

**Q: Hur installerar jag Aspose.Words för Java?**  
A: Lägg till Maven‑ eller Gradle‑beroendet som visas ovan, placera sedan din licensfil i projektet och initiera den i koden.

**Q: Kan jag använda bokmärken utan att ange konturnivåer?**  
A: Ja, men utan konturnivåer kommer PDF‑filens bokmärkespanel att visa en platt lista, vilket gör navigeringen svårare.

**Q: Finns det någon gräns för hur djupt bokmärken kan nästlas?**  
A: Tekniskt sett ingen, men håll hierarkin rimlig (3‑4 nivåer) för användarens läsbarhet.

**Q: Hur hanterar Aspose mycket stora Word‑filer?**  
A: Biblioteket strömmar innehåll och erbjuder metoder som `Document.optimizeResources()` för att hålla minnesanvändningen låg.

**Q: Kan jag redigera bokmärkena efter att PDF‑filen har genererats?**  
A: Ja, du kan använda Aspose.PDF för Java för att ändra bokmärkestitlar, destinationer eller hierarki efter skapandet.

## Resurser
- [Aspose.Words-dokumentation](https://reference.aspose.com/words/java/)
- [Ladda ner senaste versionerna](https://releases.aspose.com/words/java/)
- [Köp en licens](https://purchase.aspose.com/buy)
- [Gratis provperiod](https://releases.aspose.com/words/java/)
- [Ansökan om tillfällig licens](https://purchase.aspose.com/temporary-license/)
- [Aspose supportforum](https://forum.aspose.com/c/words/10)

---

**Senast uppdaterad:** 2026-04-02  
**Testad med:** Aspose.Words 25.3 for Java  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}