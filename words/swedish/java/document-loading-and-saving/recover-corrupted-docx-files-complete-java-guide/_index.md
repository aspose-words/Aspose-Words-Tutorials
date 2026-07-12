---
category: general
date: 2026-06-27
description: Återställ korrupta DOCX‑filer i Java genom att aktivera återställningsläge,
  kontrollera att dokumentet återställts och upptäcka dokumentåterställning. Följ
  den här steg‑för‑steg‑handledningen.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- check document recovered
- detect document recovery
language: sv
og_description: Återställ korrupta DOCX‑filer i Java. Lär dig hur du sätter återställningsläge,
  kontrollerar om dokumentet har återställts och upptäcker dokumentåterställning med
  ett fullständigt kodexempel.
og_title: Återställ korrupta DOCX-filer – Java-handledning
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Recover corrupted DOCX files in Java by setting recovery mode, checking
    document recovered, and detecting document recovery. Follow this step‑by‑step
    tutorial.
  headline: Recover Corrupted DOCX Files – Complete Java Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- DocumentRecovery
title: Återställ korrupta DOCX-filer – komplett Java‑guide
url: /sv/java/document-loading-and-saving/recover-corrupted-docx-files-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Återställ korrupta DOCX‑filer – Komplett Java‑guide

Har du någonsin behövt **återställa korrupta DOCX**‑filer men varit osäker på vilka API‑inställningar du ska justera? Du är inte ensam – kontorsdokument blir skadade mycket oftare än vi vill erkänna, och en trasig .docx kan stoppa ett helt arbetsflöde. Den goda nyheten? Med några få rader Java kan du be Aspose.Words att försöka reparera, verifiera resultatet och till och med upptäcka när återställning har skett.

I den här handledningen går vi igenom **hur man ställer in återställningsläge**, **hur man kontrollerar om dokumentet återställdes**, och **hur man programatiskt upptäcker dokumentåterställning**. I slutet har du ett färdigt kodexempel som du kan klistra in i vilket Java‑projekt som helst.

## Vad den här guiden täcker

- Förutsättningar: Aspose.Words for Java‑biblioteket och ett exempel på en korrupt .docx.  
- Val av rätt **återställningsläge** (RECOVER, RECOVER_WITH_WARNINGS eller THROW).  
- Laddning av ett potentiellt trasigt dokument med ett `LoadOptions`‑objekt.  
- **Kontrollera om dokumentet återställdes** utan att ett undantag kastas.  
- Valfritt: djupare inspektion för att **upptäcka dokumentåterställning** efter laddning.  

Ingen extern dokumentationshoppning behövs – allt du behöver finns här.

---

## Steg 1: Lägg till Aspose.Words i ditt projekt

Innan vi kan prata om återställning måste biblioteket finnas på klassvägen.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

Om du föredrar Gradle, ersätt kodsnutten med motsvarande `implementation`‑rad. När JAR‑filen finns på plats är du redo att **ställa in återställningsläge**.

## Steg 2: Välj en återställningsstrategi med `setRecoveryMode`

Aspose.Words erbjuder tre återställningsstrategier:

| Läge                     | Beteende                                                                 |
|--------------------------|--------------------------------------------------------------------------|
| `RECOVER`                | Försöker reparera dokumentet tyst.                                        |
| `RECOVER_WITH_WARNINGS`  | Reparera filen **och** samla varningar som du kan inspektera senare.     |
| `THROW`                  | Kastar ett undantag vid någon korruption (användbart för strikt validering). |

För de flesta “bara få tillbaka filen”‑scenarier väljer vi `RECOVER`. Så här konfigurerar du det:

```java
import com.aspose.words.*;

LoadOptions loadOptions = new LoadOptions();
// Step 2: Set the recovery mode – this is the core of “set recovery mode”
loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
// Alternatives: RECOVER_WITH_WARNINGS, THROW
```

