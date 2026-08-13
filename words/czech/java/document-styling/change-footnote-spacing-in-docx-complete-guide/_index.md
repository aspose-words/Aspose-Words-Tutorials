---
category: general
date: 2026-07-20
description: Jednoduše změňte rozestupy poznámek pod čarou v souborech DOCX. Naučte
  se nastavit rozestupy, upravit oddělovač poznámek pod čarou a nastavit řádkování
  odstavců pomocí Javy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: cs
lastmod: 2026-07-20
og_description: Rychle změňte rozestupy poznámek pod čarou v souborech DOCX. Tento
  průvodce ukazuje, jak nastavit rozestupy, upravit oddělovač poznámek pod čarou a
  přizpůsobit řádkování odstavců v Javě.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Změna rozestupu poznámek pod čarou v DOCX – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Změna rozestupů poznámek pod čarou v DOCX – Kompletní průvodce
url: /cs/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Změna rozestupů poznámek pod čarou v DOCX – Kompletní průvodce

Už jste někdy potřebovali **změnit rozestupy poznámek pod čarou** v dokumentu Word, ale nevedeli jste, kde začít? Nejste v tom sami. Ať už vylepšujete diplomovou práci nebo upravujete smlouvu, správné nastavení oddělovače poznámek pod čarou může udělat velký rozdíl.  

V tomto tutoriálu vás provedeme **nastavením rozestupů**, úpravou oddělovače poznámek pod čarou a **nastavením řádkování odstavců** pomocí knihoven založených na Javě. Na konci budete mít připravený příklad, který můžete vložit do libovolného projektu.

## Co budete potřebovat

- Java 17 nebo novější (kód používá moderní jazykové funkce)
- Maven nebo Gradle pro správu závislostí
- Soubor DOCX s alespoň jednou poznámkou pod čarou (nebo si ji můžete vytvořit ručně)
- Knihovna **Aspose.Words for Java** (nebo jakékoli kompatibilní API; v příkladu použijeme Aspose)

To je vše—žádné těžkopádné frameworky, jen čistá Java a jedna knihovna.

![Příklad změny rozestupů poznámek pod čarou v DOCX](/images/footnote-spacing.png){alt="Příklad změny rozestupů poznámek pod čarou v DOCX"}

## Krok 1: Načtení DOCX dokumentu (Změna rozestupů poznámek pod čarou)

Prvním krokem je otevřít soubor Word. Tím získáte objekt `Document`, který můžete upravovat.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Proč je to důležité*: Načtení dokumentu je vstupním bodem pro **změnu rozestupů poznámek pod čarou**. Bez instance `Document` nemůžete dosáhnout na oddělovač poznámek pod čarou ani na formáty odstavců.

## Krok 2: Získání a úprava oddělovače poznámek pod čarou (Úprava oddělovače poznámek pod čarou)

Oddělovač poznámek pod čarou je skrytý odstavec, který se nachází mezi hlavním textem a seznamem poznámek pod čarou. Pro změnu jeho řádkování musíte získat tento odstavec a upravit jeho formát.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Jak to řeší problém

- **Získání oddělovače poznámek pod čarou** – to je část, kterou skutečně chcete upravit, splňující požadavek *úprava oddělovače poznámek pod čarou*.
- **Nastavení řádkování** – `setLineSpacing(12.0)` přímo odpovídá na otázku *jak nastavit rozestupy* pro tento skrytý odstavec.
- **Ošetření okrajových případů** – pokud dokument z nějakého důvodu neobsahuje oddělovač, vytvoříme jej za běhu, čímž zabráníme `NullPointerException`.

## Krok 3: Ověření změny a uložení (Nastavení řádkování odstavce)

Po úpravě oddělovače budete chtít ověřit, že změna byla uložena. Otevření uloženého souboru ve Wordu zobrazí nové řádkování, ale můžete to také programově zkontrolovat.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Přidejte volání `verifySpacing(doc);` těsně před `doc.save(...)` v metodě `main`. Když spustíte program, měli byste vidět:

```
Current footnote separator line spacing: 12.0
```

To potvrzuje, že operace **změny řádkování v docx** byla úspěšná.

## Časté úskalí a tipy

- **Úskalí**: Použití `setLineSpacing` s hodnotou, která vypadá jako “12”, ale je interpretována jako “12 pt” versus “12 řádků”. Aspose očekává body, takže 12 znamená 12 pt. Pro dvojité řádkování použijte `24.0`.
- **Tip**: Pokud potřebujete jednotný vzhled napříč všemi typy poznámek pod čarou (oddělovač, oddělovač pokračování atd.), opakujte stejné kroky pro `doc.getFootnoteContinuationSeparator()` a `doc.getFootnoteContinuationNotice()`.
- **Úskalí**: Zapomenutí zavolat `save()` po úpravách. Dokument v paměti se změní, ale soubor na disku zůstane stejný.
- **Tip**: Kombinujte změny rozestupů se změnami stylu (`ParagraphStyle`) pro kompletně vylepšenou sekci poznámek pod čarou.

## Kompletní funkční příklad (Všechny kroky v jednom souboru)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Zkopírujte výše uvedený kód do nové Java třídy, přidejte Maven závislost na Aspose.Words a spusťte jej. Váš `output.docx` bude mít nyní řádkování oddělovače poznámek pod čarou nastavené na **12 pt**, čímž efektivně **změní rozestupy poznámek pod čarou**.

### Maven závislost

Přidejte tento úryvek do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Pokud dáváte přednost Gradlu, ekvivalent je:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Závěr

Právě jste se naučili, jak **změnit rozestupy poznámek pod čarou** v souboru DOCX pomocí Javy. Načtením dokumentu, získáním **oddělovače poznámek pod čarou** a aplikací **nastavení řádkování odstavce**, získáte přesnou kontrolu nad vzhledem poznámek pod čarou.  

Odtud můžete zkoumat související úpravy, jako je změna stylu textu poznámek pod čarou, přidání vlastních oddělovačů nebo dokonce automatizace hromadných aktualizací napříč více dokumenty.  

Máte další otázky ohledně **úpravy oddělovače poznámek pod čarou** nebo jiných úkolů automatizace Wordu? Zanechte komentář a šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Změna asijského řádkování a odsazení odstavců ve Word dokumentu](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Změna asijského řádkování a odsazení odstavců](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Změna asijského řádkování a odsazení odstavců](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}