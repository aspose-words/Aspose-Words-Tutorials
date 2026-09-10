---
category: general
date: 2026-02-15
description: Naučte se, jak získat chybějící písma při načítání dokumentu Word v Javě
  pomocí Aspose.Words. Zahrnuje zpětné volání varování a zpracování náhrady písem.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: cs
og_description: Jak získat chybějící písma v Javě s Aspose.Words. Objevte callbacky
  varování, zpracování náhrady písem a osvědčené postupy při zpracování dokumentů.
og_title: Jak získat chybějící písma v Javě – Průvodce Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Jak získat chybějící fonty v Javě – Průvodce Aspose.Words
url: /cs/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak získat chybějící písma v Javě – průvodce Aspose.Words

Už jste někdy otevřeli dokument Word v Javě a viděli podivné nahrazení písem a přemýšleli **jak získat chybějící písma**? Nejste první, kdo se s tím setkal. V mnoha podnikových aplikacích mohou varování o chybějících písmenech narušit vizuální věrnost zpráv, smluv nebo marketingových materiálů.

Dobrá zpráva? Aspose.Words vám poskytuje čistý způsob, jak zachytit tato varování pomocí callbacku, takže můžete logovat, nahrazovat nebo dokonce upozornit uživatele před vykreslením dokumentu. V tomto tutoriálu projdeme kompletním, spustitelným příkladem, který ukazuje **jak získat chybějící písma**, vysvětluje, proč je callback důležitý, a pokrývá několik triků pro okrajové případy, které můžete potřebovat v reálných projektech.

> **Tip:** Pokud již používáte Aspose.Words 22.12 nebo novější, API zobrazené níže funguje hned po vybalení bez další konfigurace.

---

![Diagram ilustrující, jak získat chybějící písma pomocí Aspose.Words warning callback](how-to-get-missing-fonts-diagram.png "diagram jak získat chybějící písma")

## Co tento tutoriál pokrývá

- Nastavení **Java LoadOptions warning callback** pro zachycení varování o nahrazení písem.  
- Filtrování varování, aby se zobrazovaly jen ta související s chybějícími písmy.  
- Vytištění přehledné, lidsky čitelné zprávy o tom, která písma byla nahrazena a čím byla nahrazena.  
- Tipy pro práci s velkými dokumenty, přizpůsobení úrovně varování a integraci řešení do většího zpracovatelského pipeline.

Na konci tohoto průvodce budete schopni odpovědět na otázku “**jak získat chybějící písma**?” pomocí připraveného spustitelného úryvku kódu a solidního pochopení základních mechanismů.

### Požadavky

- Java 8 nebo novější nainstalována.  
- Knihovna Aspose.Words pro Java (stáhněte z oficiálního webu nebo přidejte pomocí Maven/Gradle).  
- Dokument Word, který odkazuje na písmo, které není nainstalováno na vašem počítači (např. `MissingFont.docx`).  

Pokud vám něco chybí, stáhněte si knihovnu hned—přidání do Maven je tak jednoduché:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Krok 1: Připravte kolekci pro varování o nahrazení písem

Před načtením dokumentu potřebujeme místo pro uložení všech varování, která Aspose.Words generuje. `ArrayList<WarningInfo>` funguje dobře, protože zachovává pořadí a umožňuje pozdější iteraci.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Proč je to důležité:* Callback varování může být vyvolán desítkykrát pro jeden soubor—myslete na každou chybějící glyfu, každou problém s vloženým obrázkem atd. Tím, že je nejprve shromáždíte, udržíte fázi načítání rychlou a odložíte zpracování do řízené smyčky.

---

## Krok 2: Nakonfigurujte LoadOptions s varovným callbackem

Aspose.Words vám umožní připojit `IWarningCallback`. Uvnitř callbacku přidáme každé `WarningInfo` do našeho seznamu z Kroku 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Vysvětlení:* Metoda `warning` je volána **synchronně** během načítání dokumentu. Pouhým vložením `WarningInfo` do `fontWarnings` se vyhneme těžkému I/O (např. logování do souboru), které by mohlo načítání zpomalit. Tento vzor—shromáždit‑pak‑zpracovat—je doporučený způsob, jak zacházet s velkými dávkami varování.