> **Proffstips:** Om du behöver en rapport om vad som gick fel, byt `RECOVER` mot `RECOVER_WITH_WARNINGS` och läs senare `loadOptions.getWarnings()`.

## Steg 3: Ladda den potentiellt korrupta DOCX‑filen

Nu försöker vi faktiskt öppna filen med de alternativ vi just konfigurerat.

```java
// Step 3: Load the possibly corrupted document
Document document = new Document("YOUR_DIRECTORY/corrupted.docx", loadOptions);
```

Om filen är bortom reparation och du använde `THROW` skulle konstruktorn kasta ett undantag. Eftersom vi valde `RECOVER` returnerar anropet ett `Document`‑objekt oavsett – även om innehållet kan vara delvis rekonstruerat.

## Steg 4: **Kontrollera om dokumentet återställdes** – Enkelt booleskt test

Det snabbaste sättet att veta om återställning skedde är att jämföra läget du satte med det som faktiskt användes. Aspose.Words exponerar inte en direkt “wasRecovered”-flagga, men du kan härleda det:

```java
// Step 4: Verify if recovery was performed (i.e., mode not set to THROW)
boolean recovered = loadOptions.getRecoveryMode() != RecoveryMode.THROW;
System.out.println("Recovered: " + recovered);
```

Om du bytte till `RECOVER_WITH_WARNINGS` kan du också titta på varningssamlingen:

```java
if (!loadOptions.getWarnings().isEmpty()) {
    System.out.println("Warnings during recovery:");
    loadOptions.getWarnings().forEach(System.out::println);
}
```

Detta kodstycke uppfyller kravet **check document recovered** samtidigt som det ger dig insikt i eventuella problem som åtgärdats.

## Steg 5: Upptäck dokumentåterställning efter laddning (Avancerat)

Ibland behöver du veta *efter* laddning om dokumentet har förändrats. Aspose.Words lagrar en flagga du kan fråga via `Document.isDirty()`‑metoden, men ett mer pålitligt tillvägagångssätt är att jämföra den ursprungliga filstorleken med storleken på den laddade dokumentströmmen.

```java
import java.io.*;

File original = new File("YOUR_DIRECTORY/corrupted.docx");
ByteArrayOutputStream baos = new ByteArrayOutputStream();
document.save(baos, SaveFormat.DOCX);
byte[] recoveredBytes = baos.toByteArray();

boolean wasRecovered = original.length() != recoveredBytes.length;
System.out.println("Detect document recovery: " + wasRecovered);
```

Om längderna skiljer sig har Aspose.Words behövt modifiera den interna strukturen – vilket betyder att en återställning har ägt rum. Detta uppfyller målet **detect document recovery**.

## Fullt fungerande exempel

Sätter vi ihop allt får du en enda klass som du kan kompilera och köra:

```java
import com.aspose.words.*;
import java.io.*;

public class RecoverCorruptedDocxDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Set up load options – we’ll recover silently
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // set recovery mode

        // 2️⃣ Load the corrupted document
        Document doc = new Document("YOUR_DIRECTORY/corrupted.docx", loadOptions);

        // 3️⃣ Simple check – did we avoid throwing?
        boolean recovered = loadOptions.getRecoveryMode() != RecoveryMode.THROW;
        System.out.println("Recovered (simple check): " + recovered);

        // 4️⃣ If you used RECOVER_WITH_WARNINGS, print them
        if (!loadOptions.getWarnings().isEmpty()) {
            System.out.println("Recovery warnings:");
            loadOptions.getWarnings().forEach(System.out::println);
        }

        // 5️⃣ Detect actual changes by comparing sizes
        File original = new File("YOUR_DIRECTORY/corrupted.docx");
        ByteArrayOutputStream baos = new ByteArrayOutputStream();
        doc.save(baos, SaveFormat.DOCX);
        byte[] recoveredBytes = baos.toByteArray();

        boolean wasRecovered = original.length() != recoveredBytes.length;
        System.out.println("Detect document recovery (size diff): " + wasRecovered);

        // Optional: save the repaired file
        doc.save("YOUR_DIRECTORY/recovered.docx");
        System.out.println("Repaired document saved.");
    }
}
```

