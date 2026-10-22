---
category: general
date: 2026-05-04
description: Naučte se, jak mohou aspose words loadoptions obnovit poškozené soubory
  Word, použít režim obnovy, opravit poškozený docx a získat počet stránek ve Wordu
  v jediném tutoriálu.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: cs
og_description: Ovládněte možnosti načítání Aspose.Words pro obnovu poškozených souborů
  Word, vyberte správný režim obnovy, opravte poškozené docx a zjistěte počet stránek.
og_title: aspose words loadoptions – Obnovit poškozené dokumenty Word
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Obnovte poškozené Word dokumenty v Javě
url: /cs/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Obnova poškozených Word dokumentů v Javě

Už jste někdy zkoušeli otevřít soubor Word, který najednou odmítá načíst? Je to ten nepříjemný pocit, když vám klient pošle **poškozený docx** a nemáte tušení, jestli jej lze zachránit. Dobrá zpráva? S **aspose words loadoptions** můžete Aspose.Words přesně říct, jak se má chovat, když narazí na poškozený dokument – zda má vyhodit výjimku nebo se pokusit o tichou opravu.  

V tomto průvodci si projdeme používání `LoadOptions` k **obnovení poškozených Word** souborů, prozkoumáme nastavení **use recovery mode**, uvidíme, jak **automaticky opravit poškozený docx**, a nakonec **získáme počet stránek** obnoveného dokumentu. Žádné externí nástroje, jen čistá Java a Aspose.Words.

## Co budete potřebovat

- **Aspose.Words for Java** (v24.12 nebo novější) – nejnovější verze přidává několik dalších bezpečnostních kontrol.
- **Java IDE** (IntelliJ IDEA, Eclipse nebo i jednoduchý textový editor s `javac`).
- **Poškozený DOCX**, který chcete otestovat (budeme ho nazývat `Corrupted.docx`).
- **Základní znalost** syntaxe Javy – nic složitého, jen obvyklé `public static void main`.

> **Tip:** mějte zálohu původního souboru; pokusy o obnovu mohou někdy přepsat části binárky.

## Krok 1: Vytvořte LoadOptions – jádro obnovy

První, co uděláte, je vytvořit objekt `LoadOptions`. Tento objekt je vaše ovládací panel; říká Aspose.Words, jak má soubor zacházet, když narazí na problémy.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Proč je tento krok zásadní? Protože bez `LoadOptions` knihovna přechází na výchozí chování, které může tiše ignorovat chyby nebo, co je horší, vrátit částečně načtený dokument, který později spadne. Explicitním nastavením možností získáte deterministické zpracování chyb.

## Krok 2: Vyberte správný režim obnovy

Aspose.Words nabízí dvě strategie obnovy:

| Režim | Chování |
|------|-----------|
| `RecoveryMode.STRICT` | Vyhodí výjimku, pokud dokument nelze plně opravit. |
| `RecoveryMode.REPAIR` | Pokusí se soubor opravit a pokračuje v načítání, i když je část obsahu ztracena. |

Pro scénář **recover corrupted word**, kde potřebujete vědět, jestli oprava uspěla, je `STRICT` nejbezpečnější volbou. Pokud dáváte přednost přístupu „nejlepší snaha“, přepněte na `REPAIR`.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Proč zvolit jeden nad druhým?**  
> *STRICT* vám dává jasný signál – buď je dokument použitelný, nebo musíte uživatele upozornit. *REPAIR* je užitečný v dávkových úlohách, kde můžete tolerovat ztrátu jedné‑dvou obrázků.

## Krok 3: Načtěte možná poškozený dokument

Nyní skutečně otevřete soubor a předáte mu `LoadOptions`, které jste právě nakonfigurovali. Pokud je soubor mimo opravu a zvolili jste `STRICT`, vyvolá se výjimka; jinak získáte objekt `Document` připravený k inspekci.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Všimněte si, že cesta může být absolutní nebo relativní k kořeni projektu. Třída `Document` abstrahuje celý Word soubor, což usnadňuje dotazování na věci jako počet stránek, sekce nebo dokonce úpravu obsahu po obnově.

