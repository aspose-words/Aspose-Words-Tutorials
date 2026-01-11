---
date: 2026-01-11
description: Lär dig hur du visar och döljer bokmärken samt skapar bokmärken i Java
  med Aspose.Words för Java för effektiv dokumentnavigering och -manipulering.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Visa/Dölj bokmärken med Aspose.Words för Java
url: /sv/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Visa/Dölj bokmärken med Aspose.Words för Java

## Introduktion till användning av bokmärken i Aspose.Words för Java

Bokmärken är en kraftfull funktion i Aspose.Words för Java som låter dig **create bookmark java**, navigera till specifikt innehåll och till och med **show hide bookmarks** när du behöver generera olika dokumentversioner. I den här steg‑för‑steg‑guiden går vi igenom hur du skapar, kommer åt, uppdaterar, kopierar och växlar synligheten för bokmärken, så att du får full kontroll över dokumentmanipulering.

## Snabba svar
- **Vad är det primära syftet med bokmärken?** Att markera och senare hämta specifika delar av ett dokument.  
- **Kan jag dölja bokmärkesmarkörer i slutresultatet?** Ja — använd show/hide‑API:t för att växla deras synlighet.  
- **Hur skapar jag ett bokmärke i en tabellcell?** Starta och avsluta bokmärket med `DocumentBuilder` medan markören är i cellen.  
- **Är det möjligt att kopiera bokmärkt text till ett annat dokument?** Absolut — använd `NodeImporter` för att bevara formatering.  
- **Vilken version av Aspose.Words krävs?** Vilken som helst av de senaste; koden fungerar med den senaste 2026‑byggnaden.

## Vad är “show hide bookmarks”?

Funktionen **show hide bookmarks** låter dig programatiskt visa eller dölja bokmärkesavgränsare i det sparade dokumentet. Detta är användbart när du vill generera ett rent utdata för slutanvändare samtidigt som du behåller bokmärkesdata för intern bearbetning.

## Varför använda bokmärken i Java‑dokumentautomatisering?

- **Effektiv navigering** – Hoppa direkt till sektioner utan att skanna hela filen.  
- **Dynamisk innehållsgenerering** – Infoga, ersätta eller ta bort text som är knuten till ett bokmärke.  
- **Villkorlig synlighet** – Visa eller dölja bokmärkesmarkörer baserat på användarpreferenser eller utdataformat.  
- **Återanvändning** – Kopiera bokmärkta fragment mellan dokument samtidigt som stilar bevaras.

## Förutsättningar
- Java Development Kit (JDK) 8 eller högre.  
- Aspose.Words för Java‑biblioteket tillagt i ditt projekt (Maven/Gradle eller JAR).  
- Grundläggande kunskap om klasserna `Document` och `DocumentBuilder`.

## Steg‑för‑steg‑guide

### Steg 1: Skapa ett bokmärke (create bookmark java)

För att lägga till ett bokmärke startar du det, skriver innehållet och avslutar det. Detta exempel skapar ett enkelt bokmärke med namnet **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Steg 2: Komma åt bokmärken (access bookmarks java)

Bokmärken kan hämtas antingen via deras noll‑baserade index eller via namn. Koden nedan demonstrerar båda metoderna.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Steg 3: Uppdatera bokmärkesdata (update bookmark text)

Du kan byta namn på ett bokmärke eller ersätta dess textinnehåll. Detta är praktiskt när det underliggande dokumentet förändras.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Steg 4: Arbeta med bokmärkt text (copy bookmarked text)

Att kopiera ett bokmärkt fragment till ett annat dokument samtidigt som den ursprungliga formateringen behålls är enkelt med `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Steg 5: Visa och dölja bokmärken (show hide bookmarks)

Följande kodsnutt visar hur du döljer ett bokmärkes markörer i den sparade filen. Skicka `false` för att dölja, `true` för att visa.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Steg 6: Avtråda radbokmärken (bookmark table cell)

När bokmärken sträcker sig över tabellrader kan de bli trassliga. Verktygsmetoderna nedan avtrådar dem och låter dig ta bort en specifik rad via dess bokmärke.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Vanliga problem och lösningar

| Problem | Lösning |
|-------|----------|
| **Bokmärke hittades inte** | Kontrollera att bokmärkesnamnet exakt matchar (skiftlägeskänsligt) och att dokumentet sparades efter skapandet. |
| **Kopierad text förlorar formatering** | Använd `ImportFormatMode.KEEP_SOURCE_FORMATTING` med `NodeImporter` som visas i Steg 4. |
| **Visa/dölj påverkar inte utdata** | Säkerställ att du anropar `showHideBookmarkedContent` **innan** du sparar dokumentet. |
| **Bokmärke i en tabellcell ignoreras** | Placera start-/slut‑anropen medan builder‑markören är i den önskade cellen. |

## Vanliga frågor

**Q: Hur skapar jag ett bokmärke i en tabellcell?**  
A: Använd `DocumentBuilder` för att flytta markören till den önskade cellen och anropa sedan `startBookmark` och `endBookmark` runt cellens innehåll.

**Q: Kan jag kopiera ett bokmärke till ett annat dokument?**  
A: Ja — använd klassen `NodeImporter` (se Steg 4) för att importera det bokmärkta noden samtidigt som den ursprungliga formateringen bevaras.

**Q: Hur kan jag ta bort en rad via dess bokmärke?**  
A: Lokalisera först raden som innehåller bokmärket och anropa sedan `remove` på radnoden (som demonstrerat i Steg 6).

**Q: Vilka är vanliga användningsområden för bokmärken?**  
A: Generera en innehållsförteckning, extrahera specifika sektioner för rapportering och automatisera dokumentmontering baserat på användarval.

**Q: Var kan jag hitta mer information om Aspose.Words för Java?**  
A: För detaljerad dokumentation och nedladdningar, besök [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Senast uppdaterad:** 2026-01-11  
**Testad med:** Aspose.Words för Java 24.11 (2026)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}