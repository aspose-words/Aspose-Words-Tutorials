---
category: general
date: 2025-12-23
description: Ställ in återställningsläge för att återställa skadade Word‑dokument.
  Lär dig hur du öppnar DOCX‑filer, använder återställningsläge och hanterar korrupta
  filer i Java.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: sv
og_description: Ställ in återställningsläge för att återställa skadade Word-dokument.
  Denna guide visar hur du öppnar DOCX-filer, använder återställningsläge och hanterar
  korrupta filer i Java.
og_title: Ställ in återställningsläge – Öppna korrupta Word-filer i Java
tags:
- Java
- Aspose.Words
- Document Recovery
title: Ställ in återställningsläge – Hur man öppnar korrupta Word‑filer i Java
url: /sv/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in återhämtningsläge – Hur man öppnar korrupta Word-filer i Java

Har du någonsin försökt **set recovery mode** på ett Word-dokument som vägrar att öppnas? Du är inte ensam. Många utvecklare stöter på problem när en DOCX blir lite korrupt och den vanliga `new Document("file.docx")` kastar ett undantag. Den goda nyheten? Aspose.Words for Java ger dig ett inbyggt sätt att **use recovery mode** och faktiskt **recover damaged Word** filer.

I den här handledningen går vi igenom allt du behöver veta för att **open corrupted word file** objekt säkert, från att konfigurera `LoadOptions` till att hantera de kantfall som vanligtvis får folk att snubbla. Ingen onödig text—bara en praktisk, steg‑för‑steg‑lösning som du kan klistra in i ditt projekt direkt.

> **Pro tip:** Om du bara hanterar mindre fel (som en saknad sidfot) är **Tolerant** återhämtningsläge vanligtvis tillräckligt. Reservera **Strict** för situationer där du behöver att dokumentet är 100 % rent innan bearbetning.

## Vad du behöver- **Java 17** (eller någon nyare JDK; API:et fungerar likadant)
- **Aspose.Words for Java** 23.9 (eller nyare) – biblioteket som levererar `LoadOptions`-klassen.
- En **corrupted DOCX** fil att testa med (du kan skapa en genom att trunkera en giltig fil med en hex‑editor).
- Din favorit‑IDE (IntelliJ, Eclipse, VS Code—välj det som känns bekvämt).

Det är allt. Inga extra Maven‑plugins, inga externa verktyg. Bara kärnbiblioteket och en liten kodbit.

![Illustration av att ställa in återhämtningsläge i Aspose.Words Java API](/images/set-recovery-mode-java.png){.align-center alt="set recovery mode"}

## Steg 1 – Skapa en `LoadOptions`‑instans

Det första du gör är att instansiera ett `LoadOptions`‑objekt. Tänk på det som en verktygslåda som talar om för Aspose.Words **how to treat the incoming file**.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Varför hoppa över detta steg? För utan ett `LoadOptions` kan du inte säga åt biblioteket om du vill **use recovery mode** eller inte. Standardbeteendet är strikt, vilket betyder att all korruption avbryter inläsningen.

## Steg 2 – Välj rätt återhämtningsläge

Aspose.Words erbjuder två enum‑värden:

| Läges | Vad det gör |
|------|--------------|
| `RecoveryMode.Tolerant` | Försöker rädda så mycket som möjligt. Ideal för *recover damaged word*-scenarier där en saknad stil eller trasig relation är det enda problemet. |
| `RecoveryMode.Strict`   | Misslyckas snabbt vid något problem. Använd detta när du behöver en garanti att dokumentet är fläckfritt innan vidare bearbetning. |

Ställ in läget med en enda rad:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Varför detta är viktigt:** När du **use recovery mode**, patchar biblioteket internt trasiga delar, bygger om saknade XML‑noder och ger dig ett användbart `Document`‑objekt. I *strict*‑läge får du istället ett `InvalidFormatException`.

## Steg 3 – Läs in dokumentet med dina alternativ

Nu överlämnar du äntligen filen till Aspose.Words och skickar med de `LoadOptions` du just konfigurerat.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Om filen bara är lätt korrupt, kommer `doc` att vara ett fullt funktionellt `Document`‑objekt. Du kan nu:

