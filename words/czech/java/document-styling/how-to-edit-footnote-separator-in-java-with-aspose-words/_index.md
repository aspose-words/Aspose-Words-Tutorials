---
category: general
date: 2026-10-04
description: Upravte oddělovač poznámek pod čarou v Javě pomocí Aspose.Words – naučte
  se, jak změnit oddělovač poznámek pod čarou a přidat vlastní slovo oddělovače do
  dokumentů Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: cs
lastmod: 2026-10-04
og_description: Upravte oddělovač poznámky pod čarou v Javě pomocí Aspose.Words. Tento
  tutoriál ukazuje, jak změnit oddělovač poznámky pod čarou a vložit vlastní slovo
  oddělovače.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Upravit oddělovač poznámky pod čarou v Javě – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: Jak upravit oddělovač poznámky pod čarou v Javě s Aspose.Words
url: /cs/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak upravit oddělovač poznámky pod čarou v Javě s Aspose.Words

Pokud potřebujete **edit footnote separator** v dokumentu Word, tento průvodce vám přesně ukáže, jak to provést v Javě. Ať už chcete **change footnote separator** na pomlčku, hvězdičku nebo jakékoli **custom separator word**, níže uvedené kroky pokrývají vše, co potřebujete.

Naučíte se, jak načíst soubor `.docx`, získat speciální sekci oddělovače, upravit její obsah a uložit výsledek. Nepotřebujete žádné externí skripty ani ruční úpravy – vše je provedeno programově pomocí knihovny Aspose.Words for Java.

## Požadavky

- Nainstalovaný Java 17 nebo novější.
- Maven nebo Gradle pro správu závislostí (příklad používá Maven).
- Platná licence Aspose.Words for Java (nebo bezplatný evaluační klíč).
- Dokument Word, který již obsahuje poznámky pod čarou (oddělovač existuje pouze, pokud jsou poznámky pod čarou přítomny).

## Přidejte Aspose.Words do svého projektu

Pokud používáte Maven, přidejte následující závislost do souboru `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Pro Gradle přidejte:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Krok 1: Načtěte dokument, který obsahuje poznámky pod čarou

Prvním krokem je otevřít soubor Word, který chcete upravit. Aspose.Words načte soubor do objektu `Document`, který vám poskytuje plný přístup ke všem částem dokumentu, včetně oddělovačů poznámek pod čarou.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**Proč je to důležité:** Načtení dokumentu vytvoří reprezentaci v paměti, takže můžete bezpečně upravovat libovolný uzel, aniž byste se dotkli původního souboru, dokud jej výslovně neuložíte.

## Krok 2: Získejte sekci oddělovače poznámek pod čarou

Word ukládá oddělovač poznámek pod čarou jako speciální uzel `Separator`. Aspose.Words poskytuje metodu `getFootnoteSeparator()`, která jej získá přímo.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Tip:** Uzol oddělovače existuje pouze, pokud dokument již obsahuje alespoň jednu poznámku pod čarou. Pokud se pokusíte upravit dokument bez poznámek pod čarou, `getFootnoteSeparator()` vrátí `null`, takže vždy tuto podmínku kontrolujte.

## Krok 3: Vložte vlastní slovo oddělovače

Nyní můžete změnit vzhled oddělovače. V tomto příkladu nahrazujeme výchozí čáru em‑pomlčkou (`—`). Místo toho můžete vložit libovolné **custom separator word**, například `"NOTE:"` nebo `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### Co kód dělá

1. **`clearChildren()`** odstraňuje všechny existující běhy (runs), čímž zajišťuje, že oddělovač obsahuje pouze text, který poskytnete.
2. **`new Run(document, "—")`** vytvoří textový uzel s požadovaným oddělovačem. Objekt `Run` respektuje styl dokumentu, takže oddělovač dědí formátování původního oddělovače poznámek pod čarou.
3. **`appendChild(customRun)`** vloží nový běh do odstavce oddělovače.

Můžete také aplikovat formátování na běh, například:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Krok 4: Uložte upravený dokument

Po úpravě oddělovače zapište dokument zpět na disk. Zvolte nový název souboru, aby originální soubor zůstal nedotčený.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**Ověření výsledku:** Otevřete `ModifiedNotes.docx` v Microsoft Word. Oddělovač poznámek pod čarou by nyní měl zobrazovat vlastní pomlčku (nebo jakékoli slovo, které jste zvolili) místo výchozí čáry.

## Zpracování více oddělovačů poznámek pod čarou

Word podporuje tři speciální typy oddělovačů:

| Typ oddělovače | Metoda |
|----------------|----------------------------|
| Footnote separator | `getFootnoteSeparator()` |
| Footnote continuation separator | `getFootnoteContinuationSeparator()` |
| Footnote separator for the first page | `getFootnoteSeparatorForFirstPage()` |

Pokud potřebujete upravit všechny, opakujte **Krok 2** a **Krok 3** pro každou metodu. Příklad:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Časté úskalí a jak se jim vyhnout

| Problém | Příčina | Řešení |
|-------|-------|-----|
| Po uložení se nezobrazí žádný oddělovač | Dokument neobsahoval poznámky pod čarou → uzel oddělovače je `null` | Přidejte alespoň jednu poznámku pod čarou před úpravou, nebo vytvořte programově fiktivní poznámku. |
| Oddělovač zobrazuje nadbytečné mezery | Existující běhy (runs) nebyly vymazány | Zavolejte `clearChildren()` před přidáním nového běhu. |
| Formátování vypadá odlišně | Běh dědí styl z původního oddělovače | Explicitně nastavte vlastnosti písma na objektu `Run`, pokud potřebujete konkrétní vzhled. |

## Kompletní funkční příklad

Spojením všech částí dohromady získáte samostatnou třídu Java, kterou můžete zkopírovat, zkompilovat a spustit:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

Spusťte program a poté otevřete `ModifiedNotes.docx`, abyste potvrdili, že oddělovač byl aktualizován.

## Závěr

Nyní víte, jak **edit footnote separator** v dokumentu Word pomocí Javy a Aspose.Words. Tutoriál pokryl načtení dokumentu, získání speciálního uzlu oddělovače, vložení **custom separator word** a uložení výsledku. Dodržením těchto kroků můžete také **change footnote separator** pro sekce pokračování nebo poznámky pod čarou na první stránce.

Dále můžete zkoumat:

- Přidání různých oddělovačů pro poznámky pod čarou na první stránce (`getFootnoteSeparatorForFirstPage()`).
- Programové vytváření poznámek pod čarou, pokud neexistují.
- Použití Aspose.Words k formátování textu poznámek pod čarou (písma, barvy, odsazení).

Klidně experimentujte s dalšími znaky nebo slovy, aby odpovídaly brandingu vašeho dokumentu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}