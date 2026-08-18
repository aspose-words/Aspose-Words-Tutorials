---
category: general
date: 2026-07-03
description: Ställ in återställningsläge för att återställa skadade Word‑filer i Java
  och visa sidantalet efter inläsning. Lär dig steg för steg med Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: sv
og_description: Ställ in återställningsläge i Aspose.Words för Java för att återställa
  korrupta Word-filer och visa sidantal. Följ hela exemplet nu.
og_title: Ställ in återställningsläge i Aspose.Words för Java – Komplett handledning
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Ställ in återhämtningsläge i Aspose.Words för Java – Fullständig guide
url: /sv/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in återhämtningsläge i Aspose.Words för Java – Fullständig guide

Har du någonsin funderat på hur du **ställer in återhämtningsläge** när du laddar en trasig `.docx`‑fil med Aspose.Words? Du är inte den enda som kliar sig i huvudet över korrupta Word‑dokument som vägrar öppnas. I den här handledningen går vi igenom exakt det – hur du konfigurerar biblioteket för att **återställa korrupta Word**‑filer och sedan **visa sidantalet** för det framgångsrikt laddade innehållet.

Vi täcker allt från den lilla `LoadOptions`‑justeringen till den sista `System.out.println` som berättar hur många sidor som överlevde räddningsuppdraget. Inga onödiga detaljer, bara en praktisk, kopiera‑och‑klistra‑klar lösning som fungerar med den senaste Aspose.Words 23.12‑utgåvan.

## Vad du kommer att lära dig

- Varför återhämtningsläget är viktigt och vilka alternativ Aspose.Words erbjuder.  
- Hur du **ställer in återhämtningsläge** programatiskt med Java.  
- Sätt att **visa sidantal** efter att dokumentet har laddats, för att bekräfta att återhämtningen lyckades.  
- Vanliga fallgropar när du hanterar korrupta Word‑filer och hur du undviker dem.  

Innan vi dyker ner, se till att du har:

1. En giltig Aspose.Words‑licens för Java (eller en tillfällig utvärderingsnyckel).  
2. Java 17 eller nyare installerat på din maskin.  
3. Den korrupta `Corrupted.docx`‑filen du vill testa.  

Har du allt? Bra – låt oss sätta igång.

> **Proffstips:** Även om du använder en provversion fungerar återhämtningsfunktionerna exakt likadant som i en licensierad build.

---

## ## Så här ställer du in återhämtningsläge med Aspose.Words för Java

Kärnan i lösningen finns i klassen `LoadOptions`. Som standard försöker Aspose.Words göra sitt bästa för att ladda ett dokument, men när filen är allvarligt skadad måste du tala om för den *hur* den ska bete sig. Det är här **set recovery mode** kommer in i bilden.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Varför `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words parserar alla fragment den kan förstå och sätter ihop ett delvis fungerande dokument. Idealiskt när du behöver *något* innehåll från en trasig fil.  
- **SKIP** – Biblioteket hoppar över korrupta sektioner helt, vilket kan vara snabbare men kan också kasta bort mer data.  

I de flesta verkliga scenarier är **PARSE** det säkrare valet eftersom det maximerar mängden återställbar text, bilder och formatering.

---

## ## Visa sidantal efter återhämtning

När dokumentet är laddat är nästa logiska steg att verifiera att operationen lyckades. Det enklaste, men ändå mest informativa, måttet är sidantalet. Metoden `Document.getPageCount()` gör exakt det.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Om filen var helt oläsbar kommer Aspose.Words att kasta ett undantag *innan* du ens når den här raden. När du ser ett sidantal på `0` eller ett mycket lågt tal betyder det vanligtvis att återhämtningsläget var tvungen att kasta stora delar av den ursprungliga filen.

**Förväntad utskrift (exempel):**

```
Document loaded, page count = 12
```

Det visar att biblioteket lyckades rekonstruera tolv sidor från den korrupta källan – ganska imponerande för en trasig `.docx`.

---

## ## Edge Cases & vanliga fallgropar

### 1️⃣ Korrupta sidhuvud-/sidfot‑sektioner
Ibland parseras bara huvudkroppen medan sidhuvuden och sidfötter går förlorade. Om du är beroende av dem för varumärkesprofilering kan du behöva återinföra dem efter återhämtning.

### 2️⃣ Bilder som inte laddas
Inbäddade bilder tas ofta bort när zip‑behållaren (det underliggande `.docx`‑formatet) är skadad. Du kan fånga detta genom att iterera över `doc.getSections()` och kontrollera `Section.getBody().getParagraphs()` för `Shape`‑objekt.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Om loopen inte skriver ut något har återhämtningsläget troligen hoppat över bilderna.

### 3️⃣ Stora dokument och minne
Att återställa ett 200‑sidigt korrupt dokument kan vara minnesintensivt. Överväg att öka JVM‑heap‑storleken (`-Xmx2g`) när du förväntar dig stora dokument.

### 4️⃣ Licensbegränsningar
Utvärderingsversionen begränsar vissa funktioner, men **återhämtning** är fullt funktionell. Däremot kan det utskrivna sidantalet vara begränsat till några få sidor i provversionen. Testa alltid med en licensierad build för produktion.

---

## ## Fullt end‑to‑end‑exempel (körbart)

Nedan finns ett självständigt program som du kan släppa in i vilket Maven‑ eller Gradle‑projekt som helst. Det inkluderar den nödvändiga beroendekonstruktionen för Aspose.Words 23.12.

### Maven `pom.xml`‑snippet

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Java‑källfil `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Vad detta gör:**

