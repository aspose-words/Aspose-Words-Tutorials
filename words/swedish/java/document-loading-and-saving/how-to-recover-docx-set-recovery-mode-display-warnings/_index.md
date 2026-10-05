---
category: general
date: 2026-03-04
description: Hur man återställer DOCX-filer med Java – lär dig att sätta återställningsläge
  och visa laddningsvarningar för korrupta dokument i några enkla steg.
draft: false
keywords:
- how to recover docx
- set recovery mode
- use recovery mode
- recover corrupted docx
- display load warnings
language: sv
og_description: How to recover DOCX files using Java. This guide shows how to set
  recovery mode and display load warnings when loading corrupted documents.
og_title: Hur man återställer DOCX – Ställ in återställningsläge och visa varningar
tags:
- Java
- Aspose.Words
- Document Recovery
title: How to Recover DOCX – Set Recovery Mode & Display Warnings
url: /sv/java/document-loading-and-saving/how-to-recover-docx-set-recovery-mode-display-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man återställer DOCX – Ställ in återställningsläge & visa varningar

Har du någonsin öppnat en **DOCX**‑fil och bara sett förvrängd text eller ett saknat stycke? Det är då du börjar fundera på *hur man återställer docx*‑filer utan att förlora timmar av arbete. Den goda nyheten är att Aspose.Words for Java erbjuder ett inbyggt återställningsläge som kan sniffa upp problem, behålla de bra delarna och till och med berätta vad som gick fel.

I den här handledningen går vi igenom de exakta stegen för att **ställa in återställningsläge**, **använda återställningsläge** när du laddar ett korrupt dokument, och **visa laddningsvarningar** så att du vet exakt vad som reparerades. I slutet har du ett färdigt kodexempel som återställer en trasig DOCX och berättar hur många varningar som genererades.

> **Förutsättning:** Du behöver Aspose.Words for Java (v23.9 eller senare) på din classpath. Om du inte har det ännu, hämta Maven‑artefakten `com.aspose:aspose-words:23.9` eller ladda ner JAR‑filen från Aspose‑webbplatsen.

![hur man återställer docx](/images/recover-docx.png)

---

## Vad den här guiden täcker

* Hur du konfigurerar **LoadOptions** för att styra återställningsbeteendet.  
* Skillnaden mellan `RECOVER_WITH_WARNINGS` och `RECOVER_SILENTLY`.  
* Hur du **visar laddningsvarningar** efter att dokumentet har öppnats.  
* Ett komplett, körbart Java‑program som du kan kopiera‑klistra in i din IDE.

Låt oss dyka ner – inga onödiga utsvävningar, bara det som faktiskt får jobbet gjort.

---

## Steg 1: Förbered LoadOptions – Välj rätt återställningsläge

Innan du ens rör filen måste du tala om för Aspose.Words hur den ska bete sig när den stöter på korrupt data. Här kommer **set recovery mode** in i bilden.

```java
import com.aspose.words.LoadOptions;
import com.aspose.words.LoadOptions.RecoveryMode;

// Create a LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Choose a recovery strategy
// 1️⃣ Recover with warnings – you’ll get a list of issues.
// 2️⃣ Recover silently – the library fixes everything quietly.
loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
// Or, if you prefer no output:
// loadOptions.setRecoveryMode(RecoveryMode.RECOVER_SILENTLY);
```

*Varför detta är viktigt:* `RECOVER_WITH_WARNINGS` är perfekt när du behöver granska reparationsprocessen, medan `RECOVER_SILENTLY` är användbart för batch‑jobb där du inte vill ha konsolbrus.

---

## Steg 2: Ladda den korrupta DOCX‑filen med de konfigurerade alternativen

Nu när **load options** är klara är själva öppnandet av filen en barnlek. Lägg märke till hur vi skickar `loadOptions`‑objektet till `Document`‑konstruktorn – detta är steget **use recovery mode**.

```java
import com.aspose.words.Document;

// Path to the potentially corrupted file
String corruptedPath = "C:/Docs/corrupted.docx";

// Load the document with the previously defined options
Document document = new Document(corruptedPath, loadOptions);
```

Om filen är bortom reparation kommer Aspose.Words ändå att kasta ett `FileCorruptedException`. I de flesta verkliga scenarier räddar biblioteket de läsbara delarna och flaggar resten.

---

## Steg 3: Visa laddningsvarningar – Vet exakt vad som fixades

Efter att dokumentet har laddats kan du fråga varningssamlingen. Detta är delen **display load warnings** i vår handledning.

```java
// Retrieve the warning collection
int warningCount = document.getWarningInfo().size();

// Print a friendly message
System.out.println("Document loaded with warnings: " + warningCount);

// Optional: iterate and print each warning for deeper insight
document.getWarningInfo().forEach(w -> System.out.println("- " + w.getDescription()));
```

