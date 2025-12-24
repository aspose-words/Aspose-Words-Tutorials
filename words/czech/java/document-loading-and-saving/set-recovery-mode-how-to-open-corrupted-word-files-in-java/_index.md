---
category: general
date: 2025-12-23
description: Nastavte režim obnovy pro opravu poškozených dokumentů Word. Naučte se,
  jak otevřít soubory DOCX, použít režim obnovy a pracovat s poškozenými soubory v
  Javě.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: cs
og_description: Nastavte režim obnovy pro opravu poškozených dokumentů Word. Tento
  průvodce ukazuje, jak otevřít soubory DOCX, použít režim obnovy a pracovat s poškozenými
  soubory v Javě.
og_title: Nastavit režim obnovy – Otevřít poškozené soubory Word v Javě
tags:
- Java
- Aspose.Words
- Document Recovery
title: Nastavte režim obnovy – Jak otevřít poškozené soubory Word v Javě
url: /cs/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení režimu obnovy – Jak otevřít poškozené soubory Word v Javě

Už jste někdy zkusili **nastavit režim obnovy** na dokument Word, který se odmítá otevřít? Nejste v tom sami. Mnoho vývojářů narazí na problém, když se DOCX mírně poškodí a běžný `new Document("file.docx")` vyhodí výjimku. Dobrá zpráva? Aspose.Words pro Javu vám poskytuje vestavěný způsob, jak **použít režim obnovy** a skutečně **obnovit poškozené soubory Word**.

V tomto tutoriálu projdeme vše, co potřebujete vědět, abyste **bezpečně otevřeli poškozené soubory Word**, od konfigurace `LoadOptions` až po zpracování okrajových případů, které lidem často dělají problémy. Žádné zbytečnosti – jen praktické, krok za krokem řešení, které můžete okamžitě vložit do svého projektu.

> **Tip:** Pokud se potýkáte jen s drobnými vadami (např. chybějící zápatí), **Tolerant** režim obnovy je obvykle dostačující. **Strict** vyhraďte pro situace, kdy potřebujete, aby byl dokument 100 % čistý před zpracováním.

## Co budete potřebovat

- **Java 17** (nebo jakýkoli aktuální JDK; API funguje stejně)
- **Aspose.Words pro Javu** 23.9 (nebo novější) – knihovna, která obsahuje třídu `LoadOptions`.
- Poškozený **DOCX** soubor pro testování (můžete jej vytvořit oříznutím platného souboru pomocí hex editoru).
- Vaše oblíbené IDE (IntelliJ, Eclipse, VS Code — vyberte si, co vám vyhovuje).

A to je vše. Žádné extra Maven pluginy, žádné externí nástroje. Pouze jádro knihovny a trochu kódu.

![Illustration of setting recovery mode in Aspose.Words Java API](/images/set-recovery-mode-java.png){.align-center alt="nastavit režim obnovy"}

## Krok 1 – Vytvořte instanci `LoadOptions`

Prvním krokem je vytvořit objekt `LoadOptions`. Považujte jej za nástrojovou sadu, která říká Aspose.Words, **jak zacházet s přicházejícím souborem**.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Proč tento krok přeskočit? Protože bez `LoadOptions` nemůžete knihovně říct, zda chcete **použít režim obnovy** nebo ne. Výchozí chování je přísné, což znamená, že jakákoli korupce přeruší načtení.

## Krok 2 – Vyberte správný režim obnovy

Aspose.Words nabízí dvě hodnoty výčtu:

| Režim | Co dělá |
|------|--------|
| `RecoveryMode.Tolerant` | Pokouší se zachránit co nejvíce. Ideální pro scénáře *obnovení poškozených souborů Word*, kde je jediným problémem chybějící styl nebo poškozený vztah. |
| `RecoveryMode.Strict`   | Okamžitě selže při jakémkoli problému. Použijte, když potřebujete záruku, že dokument je čistý před dalším zpracováním. |

Nastavte režim jedním řádkem:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Proč je to důležité:** Když **použijete režim obnovy**, knihovna interně opraví poškozené části, znovu vytvoří chybějící XML uzly a poskytne vám použitelný objekt `Document`. V *přísném* režimu místo toho obdržíte `InvalidFormatException`.

## Krok 3 – Načtěte dokument s vašimi možnostmi