---

## Krok 3: Načtěte dokument pomocí nakonfigurovaných možností

Nyní skutečně načteme soubor Word. Pokud dokument obsahuje písma, která nejsou nainstalována, Aspose.Words je automaticky nahradí a spustí callback varování, který jsme právě nastavili.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Co se děje pod kapotou?* Aspose.Words parsuje tabulku písem v souboru, porovnává ji s písmy dostupnými v hostitelském OS a pro každý chybějící záznam vytvoří `WarningInfo` s `WarningSource.FontSubstitution`. Tento zdroj bude klíčem, který použijeme k izolaci varování o chybějících písmenech.

---

## Krok 4: Filtrujte a zobrazte pouze varování o nahrazení písem

Po načtení může `fontWarnings` obsahovat směs zpráv (např. zastaralé funkce, problémy s obrázky). Zajímáme se jen o chybějící písma, takže projdeme seznam a vytiskneme stručnou zprávu.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Ukázkový výstup**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Proč je to užitečné:* Pole `description` vám říká, které písmo dokument požadoval, zatímco `additionalInfo` říká, co Aspose.Words ve skutečnosti použil. S těmito údaji můžete:

- Vyzvat uživatele k instalaci chybějícího písma.  
- Programově vložit náhradní písmo do dokumentu (`doc.getFontInfos().add(...)`).  
- Zaznamenat událost pro audity souladu.

---

## Řešení okrajových případů a běžných variant

### 1. Potlačení ne‑písmových varování

Pokud chcete jen zprávy související s písmy, můžete callback zpřesnit:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Tím se snižuje zatížení paměti při zpracování obrovských dávek.

### 2. Úprava závažnosti varování

Aspose.Words kategorizuje varování podle `WarningType`. Pro chybějící písma obvykle uvidíte `WarningType.FontSubstitution`. Pokud je potřebujete považovat za chyby (např. přerušit načítání), vyhoďte výjimku uvnitř callbacku:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Práce se streamy místo souborů

Někdy dokumenty pocházejí z databáze nebo HTTP požadavku. Stejný přístup funguje s `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Jen nezapomeňte po načtení stream uzavřít.

### 4. Použití vlastního adresáře s písmy

Pokud máte kolekci firemních písem uložených na sdíleném disku, nasměrujte Aspose.Words na tento adresář:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Nyní knihovna bude hledat tam *před* tím, než se vrátí k systémovým písmům, což dramaticky snižuje počet varování o chybějících písmenech.

---

## Kompletní funkční příklad

Spojením všeho dohromady zde máte samostatnou třídu, kterou můžete vložit do libovolného Java projektu:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Spusťte tento program a uvidíte přehledný seznam všech písem, která Aspose.Words muselo nahradit. Žádné extra knihovny, žádná skrytá magie—pouze čistá Java a síla **Aspose.Words missing font** API.

---

## Závěr

Odpověděli jsme na hlavní otázku **jak získat chybějící písma** v prostředí Java pomocí Aspose.Words. Připojením `LoadOptions` varovného callbacku, sběrem objektů `WarningInfo` a filtrováním podle zdrojů `FontSubstitution` získáte úplnou přehlednost o problémech souvisejících s písmy před jakýmkoli vykreslením. Přístup škáluje od utilit pro jeden soubor po masivní dávkové procesory a je dostatečně flexibilní, aby podporoval vlastní adresáře s písmy, zpracování závažnosti nebo vstupy založené na streamech.

Další kroky? Zkuste vložit náhradní písma přímo do dokumentu (`doc.getFontInfos().add(...)`), aby finální soubor byl skutečně samostatný, nebo integrujte zprávu o varování do monitorovacího dashboardu. Můžete také prozkoumat související témata jako **document processing Java**, **Aspose.Words font substitution warning** a **Java LoadOptions warning callback**, abyste prohloubili své znalosti.

Šťastné programování a ať se vaše dokumenty vždy vykreslují s očekávanými písmy!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}