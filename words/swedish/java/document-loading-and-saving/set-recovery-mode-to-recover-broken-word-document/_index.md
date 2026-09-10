---
category: general
date: 2026-02-15
description: Återställningsläget låter dig öppna dokument med återställning, vilket
  gör det enkelt att återställa ett trasigt Word‑dokument och åtgärda fel vid återställning
  av Word‑dokument.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: sv
og_description: Att sätta återställningsläge är nyckeln till att ladda ett dokument
  med återställning, vilket låter dig återställa fel i trasiga Word‑dokument i Java.
og_title: Ställ in återställningsläge – Återställ trasigt Word-dokument snabbt
tags:
- Aspose.Words
- Java
- Document Recovery
title: Ställ in återställningsläge för att återställa ett trasigt Word‑dokument
url: /sv/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Hur man återställer ett trasigt Word-dokument med Aspose.Words

Har du någonsin försökt öppna en Word-fil som plötsligt vägrar att laddas? Du kanske stirrar på en korrupt *.docx* och undrar om du måste börja om från början. De goda nyheterna? **set recovery mode** i Aspose.Words ger dig ett smidigt sätt att *load document with recovery* och behålla det mesta av innehållet intakt.  

I den här handledningen kommer du att lära dig exakt hur du **set recovery mode**, varför *RELAXED*-alternativet vanligtvis är det bästa valet för trasiga filer, och hur du hanterar de enstaka *recover word document errors* som fortfarande kan uppstå. Inga externa verktyg, bara ren Java och några rader kod.

> **Vad du får med dig:** ett komplett, körbart exempel som laddar en korrupt Word-fil, hoppar över oläsliga delar, och lämnar dig med ett användbart `Document`-objekt redo för vidare bearbetning.

---

## Förutsättningar

Innan vi hoppar in, se till att du har:

- **Aspose.Words for Java** (v24.9 eller nyare) tillagt i ditt projekt via Maven eller en manuell JAR.
- En **corrupted .docx**-fil som du vill testa (vi kallar den `Corrupted.docx`).
- Grundläggande Java‑kunskaper – du behöver inte vara en Word‑processningsguru, bara bekväm med en `main`‑metod.

Om du saknar någon av dessa, hämta den senaste Aspose.Words JAR från den [officiella webbplatsen](https://products.aspose.com/words/java) och lägg till den i din classpath. Det är allt—inga extra beroenden.

---

## Steg 1: Förstå återhämtningslägena

Aspose.Words offers two recovery strategies:

| Mode | Beteende | När det ska användas |
|------|----------|----------------------|
| **RELAXED** | Hoppar över oläsliga delar, behåller resten. | De flesta korrupta filer – du vill **recover broken word document** utan ett undantag. |
| **STRICT** | Kastar ett undantag vid varje fel. | När du måste garantera en perfekt, felfri laddning (sällsynt för korrupta källor). |

> **Proffstips:** *RELAXED* är standard för scenarier där du bara vill ha tillbaka något, medan *STRICT* är användbart i automatiserade pipelines där ett fel måste stoppa processen.

---

## Steg 2: Skapa ett `LoadOptions`-objekt och **set recovery mode**

Här är där det primära nyckelordet visas i koden. Vi **set recovery mode** explicit på en `LoadOptions`-instans innan filen laddas.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Varför detta är viktigt:** Genom att anropa `setRecoveryMode` talar du om för Aspose.Words hur aggressivt den ska försöka rädda filen. Utan detta anrop använder biblioteket som standard *STRICT*, vilket skulle avbryta vid det första tecknet på problem—vilket undergräver syftet med ett *recover broken word document*-arbetsflöde.

---

## Steg 3: Verifiera laddningen – Återställde vi verkligen **recover broken word document**?

Efter laddningen kan du inspektera `Document`-objektet:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Om konsolen visar ett rimligt antal sektioner har du framgångsrikt *load document with recovery*. I praktiken kommer du att märka att det mesta av text, tabeller och bilder överlever, medan de korrupta delarna helt enkelt försvinner.

---

## Steg 4: Hantera återstående **recover word document errors** på ett smidigt sätt

Även med *RELAXED*-läge kan några kantfall fortfarande ge varningar. Omge laddningen med en try‑catch för att hålla din app vid liv:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**När kan detta hända?** Om filen är så skadad att även en avslappnad parser inte kan identifiera en giltig dokumentstruktur, kommer Aspose.Words fortfarande att kasta ett undantag. I de sällsynta fallen kan du behöva be användaren att tillhandahålla en annan kopia.

---

## Steg 5: Spara den återställda filen (valfritt)

De flesta utvecklare vill ha en ren version att vidarebefordra till nedströmsystem. `save`‑anropet nedan skriver en ny `.docx` som inte längre innehåller de korrupta fragmenten.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Nu har du ett **recover broken word document** som kan öppnas i Microsoft Word, Google Docs eller någon annan visare—utan felmeddelanden.

---

## Visuell översikt (Bild)

![Diagram som visar set recovery mode-flöde – från korrupt fil till återställt dokument](https://example.com/images/recovery-flow.png "set recovery mode-flödesdiagram")

*Alt‑texten innehåller uttryckligen det primära nyckelordet, vilket hjälper både sökmotorer och skärmläsare.*

---

## Vanliga frågor & kantfall

| Question | Answer |
|----------|--------|
| *Vad händer om jag behöver behålla de korrupta delarna för forensisk analys?* | Använd `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` och fånga undantaget. Undantagsmeddelandet innehåller detaljer om de problematiska delarna. |
| *Kan jag växla mellan RELAXED och STRICT vid körning?* | Absolut—skapa bara en ny `LoadOptions`-instans med önskat läge innan varje laddning. |
| *Fungerar detta med äldre .doc-filer?* | Ja. Samma `LoadOptions` gäller både för `.doc` och `.docx`-format. |
| *Finns det någon prestandapåverkan?* | Minimal. Den extra parsningsoverheaden är försumbar jämfört med kostnaden för en fullständig dokumentladdning. |

---

## Fullt fungerande exempel (Klar att kopiera och klistra in)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Kör programmet, peka på din trasiga fil, och observera utskriften. Om allt gick smidigt kommer du att se sidantalet skrivet och en ny `Recovered.docx` dyka upp bredvid din källa.

---

## Slutsats

Vi har gått igenom allt du behöver för att **set recovery mode** i Aspose.Words, från att välja rätt `RecoveryMode`‑enum till att hantera de få *recover word document errors* som fortfarande kan dyka upp. Genom att följa stegen ovan kan du på ett pålitligt sätt **load document with recovery**, behålla de bra delarna av en korrupt fil och skapa en ren version klar för vidare bearbetning.

Redo för nästa utmaning? Prova att kombinera **set recovery mode** med Aspose.Words **document cleaning**‑API:er—ta bort dolda stycken, reparera trasiga hyperlänkar, eller till och med konvertera den återställda filen till PDF i ett svep. Möjligheterna är oändliga, och nu har du en solid grund för att tackla korrupta Word-filer direkt.

Lycka till med kodandet, och må dina dokument förbli friska!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}