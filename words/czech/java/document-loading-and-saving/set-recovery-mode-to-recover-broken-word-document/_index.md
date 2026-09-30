---
category: general
date: 2026-02-15
description: Nastavení režimu obnovy vám umožňuje načíst dokument s obnovou, což usnadňuje
  obnovení poškozeného dokumentu Word a opravu chyb při obnově dokumentu Word.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: cs
og_description: Nastavení režimu obnovy je klíčem k načtení dokumentu s obnovou, což
  vám umožní obnovit poškozené dokumenty Wordu v Javě.
og_title: Nastavte režim obnovy – Rychle obnovte poškozený dokument Word
tags:
- Aspose.Words
- Java
- Document Recovery
title: Nastavit režim obnovy k obnovení poškozeného dokumentu Word
url: /cs/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Jak obnovit poškozený Word dokument pomocí Aspose.Words

Už jste někdy zkusili otevřít soubor Word, který najednou odmítá načíst? Můžete se dívat na poškozený *.docx* a přemýšlet, jestli musíte začít od nuly. Dobrá zpráva? **set recovery mode** v Aspose.Words vám poskytuje elegantní způsob, jak *load document with recovery* a zachovat většinu obsahu nedotčenou.  

V tomto tutoriálu se přesně naučíte, jak **set recovery mode**, proč je volba *RELAXED* obvykle nejlepší pro poškozené soubory, a jak zacházet s občasnými *recover word document errors*, které stále unikají. Žádné externí nástroje, jen čistý Java a několik řádků kódu.

> **Co získáte:** kompletní, spustitelný příklad, který načte poškozený Word soubor, přeskočí nečitelné části a zanechá vás s použitelným objektem `Document`, připraveným k dalšímu zpracování.

---

## Předpoklady

- **Aspose.Words for Java** (v24.9 nebo novější) přidaný do vašeho projektu přes Maven nebo ručně jako JAR.
- **Poškozený .docx** soubor, který chcete otestovat (budeme ho nazývat `Corrupted.docx`).
- Základní znalost Javy – nemusíte být mistr Word‑processing, stačí vám pohodlné používání metody `main`.

Pokud vám něco chybí, stáhněte si nejnovější Aspose.Words JAR z [oficiálního webu](https://products.aspose.com/words/java) a přidejte jej do classpathu. To je vše – žádné další závislosti.

## Krok 1: Pochopte režimy obnovy

Aspose.Words nabízí dvě strategie obnovy:

| Mode | Behavior | When to use |
|------|----------|------------|
| **RELAXED** | Přeskočí nečitelné části, zbytek zachová. | Většina poškozených souborů – chcete **recover broken word document** bez výjimky. |
| **STRICT** | Vyvolá výjimku při jakékoli chybě. | Když potřebujete garantovat dokonalé, bezchybné načtení (zřídka u poškozených zdrojů). |

> **Pro tip:** *RELAXED* je výchozí pro scénáře „jen získat něco zpět“, zatímco *STRICT* je užitečný v automatizovaných pipelinech, kde selhání musí proces zastavit.

## Krok 2: Vytvořte objekt `LoadOptions` a **set recovery mode**

Zde se hlavní klíčové slovo objevuje v kódu. Výslovně **set recovery mode** na instanci `LoadOptions` před načtením souboru.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Proč je to důležité:** Voláním `setRecoveryMode` říkáte Aspose.Words, jak agresivně má soubor zachraňovat. Bez tohoto volání knihovna výchozí nastavení používá *STRICT*, což by přerušilo načítání při první známce potíží – čímž by se zmařil smysl workflow *recover broken word document*.

## Krok 3: Ověřte načtení – Opravdu jsme **recover broken word document**?

Po načtení můžete zkontrolovat objekt `Document`:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Pokud konzole zobrazí rozumný počet sekcí, úspěšně jste *load document with recovery*. V praxi si všimnete, že většina textu, tabulek a obrázků přežije, zatímco poškozené části jednoduše zmizí.

## Krok 4: Elegantně ošetřete zbývající **recover word document errors**

I v režimu *RELAXED* může několik okrajových případů stále vyvolat varování. Zabalte načítání do try‑catch, aby vaše aplikace zůstala funkční:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Kdy k tomu může dojít?** Pokud je soubor tak poškozený, že i uvolněný parser nedokáže identifikovat platnou strukturu dokumentu, Aspose.Words stále vyhodí výjimku. V těchto vzácných případech můžete požádat uživatele, aby poskytl jinou kopii.

## Krok 5: Uložte obnovený soubor (volitelné)

Většina vývojářů chce čistou verzi, kterou předají downstream systémům. Volání `save` níže zapíše nový `.docx`, který již neobsahuje poškozené fragmenty.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Nyní máte **recover broken word document**, které lze otevřít v Microsoft Word, Google Docs nebo jakémkoli jiném prohlížeči – bez chybových dialogů.

## Vizualizace (Obrázek)

![Diagram ukazující tok set recovery mode – od poškozeného souboru po obnovený dokument](https://example.com/images/recovery-flow.png "set recovery mode flow diagram")

*Alt text explicitně obsahuje primární klíčové slovo, pomáhá jak vyhledávačům, tak čtečkám obrazovek.*

## Časté otázky a okrajové případy

| Question | Answer |
|----------|--------|
| *Co když potřebuji zachovat poškozené části pro forenzní analýzu?* | Použijte `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` a zachyťte výjimku. Zpráva výjimky obsahuje podrobnosti o problematických částech. |
| *Mohu během běhu přepínat mezi RELAXED a STRICT?* | Ano – stačí vytvořit novou instanci `LoadOptions` s požadovaným režimem před každým načtením. |
| *Funguje to i se staršími .doc soubory?* | Ano. Stejné `LoadOptions` platí pro formáty `.doc` i `.docx`. |
| *Existuje penalizace výkonu?* | Minimální. Dodatečné zatížení parsování je zanedbatelné ve srovnání s náklady na plné načtení dokumentu. |

## Kompletní funkční příklad (připravený ke zkopírování)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Spusťte program, nasměrujte jej na váš poškozený soubor a sledujte výstup. Pokud vše proběhne hladce, uvidíte vytištěný počet stránek a vedle zdroje se objeví nový `Recovered.docx`.

## Závěr

Probrali jsme vše, co potřebujete k **set recovery mode** v Aspose.Words, od výběru správného výčtu `RecoveryMode` až po ošetření několika *recover word document errors*, které mohou stále nastat. Dodržením výše uvedených kroků můžete spolehlivě **load document with recovery**, zachovat dobré části poškozeného souboru a vytvořit čistou verzi připravenou pro jakékoli downstream zpracování.

Připraveni na další výzvu? Zkuste kombinovat **set recovery mode** s API pro **document cleaning** v Aspose.Words – odstraňování skrytých odstavců, opravu poškozených hypertextových odkazů nebo dokonce převod obnoveného souboru do PDF v jednom kroku. Možnosti jsou neomezené a nyní máte solidní základ pro řešení poškozených Word souborů naplno.

Šťastné programování a ať vaše dokumenty zůstávají zdravé!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}