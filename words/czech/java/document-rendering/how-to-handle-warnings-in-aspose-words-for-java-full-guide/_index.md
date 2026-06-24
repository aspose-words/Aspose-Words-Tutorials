---
category: general
date: 2026-06-24
description: Jak zacházet s varováními při zpracování souborů Word v Javě. Naučte
  se zachytávat písma, vypisovat zprávy o písmu a plynule řešit chybějící písma.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: cs
og_description: jak zacházet s varováními v Aspose.Words pro Javu. Tento průvodce
  ukazuje, jak zachytit písma, tisknout zprávy o písmu a efektivně spravovat chybějící
  písma.
og_title: Jak zacházet s varováními v Aspose.Words – kompletní Java tutoriál
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Jak zpracovávat varování v Aspose.Words pro Java – kompletní průvodce
url: /cs/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak zacházet s varováními v Aspose.Words pro Java – Kompletní průvodce

Už jste se někdy zamýšleli **jak zacházet s varováními**, která se objeví při načítání Word dokumentu pomocí Aspose.Words? Možná jste narazili na kryptické zprávy o chybějících fontech a pomysleli si: „Skvěle, můj PDF je posunutý – co dál?“ Nejste v tom sami. V mnoha reálných projektech jsou varování o substituci fontů tichými viníky, kteří narušují věrnost rozvržení.

V tomto tutoriálu vás provedeme praktickým řešením: registrací callbacku pro varování, detekcí upozornění souvisejících s fonty a **tiskem zpráv o fontech**, abyste se mohli rozhodnout, zda vložit náhradní font nebo dodat vlastní soubor fontu. Na konci budete vědět **jak zachytit fonty**, jak **elegantně řešit chybějící fonty** a jak udržet vaši konverzní pipeline dokumentů pevnou jako skála.

## Co se naučíte

- Účel callbacků pro varování v Aspose.Words.
- Jak detekovat a filtrovat varování o *substituci fontů*.
- Způsoby, jak zaznamenat nebo zobrazit **tisk zpráv o fontech** pro ladění.
- Strategie pro **řešení chybějících fontů** v produkčních prostředích.
- Kompletní, připravený příklad v Javě, který můžete vložit do libovolného Maven nebo Gradle projektu.

### Předpoklady

- Java 8 nebo novější (kód funguje také s JDK 11).
- Knihovna Aspose.Words pro Java (stáhněte z webu Aspose nebo přidejte Maven/Gradle závislost).
- Vzorek `input.docx`, který odkazuje na font, který nemáte nainstalovaný lokálně (ideální pro testování callbacku).

---

## Krok 1: Nastavte svůj projekt a importujte Aspose.Words