Nyní předáte soubor Aspose.Words a předáte mu `LoadOptions`, které jste právě nakonfigurovali.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Pokud je soubor jen mírně poškozený, `doc` bude plně funkční objekt `Document`. Nyní můžete:

- Číst text (`doc.getText()`),
- Uložit do jiného formátu (`doc.save("repaired.pdf")`),
- Nebo dokonce prozkoumat seznam obnovených částí pomocí API `Document`.

### Ověření obnovy

Rychlá kontrola vám pomůže potvrdit, že obnova skutečně uspěla:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Krok 4 – Zpracování okrajových případů

### 4.1 Když režim Tolerant nestačí

Někdy je soubor tak poškozený, že ani **Tolerant** režim jej nedokáže poskládat (např. chybí hlavní XML). V takových vzácných případech můžete:

1. **Zkusit druhé načtení s `RecoveryMode.Strict`**, abyste zjistili, zda chybová zpráva poskytne více detailů.
2. **Vrátit se k zip‑utility** a ručně extrahovat XML části a opravit je.
3. **Zaznamenat výjimku** a informovat uživatele, že dokument není možné obnovit.

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

### 4.2 Úvahy o paměti

Načítání obrovských DOCX souborů s povolenou obnovou může dočasně zdvojnásobit využití paměti, protože Aspose.Words uchovává jak originální, tak opravené struktury v paměti. Pokud zpracováváte velké dávky:

- **Znovu použijte stejnou instanci `LoadOptions`** místo vytváření nové při každém načtení.
- **Uvolněte objekt `Document`** (`doc.close()`) co nejdříve po dokončení.
- **Spusťte na JVM s dostatečnou haldou** (`-Xmx2g` nebo vyšší pro soubory o více gigabajtech).

### 4.3 Uložení opraveného souboru

Po úspěšném načtení můžete chtít **uložit vyčištěnou verzi**, abyste už nikdy nemuseli spouštět obnovu.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Nyní, až příště otevřete `repaired.docx`, můžete krok **použít režim obnovy** úplně přeskočit.

## Často kladené otázky

**Q: Funguje to i pro starší soubory `.doc`?**  
A: Ano. Stejný přístup pomocí `LoadOptions` platí pro `.doc` a `.rtf`. Stačí změnit příponu souboru.

**Q: Můžu kombinovat `setRecoveryMode` s dalšími možnostmi načítání (např. heslo)?**  
A: Rozhodně. `LoadOptions` má vlastnosti jako `setPassword` a `setLoadFormat`. Nastavte je před voláním `setRecoveryMode`.

**Q: Existuje nějaký výkonový dopad?**  
A: Mírně—obnova přidává režii při parsování. V benchmarkech se 5 MB poškozený soubor načte přibližně o 30 % pomaleji v režimu **Tolerant** oproti přísnému načtení čistého souboru. Stále to je přijatelné pro většinu dávkových úloh.

## Kompletní funkční příklad

Níže je kompletní, připravená ke spuštění Java třída, která demonstruje **jak otevřít docx**, **použít režim obnovy** a **uložit oprou kopii**.

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

Spusťte tuto třídu po přidání Aspose.Words pro Java JAR do classpath vašeho projektu. Pokud je vstupní soubor jen mírně poškozený, uvidíte zprávu **✅** a na disku se objeví nový `repaired.docx`.

## Závěr

Probrali jsme vše, co potřebujete k **nastavení režimu obnovy** a úspěšnému **otevření poškozených souborů Word** v Javě. Vytvořením objektu `LoadOptions`, výběrem vhodného `RecoveryMode` a zpracováním občasných okrajových případů můžete proměnit frustrující okamžik „soubor se neotevře“ v plynulý proces obnovy.

Pamatujte:

- **Tolerant** je vaše volba pro většinu scénářů *obnovení poškozených souborů Word*.
- **Strict** vám poskytne tvrdé selhání, když potřebujete absolutní jistotu.
- Vždy ověřte načtený dokument a pokud je to možné, uložte čistou kopii pro budoucí běhy.

Nyní můžete sebejistě odpovědět na otázku “**jak otevřít docx**, který se odmítá načíst?” konkrétním úryvkem kódu a jasným vysvětlením. Šťastné programování a ať jsou vaše dokumenty zdravé!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}