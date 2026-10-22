---
category: general
date: 2026-09-11
description: Naučte se, jak změnit formátování poznámek pod čarou v Javě pomocí Aspose.Words.
  Tento průvodce vysvětluje, jak upravit poznámku pod čarou, aktualizovat styl poznámky
  pod čarou a upravit oddělovač poznámek pod čarou.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: cs
lastmod: 2026-09-11
og_description: Změňte formátování poznámek pod čarou v Javě pomocí Aspose.Words.
  Postupujte podle tohoto kompletního průvodce a upravte poznámku pod čarou, aktualizujte
  její styl a změňte oddělovač poznámek pod čarou.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Změna formátování poznámek pod čarou v Javě – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Jak změnit formátování poznámek pod čarou v dokumentu Word pomocí Javy
url: /cs/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak změnit formátování poznámky pod čarou v dokumentu Word pomocí Javy

Pokud potřebujete **změnit formátování poznámky pod čarou** v dokumentu Word, tento tutoriál vás provede přesné kroky pomocí Aspose.Words for Java. Ať už budujete publikační pipeline nebo jen potřebujete **jak upravit vzhled poznámky pod čarou** programově, níže uvedené řešení pokrývá vše od načtení souboru až po uložení aktualizované verze.

Naučíte se, jak **aktualizovat styl poznámky pod čarou**, udělat oddělovač poznámek pod čarou tučným a dokonce **upravit vlastnosti oddělovače poznámky pod čarou**, jako je velikost písma nebo barva. Průvodce předpokládá, že máte základní znalosti Javy a funkční licenci Aspose.Words for Java.

## Požadavky

* Nainstalovaná Java 17 nebo novější.
* Aspose.Words for Java (verze 23.12 nebo novější) přidaná do classpath vašeho projektu.
* Dokument Word (`input.docx`) obsahující alespoň jednu poznámku pod čarou.
* IDE nebo nástroj pro sestavení (Maven/Gradle) pro kompilaci a spuštění kódu.

Pokud si nejste jisti, jak přidat Aspose.Words do Maven projektu, zahrňte následující závislost do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Změna formátování poznámky pod čarou pomocí Aspose.Words for Java

Jádrem řešení je krátký program v Javě, který načte dokument, získá odstavec oddělovače poznámky pod čarou, změní jeho formátování a uloží výsledek. Kód je zcela samostatný, takže jej můžete zkopírovat do nové třídy a okamžitě spustit.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Proč je každý krok důležitý

* **Načtení dokumentu** (`new Document`) vytvoří v‑paměti reprezentaci, kterou může Aspose.Words manipulovat.  
* **Získání oddělovače poznámky pod čarou** (`getFootnoteSeparator`) vám poskytne přímý přístup k odstavci, který odděluje poznámky pod čarou od hlavního textu. Toto je prvek, který musíte cílit, když chcete **změnit formátování poznámky pod čarou**.  
* **Formátování běhu** (`setBold`, `setItalic`, `setSize`, `setColor`) ukazuje, jak **upravit vlastnosti oddělovače poznámky pod čarou**. Můžete zde přidat další atributy písma, jako podtržení nebo zvýraznění, abyste plně kontrolovali vzhled.  
* **Uložení dokumentu** zapíše změny zpět na disk a vytvoří nový soubor (`output.docx`), který odráží aktualizovaný styl poznámky pod čarou.

> **Tip:** Pokud váš zdrojový dokument používá vlastní oddělovač poznámky pod čarou, který obsahuje více běhů (např. kombinaci symbolů), projděte smyčkou `footnoteSeparator.getRuns()` a aplikujte stejná nastavení `Font` na každý běh pro konzistentní styl.

## Jak programově upravit oddělovač poznámky pod čarou

Někdy může být potřeba upravit nejen oddělovač, ale také samotný text poznámky pod čarou. Stejná API může být použita k přístupu ke každé poznámce, úpravě formátování odstavce nebo změně stylu číslování.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

Ukázkový kód výše ukazuje **jak upravit těla poznámek pod čarou** poté, co jste již **změnili formátování poznámky pod čarou** pro oddělovač. Iterací přes `doc.getFootnotes()` zajistíte, že každá poznámka pod čarou zdědí stejný styl, což je nezbytné pro profesionálně vypadající dokument.

## Aktualizace stylu poznámky pod čarou pro konzistentní vzhled dokumentu

Pokud dáváte přednost práci se styly místo jednotlivých běhů, Aspose.Words vám umožní vytvořit nebo upravit objekt `Style` a poté jej použít na poznámky pod čarou a oddělovač. Tento přístup je užitečný, když potřebujete **aktualizovat styl poznámky pod čarou** napříč mnoha dokumenty.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Použití dedikovaného stylu usnadňuje budoucí údržbu – změňte styl jednou a každá poznámka pod čarou i oddělovač se automaticky aktualizují. Tato technika je doporučený způsob, jak **aktualizovat styl poznámky pod čarou** ve velkorozsáhlých publikačních pracovních postupech.

## Úprava oddělovače poznámky pod čarou podle vaší značky

Pokyny značky někdy vyžadují, aby oddělovač poznámky pod čarou používal konkrétní znak (např. hvězdičku) nebo vlastní čáru. Aspose.Words vám umožní zcela nahradit výchozí obsah oddělovače.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

Výše uvedený kód **upravit oddělovač poznámky pod čarou** vymazáním všech existujících běhů a vložením nového běhu s požadovaným textem a formátováním. Můžete také použít Unicode znaky jako `\u2022` (bullet) nebo `\u2014` (em dash) k dosažení přesného vizuálního efektu požadovaného vaší značkou.

## Očekávaný výsledek

Po spuštění programu:

* Oddělovač poznámky pod čarou v `output.docx` se zobrazí **tučně**, **kurzívou**, 10 pt a šedě (nebo jakoukoliv barvou, kterou nastavíte).  
* Všechny odstavce poznámek pod čarou přebírají styl, který jste definovali, což zajišťuje jednotný vzhled v celém dokumentu.  
* Pokud jste nahradili text oddělovače, nová vlastní čára je viditelná přesně tam, kde byla původní čára.

Otevřete výsledný soubor v Microsoft Word nebo LibreOffice Writer a ověřte změny. Měli byste vidět aktualizovaný oddělovač těsně nad první poznámkou pod čarou a text poznámky pod čarou by měl odrážet všechny provedené úpravy stylu.

## Časté problémy a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` vyvolá výjimku | Některé dokumenty mají prázdný odstavec oddělovače. | Přidejte obrannou kontrolu a vytvořte běh, pokud neexistuje (viz ukázkový kód). |
| Změny písma nejsou viditelné | Dokument používá téma, které přepisuje přímé formátování. | Nastavte `font.setThemeFont(null)` nebo použijte vlastní styl místo přímého formátování. |
| Uložený soubor neodráží změny | Původní soubor je stále otevřený ve Wordu, což blokuje výstupní cestu. | Zavřete všechny instance souboru před spuštěním programu, nebo

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Zpracování slov s poznámkami pod čarou a koncovými poznámkami](/words/english/net/working-with-footnote-and-endnote/)
- [Nastavení pozice poznámky pod čarou a koncové poznámky](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Jak zobrazit informace o verzi Aspose.Words v Javě: komplexní průvodce](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}