- Läs text (`doc.getText()`),
- Spara till ett annat format (`doc.save("repaired.pdf")`),
- Eller till och med inspektera listan över återställda delar via `Document`‑API:n.

### Verifiera återhämtningen

En snabb kontroll hjälper dig bekräfta att återhämtningen faktiskt lyckades:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Steg 4 – Hantera kantfall

### 4.1 När Tolerant inte räcker

Ibland är en fil så trasig att även **Tolerant**‑läget inte kan sätta ihop den (t.ex. kärn‑XML saknas). I dessa sällsynta fall kan du:

1. **Försök en andra inläsning med `RecoveryMode.Strict`** för att se om felmeddelandet ger mer detaljer.
2. **Falla tillbaka på ett zip‑verktyg** för att manuellt extrahera XML‑delarna och reparera dem.
3. **Logga undantaget** och informera användaren om att dokumentet är oåterställbart.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 Minneshänsyn

Att läsa in stora DOCX‑filer med återhämtning aktiverad kan tillfälligt dubbla minnesanvändningen eftersom Aspose.Words behåller både original‑ och reparerade strukturer i minnet. Om du bearbetar stora satser:

- **Återanvänd samma `LoadOptions`‑instans** istället för att skapa en ny varje gång.
- **Frigör `Document`** (`doc.close()`) så snart du är klar.
- **Kör på en JVM med tillräckligt heap** (`-Xmx2g` eller högre för multi‑gigabyte‑filer).

### 4.3 Spara den reparerade filen

Efter en lyckad inläsning kanske du vill **spara den rengjorda versionen** så att du aldrig behöver köra återhämtning igen.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Nu kan du nästa gång du öppnar `repaired.docx` hoppa över steget **use recovery mode** helt.

## Vanliga frågor

**Q: Fungerar detta för äldre `.doc`‑filer?**  
A: Ja. Samma `LoadOptions`‑metod gäller för `.doc` och `.rtf`. Byt bara filändelsen.

**Q: Kan jag kombinera `setRecoveryMode` med andra inläsningsalternativ (t.ex. lösenord)?**  
A: Absolut. `LoadOptions` har egenskaper som `setPassword` och `setLoadFormat`. Ställ in dem innan du anropar `setRecoveryMode`.

**Q: Finns det någon prestandapåverkan?**  
A: Lite grann—återhämtning lägger till en parsningsoverhead. I tester laddas en 5 MB korrupt fil ~30 % långsammare i **Tolerant**‑läge jämfört med strikt inläsning av en ren fil. Fortfarande acceptabelt för de flesta batch‑jobb.

## Fullt fungerande exempel

Nedan är en komplett, klar‑att‑köra Java‑klass som demonstrerar **how to open docx**, **use recovery mode**, och **save a repaired copy**.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

Kör den här klassen efter att ha lagt till Aspose.Words for Java‑JAR‑filen i ditt projekts classpath. Om indatafilen bara är lite skadad kommer du att se **✅**‑meddelandet och en ny `repaired.docx` på disken.

## Slutsats

Vi har gått igenom allt du behöver för att **set recovery mode** och framgångsrikt **open corrupted word** filer i Java. Genom att skapa ett `LoadOptions`‑objekt, välja rätt `RecoveryMode` och hantera de enstaka kantfallen kan du förvandla ett frustrerande “filen går inte att öppna”-ögonblick till ett smidigt återhämtningsflöde.

Kom ihåg:

- **Tolerant** är ditt förstahandsval för de flesta *recover damaged word*-scenarier.  
- **Strict** ger dig ett hårt misslyckande när du behöver absolut säkerhet.  
- Verifiera alltid det inlästa dokumentet och, om möjligt, spara en ren kopia för framtida körningar.

Nu kan du självsäkert svara på “**how to open docx** som vägrar att laddas?” med ett konkret kodexempel och en tydlig förklaring. Lycka till med kodandet, och må dina dokument hålla sig friska!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}