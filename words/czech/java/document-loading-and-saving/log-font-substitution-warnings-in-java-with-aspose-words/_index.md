---
category: general
date: 2026-06-17
description: Zaznamenávejte varování o náhradě písma v Javě pomocí Aspose.Words –
  zachyťte chybějící písma při načítání dokumentu a zajistěte konzistentní výstup.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: cs
og_description: Zaznamenávejte varování o nahrazení písma v Javě s Aspose.Words. Naučte
  se zachytávat upozornění na chybějící písmo při načítání dokumentu a udržujte své
  PDF soubory v dokonalém stavu.
og_title: Zaznamenávání varování o nahrazování fontů v Javě – Kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Zaznamenání varování o nahrazení písma v Javě pomocí Aspose.Words
url: /cs/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zaznamenávání varování o náhradě fontů v Javě – Kompletní průvodce

Už jste se někdy zamysleli, jak **zaznamenávat varování o náhradě fontů**, když Word dokument načte font, který na serveru nemáte? Nejste jediní, kdo se trápí s chybějícími fonty, které jsou tiše nahrazeny. Dobrá zpráva? Aspose.Words for Java vám poskytuje čistý způsob, jak zachytit tyto náhrady v okamžiku načtení dokumentu.

V tomto tutoriálu vás provedeme praktickým příkladem, který přesně ukazuje, jak zaregistrovat callback pro varování, filtrovat upozornění na náhradu fontů a zapsat je do konzole (nebo libovolného loggeru, který preferujete). Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného Java projektu používajícího **Aspose.Words Java**.

## Co se naučíte

- Jak nakonfigurovat **LoadOptions** pro zachycení varování.
- Jak implementovat **IWarningCallback**, který reaguje pouze na události **font substitution**.
- Jak bezpečně načíst dokument a zároveň mít jasný auditní záznam chybějících fontů.
- Tipy, jak rozšířit řešení na souborové logy nebo monitorovací systémy.

### Předpoklady

- Java 8 nebo novější (kód funguje také s Java 11+).
- Knihovna Aspose.Words for Java (doporučena verze 23.10 nebo novější).
- Ukázkový `.docx`, který odkazuje na font, který není nainstalován ve vašem systému (např. `MissingFont.docx`).

Nejsou vyžadovány žádné další frameworky – stačí čistá Java a Aspose.JARs.

---

## Krok 1: Nakonfigurujte LoadOptions pro Aspose.Words Java

Než budete moci zachytit jakákoli varování, potřebujete instanci **LoadOptions**. Tento objekt říká Aspose.Words, jak se má chovat při parsování vstupního souboru.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Proč je tento krok zásadní? Bez objektu `LoadOptions` knihovna tiše nahrazuje chybějící fonty a nikdy nevidíte žádný záznam. Explicitním vytvořením takového objektu otevřete cestu k vlastnímu **warning callback**, který může zaznamenat přesně to, na co vám záleží.

> **Tip:** Pokud načítáte mnoho dokumentů najednou, znovu použijte jedinou instanci `LoadOptions`, abyste se vyhnuli zbytečnému vytváření objektů.

---

## Krok 2: Implementujte Warning Callback pro náhradu fontů

Aspose.Words poskytuje rozhraní `IWarningCallback`. Jeho implementací můžete rozhodnout, co se má stát, když engine vyvolá `WarningInfo`. V našem případě chceme reagovat pouze na `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

**Filtrování** – `if` podmínka zajišťuje, že ignorujeme nesouvisející varování (např. problémy s rozvržením) a udržuje log přehledný.  
**Bezpečnost vláken** – Callback běží ve stejném vlákně, které načítá dokument, takže pro jednoduchý výstup do konzole nepotřebujete další synchronizaci. Pokud zapisujete do sdíleného loggeru, ujistěte se, že je thread‑safe.  
**Rozšiřitelnost** – Chcete zapisovat do souboru? Nahraďte `System.out.println` za `java.util.logging.Logger` nebo jiný třetí‑stranový logging framework.

---

## Krok 3: Načtěte dokument pomocí nakonfigurovaných možností

Nyní, když je callback nastaven, načtěte svůj Word soubor. V okamžiku, kdy Aspose.Words parsuje dokument, jakýkoli chybějící font spustí výše definovaný callback.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Pokud zdrojový soubor odkazuje na font, který není nainstalován, uvidíte výstup podobný:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Tento řádek je **log font substitution warnings**, který jste hledali. Nyní můžete na to reagovat – například upozornit uživatele, přepnout na náhradní stylopis nebo si jednoduše uchovat záznam pro soulad s předpisy.

---

## Krok 4: Pokračujte v běžném zpracování

Po načtení se dokument chová jako jakýkoli jiný objekt `Document`. Klidně prozkoumejte sekce, extrahujte text nebo převádějte do PDF. Zaznamenávání varování probíhá automaticky během kroku načtení, takže nepotřebujete další kód.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Konzole nyní zobrazí jak varování o náhradě fontu (pokud existuje) **tak** i počet sekcí, což potvrzuje, že dokument je plně funkční.

---

## Pokročilé tipy a okrajové případy

### Zaznamenávání do souboru místo konzole

Pokud upřednostňujete trvalý log, nahraďte volání `System.out.println` za `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Nezapomeňte v produkčním kódu správně ošetřit `IOException`.

### Zachycení více dokumentů ve smyčce

Při zpracování složky s dokumenty můžete znovu použít stejný callback:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Protože je callback připojen k `loadOptions`, každá iterace automaticky zaznamená jakékoli události náhrady fontu.

### Práce s vloženými fonty

Aspose.Words může vložit chybějící fonty, pokud to povolíte:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

I když je vkládání povoleno, callback pro varování se stále spouští, což vám poskytuje přehled o tom, co bylo nahrazeno.

---

## Úplný funkční příklad

Níže je kompletní, připravený k spuštění program. Zkopírujte jej do třídy s názvem `FontSubstitutionDiagnostics.java`, upravte cestu k souboru a spusťte.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Očekávaný výstup** (předpokládáme, že zdrojový dokument odkazuje na chybějící font):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Jak konzole, tak `font_substitution_log.txt` budou obsahovat varování, což vám poskytne spolehlivý auditní záznam.

---

## Závěr

Právě jsme vám ukázali, jak **zaznamenávat varování o náhradě fontů** v Javě pomocí Aspose.Words. Nakonfigurováním `LoadOptions`, připojením `IWarningCallback` a načtením dokumentu získáte úplnou přehlednost o všech událostech chybějících fontů, které by jinak mohly zůstat nepovšimnuty. Odtud můžete:

- Přesměrovat varování do centrálního logovacího servisu.
- Spouštět upozornění pro pipeline kontroly kvality.
- Kombinovat tuto techniku s dalšími strategiemi **document loading**, jako je konverze do PDF nebo hromadná korespondence.

Klidně experimentujte – nahraďte konzolový logger za SLF4J, přidejte časové značky nebo dokonce posílejte upozornění na monitorovací dashboard. Základní vzor zůstává stejný a nyní máte solidní základ pro spolehlivé zacházení s fonty v jakémkoli Java‑založeném workflow dokumentů.

Máte nějaký vlastní tip, který byste chtěli sdílet? Možná jste to integrovali se Spring Boot nebo cloudovou funkcí. Zanechte komentář níže a pojďme pokračovat v diskuzi. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}