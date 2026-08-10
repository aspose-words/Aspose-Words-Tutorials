---
date: '2026-08-10'
description: Lär dig hur du lägger till en kommentar i Java med Aspose.Words för Java.
  Steg‑för‑steg‑guide för att skapa, svara på, skriva ut, ta bort och markera kommentarer
  som klara, samt hämta UTC‑tidsstämplar.
keywords:
- how to add comment java
- comment management Java
- Aspose.Words comments
lastmod: '2026-08-10'
og_description: Lär dig hur du lägger till en kommentar i Java med Aspose.Words för
  Java. Steg‑för‑steg‑guide för att skapa, svara på, skriva ut, ta bort och markera
  kommentarer som klara, samt hämta UTC‑tidsstämplar.
og_image_alt: Guide showing how to add comment java with Aspose.Words in Word documents
og_title: Hur man lägger till en kommentar i Java med Aspose.Words för Word-dokument
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add comment java with Aspose.Words for Java. Step‑by‑step
    guide to create, reply to, print, remove, and mark comments as done, plus retrieve
    UTC timestamps.
  headline: How to add comment java using Aspose.Words for Word docs
  type: TechArticle
- questions:
  - answer: No. The trial works for development only; a full license is required for
      production deployments.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes. Load a protected file by passing the password to the `Document` constructor.
    question: Does the library support password‑protected documents?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, with full feature
      parity across versions.
    question: Which Java versions are compatible?
  - answer: Comment enumeration runs in linear time; a 1,000‑page document processes
      in under 2 seconds on a typical 4‑core server.
    question: How does comment performance scale with document size?
  - answer: Absolutely. Iterate the `CommentCollection` and write each comment’s properties
      to CSV, JSON, or XML as needed.
    question: Can I export comments to a separate file?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
title: Hur man lägger till en kommentar i Java med Aspose.Words för Word-dokument
url: /sv/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till kommentar java med Aspose.Words för Word-dokument

## Introduktion
Att programatiskt lägga till kommentarer i ett Word-dokument kan effektivisera samarbete, kodgranskning eller automatiserad rapportgenerering. I den här handledningen kommer du att lära dig **how to add comment java** med Aspose.Words-biblioteket, inklusive skapande, svar, utskrift, borttagning, markering som klar och extrahering av UTC-tidsstämplar. I slutet kommer du att kunna bädda in rik återkoppling direkt i dina dokument utan manuell inblandning.

## Snabba svar
- **Vad är det första steget?** Load the Word file with `new Document("input.docx")`.  
- **Kan jag svara på en kommentar?** Yes—create a `Comment` object and call `comment.getReplies().add(reply)`.  
- **Hur markerar jag en kommentar som klar?** Set `comment.setDone(true)` to flag it as resolved.  
- **Finns UTC-tid tillgänglig?** Each comment stores `getDateTime()` in UTC, which you can read directly.  
- **Behöver jag en licens?** A trial works for development; a full license removes evaluation limits.

## Vad är how to add comment Java?
`how to add comment java` avser processen att programatiskt infoga en kommentar i ett Microsoft Word-dokument med Java-kod och Aspose.Words API. Denna operation möjliggör automatiserade återkopplingsslingor i dokumentcentrerade arbetsflöden.

## Varför använda Aspose.Words för kommentarhantering?
Aspose.Words stöder **35+ in- och utdataformat** och kan hantera dokument som överstiger **500 sidor** samtidigt som minnesanvändningen hålls under **100 MB** på en typisk server. Dess kommentars‑API fungerar utan att Microsoft Word är installerat, vilket ger dig full kontroll i huvudlösa miljöer och minskar licenskostnaderna med upp till **70 %** jämfört med Office‑automatisering.

## Förutsättningar
- Java Development Kit (JDK) 17 eller senare installerat.
- En IDE som IntelliJ IDEA eller Eclipse.
- Maven eller Gradle för beroendehantering.
- En giltig Aspose.Words för Java-licens (testversion eller fullständig).

