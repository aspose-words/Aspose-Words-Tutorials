---
category: general
date: 2026-01-11
description: Naučte se zachytávat varování o nahrazení písma pomocí Aspose.Words pro
  Java. Tento tutoriál krok za krokem také pokrývá LoadOptions a zpětné volání varování.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: cs
og_description: Zachyťte varování o nahrazení písma pomocí Aspose.Words pro Javu.
  Postupujte podle tohoto návodu k nastavení LoadOptions a zpětného volání varování
  pro spolehlivé načítání dokumentů.
og_title: Zachycení varování o nahrazení fontů v Javě – kompletní tutoriál
tags:
- Aspose.Words
- Java
- Document Processing
title: Zachycení upozornění na nahrazení písma v Javě s Aspose.Words – Kompletní průvodce
url: /cs/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachycení varování o nahrazení písma – kompletní Java tutoriál

Už jste někdy potřebovali **zachytit varování o nahrazení písma** při otevírání Word dokumentu s chybějícími fonty? Je to častý problém, zejména když generujete PDF nebo tisknete na serveru, který nemá nainstalována všechna písma. Dobrá zpráva? Aspose.Words for Java to řeší jednoduše – stačí nakonfigurovat objekt `LoadOptions` a připojit varovný callback. V tomto průvodci uvidíte přesně, jak na to, proč je to důležité a co očekávat, když se varování spustí.

Dotkneme se také souvisejících témat, jako je **Aspose.Words font substitution**, použití **Java warning callback** a osvědčené postupy pro **LoadOptions usage**. Na konci budete mít připravený úryvek kódu, který zaznamená každou událost chybějícího fontu, takže vaše následné zpracování vás nikdy nepřekvapí.

## Požadavky

Než se pustíme dál, ujistěte se, že máte:

- Java 17 (nebo jakýkoli aktuální JDK) nainstalovaný a nakonfigurovaný.
- Aspose.Words for Java 23.10 (nebo novější) na classpath.
- Word dokument, který odkazuje na písmo, které nemáte lokálně (např. `DocWithMissingFont.docx`).
- Základní znalost Java bloků try/catch – nic složitého.

Pokud vám některá z těchto položek není známá, zastavte se na chvíli a nainstalujte knihovnu z Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Nyní, když je vše připraveno, pojďme na kód.

## Krok 1: Nastavte varovný callback pro **zachycení varování o nahrazení písma**

První, co potřebujete, je callback, který Aspose.Words zavolá vždy, když narazí na chybějící font. Zde **zachytíme varování o nahrazení písma**. Callback implementuje rozhraní `IWarningCallback` a kontroluje `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Proč je to důležité:** Bez callbacku Aspose.Words tiše nahrazuje chybějící font výchozím, a nikdy se nedozvíte, že se vizuální výstup změnil. Zachycením varování můžete logovat, upozorňovat nebo dokonce přerušit načítání, pokud je chybějící font kritický.

## Krok 2: Nakonfigurujte **LoadOptions** a zaregistrujte callback

Nyní vytvoříme instanci `LoadOptions` a připojíme náš `FontWarningCallback`. Tento krok je zásadní pro **LoadOptions usage** a zajišťuje, že každé načtení dokumentu projde stejným varovným filtrem.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

Tip: Můžete znovu použít stejný objekt `LoadOptions` pro více dokumentů, což ušetří několik řádků boilerplate kódu a zaručí konzistentní zpracování **document loading warnings** napříč aplikací.

## Krok 3: Načtěte dokument a pozorujte výstup

S připojeným callbackem stačí načíst váš Word soubor. Pokud dokument odkazuje na písmo, které není nainstalováno, callback se spustí a vypíše podrobnosti do konzole.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Očekávaný výstup v konzoli

Za předpokladu, že `DocWithMissingFont.docx` odkazuje na chybějící font *“Comic Sans MS”*, uvidíte něco podobného:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Pokud dokument **neobsahuje žádná chybějící písma**, konzole zobrazí jen poslední řádek, což potvrzuje, že váš callback nevytvořil žádné falešné poplachy.

## Krok 4: Řešení okrajových případů a běžných úskalí

### Více chybějících písem

Pokud dokument používá několik nedostupných fontů, callback se spustí jednou pro každý font. Dostanete sérii zpráv, každou s vlastním `source` a `description`. Žádný další kód není potřeba – jen se ujistěte, že váš logovací systém zvládne rychlé po sobě jdoucí volání.

### Potlačení varování

V ojedinělých případech můžete chtít ignorovat určité nahrazení (např. víte, že konkrétní fallback je přijatelný). Rozšiřte logiku callbacku:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Bezpečnost vlákna

Aspose.Words `LoadOptions` není ve výchozím nastavení thread‑safe. Pokud načítáte dokumenty paralelně, vytvořte samostatnou instanci `LoadOptions` pro každé vlákno nebo synchronizujte callback, aby nedošlo k závodním podmínkám.

## Krok 5: Ověření nahrazeného písma ve výsledném dokumentu

Po načtení můžete chtít potvrdit, že nahrazení skutečně proběhlo. API vám umožní iterovat přes všechny běhy (runs) a zkontrolovat efektivní název písma:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Tento úryvek vypíše každý textový běh s jeho finálním fontem. Je to užitečná kontrola, když stavíte automatizované pipeline pro konverzi do PDF.

## Kompletní funkční příklad

Spojením všech částí získáte kompletní, připravený program:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Uložte jej jako `FontSubstitutionInfo.java`, zkompilujte pomocí `javac` a spusťte `java FontSubstitutionInfo`. Měli byste vidět varovné zprávy (pokud nějaké jsou) následované seznamem běhů a jejich finálních fontů.

## Vizuální pomůcka

![Snímek obrazovky výstupu konzole zobrazující varování o nahrazení písma](/images/font-substitution-warning.png "příklad zachycení varování o nahrazení písma")

*Alt text:* **zachycení varování o nahrazení písma** – výstup v konzoli po načtení dokumentu s chybějícími písmy.

## Závěr

Nyní víte, jak **zachytit varování o nahrazení písma** pomocí Aspose.Words for Java. Nakonfigurováním objektu `LoadOptions` a poskytnutím vlastního `IWarningCallback` získáte úplnou přehlednost o všech událostech chybějícího fontu, které by jinak tiše ovlivnily vzhled dokumentu. Tento postup se přímo integruje do **Aspose.Words font substitution** handling, zajišťuje spolehlivé **document loading warnings** a dává vám flexibilitu logovat, upozorňovat nebo přerušovat podle vašich obchodních pravidel.

### Co dál?

- Prozkoumejte vzory **Java warning callback** pro jiné typy varování (např. `DEPRECATED_FEATURE`).
- Kombinujte tento přístup s **PDF konverzí**, aby bylo zajištěno, že nahrazená písma neporuší rozvržení.
- Ponořte se hlouběji do **LoadOptions usage** – experimentujte s `Password`, `Encoding` a `ResourceLoadingCallback` pro pokročilejší scénáře.

Neváhejte upravit callback, směrovat varování do logovacího frameworku nebo dokonce vyhodit vlastní výjimku, pokud chybí kritické písmo. Možnosti jsou neomezené a nyní máte pevný základ, na kterém můžete stavět.

Šťastné programování a ať se vaše dokumenty vždy vykreslí přesně tak, jak očekáváte!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}