Než budete moci **zacházet s varováními**, potřebujete Java projekt, který zná Aspose.Words. Pokud používáte Maven, přidejte tento úryvek do svého `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Pro Gradle je ekvivalentní:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

Jakmile je závislost vyřešena, importujte potřebné třídy ve svém Java zdrojovém souboru:

```java
import com.aspose.words.*;
```

> **Pro tip:** Udržujte své Aspose knihovny aktuální. Nová vydání často vylepšují zpracování varování a přidávají podrobnější informace v `WarningInfo`.

---

## Krok 2: Načtěte Word dokument a zaregistrujte callback pro varování

Nyní, když je knihovna na classpath, můžeme **zachytit fonty**, které engine nahrazuje. Klíčové je `Document.setWarningCallback`, který přijímá libovolnou implementaci `IWarningCallback`. Níže je stručný, ale kompletní příklad, který vypisuje každé varování o substituci fontu do konzole.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### Proč to funguje

- **`Document.setWarningCallback`** říká Aspose.Words, aby volalo váš kód pokaždé, když narazí na situaci vyžadující varování.
- **`WarningInfo.getWarningType()`** nám umožňuje rozlišovat mezi různými kategoriemi (např. `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`). Zaměřením se na `FONT_SUBSTITUTION` **řešíme chybějící fonty** bez zaplňování logu.
- Řádek `System.out.println` **vypisuje zprávy o fontech** v reálném čase, což je neocenitelné během vývoje nebo při řešení problémů v produkční pipeline.

---

## Krok 3: Otestujte callback s chybějícím fontem

Abychom potvrdili, že náš callback skutečně **zachytává fonty**, vytvořte Word soubor, který používá font neinstalovaný na vašem stroji – například “Comic Sans MS” na Linux serveru, kde je jen “DejaVu Sans”. Když spustíte demo, měli byste vidět výstup podobný tomuto:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Pokud nevidíte žádné zprávy, zkontrolujte:

1. Dokument skutečně odkazuje na chybějící font.
2. Cesta k `input.docx` je správná.
3. Používáte aktuální verzi Aspose.Words (starší buildy někdy potlačují určitá varování).

---

## Krok 4: Pokročilé zacházení – Vkládání náhradních fontů

Vypisování varování je skvělé, ale v produkčním systému můžete chtít **automaticky řešit chybějící fonty**. Jeden běžný přístup je vložit náhradní font (např. “Liberation Sans”) před uložením. Zde je, jak můžete rozšířit callback tak, aby programově nahradil chybějící font:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**Co se děje?**

- Analyzujeme popis varování a získáme název chybějícího fontu.
- Pomocí `FontSettings` řekneme Aspose.Words, aby nahradil *každý* výskyt tohoto fontu fontem “Liberation Sans”.
- Při dalším renderování nebo ukládání dokumentu se náhrada použije tiše.

> **Upozornění:** Nadměrné používání automatické substituce může zakrýt skutečné designové problémy. Je nejlepší zaznamenat substituci (jak už **vypisujeme zprávy o fontech**) a během QA ručně zkontrolovat výstup.

---

## Krok 5: Logování místo vypisování – Připraveno pro produkci

V CI/CD pipeline pravděpodobně nechcete výstup do konzole. Nahraďte `System.out.println` vhodným loggerem (např. SLF4J). Zde je rychlá úprava:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

Nyní se vaše varování integrují s existujícími nástroji pro agregaci logů (ELK, Splunk atd.), což usnadňuje **řešení chybějících fontů** napříč mnoha úlohami.

---

## Krok 6: Časté úskalí a jak se jim vyhnout

| Problém | Proč se vyskytuje | Oprava |
|---------|-------------------|--------|
| Neobjevují se žádná varování | Font ve skutečnosti existuje v systému, nebo dokument používá vložené fonty. | Ověřte, že testovací dokument skutečně odkazuje na nedostupný font. |
| Callback není volán | `setWarningCallback` byl zavolán **po** načtení dokumentu. | Zaregistrujte callback **před** jakoukoliv operací, která může varování vyvolat (např. před `Document.save`). |
| Více varování zaplaví log | Velké dokumenty spouštějí mnoho substitucí. | Přidejte throttling mechanismus nebo agregujte zprávy před logováním. |
| Substituce se neaplikuje | `FontSettings` není propojen s instancí dokumentu. | Ujistěte se, že `FontSettings` nastavujete na stejný objekt `Document`, který ukládáte. |

---

## Krok 7: Kompletní, připravený příklad

Níže je kompletní program, připravený ke zkopírování. Obsahuje importy, callback, logování a strategii náhradního fontu.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**Očekávaný výstup do konzole/logu** (při chybějícím “Comic Sans MS”):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

Výsledný `output.pdf` použije “Liberation Sans” všude, kde byl v dokumentu odkazován “Comic Sans MS”, díky automatické substituci, kterou jsme přidali.

---

## Závěr

Právě jsme prošli **zacházením s varováními** v Aspose.Words pro Java od začátku do konce. Registrací callbacku pro varování, filtrováním **varování o substituci fontů** a **vypisováním zpráv o fontech** získáte plnou přehlednost o scénářích s chybějícími fonty. Přidáním náhrady pomocí `FontSettings` můžete **řešit chybějící fonty** bez manuální intervence, zatímco správný logging framework učiní řešení připraveným pro produkci.

Další kroky? Zkuste spojit tento přístup s Aspose.PDF a ověřit, že vložené fonty přežijí konverzi, nebo prozkoumejte další typy varování (např. `DEPRECATED_FEATURE`) a připravte svůj kód na budoucnost. A pokud vás zajímá **jak zachytit fonty** z vzdáleného úložiště, podívejte se dál.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Zachycení varování o substituci fontů v Javě s Aspose.Words – Kompletní průvodce](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Jak detekovat fonty v Aspose.Words – Zpracování varování a nastavení](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak zachytit fonty v Aspose.Words – Kompletní průvodce](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}