## Krok 4: Ověřte načtení – Získejte počet stránek Wordu

Rychlá kontrola je zeptat se Aspose.Words, kolik stránek podle něj dokument má. Pokud je počet nenulový, pravděpodobně se vám podařilo **repair corrupted docx**.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Typický výstup:

```
Loaded successfully, page count = 12
```

Pokud byl dokument skutečně nečitelný při `STRICT`, kód by před dosažením tohoto řádku vyhodil výjimku. To dělá kontrolu `page count` jak ověřením, tak užitečnou informací pro následnou logiku (např. stránkování ve webovém prohlížeči).

## Kompletní funkční příklad

Níže je kompletní, připravený ke spuštění Java program, který spojuje všechny části. Zkopírujte jej do souboru s názvem `RecoveryModeDemo.java`, upravte cestu a spusťte `javac RecoveryModeDemo.java && java RecoveryModeDemo`.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Očekávaný výsledek

- **Pokud je soubor obnovitelný:** konzole vypíše počet stránek a můžete bezpečně pokračovat se zpracováním objektu `Document`.
- **Pokud je soubor mimo opravu (režim STRICT):** vyvolá se `com.aspose.words.UnsupportedFileFormatException` (nebo podobná) výjimka, kterou můžete zachytit a elegantně ošetřit.

## Často kladené otázky a okrajové případy

### Co když potřebuji zaznamenat přesné podrobnosti chyby?

Zabalte kód načítání do bloku `try‑catch` a logujte `e.getMessage()`. Dostanete tak jasný důvod – zda chybí část, je poškozený vztah nebo poškozený stream.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Můžu obnovit jen konkrétní části (např. text, ale ne obrázky)?

Aspose.Words neumožňuje jemné přepínače obnovy, ale po načtení můžete iterovat přes elementy `NodeType` a odstranit všechny, které jsou `NodeType.SHAPE` (obrázky), pokud způsobují problémy v dalším zpracování.

### Funguje to i se staršími soubory `.doc`?

Ano. `LoadOptions` funguje se všemi formáty Wordu (`.doc`, `.docx`, `.dot`, `.dotx`). Stejná logika obnovy se použije.

### Jak knihovna zachází se soubory chráněnými heslem?

Pokud je soubor šifrovaný, `LoadOptions` heslo nepřekoná. Musíte heslo předat pomocí `loadOptions.setPassword("yourPassword")`. Režim obnovy se aktivuje až po úspěšném dešifrování.

## Tipy pro produkční nasazení

- **Logujte zvolený režim obnovy** – pomůže při pozdější auditaci, proč konkrétní soubor uspěl nebo selhal.
- **Nikdy nepřepisujte původní soubor** – uložte obnovený dokument na nové místo (`document.save("Recovered.docx")`).
- **Kombinujte s validací** – po obnově spusťte rychlou kontrolu pravopisu nebo strukturální validaci, aby dokument splňoval vaše obchodní pravidla.
- **Dávkové zpracování** – při práci s mnoha soubory je iterujte, zachytávejte výjimky individuálně a vytvářejte souhrnnou zprávu o úspěších a neúspěších.

## Závěr

Nyní máte solidní, end‑to‑end recept na použití **aspose words loadoptions** k **recovery corrupted Word** dokumentů, rozhodnutí, zda **use recovery mode** přísně nebo permisivně, volitelně **repair corrupted docx**, a nakonec **get the word page count** obnoveného souboru. Přístup je deterministický, snadno se integruje do existujících Java pipeline a dává vám plnou kontrolu nad tím, jak agresivně má knihovna jednat při setkání s poškozenými binárními soubory.

Chcete jít dál? Vyzkoušejte výměnu `RecoveryMode.STRICT` za `REPAIR` v dávkové úloze, nebo rozšiřte příklad o automatické uložení opraveného souboru do bezpečné složky. Možnosti jsou neomezené a s Aspose.Words jste připraveni zvládnout i ty nejhorší Word souborové chyby.

Šťastné programování a ať se vaše dokumenty vždy načítají čistě!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}