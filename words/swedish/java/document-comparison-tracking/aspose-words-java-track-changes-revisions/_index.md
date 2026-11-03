---
date: '2026-11-02'
description: Lär dig hur du spårar ändringar i Word-dokument med Aspose.Words för
  Java, covering document comparison, inline revision handling, licensing, and performance
  tips.
keywords:
- how to track changes
- track formatting changes
- document comparison aspose
- aspose.words license java
lastmod: '2026-11-02'
og_description: Lär dig hur du spårar ändringar i Word-dokument med Aspose.Words för
  Java, including document comparison, inline revision handling, and licensing details.
og_image_alt: Guide showing how to track changes in Word documents with Aspose.Words
  Java
og_title: Hur du spårar ändringar i Word-dokument med Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-11-02'
  description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  headline: How to track changes in Word docs with Aspose.Words Java
  type: TechArticle
- description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  name: How to track changes in Word docs with Aspose.Words Java
  steps:
  - name: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
    text: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
  - name: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
    text: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
  - name: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
    text: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
  - name: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
    text: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
  - name: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
    text: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
  - name: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
    text: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
  type: HowTo
- questions:
  - answer: An inline node represents a run of text or a character‑level element inside
      a paragraph, such as a `Run` or a `Field`.
    question: What is an inline node in Aspose.Words?
  - answer: Call `document.startTrackRevisions()` on your `Document` instance before
      making any edits.
    question: How do I start tracking revisions with Aspose.Words Java?
  - answer: Yes, use `document.acceptAllRevisions()` or `document.rejectAllRevisions()`
      to apply the changes programmatically.
    question: Can I automate accepting or rejecting revisions in a document?
  - answer: It supports DOCX, PDF, HTML, ODT, RTF, EPUB, and more than 35 formats
      for both import and export.
    question: What types of documents does Aspose.Words support?
  - answer: Process the file section by section, use low‑memory load options, and
      leverage batch revision methods to keep CPU and RAM usage optimal.
    question: How do I handle large documents efficiently with Aspose.Words?
  type: FAQPage
tags:
- track changes
- Aspose.Words Java
- document revisions
- inline revisions
- Java document processing
title: Hur du spårar ändringar i Word-dokument med Aspose.Words Java
url: /sv/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man spårar ändringar i Word-dokument med Aspose.Words Java

Att samarbeta på viktiga dokument innebär ofta att du måste **spåra ändringar i Word-dokument** så att varje redigering är synlig och kontrollerbar. Aspose.Words för Java ger dig en programmatisk “Track Changes”-motor som fungerar utan Microsoft Word, vilket låter dig starta, fråga, acceptera eller avvisa revisioner direkt från din kod. I den här guiden kommer du att installera biblioteket, utforska hantering av inline‑revisioner och upptäcka prestandavänliga tekniker för stora filer.

## Snabba svar
- **Vilket bibliotek möjliggör spårning av ändringar i Word-dokument?** Aspose.Words for Java  
- **Vilken beroendehanterare rekommenderas?** Maven eller Gradle (båda stöds)  
- **Behöver jag en licens för utveckling?** En gratis provversion fungerar för utvärdering; en licens krävs för produktionsanvändning  
- **Kan jag bearbeta stora dokument effektivt?** Ja – använd sektion‑för‑sektion‑bearbetning och batch‑operationer  
- **Finns det en metod för att starta spårning programatiskt?** `document.startTrackRevisions()` startar spårningssessionen  

## Vad innebär att spåra ändringar?
`how to track changes` avser processen att programatiskt aktivera Words inbyggda revisionsspårningsfunktion. När den är aktiv registreras varje insättning, borttagning, formateringsändring eller flyttning som ett separat revisionsobjekt. Dessa objekt kan senare enumereras, granskas och antingen accepteras för att göra ändringen permanent eller avvisas för att förkasta den, vilket ger full spårbarhet av dokumentredigeringar.

## Varför använda Aspose.Words för spårning av ändringar?
Aspose.Words stöder **35+ in- och utdataformat** — inklusive DOCX, PDF, HTML och ODT — och kan bearbeta **500‑sidiga dokument på under 3 sekunder** på standard serverhårdvara utan att kräva Microsoft Word. API:et fungerar på Windows, Linux och macOS, vilket gör det idealiskt för molnbaserade eller lokala lösningar som behöver pålitlig revisionshantering.

## Förutsättningar