Typisk output kan se ut så här:

```
Document loaded with warnings: 3
- Warning: Missing end tag for <w:p>.
- Warning: Invalid hyperlink target.
- Warning: Unsupported bitmap format.
```

Att se listan låter dig avgöra om du behöver fixa något manuellt senare eller om det återställda dokumentet är tillräckligt för ditt användningsområde.

---

## Fullt fungerande exempel – Från början till slut

Nedan är en självständig Java‑klass som du kan släppa in i vilket projekt som helst. Den demonstrerar **hur man återställer docx**, **ställer in återställningsläge**, **använder återställningsläge** och **visar laddningsvarningar** – allt i ett.

```java
import com.aspose.words.*;

public class DocxRecoveryDemo {

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with the desired recovery strategy
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
            // Uncomment the line below to suppress warnings
            // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_SILENTLY);

            // 2️⃣ Load the potentially corrupted DOCX file
            String filePath = "C:/Docs/corrupted.docx";
            Document doc = new Document(filePath, loadOptions);

            // 3️⃣ Show how many warnings were generated
            int warnings = doc.getWarningInfo().size();
            System.out.println("Document loaded with warnings: " + warnings);

            // Optional: print each warning for debugging
            for (WarningInfo wi : doc.getWarningInfo()) {
                System.out.println("- " + wi.getDescription());
            }

            // 4️⃣ Save the recovered document (optional)
            String outputPath = "C:/Docs/recovered.docx";
            doc.save(outputPath);
            System.out.println("Recovered document saved to: " + outputPath);

        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Förväntat resultat:** Programmet skriver ut antalet varningar, listar varje varning och sparar en ren `recovered.docx` till disk. Även om den ursprungliga filen var halvt trasig kommer outputen att innehålla allt återställningsbart innehåll.

---

## Vanliga frågor & kantfall

### Vad händer om jag måste återställa en DOCX från en ström istället för en filsökväg?
Skicka bara ett `InputStream` till `Document`‑konstruktorn tillsammans med samma `LoadOptions`. API‑et fungerar identiskt.

```java
InputStream is = new FileInputStream("corrupted.docx");
Document doc = new Document(is, loadOptions);
```

### Kan jag ändra återställningsläget efter att dokumentet redan har laddats?
Nej. Lägget är endast läsbart under laddningsfasen. Om du behöver en annan strategi, ladda om filen med en ny `LoadOptions`‑instans.

### Hur skiljer sig **recover corrupted docx** från att bara öppna den i Microsoft Word?
Word försöker auto‑reparera men döljer ofta detaljerna. Aspose.Words ger dig en programmerbar lista över varje problem via **display load warnings**, vilket är ovärderligt för automatiserade pipelines.

### Är det någon prestandapåverkan att använda `RECOVER_WITH_WARNINGS`?
Lite grann – insamling av varningar ger en extra overhead, men den är försumbar för de flesta filer (<5 MB). För massbearbetning där hastigheten är kritisk, byt till `RECOVER_SILENTLY`.

---

## Pro‑tips & fallgropar

* **Pro‑tips:** Logga alltid varningarna till en fil när du bearbetar batcher. På så sätt kan du granska problematiska filer senare utan att fylla konsolen.
* **Se upp för:** Mycket stora DOCX‑filer (>100 MB) kan orsaka `OutOfMemoryError` om du också har `RECOVER_WITH_WARNINGS` aktiverat. Överväg att öka JVM‑heapen eller använda `RECOVER_SILENTLY` för dessa fall.
* **Tips:** Efter återställning, kör en snabb kontroll – t.ex. `doc.getSections().size()` – för att säkerställa att dokumentstrukturen är intakt innan du vidarebefordrar den till downstream‑tjänster.

---

## Slutsats

Vi har precis gått igenom **hur man återställer docx**‑filer genom att konfigurera **load options**, **ställa in återställningsläge**, **använda återställningsläge** och **visa laddningsvarningar** för alla korrupta DOCX‑filer du stöter på. Det kompletta exemplet ovan är redo att kopieras, köras och anpassas till dina egna arbetsflöden.

Nästa steg? Prova att byta `RECOVER_WITH_WARNINGS` mot `RECOVER_SILENTLY` i ett högvolymsjobb, eller integrera varningslistan i ditt övervakningssystem. Du kan också utforska andra Aspose.Words‑funktioner som **document protection** eller **format conversion** – alla respekterar samma återställningsinställningar.

Har du fler frågor om att återställa dokument, hantera andra Office‑format eller justera Aspose.Words‑inställningar? Lämna en kommentar, och lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}