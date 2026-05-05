---
category: general
date: 2026-05-04
description: Lär dig hur Aspose Words LoadOptions kan återställa korrupta Word‑filer,
  använda återställningsläge, reparera korrupta docx och få Word‑sidantal i en enda
  handledning.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: sv
og_description: Mästra Aspose Words LoadOptions för att återställa korrupta Word-filer,
  välj rätt återställningsläge, reparera korrupta docx och hämta sidantal.
og_title: aspose words loadoptions – Återställ korrupta Word-dokument
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Återställ korrupta Word-dokument i Java
url: /sv/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Återställ korrupta Word-dokument i Java

Har du någonsin försökt öppna en Word‑fil som plötsligt vägrar att laddas? Det är den där magkänslan när en kund skickar dig en **corrupted docx** och du inte har någon aning om du kan rädda den. De goda nyheterna? Med **aspose words loadoptions** kan du tala om för Aspose.Words exakt hur den ska bete sig när ett dokument är skadat, om den ska kasta ett undantag eller försöka en tyst reparation.  

I den här guiden går vi igenom hur du använder `LoadOptions` för att **recover corrupted Word**‑filer, utforskar inställningarna för **use recovery mode**, ser hur du automatiskt **repair corrupted docx**, och avslutar med att **getting the word page count** för det återställda dokumentet. Inga externa verktyg, bara ren Java och Aspose.Words.

## Vad du behöver

- **Aspose.Words for Java** (v24.12 eller senare) – den senaste versionen lägger till några extra säkerhetskontroller.
- En **Java IDE** (IntelliJ IDEA, Eclipse eller till och med en enkel textredigerare med `javac`).
- Den **corrupted DOCX** du vill testa (vi kallar den `Corrupted.docx`).
- En **basic understanding** av Java‑syntax – inget avancerat, bara den vanliga `public static void main`.

> **Pro tip:** behåll en backup av originalfilen; återställningsförsök kan ibland skriva om delar av binärfilen.

## Steg 1: Skapa LoadOptions – kärnan i återställning

Det första du gör är att instansiera ett `LoadOptions`‑objekt. Detta objekt är din kontrollpanel; det talar om för Aspose.Words hur filen ska behandlas när den stöter på problem.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Varför är detta steg avgörande? För utan `LoadOptions` återgår biblioteket till sitt standardbeteende, vilket kan ignorera fel tyst eller, ännu värre, returnera ett delvis laddat dokument som kraschar senare. Genom att explicit konfigurera alternativen får du deterministisk felhantering.

## Steg 2: Välj rätt återställningsläge

Aspose.Words erbjuder två återställningsstrategier:

| Läge | Beteende |
|------|-----------|
| `RecoveryMode.STRICT` | Kastar ett undantag om dokumentet inte kan repareras helt. |
| `RecoveryMode.REPAIR` | Försöker reparera filen och fortsätter laddningen, även om en del innehåll går förlorat. |

För ett **recover corrupted word**‑scenario där du behöver veta om reparationen lyckades, är `STRICT` det säkraste alternativet. Om du föredrar en bästa‑insats‑metod, byt till `REPAIR`.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Varför välja den ena framför den andra?**  
> *STRICT* ger dig en tydlig signal—antingen är dokumentet användbart eller så måste du varna användaren. *REPAIR* är praktiskt i batch‑jobb där du kan acceptera att förlora en eller två bilder.

## Steg 3: Ladda det eventuellt korrupta dokumentet

Nu öppnar du faktiskt filen och skickar med `LoadOptions` som du just konfigurerade. Om filen är oåterställbar och du valde `STRICT` kommer ett undantag att bubbla upp; annars får du ett `Document`‑objekt redo för inspektion.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Observera att sökvägen kan vara absolut eller relativ till ditt projektrot. `Document`‑klassen abstraherar hela Word‑filen, vilket gör det enkelt att fråga efter exempelvis sidantal, sektioner eller till och med redigera innehållet efter återställning.

