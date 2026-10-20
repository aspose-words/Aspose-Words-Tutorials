---
category: general
date: 2026-08-04
description: Načtěte podtržení markdownu v Javě a zachovejte formátování markdownu
  při načítání markdownu do dokumentu. Postupujte podle tohoto krok‑za‑krokem návodu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: cs
lastmod: 2026-08-04
og_description: Načtěte podtržení v markdownu v Javě a zachovejte formátování markdownu.
  Naučte se, jak načíst markdown do dokumentu s plnou podporou podtržení.
og_image_alt: Diagram showing load markdown underline process
og_title: Načíst podtržení markdown v Javě – krok za krokem průvodce
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Načtení podtržení v Markdownu v Javě – kompletní programovací průvodce
url: /cs/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Načtení podtržení v Markdownu v Javě – kompletní programovací průvodce

Pokud potřebujete **load markdown underline** při převodu souboru Markdown na objekt `Document`, tento průvodce vám přesně ukáže, jak na to. Také se naučíte, jak **load markdown into document** bez ztráty podtržení, což zajistí, že původní formátování Markdownu bude zcela zachováno.

Tutoriál pokrývá vše, co potřebujete vědět: požadované knihovny, každý konfigurační krok a jak ověřit, že podtržení přežilo import. Na konci budete mít znovupoužitelný úryvek kódu, který můžete vložit do libovolného Java projektu.

## Požadavky

- Java 17 nebo novější nainstalovaná (příklad používá moderní modulový systém)
- Nejnovější verze **GroupDocs.Viewer** (nebo kompatibilní knihovna, která poskytuje `LoadOptions` a `Document`)
- Soubor Markdown (`sample.md`) obsahující podtržený text, např. `<u>underlined</u>` nebo syntaxi GitHub‑flavored `__underlined__`
- IDE jako IntelliJ IDEA nebo VS Code, i když funguje jakýkoli textový editor

Tyto požadavky zaručují, že kód poběží bez další konfigurace.

## Načtení podtržení v Markdownu – krok za krokem průvodce

Proces se skládá ze tří základních akcí: vytvořit instanci `LoadOptions`, povolit detekci podtržení a nakonec načíst soubor Markdown s těmito možnostmi. Každý krok je vysvětlen níže.

### Krok 1: Vytvořte `LoadOptions` pro dokument

`LoadOptions` vám umožňuje přizpůsobit, jak knihovna parsuje zdrojový soubor. Vytvoření nové instance vám poskytne čistý základ pro další nastavení.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

Objekt `LoadOptions` je vstupním bodem pro všechna vylepšení související s importem. V dalším kroku jej použijete k zapnutí detekce podtržení.

### Krok 2: Povolit detekci formátování podtržení při načítání

Ve výchozím nastavení může prohlížeč ignorovat tagy podtržení, protože jsou v Markdownu méně běžné. Povolení tohoto příznaku řekne parseru, aby zachoval podtržené úseky nedotčeny.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Nastavení `setImportUnderlineFormatting(true)` zajistí, že jakýkoli HTML tag `<u>` nebo syntaxi podtržení ve stylu GitHub‑flavored bude přeložena do modelu `Document` jako podtržený styl. Toto je klíčová akce, která umožňuje, aby **load markdown underline** fungovalo podle očekávání.

### Krok 3: Načtěte soubor Markdown pomocí nakonfigurovaných možností

Nyní můžete soubor načíst. Předávejte objekt `loadOptions` do konstruktoru `Document`, aby parser respektoval příznak podtržení.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Po dokončení konstruktoru obsahuje `markdownDoc` kompletní paměťovou reprezentaci zdroje Markdown, včetně podtržených úseků.

### Krok 4: Ověřte, že formátování podtržení je zachováno

Rychlá kontrola vám pomůže potvrdit, že **preserve markdown formatting** fungovalo. Následující úryvek vypíše text každého odstavce a označí podtržené fragmenty vlnovkou (`~`) pro lepší viditelnost.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Očekávaný výstup** (předpokládáme, že `sample.md` obsahuje `This is __underlined__ text`):

```
This is ~underlined~ text
```

Vlnovky naznačují, že styl podtržení přežil import, což potvrzuje, že operace **load markdown into document** zachovala původní formátování.

## Časté úskalí a jak se jim vyhnout

| Symptom | Příčina | Řešení |
|---|---|---|
| Podtržení zmizí po načtení | `setImportUnderlineFormatting` ponechán na výchozím `false` | Ujistěte se, že voláte `loadOptions.setImportUnderlineFormatting(true)` před vytvořením `Document`. |
| Pouze část textu je podtržena | Smíšená syntaxe Markdown (např. HTML `<u>` smíšené s `__underline__`) | Knihovna podporuje obojí; ověřte, že zdrojový soubor používá jednotný znak pro podtržení. |
| Dokument se nenačte | Nesprávná cesta k souboru nebo chybějící závislosti knihovny | Použijte absolutní cestu nebo umístěte `sample.md` relativně k pracovnímu adresáři; zahrňte JAR soubory vieweru do classpath. |

**Pro tip:** Pokud také potřebujete zachovat tučné nebo kurzívní styly, povolte je pomocí `setImportBoldFormatting(true)` a `setImportItalicFormatting(true)`. Kombinací těchto příznaků získáte plně věrný import většiny běžných stylů v Markdownu.

## Kompletní spustitelný příklad

Níže je samostatný Java program, který spojuje vše dohromady. Zkopírujte kód do souboru pojmenovaného `LoadMarkdownUnderlineDemo.java`, upravte cestu k souboru a spusťte jej pomocí `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Spuštěním programu se vypíše obsah dokumentu s podtrženými značkami, což dokazuje, že funkce **load markdown underline** funguje a že můžete **preserve markdown formatting** po celou dobu importního řetězce.

## Závěr

Nyní víte, jak **load markdown underline** v Javě, jak **load markdown into document** při zachování původního stylu, a jak ověřit, že formátování podtržení je neporušené. Tento přístup funguje s nejnovějšími verzemi GroupDocs.Viewer a lze jej rozšířit o podporu dalších funkcí Markdownu, jako jsou tučné, kurzívní a tabulky.

Dále prozkoumejte související témata jako **preserve markdown formatting for tables**, **render Markdown to PDF**, nebo **custom styling of imported Markdown elements**. Přizpůsobte příznaky `LoadOptions` tak, aby odpovídaly přesným požadavkům na formátování vaší aplikace, a získáte detailní kontrolu nad každým krokem importu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Ovládněte možnosti načítání Markdownu s Aspose.Words pro Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Ovládněte možnosti načítání Markdownu Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}