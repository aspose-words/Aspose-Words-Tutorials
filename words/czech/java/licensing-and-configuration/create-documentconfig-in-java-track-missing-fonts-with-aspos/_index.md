---
category: general
date: 2026-07-06
description: Vytvořte DocumentConfig v Javě pro sledování chybějících fontů pomocí
  Aspose.Words – kompletní, krok za krokem průvodce pro vývojáře.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: cs
og_description: Vytvořte DocumentConfig v Javě pro sledování chybějících fontů pomocí
  Aspose.Words. Naučte se celý pracovní postup, od nastavení po zpracování varování.
og_title: Vytvořte DocumentConfig v Javě – Sledujte chybějící písma
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Vytvořte DocumentConfig v Javě – Sledujte chybějící fonty pomocí Aspose.Words
url: /cs/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte DocumentConfig v Javě – Sledujte chybějící písma s Aspose.Words

**Create DocumentConfig in Java** pro sledování varování o nahrazení písma při načítání dokumentu Word. Už jste se někdy ptali, proč některé znaky vypadají podivně po otevření DOCX? Pravděpodobně původní písmo není nainstalováno a Aspose.Words jej tiše nahradí. V tomto tutoriálu vám ukážeme, jak **sledovat chybějící písma**, abyste už nikdy nebyli překvapeni neznámým glyphem.

Provedeme vás vším, co potřebujete: nastavením Maven/Gradle, kódem, který vytváří `DocumentConfig`, vlastním `IWarningCallback`, který filtruje pouze upozornění na nahrazení písma, a rychlým způsobem, jak tyto zprávy zaznamenat. Na konci budete mít spustitelný příklad, který vypíše každé varování o chybějícím písmu do konzole (nebo do souboru, pokud chcete).

---

## Co se naučíte

- Proč je `DocumentConfig` správným místem pro zachycení událostí nahrazení písma.  
- Jak **sledovat chybějící písma** bez zaplňování logů nesouvisejícími varováními.  
- Kompletní, připravený Java program ke kopírování, který demonstruje techniku.  
- Tipy pro rozšíření řešení – např. zapisování varování do databáze nebo odesílání e‑mailových upozornění.

### Předpoklady

| Požadavek | Důvod |
|-------------|--------|
| Java 8 nebo novější | Aspose.Words for Java podporuje JDK 8+. |
| Knihovna Aspose.Words pro Java (nejnovější verze) | Poskytuje `DocumentConfig`, `IWarningCallback` atd. |
| IDE nebo nástroj pro sestavení (IntelliJ, Eclipse, Maven/Gradle) | Pro kompilaci a spuštění ukázky. |
| DOCX soubor, který odkazuje na písma, která nemáte nainstalována | Pro zobrazení varování v akci. |

Pokud už máte projekt, stačí přidat závislost Aspose a můžete začít.

---

## Krok 1: Přidejte Aspose.Words do svého projektu

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Tip:** Verze zdarma funguje perfektně pro testování, ale nezapomeňte použít licenci pro produkci, aby se odstranila vodotisková značka hodnocení.

---

## Krok 2: Vytvořte DocumentConfig a zaregistrujte Warning Callback

Srdce řešení spočívá v tomto úryvku. **Vytvoříme DocumentConfig**, připojíme vlastní `IWarningCallback` a řekneme mu, aby **sledoval pouze chybějící písma**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Proč to funguje:** Když Aspose.Words parsuje dokument, vydává objekty `WarningInfo` pro jakékoli nesrovnalosti. Poskytnutím callbacku zachytíte tato varování *před* tím, než zmizí do prázdnoty. Podmínka `if` zajišťuje, že **sledujeme jen chybějící písma**, a ignorujeme ostatní varování, jako jsou zastaralé značky nebo nepodporované funkce.

---

## Krok 3: Spusťte příklad a pozorujte výstup