## Steg 4: Verifiera inläsningen – hämta Word‑sidantal

En snabb kontroll är att fråga Aspose.Words hur många sidor den tror att dokumentet har. Om antalet är större än noll har du troligen lyckats med **repair corrupted docx**.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Typisk utskrift:

```
Loaded successfully, page count = 12
```

Om dokumentet verkligen var oläsbart under `STRICT` skulle koden ha kastat ett undantag innan den nådde den här raden. Det gör `page count`‑kontrollen både till en verifiering och en användbar information för efterföljande logik (t.ex. paginering i en webbläsare).

## Fullt fungerande exempel

Nedan är det kompletta, färdiga Java‑programmet som sätter ihop alla delar. Kopiera och klistra in det i en fil med namnet `RecoveryModeDemo.java`, justera sökvägen och kör `javac RecoveryModeDemo.java && java RecoveryModeDemo`.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Förväntat resultat

- **If the file is recoverable:** konsolen skriver ut sidantalet, och du kan säkert fortsätta bearbeta `Document`‑objektet.
- **If the file is beyond repair (STRICT mode):** ett `com.aspose.words.UnsupportedFileFormatException` (eller liknande) kastas, vilket du kan fånga och hantera på ett smidigt sätt.

## Vanliga frågor & kantfall

### Vad gör jag om jag behöver logga de exakta feluppgifterna?

Omge laddningskoden med ett `try‑catch`‑block och logga `e.getMessage()`. Detta ger dig en tydlig anledning—om det är en saknad del, ett brutet förhållande eller en korrupt ström.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Kan jag återställa endast specifika delar (t.ex. text men inte bilder)?

Aspose.Words erbjuder inte finmaskiga återställningsinställningar, men efter inläsning kan du iterera över `NodeType`‑element och kasta bort de som är `NodeType.SHAPE` (bilder) om de orsakar problem i efterföljande steg.

### Fungerar detta med äldre `.doc`‑filer?

Ja. `LoadOptions` fungerar för alla Word‑format (`.doc`, `.docx`, `.dot`, `.dotx`). Samma återställningslogik gäller.

### Hur hanterar biblioteket lösenordsskyddade filer?

Om en fil är krypterad kommer `LoadOptions` inte att kringgå lösenordet. Du måste ange lösenordet via `loadOptions.setPassword("yourPassword")`. Återställningsläget aktiveras först när dekrypteringen lyckas.

## Tips för produktionsanvändning

- **Log the chosen recovery mode** – Det hjälper när du senare granskar varför en viss fil lyckades eller misslyckades.
- **Never overwrite the original file** – Spara det återställda dokumentet till en ny plats (`document.save("Recovered.docx")`).
- **Combine with validation** – Efter återställning, kör en snabb stavningskontroll eller strukturell validering för att säkerställa att dokumentet uppfyller dina affärsregler.
- **Batch processing** – När du hanterar många filer, loopa över dem, fånga undantag individuellt och håll en sammanfattningsrapport över lyckade och misslyckade.

## Slutsats

Du har nu ett gediget, helhetsrecept för att använda **aspose words loadoptions** för att **recover corrupted Word**‑dokument, bestämma om du ska **use recovery mode** strikt eller tillåtande, eventuellt **repair corrupted docx**, och slutligen **get the word page count** för den återställda filen. Metoden är deterministisk, enkel att integrera i befintliga Java‑pipelines, och ger dig full kontroll över hur aggressivt biblioteket ska vara när det möter trasiga binärer.

Redo att gå vidare? Prova att byta `RecoveryMode.STRICT` mot `REPAIR` i ett batch‑jobb, eller utöka exemplet för att automatiskt spara den reparerade filen till en säker mapp. Möjligheterna är oändliga, och med Aspose.Words är du rustad att hantera även de mest envisa Word‑filproblemen.

Lycka till med kodningen, och må dina dokument alltid laddas utan problem!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}