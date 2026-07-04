---
category: general
date: 2026-05-26
description: Öppna korrupt Word-dokument i Java med Aspose.Words. Lär dig hur du ställer
  in återställningsläge och på ett pålitligt sätt återställer korrupta Word-filer.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: sv
og_description: Öppna korrupt Word-dokument i Java med Aspose.Words. Denna guide visar
  hur du ställer in återställningsläge och återställer korrupta Word-filer effektivt.
og_title: Öppna korrupt Word-dokument – Ställ in återställningsläge i Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Öppna korrupt Word-dokument – Ställ in återställningsläge i Java
url: /sv/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Öppna korrupt Word-dokument – Ställ in återhämtningsläge i Java

Har du någonsin försökt öppna ett korrupt Word-dokument och sett programmet kvävas av ett undantag? Du är inte ensam—de där trasiga .docx‑filerna kan vara ett riktigt huvudvärk. Den goda nyheten är att Aspose.Words for Java ger dig fin‑granulär kontroll så att du kan **open corrupted word document** utan att appen kraschar, och till och med bestämma om du vill ha varningar, tyst återhämtning eller ett hårt avslag.

I den här handledningen går vi igenom hela processen: från att skapa rätt `LoadOptions`, till att välja rätt **set recovery mode**‑värde, och slutligen bekräfta att dokumentet faktiskt har laddats. I slutet kommer du att veta **how to recover corrupted word file** programatiskt, utan att behöva kopiera‑klistra manuellt.

> **Vad du behöver**  
> * Java 8 eller nyare (API:et fungerar även med Java 11)  
> * Aspose.Words for Java 23.9 (eller den senaste versionen)  
> * En exempelkorrupt .docx‑fil—byt bara namn på en giltig fil för att simulera korruption om du inte har en till hands  

Låt oss dyka in.

## Öppna korrupt Word-dokument – Steg‑för‑steg‑översikt

Nedan är den övergripande flödet vi kommer att implementera:

1. **Create `LoadOptions`** – detta objekt talar om för Aspose.Words hur det ska bete sig när det stöter på problem.  
2. **Set recovery mode** – välj `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS` eller `REJECT_CORRUPTED`.  
3. **Load the document** med de konfigurerade alternativen.  
4. **Verify** att laddningen lyckades (t.ex. skriv ut sidantal).  

Varje steg förklaras i detalj, med kodsnuttar som du kan kopiera‑klistra direkt in i din IDE.

## Ställ in återhämtningsläge för olika scenarier

Aspose.Words definierar tre återhämtningsstrategier i `LoadOptions.RecoveryMode`:

| Läge | Beteende | När den ska användas |
|------|----------|----------------------|
| `RECOVER_WITH_WARNINGS` | Försöker ladda dokumentet, men visar eventuella problem som varningar i konsolen. | Du vill se *vad* som gick fel utan att avbryta. |
| `RECOVER_WITHOUT_WARNINGS` | Fixar tyst vad den kan och undertrycker varningar. | Produktionsmiljöer där loggar måste hållas rena. |
| `REJECT_CORRUPTED` | Kastar ett undantag så snart korruption upptäcks. | Strikta valideringspipelines som måste misslyckas snabbt. |

Att välja rätt läge är kärnan i att **set recovery mode** korrekt. I de flesta felsökningssessioner är `RECOVER_WITH_WARNINGS` den bästa balansen eftersom den visar exakt vilka delar som reparerades.

## Så återställer du korrupt Word-fil med Aspose.Words

Nedan är ett **komplett, körbart Java‑program** som demonstrerar hela processen. Känn dig fri att lägga det i en `RecoveryModeDemo.java`‑fil, justera sökvägen och köra.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Varför varje rad är viktig

* **`LoadOptions loadOptions = new LoadOptions();`** – utan detta objekt använder Aspose.Words standardåterhämtning, som *avvisar* korrupta filer. Att skapa det ger dig en möjlighet att ändra det beteendet.  
* **`setRecoveryMode(...)`** – detta är anropet **set recovery mode** som bestämmer om varningar visas, hålls dolda eller orsakar ett undantag.  
* **`new Document(path, loadOptions);`** – konstruktorn accepterar de `LoadOptions` vi just konfigurerade, så biblioteket vet hur det ska behandla den trasiga filen från början.  
* **`doc.getPageCount()`** – en snabb kontroll. Om dokumentet laddas och returnerar ett sidantal har du lyckats **how to recover corrupted word file**.  
* **`doc.save(...)`** – valfri men praktisk; du kan skriva den reparerade versionen tillbaka till disk för senare bruk.  

## Hantera vanliga kantfall

### 1. Filen hittades inte

Om sökvägen är fel, kastar `Document` ett `FileNotFoundException`. Omge laddningen med ett try‑catch‑block och logga ett vänligt meddelande:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Oåterställbar korruption

Även med `RECOVER_WITH_WARNINGS` är vissa strukturer bortom reparation. I så fall laddar Aspose.Words fortfarande vad den kan, men du kommer att se varningar som “Cannot read paragraph properties”. Uppmärksamma konsolutdata; dessa varningar pekar ofta på saknade sektioner som du kan behöva återskapa manuellt.

### 3. Stora filer och prestanda

Återhämtning lägger till en liten overhead eftersom biblioteket parsar filen två gånger—en gång för att upptäcka problem, en gång till för att bygga om. För dokument på flera gigabyte, överväg att strömma filen eller öka JVM‑heapen (`-Xmx2g`) för att undvika `OutOfMemoryError`.

## Pro‑tips – Gör återhämtning robust

* **Log warnings to a file** – omdirigera `System.err` till en logger så att du har ett revisionsspår av vad som har fixats.  
* **Validate after recovery** – kör `doc.updatePageLayout();` och kontrollera sedan sidantalet igen; ibland ändras layouten efter att trasiga sektioner har fixats.  
* **Automate batch recovery** – omge demon i en loop som bearbetar en mapp med korrupta filer, med samma `LoadOptions` varje gång.  

## Slutsats

Du vet nu exakt **how to recover corrupted word file** med Aspose.Words för Java. Genom att skapa en `LoadOptions`‑instans, **set recovery mode** till den strategi som passar ditt scenario, och ladda dokumentet med dessa alternativ, kan du säkert **open corrupted word document** utan att krascha din applikation. Exempelkoden ovan är en komplett, färdig‑att‑köra lösning som skriver ut sidantalet och även sparar en rengjord kopia.

Vad blir nästa? Prova att byta återhämtningsläget till `RECOVER_WITHOUT_WARNINGS` och jämför konsolutdata, eller experimentera med att ladda krypterade dokument (du måste ange ett lösenord via

## Relaterade handledningar

- [Aspose.Words Java&#58; Omfattande guide till Word-dokumenthantering](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Så konverterar du Word till PDF med Aspose.Words för Java](/words/english/java/document-converting/using-document-converting/)
- [Så jämför du två Word-filer med Aspose.Words för Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}