Umístěte DOCX, který odkazuje na písmo, které nemáte (např. „Comic Sans MS“ na Linuxu). Spusťte program:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Měli byste vidět něco podobného:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Každý řádek odpovídá chybějícímu písmu, které Aspose automaticky nahradil. Pokud neexistují žádná chybějící písma, program zůstane tichý – přesně to, co chcete pro čistý log.

---

## Krok 4: Uložte seznam chybějících písem (volitelné)

Tisk do konzole je praktický pro demonstrace, ale ve skutečné službě pravděpodobně data uložíte. Zde je rychlý způsob, jak varování zapsat do textového souboru.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Nyní každý událost chybějícího písma přidá řádek do `missing-fonts.log`. Později můžete tento soubor parsovat, přenést do monitorovacího dashboardu nebo dokonce spustit upozornění, pokud kritické písmo zmizí ze serveru.

---

## Krok 5: Časté problémy a jak se jim vyhnout

| Příznak | Pravděpodná příčina | Řešení |
|---------|---------------------|--------|
| Neobjevují se žádná varování, i když DOCX používá neznámá písma | Callback není zaregistrován nebo `setWarningCallback` byl zavolán po načtení dokumentu | Ujistěte se, že `config.setWarningCallback(...)` je vykonáno **před** vytvořením instance `Document`. |
| Aplikace spadne s `NullPointerException` | `info.getDescription()` vrací `null` pro některé vzácné typy varování | Ošetřete null: `String desc = info.getDescription(); if (desc != null) …` |
| Příliš mnoho nesouvisejících varování zaplavuje konzoli | Callback filtruje pouze `FONT_SUBSTITUTION`? | Zkontrolujte podmínku `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Zpomalení výkonu při velkých dávkách | Synchronní zápis do souboru pro každé varování | Zapisujte po dávkách nebo použijte `BufferedWriter` ke snížení I/O zátěže. |

---

## Krok 6: Rozšíření řešení – od konzole k podnikovému nasazení

- **Zaznamenávání do databáze:** Nahraďte `FileWriter` JDBC insertem; uložte `documentName`, `missingFont` a `timestamp`.  
- **E‑mailová upozornění:** Připojte se k JavaMail; pošlete souhrn po zpracování dávky dokumentů.  
- **Vlastní logika nahrazení:** Místo toho, aby Aspose vybral náhradní písmo, můžete načíst lokální kolekci písem pomocí `FontSettings.setFontsFolder()` a znovu načíst dokument, pokud dojde k nahrazení.

Tyto rozšíření zachovávají jádro myšlenky – **vytvořit DocumentConfig** a **sledovat chybějící písma** – a zároveň umožňují škálovat řešení pro produkční potřeby.

---

## Závěr

Nyní máte solidní, připravený ke kopírování vzor pro **vytvoření DocumentConfig** v Javě a jeho použití k **sledování chybějících písem** s Aspose.Words. Přístup je nenáročný, vyžaduje jen několik řádků kódu a dává vám plnou kontrolu nad tím, jak jsou varování o nahrazení písem zpracovávána. Ať už budujete službu pro konverzi dokumentů, automatizovaný generátor reportů nebo nástroj pro audit souladu, přesná znalost chybějících písem vám může ušetřit hodiny ladění.

Další kroky? Zkuste nahradit výstup do konzole strukturovaným JSON logem nebo integrovat callback do Spring Boot mikroservisu, který zpracovává nahrané soubory v reálném čase. A pokud narazíte na nějaké okrajové případy – například vlastní OpenType písmo, které Aspose nedokáže parsovat – zanechte komentář níže; společně to vyřešíme.

Šťastné programování a ať se vaše PDF vždy vykreslují s očekávanými písmy!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Používání písem v Aspose.Words pro Java](/words/english/java/using-document-elements/using-fonts/)
- [Přizpůsobení barev motivu a písem v Aspose.Words Java: Komplexní průvodce](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Jak vytvořit PDF dokumenty s Aspose.Words pro Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}