- **Java Development Kit (JDK):** version 8 eller högre.  
- **IDE:** IntelliJ IDEA, Eclipse eller NetBeans.  
- **Byggverktyg:** Maven eller Gradle för beroendehantering.  
- Grundläggande Java‑kunskaper för att förstå kodsnuttarna.

## Konfigurera Aspose.Words

### Maven‑konfiguration

Lägg till följande beroende i din `pom.xml`‑fil:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

### Gradle‑konfiguration

Inkludera den här raden i din `build.gradle`‑fil:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Licensanskaffning

Aspose erbjuder en gratis provversion för att testa dess funktioner, så att du kan utvärdera om den uppfyller dina behov. Så här kommer du igång:

1. **Gratis provversion:** Ladda ner biblioteket från [Aspose Downloads](https://releases.aspose.com/words/java/) och använd det med utvärderingsbegränsningar.  
2. **Tillfällig licens:** Skaffa en tillfällig licens för utökad användning utan utvärderingsrestriktioner genom att besöka [Temporary License](https://purchase.aspose.com/temporary-license/).  
3. **Köp licens:** Överväg att köpa om du behöver full åtkomst till Aspose.Words‑funktioner genom att följa instruktionerna på deras köpsida.

#### Grundläggande initiering

`Document` är Aspose.Words primära objekt som representerar en Word‑fil i minnet. För att initiera, skapa en instans av `Document` och börja arbeta med den:

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("input.docx");
        // Further processing here
    }
}
```

## Så spårar du ändringar i Word-dokument med Aspose.Words Java
`document.startTrackRevisions()` startar en revisionsspårningssession på dokumentet. Ladda ett Word‑fil, anropa `startTrackRevisions()` för att påbörja en spårningssession, gör önskade redigeringar och spara slutligen dokumentet. API:et registrerar varje redigering som ett revisionsobjekt som du senare kan enumerera, acceptera eller avvisa. Detta tvåstegsmönster — starta spårning, utföra redigeringar — täcker insättningar, borttagningar, formateringsändringar och flyttningar.

## Implementeringsguide

I det här avsnittet utforskar vi hur man hanterar olika typer av revisioner med Aspose.Words Java.

### Hantera inline‑revisioner

#### Översikt

När ändringar spåras visas inline‑revisioner inom ett stycke som körningar. De kan vara insättningar, borttagningar, formateringsändringar eller flyttoperationer. Att förstå varje typ låter dig bygga UI‑vänliga granskningsverktyg.

#### Kodimplementation

Följande kodsnutt visar hur du inspekterar revisionstypen för en inline‑nod:

```java
import com.aspose.words.Document;
import com.aspose.words.Paragraph;
import com.aspose.words.Run;
import com.aspose.words.Revision;
import org.testng.Assert;

