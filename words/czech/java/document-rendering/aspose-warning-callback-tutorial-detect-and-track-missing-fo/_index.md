---
category: general
date: 2026-03-17
description: Naučte se tutoriál aspose warning callback pro detekci a sledování chybějících
  fontů v Java dokumentech s kompletním spustitelným příkladem.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: cs
og_description: Ovládněte návod aspose warning callback k detekci chybějících fontů
  a sledování chybějících fontů ve vašem Java pracovním postupu pro zpracování Wordu.
og_title: Návod na aspose warning callback – Detekce chybějících fontů
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Návod na aspose varovný callback – detekce a sledování chybějících fontů
url: /cs/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Detekce a sledování chybějících fontů

Už jste se někdy zamysleli, jak **detekovat chybějící fonty** při konverzi nebo úpravě souborů Word pomocí Aspose.Words? Nejste v tom sami. V mnoha reálných projektech může nechtěný font způsobit problémy s rozvržením a potřebujete spolehlivý způsob, jak **sledovat chybějící fonty**, než vás později překvapí.  

Dobrá zpráva? **aspose warning callback tutorial** vám poskytuje čistý programový hák, který vypisuje přesně tato varování o nahrazení fontů v reálném čase. V tomto průvodci vás provedeme nastavením callbacku, načtením dokumentu a zobrazením varování v akci – vše v Javě.

Na konci tohoto článku budete schopni automaticky odhalit chybějící fonty, zaznamenat je a rozhodnout, zda vložit náhradní font nebo upravit zdrojové soubory. Žádné externí nástroje nejsou potřeba.

## Požadavky

- **Java 8+** (kód se kompiluje s jakýmkoli aktuálním JDK)
- **Aspose.Words for Java** verze 23.10 nebo novější – stáhněte z portálu Aspose nebo přidejte Maven závislost.
- Ukázkový DOCX, který úmyslně odkazuje na font, který nemáte nainstalovaný (např. „Comic Sans MS“ na Linuxu).

To je vše – žádné další knihovny, žádné složité kroky sestavení.

## Krok 1: Registrace výstražného callbacku – Jádro aspose warning callback tutorial

První věc, kterou vás tutoriál učí, je, jak připojit posluchač výstrah. Aspose.Words vyvolá objekt `WarningInfo` pro každý problém, na který narazí, a příznak `WarningSource.FONT_SUBSTITUTION` nám přesně říká, kdy je font nahrazen.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Proč je to důležité:** Bez callbacku Aspose tiše nahrazuje chybějící fonty a nikdy nevíte, které glyfy mohou vypadat špatně. Zaznamenáním výstrahy můžete **detekovat chybějící fonty** včas a rozhodnout, zda vložit správný font.

> **Tip:** Pokud potřebujete sbírat výstrahy pro pozdější reportování, uložte je do `List<WarningInfo>` místo přímého výpisu.

## Krok 2: Načtení dokumentu – Kde se mohou skrývat chybějící fonty

Nyní načteme DOCX, který může odkazovat na fonty, které nejsou v systému nainstalovány. Samotné načtení spustí výstražný callback, pokud chybí nějaké fonty.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Co se děje v pozadí?** Aspose parsuje definice stylů dokumentu, prochází každý úsek textu a kontroluje repozitář systémových fontů. Když nenajde přesnou shodu, přejde na náhradní font a spustí výstrahu, kterou jsme právě zachytili.

## Krok 3: Uložení dokumentu – Vyprázdnění výstrah

Nakonec dokument uložíme. Operace uložení také znovu vyhodnocuje fonty, takže všechna varování, která nebyla vyvolána během načítání, se objeví nyní.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Po spuštění programu uvidíte výstup v konzoli podobný následujícímu:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Tento výstup dokazuje, že **aspose warning callback tutorial** funguje, a úspěšně jste **detekovali chybějící fonty** a nyní **sledujete chybějící fonty** prostřednictvím logu.

## Jak detekovat chybějící fonty ve Word dokumentu – Za hranice základů

Přístup s callbackem je skvělý pro jednorázové běhy, ale někdy potřebujete opakovaně použitelné utility. Zde je rychlý wrapper, který můžete vložit do libovolného projektu:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Zavolejte jej takto:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Nyní máte opakovaně použitelnou metodu **detect missing fonts**, která vrací seznam, který můžete předat do CI pipeline nebo uživatelského rozhraní.

## Sledování chybějících fontů pomocí Aspose.Words – Reportování pro týmy

Ve větším týmu možná budete chtít vytvořit CSV report všech chybějících fontů napříč mnoha dokumenty. Kombinujte předchozí utility s jednoduchou iterací souborů:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Spuštěním tohoto skriptu získáte CSV **track missing fonts**, které si každý vývojář může rychle prohlédnout před odesláním dokumentu do produkce.

## Časté úskalí a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|---------|----------------------|--------|
| **Callback nevyvolá** | Zapomněli jste nastavit callback **před** načtením dokumentu. | Umístěte `Document.setWarningCallback` na samý začátek metody `main`. |
| **Zobrazí se jen první výstraha** | Aspose ke každé instanci `Document` kešuje výstrahy. | Použijte novou instanci `Document` pro každý soubor, nebo resetujte callback mezi běhy. |
| **Špatný název fontu v logu** | Popis obsahuje nadbytečný text („Font … not found“). | Odstraňte pomocí regexu, jak je ukázáno v CSV příkladu. |
| **Pokles výkonu při velkých dávkách** | Callback se spouští pro každý úsek textu, což může být náročné. | Omezte kontrolu na předběžný krok; při pouhé detekci můžete vynechat ukládání. |

## Očekávané výsledky a ověření

1. **Výstup v konzoli** – Měli byste vidět alespoň jeden řádek „Font substitution warning“ pro každý chybějící font.  
2. **CSV report** – Po dokončení skriptu otevřete `missing-fonts-report.csv` a ověřte, že každý řádek uvádí název dokumentu a přesný chybějící font.  
3. **Uložený dokument** – Výstupní DOCX bude vykreslen s náhradními fonty, ale vizuální rozvržení se může lišit od originálu.

Pokud některý z těchto kroků neprobíhá podle popisu, zkontrolujte, že je Aspose.Words JAR na vašem classpath a že `input.docx` skutečně odkazuje na font, který není ve vašem OS nainstalován.

## Závěr

Právě jste dokončili **aspose warning callback tutorial**, který ukazuje, jak **detekovat chybějící fonty** a **sledovat chybějící fonty** v Java aplikacích. Registrací posluchače výstrah, načtením dokumentu a případným exportem výsledků získáte úplnou přehlednost o problémech souvisejících s fonty ještě před jejich výskytem v produkci.

Dále můžete zkoumat:

- Vložení chybějícího fontu přímo pomocí `LoadOptions.setFontSubstitution`.
- Použití třídy `FontSettings` k mapování chybějících fontů na konkrétní náhrady.
- Integraci CSV reportu do CI/CD pipeline, aby se buildy selhaly při výskytu nezdokumentovaných fontů.

Vyzkoušejte to, upravte callbacky tak, aby vyhovovaly vašemu logovacímu frameworku, a sledujte, jak se váš dokumentový workflow stane mnohem robustnějším. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}