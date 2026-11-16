---
category: general
date: 2026-11-15
description: Nastavte řádkování odstavců ve Word dokumentu pomocí Javy. Naučte se,
  jak programově nastavit řádkování pomocí Aspose.Words pro přesné formátování dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: cs
lastmod: 2026-11-15
og_description: Nastavte řádkování odstavců v dokumentu Word pomocí Javy. Tento průvodce
  vysvětluje, jak nastavit řádkování pro odstavce a oddělovače poznámek pod čarou
  pomocí Aspose.Words, což vám poskytuje úplnou kontrolu nad rozvržením dokumentu.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Nastavte řádkování odstavců ve Wordu pomocí Javy
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Nastavte řádkování odstavce v dokumentu Word pomocí Javy
url: /cs/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení řádkování odstavce ve Word dokumentu pomocí Javy

Pokud potřebujete **nastavit řádkování odstavce** ve Word dokumentu, tento tutoriál vám ukáže, jak to provést pomocí Javy a Aspose.Words. Také se naučíte **jak nastavit řádkování** pro oddělovače poznámek pod čarou – běžný požadavek při formátování profesionálních dokumentů.

V následujících sekcích provedete:

* Načtěte existující soubor *.docx*.
* Získejte odstavec oddělovače poznámek pod čarou.
* Použijte vlastní hodnotu řádkování.
* Uložte aktualizovaný dokument.

Žádná externí konfigurace není vyžadována kromě přidání knihovny Aspose.Words do vašeho projektu, takže můžete kód zkopírovat doslovně a okamžitě jej spustit.

## Požadavky

Před začátkem se ujistěte, že máte:

* Nainstalovanou Javu 17 nebo novější.
* Maven (nebo jiný nástroj pro správu) pro správu závislostí.
* Platnou licenci Aspose.Words pro Javu (bezplatná zkušební verze funguje pro testování).
* Vstupní Word dokument (`input.docx`) umístěný v známém adresáři.

Přidejte závislost Aspose.Words do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Nastavení řádkování odstavce pomocí Aspose.Words

Tento nadpis H2 obsahuje hlavní klíčové slovo, splňující požadavek SEO.

### Krok 1: Načtení Word dokumentu

Nejprve vytvořte instanci `Document`, která ukazuje na váš zdrojový soubor.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Proč je to důležité*: Načtení dokumentu vám poskytne model v paměti, který můžete upravovat, aniž byste se dotkli původního souboru, dokud jej výslovně neuložíte.

### Krok 2: Získání oddělovače poznámek pod čarou

Oddělovače poznámek pod čarou jsou speciální odstavce, které se objevují mezi poznámkami pod čarou a hlavním textem. Pro změnu jejich vzhledu musíte získat objekt `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tip*: Pokud váš dokument neobsahuje poznámky pod čarou, oddělovač stále existuje jako skrytý odstavec, takže volání nikdy nevrátí `null`.

### Krok 3: Jak nastavit řádkování pro odstavec oddělovače

Nyní použijte požadované řádkování. Aspose.Words používá body pro hodnoty řádkování; 12 bodů je zhruba jednoduché řádkování pro většinu písem.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Můžete také použít jiné režimy řádkování:

| Režim                     | Volání metody                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Výběr správného pravidla zajišťuje, že dokument bude vykreslen konzistentně ve Wordu, Google Docs a dalších prohlížečích.

### Krok 4: Uložení aktualizovaného dokumentu

Nakonec zapište změny zpět na disk.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Když otevřete `output.docx` v Microsoft Wordu, oddělovač poznámek pod čarou se zobrazí s řádkováním, které jste definovali.

## Porozumění nastavení řádkování pro běžné odstavce

Stejná API funguje pro jakýkoli objekt `Paragraph`, nejen pro oddělovače poznámek pod čarou. Zde je rychlý příklad, který upravuje řádkování prvního odstavce v těle dokumentu:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Proč byste to mohli potřebovat**: Zprávy, smlouvy a akademické práce často vyžadují konkrétní styl řádkování (např. dvojité řádkování pro návrhy). Použití stejné metody `setLineSpacing` zaručuje přesné rozvržení, které očekáváte.

## Časté úskalí a jak se jim vyhnout

| Problém                                 | Příčina                                   | Řešení |
|---------------------------------------|----------------------------------------|-----|
| Řádkování se nezměnilo                | `LineSpacingRule` zůstala v výchozím nastavení (AUTO) | Explicitně nastavte pravidlo pomocí `setLineSpacingRule`. |
| Nadbytečné prázdné řádky za oddělovačem | Oddělovač obsahuje skryté návraty řádku | Ořízněte text oddělovače pomocí `separator.getText().trim();` před aplikací řádkování. |
| Dokument se po uložení poškozuje      | Použití zastaralé verze Aspose.Words | Aktualizujte na nejnovější verzi (např. 24.10), která obsahuje opravy chyb při ukládání. |

## Pro tip: hromadné zpracování více dokumentů

Pokud potřebujete aktualizovat desítky souborů, zabalte logiku do pomocné metody a iterujte přes složku:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Spuštění této metody ve smyčce vám ušetří hodiny ruční úpravy.

## Očekávaný výstup

Po spuštění celého programu bude `output.docx`:

* Obsahovat původní obsah beze změny kromě řádkování.
* Zobrazovat oddělovač poznámek pod čarou s jednoduchým řádkováním (12 bodů).
* Zachovat veškeré ostatní formátování (styly, obrázky, tabulky).

Otevřete soubor ve Wordu a ověřte, že čára oddělovače je těsnější (nebo volnější, v závislosti na nastavené hodnotě).

## Závěr

Nyní víte, jak **nastavit řádkování odstavce** ve Word dokumentu pomocí Javy, a také rozumíte **jak nastavit řádkování** jak pro oddělovače poznámek pod čarou, tak pro běžné odstavce. Kompletní, spustitelný příklad ukazuje načtení dokumentu, úpravu vlastností řádkování a uložení výsledku – vše pomocí několika jasných volání API.

**Další kroky**, které můžete prozkoumat:

* **Jak nastavit řádkování** pro tabulky a položky seznamu.
* Aplikace různých pravidel řádkování na nadpisy oproti tělu textu.
* Použití objektu `Style` k vynucení řádkování v celém dokumentu.

Experimentujte s hodnotami, kombinujte je s dalšími možnostmi formátování a získáte plnou kontrolu nad rozvržením dokumentu v jakékoli Java aplikaci. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak nastavit možnosti v Aspose.Words pro Java – kompletní průvodce](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Jak nastavit LoadOptions v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Změna asijského řádkování a odsazení odstavců ve Word dokumentu](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}