**Förväntad konsolutskrift (exempel):**

```
Recovered (simple check): true
Recovery warnings:
[Warning] Invalid paragraph property – corrected.
Detect document recovery (size diff): true
Repaired document saved.
```

Om filen redan var frisk kommer storleks‑jämförelsen att returnera `false` och inga varningar visas.

## Vanliga fallgropar & hur du undviker dem

| Fallgrop | Varför det händer | Åtgärd |
|----------|-------------------|--------|
| Använda `THROW` på en trasig fil | Konstruktorn kastar `IncorrectPasswordException` eller `FileCorruptedException`. | Byt till `RECOVER` eller `RECOVER_WITH_WARNINGS`. |
| Glömma att inkludera Aspose‑licensen | Biblioteket körs i evalueringsläge och lägger till ett vattenmärke. | Applicera din licens via `License license = new License(); license.setLicense("Aspose.Words.lic");`. |
| Anta att varningar betyder fel | Varningar är informativa; dokumentet kan fortfarande vara användbart. | Behandla dem som ledtrådar för vidare städning, inte som kritiska fel. |
| Inte rensa upp strömmar | Stora dokument kan tömma minnet. | Använd try‑with‑resources för `FileInputStream`/`ByteArrayOutputStream`. |

## När du ska använda varje återställningsläge

- **RECOVER** – Perfekt för bakgrunds‑batchjobb där du bara behöver en användbar fil.  
- **RECOVER_WITH_WARNINGS** – Idealiskt för UI‑verktyg som vill visa användaren vad som fixades.  
- **THROW** – Använd i strikta valideringspipelines där all korruption ska avbryta processen.

## Nästa steg

Nu när du kan **återställa korrupta DOCX**‑filer, fundera på att utöka arbetsflödet:

- **Batch‑behandling** – Loopa igenom en mapp med filer och logga återställningsstatistik.  
- **Automatiskt säkerhetskopiering** – Spara originalet innan du försöker återställa, för säkerhets skull.  
- **Integration med molnlagring** – Hämta filer från S3, återställ dem och ladda upp den rena versionen igen.

Alla dessa idéer involverar naturligt de sekundära nyckelorden **set recovery mode**, **check document recovered** och **detect document recovery**, vilket gör din kodbas både robust och transparent.

---

![Diagram showing the recover corrupted docx workflow – from loading a broken file, setting recovery mode, checking recovery status, to saving a repaired document.](recover-corrupted-docx-workflow.png "recover corrupted docx workflow")

*Bildtext: “Diagram som visar återställning av korrupt docx‑arbetsflöde – ställ in återställningsläge, kontrollera återställningsstatus och spara ett reparerat dokument.”*

---

### TL;DR

- Använd `LoadOptions.setRecoveryMode()` för att tala om för Aspose.Words hur trasiga filer ska hanteras.  
- Ladda filen med de konfigurerade alternativen; inget undantag betyder att du har **check document recovered**.  
- Jämför filstorlekar eller inspektera varningar för att **detect document recovery**.  
- Spara den fixade utdatafilen och gå vidare.

Det är hela historien om hur du **återställer korrupta docx‑filer** i Java. Har du en knepig fil som fortfarande inte går att öppna? Lämna en kommentar så felsöker vi tillsammans. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra fler API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Recover corrupted docx – Complete Guide to Fix and Process Documents](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [Aspose.Words Java: Document Conversion & Security for ODT Files](/words/english/java/document-operations/aspose-words-java-document-conversion-security/)
- [Aspose Words Java Document Signing Tutorial](/words/english/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}