1. **Ställer in återhämtningsläge** – kärnan i vår handledning.  
2. Laddar den korrupta filen med de konfigurerade `LoadOptions`.  
3. **Visar sidantal**, så du får omedelbar återkoppling.  
4. Sparar en rengjord version (`Recovered.docx`) så att du kan öppna den i Word senare.

Kör programmet med:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Du bör se sidantalet skrivet till konsolen, vilket bekräftar att återhämtningen lyckades.

---

## ## Visuell översikt (Bild)

![flödesdiagram för att ställa in återhämtningsläge](https://example.com/images/recovery-mode-flow.png "Diagram som illustrerar hur återhämtningsläge ställs in i Aspose.Words för Java")

*Alt‑texten innehåller huvudnyckelordet **set recovery mode** för att tillfredsställa SEO.*

---

## ## Vanliga frågor

**Q: Vad händer om `RecoveryMode.PARSE` fortfarande kastar ett undantag?**  
A: Det betyder vanligtvis att filen är bortom räddning – kanske är zip‑behållaren helt trasig. I sådana fall kan du behöva ett tredjepartsreparationsverktyg innan du ger den till Aspose.Words.

**Q: Kan jag kombinera `RecoveryMode.PARSE` med egna callbacks för dokumentladdning?**  
A: Absolut. Implementera `IWarningCallback` för att fånga eventuella varningar som Aspose.Words avger under parsingsprocessen. Detta ger dig insikt i vilka delar som hoppats över.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**Q: Påverkar ändring av återhämtningsläget den ursprungliga filen?**  
A: Nej. Aspose.Words arbetar på en kopia i minnet; källfilen förblir orörd såvida du inte explicit anropar `doc.save()`.

---

## ## Sammanfattning

Vi har gått igenom hur du **ställer in återhämtningsläge** i Aspose.Words för Java, varför `PARSE` generellt är det bästa valet för att rädda ett trasigt dokument, och hur du **visar sidantal** för att verifiera resultatet. Genom att följa det kompletta exemplet har du nu en färdig lösning som kan **återställa korrupta Word**‑filer och ge dig omedelbar återkoppling på operationens framgång.

Nästa steg? Prova att byta till `RecoveryMode.SKIP` för att se skillnaden, experimentera med stora fler‑sektion‑filer, eller integrera logiken i en webbtjänst som automatiskt reparerar användaruppladdade dokument. Samma mönster fungerar för PDF‑filer (med Aspose.PDF) och även för återställning av ren text med andra bibliotek – kom bara ihåg huvudidén: konfigurera laddaren, försök återhämtning, och validera sedan med ett enkelt mått som sidantal.

Lycka till med kodandet, och må dina dokument förbli intakta!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Combine Multiple Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}