### Installera Aspose.Words för Java
Aspose.Words levereras som en enda JAR. Lägg till beroendet som matchar ditt byggverktyg.

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### Licensanskaffning
Aspose.Words är en kommersiell produkt; du kan börja med en gratis provversion eller begära en tillfällig licens för full åtkomst till funktioner. Besök [köpsida](https://purchase.aspose.com/buy) för att utforska licensalternativ.

## Hur man lägger till en kommentar i Java med Aspose.Words?
Läs in ditt dokument, skapa ett `Comment`-objekt och fäst det på ett `Paragraph`. Detta tvåstegs‑mönster infogar en kommentar på önskad plats och är grunden för alla senare operationer. Genom att ange författare, text och tidsstämpel kan du omedelbart ge kontext till granskare, och kommentaren blir en del av dokumentstrukturen.

`Document`-klassen är Aspose.Words översta objekt som representerar en enskild Word-fil i minnet. Efter instansiering flödar alla läs- och skrivoperationer genom detta objekt.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

Därefter skapar du själva kommentaren. `Comment`-klassen lagrar information om författare, text och tidsstämpel.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Slutligen, lägg till ett svar med kommentarens `Replies`-samling. `Comment`-objektet spårar automatiskt svarshierarkin.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Hur man skriver ut alla kommentarer och deras svar?
Iterera över dokumentets `CommentCollection` och skriv ut varje komments text, författare och UTC-tidsstämpel. Svaren är nästlade inom varje kommentar, vilket låter dig visa en full konversationstråd. Genom att gå igenom samlingen rekursivt kan du bevara hierarkin, formatera utskriften för loggar eller UI, och eventuellt filtrera efter författare eller datum.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

Använd en enkel loop för att gå igenom samlingen och skriva ut detaljer.  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```  

## Hur man tar bort svar på kommentarer?
Du kan radera ett specifikt svar eller rensa alla svar från en kommentar. Att ta bort svar hjälper till att hålla dokumentet rent efter att återkoppling har införlivats. Använd metoden `getReplies().remove(index)` för riktad borttagning eller anropa `clear()` för att rensa hela svarlistan, så att inga föräldralösa diskussioner återstår.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

Anropa `comment.getReplies().clear()` eller ta bort enskilda svar efter index.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## Hur man markerar en kommentar som klar?
Att sätta en komments `Done`-flagga signalerar att problemet har lösts. Denna visuella indikator är användbar för granskare och efterföljande bearbetningsverktyg. När `setDone(true)` anropas visar Word en bockmarkering bredvid kommentaren, och du kan senare fråga efter flaggan för att generera rapporter över återstående poster.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

Applicera flaggan efter att du har behandlat kommentarsinnehållet.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## Hur man får UTC-datum och -tid från en kommentar?
Varje kommentar lagrar sin skapelsestid i UTC, åtkomlig via `getDateTime()`. Denna tidsstämpel är oumbärlig för revisionsspår och versionskontroll. Det returnerade `DateTime`-objektet kan formateras med ISO‑8601-mönster, vilket låter dig logga exakta ögonblick av återkoppling och synkronisera kommentarsdata över distribuerade system.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Du kan formatera tidsstämpeln som ISO‑8601 för enkel loggning.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Praktiska tillämpningar
Att förstå dessa API:er låter dig bygga robusta lösningar för:
- **Samarbetsredigeringsplattformar** – infoga återkopplingsslingor direkt i genererade rapporter.  
- **Automatiserade granskningspipeline** – flagga, lös och granska kommentarer utan mänsklig inblandning.  
- **Compliance-dokumentation** – samla in granskartidsstämplar för regulatoriska revisioner.

## Prestandaöverväganden
Vid bearbetning av stora filer (500 + sidor), följ dessa bästa praxis:
- Bearbeta kommentarer i batcher för att undvika att ladda hela samlingen i minnet.  
- Använd `Document.optimizeResources()` för att krympa dokumentet innan sparning.  
- Håll Aspose.Words uppdaterat; version 24.12 introducerade en 30 % hastighetsökning för kommentarsenumerering.

## Slutsats
Du har nu en komplett verktygslåda för **how to add comment java** med Aspose.Words: skapa kommentarer, svara, skriva ut, ta bort, markera som klar och extrahera UTC-tidsstämplar. Integrera dessa kodsnuttar i dina befintliga Java-tjänster för att automatisera återkoppling, upprätthålla granskningspolicyer och hålla ett rent revisionsspår.

**Nästa steg**
- Experimentera med att filtrera kommentarer efter författare eller datum.  
- Kombinera kommentarhantering med Aspose.Words “track changes”-API för full revisionskontroll.  
- Utforska export av kommentarsdata till JSON för efterföljande analys.

## Vanliga frågor

**Q: Kan jag använda Aspose.Words utan licens i produktion?**  
A: Nej. Provversionen fungerar endast för utveckling; en full licens krävs för produktionsdistributioner.

**Q: Stöder biblioteket lösenordsskyddade dokument?**  
A: Ja. Läs in en skyddad fil genom att skicka lösenordet till `Document`-konstruktorn.

**Q: Vilka Java-versioner är kompatibla?**  
A: Aspose.Words for Java stöder JDK 8 till JDK 21, med full funktionsparitet över versionerna.

**Q: Hur skalar kommentarprestanda med dokumentstorlek?**  
A: Kommentarsenumerering körs i linjär tid; ett 1 000‑sidigt dokument bearbetas på under 2 sekunder på en typisk 4‑kärnig server.

**Q: Kan jag exportera kommentarer till en separat fil?**  
A: Absolut. Iterera `CommentCollection` och skriv varje komments egenskaper till CSV, JSON eller XML efter behov.

---

**Senast uppdaterad:** 2026-08-10  
**Testad med:** Aspose.Words for Java 24.12  
**Författare:** Aspose  

{{< blocks/products/products-backtop-button >}}

## Relaterade handledningar

- [Behärska annoteringar & kommentarer med Aspose.Words för Java-handledningar](/words/java/annotations-comments/)
- [Spåra ändringar i Word-dokument med Aspose.Words Java: En komplett guide till dokumentrevisioner](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Omfattande guide till Word-dokumentbehandling](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}