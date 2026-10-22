---
category: general
date: 2026-08-07
description: Jak upravit poznámku pod čarou v Javě pomocí Aspose.Words – přidat vlastní
  pomlčku, změnit čáru poznámky pod čarou a nastavit zarovnání odstavce pro vylepšené
  dokumenty.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: cs
lastmod: 2026-08-07
og_description: Jak upravit poznámku pod čarou v Javě s Aspose.Words. Naučte se přidat
  vlastní pomlčku, změnit čáru poznámky pod čarou a nastavit zarovnání odstavce během
  několika kroků.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Jak upravit poznámku pod čarou v Javě – přidat pomlčku, změnit řádek, nastavit
  zarovnání
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Jak upravit poznámku pod čarou v Javě pomocí Aspose.Words
url: /cs/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak upravit poznámku pod čarou v Javě s Aspose.Words

Pokud potřebujete **jak upravit poznámku pod čarou** v dokumentu Word pomocí Javy, tento průvodce ukazuje kompletní postup. Naučíte se přidat vlastní pomlčku, změnit řádek poznámky pod čarou a nastavit zarovnání odstavce, aby oddělovač poznámky pod čarou vypadal profesionálně.

Úprava poznámek pod čarou je běžnou požadavkem při přípravě právních smluv, akademických prací nebo marketingových brožur. Níže uvedené kroky pokrývají vše, co potřebujete – od načtení dokumentu po uložení finálního souboru – bez nutnosti dalších nástrojů.

## Požadavky

Než začnete, ujistěte se, že máte:

* Java 17 nebo novější nainstalovanou.
* Aspose.Words for Java (nejnovější verze) přidanou do classpath vašeho projektu.
* Soubor DOCX (`input.docx`), který obsahuje alespoň jednu poznámku pod čarou.

Tyto položky zajišťují, že kód poběží bez runtime chyb.

## Jak upravit oddělovač a řádek poznámky pod čarou

Oddělovač poznámky pod čarou je odstavec, který se objeví mezi hlavním textem a seznamem poznámek pod čarou. Změna jeho vzhledu zlepšuje čitelnost a odpovídá firemnímu brandingu.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Proč je každý řádek důležitý

1. **Načtení dokumentu** – `new Document(...)` načte soubor DOCX do paměti a poskytne vám přístup ke všem jeho uzlům.
2. **Získání oddělovače** – `getFootnoteSeparator()` vrací speciální odstavec, který Aspose.Words považuje za řádek poznámky pod čarou. Tento objekt je jediným místem, kde můžete oddělovač bezpečně upravit.
3. **Nastavení zarovnání odstavce** – `setAlignment(ParagraphAlignment.CENTER)` mění zarovnání řádku. Klíčové slovo *set paragraph alignment* se aplikuje přímo na oddělovač, čímž zajistí centrovanou pomlčku.
4. **Přidání vlastní pomlčky** – Vymazáním existujících běhů a přidáním nového `Run` s em‑dash znakem (`—`) dosáhnete efektu *add custom dash* a zároveň *change footnote line* na požadovaný styl.
5. **Uložení dokumentu** – `doc.save(...)` zapíše změny zpět na disk a vytvoří výstupní soubor, který odráží všechny úpravy.

## Přidat vlastní pomlčku do oddělovače poznámky pod čarou

Kód v **kroku 4** demonstruje techniku *add custom dash*. Můžete nahradit em‑dash libovolným řetězcem, například `"***"` nebo `"---"`, aby odpovídal vizuálnímu stylu vašeho dokumentu.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Použití vlastní pomlčky je zvláště užitečné, když výchozí tenká čára nesplňuje brandové směrnice.

## Změnit styl řádku poznámky pod čarou

Pokud dáváte přednost plné čáře místo pomlčky, můžete vložit Unicode znak pro kreslení rámečků nebo opakovaný podtržítko.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

Krok *change footnote line* funguje stejným způsobem bez ohledu na zvolený znak, protože odstavec oddělovače pouze vykresluje text, který obsahuje.

## Nastavit zarovnání odstavce pro oddělovač poznámky pod čarou

Operace *set paragraph alignment* není omezena jen na centrované zarovnání. Můžete zarovnat doleva, doprava nebo do bloku podle potřeb vašeho rozvržení.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Zarovnání oddělovače doprava může být užitečné pro dokumenty, které používají pravostranné poznámky pod čarou, například dvojjazyčné publikace.

## Kompletní, spustitelný příklad

Níže je kompletní program, který zahrnuje všechny koncepty – načtení dokumentu, úpravu oddělovače poznámky pod čarou, přidání vlastní pomlčky, změnu stylu řádku a nastavení zarovnání.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Očekávaný výstup:** Soubor `output.docx` obsahuje centrovaný em‑dash tam, kde dříve byla tenká čára. Všechny poznámky pod čarou zůstávají nedotčeny a rozvržení dokumentu odráží nový styl oddělovače.

## Časté úskalí a jak se jim vyhnout

| Problém | Důvod | Řešení |
|-------|--------|-----|
| Oddělovač nenalezen | Dokument neobsahuje žádné poznámky pod čarou nebo používá vlastní styl poznámky pod čarou | Ujistěte se, že zdrojový DOCX obsahuje alespoň jednu poznámku pod čarou před voláním `getFootnoteSeparator()` |
| Vlastní pomlčka není viditelná | Písmo nepodporuje zvolený znak | Použijte Unicode znak, který je podporován výchozím písmem dokumentu, nebo vložte kompatibilní písmo |
| Zarovnání se nezdá změněno | Formát odstavce je později v kódu přepsán | Aplikujte zarovnání **po** všech ostatních voláních formátování, která by ho mohla resetovat |

Řešením těchto bodů se předejde runtime chybám a zaručí se spolehlivý proces *how to edit footnote*.

## Další kroky

Nyní, když znáte **jak upravit poznámku pod čarou**, můžete prozkoumat související úkoly:

* **Přidat vlastní styl odkazu na poznámku pod čarou** – upravte uzly `FootnoteReference` pro změnu číslování nebo symbolů.
* **Programově vložit nové poznámky pod čarou** – použijte `DocumentBuilder.insertFootnote()` pro dynamický obsah.
* **Použít podmíněné formátování** – změňte vzhled poznámky pod čarou na základě stylu odstavce nebo délky obsahu.

Každé z těchto rozšíření staví na stejné API vrstvě, kterou jste použili pro *add custom dash*, *change footnote line* a *set paragraph alignment*.

---

*Šťastné programování! Pokud vám tutoriál pomohl zvládnout úpravu poznámek pod čarou, zvažte jeho sdílení s týmem nebo přispění pull requestem pro další vylepšení příkladu.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Nastavit pozici poznámky pod čarou a koncové poznámky](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak nastavit LoadOptions v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}