public class RevisionHandler {
    public void handleRevisions() throws Exception {
        Document doc = new Document("Revision runs.docx");

        // Check the number of revisions
        Assert.assertEquals(6, doc.getRevisions().getCount());

        // Accessing a specific revision's parent node
        Run run = (Run) doc.getRevisions().get(0).getParentNode();

        Paragraph paragraph = run.getParentParagraph();
        com.aspose.words.RunCollection runs = paragraph.getRuns();

        Assert.assertEquals(runs.getCount(), 6);

        // Identifying different types of revisions
        Assert.assertTrue(runs.get(2).isInsertRevision());  // Insert revision
        Assert.assertTrue(runs.get(2).isFormatRevision());  // Format revision
        Assert.assertTrue(runs.get(4).isMoveFromRevision()); // Move from revision
        Assert.assertTrue(runs.get(1).isMoveToRevision());   // Move to revision
        Assert.assertTrue(runs.get(5).isDeleteRevision());   // Delete revision
    }
}
```

`RevisionType` är en uppräkning som klassificerar typen av förändring — Insert, Delete, Format, MoveFrom eller MoveTo. Genom att kontrollera denna egenskap kan du avgöra om du ska visa förändringen för användaren eller tillämpa automatiska accepteringsregler.

#### Förklaring
- **Insert‑revision:** Text som lagts till medan spårning är aktiv.  
- **Format‑revision:** Ändringar av teckensnitt, färg eller stil som tillämpas på befintlig text.  
- **Move from / to‑revisioner:** Representerar text som flyttats inom dokumentet; de visas alltid som ett par.  
- **Delete‑revision:** Text som tagits bort men behålls tills du accepterar eller avvisar den.

### Praktiska tillämpningar

Verkliga scenarier där hantering av revisioner är fördelaktig:

1. **Samarbetsredigering:** Team kan granska och godkänna ändringar innan ett slutligt avtal publiceras.  
2. **Juridisk dokumentgranskning:** Jurister spårar ändringar i klausuler och säkerställer att varje förändring är spårbar.  
3. **Programvarudokumentation:** Tekniska skribenter hanterar uppdateringar av API‑referenser samtidigt som versionshistoriken bevaras.

### Prestandaöverväganden

`LoadOptions` konfigurerar hur ett dokument laddas, inklusive minnesanvändningsinställningar. Bearbetning av stora, revisionsintensiva dokument kan vara minneskrävande. Följ dessa bästa praxis:

- **Sektion‑för‑sektion‑bearbetning:** Ladda och bearbeta en sektion åt gången för att hålla minnesanvändningen låg.  
- **Batch‑operationer:** Använd `Document.acceptAllRevisions()` eller `Document.rejectAllRevisions()` på hela sektioner istället för enskilda noder när det är möjligt.  
- **Streaming‑API:** För filer större än 1 GB, använd `LoadOptions` streaming‑läge för att undvika att ladda hela filen i RAM.

## Vanliga fallgropar och felsökning

`document.startTrackRevisions()` startar spårning av revisioner på den givna Document‑instansen.  

- **Saknade revisioner efter redigering:** Se till att du anropade `document.startTrackRevisions()` *innan* du gjorde några ändringar; att starta spårning efter redigeringar fångar inte tidigare modifieringar.  
- **Oväntade formateringsändringar:** Vissa stiländringar rapporteras som `RevisionType.Format`. Om du bara bryr dig om textinnehåll, filtrera bort formatrevisioner i din enumereringslogik.  
- **Stor dokumentnedgång:** Aktivera `LoadOptions.memoryUsage = LoadOptions.MemoryUsageMode.LowMemory` för att minska maximal minnesförbrukning.

## Vanliga frågor

`Document.acceptAllRevisions()` tillämpar alla väntande revisioner, vilket gör alla ändringar permanenta. `Document.rejectAllRevisions()` förkastar alla väntande revisioner och återställer dokumentet till dess ursprungliga tillstånd.

**Q: Vad är en inline‑nod i Aspose.Words?**  
A: En inline‑nod representerar en körning av text eller ett tecken‑nivå‑element inom ett stycke, såsom en `Run` eller ett `Field`.

**Q: Hur startar jag spårning av revisioner med Aspose.Words Java?**  
A: Anropa `document.startTrackRevisions()` på din `Document`‑instans innan du gör några redigeringar.

**Q: Kan jag automatisera att acceptera eller avvisa revisioner i ett dokument?**  
A: Ja, använd `document.acceptAllRevisions()` eller `document.rejectAllRevisions()` för att tillämpa förändringarna programatiskt.

**Q: Vilka dokumenttyper stöder Aspose.Words?**  
A: Det stöder DOCX, PDF, HTML, ODT, RTF, EPUB och mer än 35 format för både import och export.

**Q: Hur hanterar jag stora dokument effektivt med Aspose.Words?**  
A: Bearbeta filen sektion för sektion, använd låg‑minnes‑laddningsalternativ och utnyttja batch‑revisionsmetoder för att hålla CPU‑ och RAM‑användning optimal.

## Resurser

- [Aspose.Words Java-dokumentation](https://reference.aspose.com/words/java/)  
- [Ladda ner Aspose.Words för Java](https://releases.aspose.com/words/java/)  
- [Köp en licens](https://purchase.aspose.com/buy)  
- [Gratis provversion](https://releases.aspose.com/words/java/)  
- [Tillfällig licens](https://purchase.aspose.com/temporary-license/)  
- [Aspose Supportforum](https://forum.aspose.com/c/words/10)

Ge dig in på din resa med Aspose.Words Java idag, och utnyttja hela potentialen i dokumentbehandling i dina applikationer!

---

**Senast uppdaterad:** 2026-11-02  
**Testad med:** Aspose.Words 25.3 for Java  
**Författare:** Aspose

## Relaterade handledningar

- [Implementera spårning av ändringar i Aspose.Words för Java](/words/java/document-comparison-tracking/)
- [Konvertera Word till PDF med Aspose.Words för Java Dokumentkonverterings‑API](/words/java/document-converting/)
- [Aspose Words Loadoptions återställer korrupta Word‑dokument i Java](/words/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}