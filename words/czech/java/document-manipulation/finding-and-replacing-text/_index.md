---
date: 2026-01-03
description: Naučte se, jak nahradit text HTML ve Word dokumentech pomocí Aspose.Words
  pro Java. Krok za krokem průvodce s ukázkami kódu, tipy na regex nahrazování textu
  v Javě a další.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: nahraďte text HTML pomocí Aspose.Words pro Java
url: /cs/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nahrazení textu HTML v Aspose.Words pro Java

## Úvod do vyhledávání a nahrazování textu v Aspose.Words pro Java

Aspose.Words pro Java je výkonné Java API, které vám umožňuje programově manipulovat s dokumenty Word. Jedním z nejčastějších úkolů je **replace text with html**, ať už aktualizujete zástupné symboly v šabloně, vkládáte stylovaný obsah nebo provádíte hromadné transformace textu. V tomto průvodci si ukážeme, jak nahrazovat text, jak používat regex replace text java a dokonce jak nahrazovat text v záhlavích – vše při zachování čistého a efektivního kódu.

## Rychlé odpovědi
- **Jaká je hlavní metoda pro replace text with html?** Použijte `FindReplaceOptions` s vlastním callbackem, například `ReplaceWithHtmlEvaluator`.  
- **Mohu při nahrazování ignorovat pole?** Ano – nastavte `options.setIgnoreFields(true)`.  
- **Potřebuji licenci pro produkční použití?** Platná licence Aspose.Words je vyžadována pro komerční nasazení.  
- **Jaká verze Javy je podporována?** Aspose.Words pro Java funguje s Java 8 a vyšší.  
- **Je regex replace text java podporováno?** Rozhodně – předávejte objekt `Pattern` metodě `replace`.  

## Co je “replace text with html”?

Nahrazení textu HTML znamená výměnu prostého textového zástupného symbolu za bohatý HTML markup (tabulky, seznamy, stylování) při zachování struktury okolního dokumentu Word. Aspose.Words parsuje HTML a vloží odpovídající objekty Word, čímž vám poskytuje plnou kontrolu nad finálním rozvržením.

## Proč použít Aspose.Words pro tento úkol?

- **Full Word fidelity** – knihovna zachovává veškeré formátování, záhlaví, zápatí a sledované změny nedotčené.  
- **Built‑in regex support** – ideální pro složité vyhledávací vzory (`regex replace text java`).  
- **Fine‑grained control** – možnosti jako `IgnoreFields`, `IgnoreDeleted` a `UseLegacyOrder` vám umožní přizpůsobit operaci přesně podle vašich potřeb.  
- **Cross‑platform** – funguje na jakémkoli OS, který podporuje Javu.

## Požadavky

- Java vývojové prostředí (JDK 8+)  
- Aspose.Words pro Java knihovna – stáhněte ji z [here](https://releases.aspose.com/words/java/).  
- Ukázkový Word dokument (`.docx`) pro experimentování.

## Finding and Replacing Simple Text

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Tento základní příklad ukazuje **how to replace text** pomocí metody `replace`. Je to základ pro pokročilejší scénáře.

## Using Regular Expressions (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Regulární výrazy vám poskytují výkonné vyhledávání vzorů, ideální pro dynamické zástupné symboly nebo složité hranice slov.

## Ignoring Text Inside Fields (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Nastavte `IgnoreFields`, aby zůstaly slučovací pole, čísla stránek nebo jiné kódy polí nedotčeny, zatímco nahrazujete okolní obsah.

## Ignoring Text Inside Delete Revisions

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Toto zabraňuje změně textu označeného ke smazání (sledované změny).

## Ignoring Text Inside Insert Revisions

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Užitečné, když chcete během hromadného nahrazování zachovat nově vložený text nedotčený.

## Replacing Text with HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Zde **replace text with html** pomocí vlastního evaluátoru, který parsuje řetězec HTML a vloží odpovídající uzly Word.

## Replacing Text in Headers and Footers (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Cílené nahrazení v záhlavích nebo zápatích zajišťuje, že značka dokumentu zůstane konzistentní.

## Showing Changes for Header and Footer Orders

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Tento příklad zaznamenává změny, pomáhá vám auditovat úpravy pořadí záhlaví/zápatí.

## Replacing Text with Fields

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Vkládání polí (např. slučovacích polí) vám umožní vytvořit dynamické dokumenty, které lze později naplnit.

## Replacing with an Evaluator

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Vlastní evaluátory vám poskytují plnou programovou kontrolu nad nahrazovaným textem.

## Replacing with Regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Stručný způsob, jak provádět nahrazování založené na vzoru v celém dokumentu.

## Recognizing and Substitutions Within Replacement Patterns

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Povolte `UseSubstitutions`, abyste mohli odkazovat na zachycené skupiny přímo v řetězci nahrazení.

## Replacing with a String (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Nejjednodušší forma nahrazení – ideální pro statické zástupné symboly.

## Using Legacy Order

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Legacy order může být nutný při práci se staršími dokumenty, které spoléhají na původní sekvenci procházení.

## Replacing Text in a Table

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Cílené nahrazování v tabulkách zabraňuje nechtěným změnám jinde v dokumentu.

## Časté problémy a řešení
- **HTML not rendering correctly** – Ujistěte se, že vaše HTML je dobře formátováno a obsahuje požadované značky (např. `<p>`, `<table>`).  
- **Regex not matching** – Pamatujte, že je třeba escapovat speciální znaky a použít `Pattern.CASE_INSENSITIVE`, pokud je to potřeba.  
- **Fields being replaced unintentionally** – Nastavte `options.setIgnoreFields(true)`, abyste je chránili.  
- **Performance on large documents** – Použijte `UseLegacyOrder` nebo zpracovávejte sekce jednotlivě, aby se snížila paměťová náročnost.

## Často kladené otázky

**Q: Jak si mohu stáhnout Aspose.Words pro Java?**  
A: Můžete si stáhnout Aspose.Words pro Java z webových stránek návštěvou [this link](https://releases.aspose.com/words/java/).

**Q: Mohu použít regulární výrazy pro nahrazování textu?**  
A: Ano, můžete v Aspose.Words pro Java použít regulární výrazy pro nahrazování textu. To vám umožní provádět pokročilejší a flexibilnější operace vyhledávání a nahrazování.

**Q: Jak mohu během nahrazování ignorovat text uvnitř polí?**  
A: Nastavte vlastnost `IgnoreFields` objektu `FindReplaceOptions` na `true`. Tím vyloučíte obsah polí, jako jsou slučovací pole, z nahrazování.

**Q: Je možné nahrazovat text v záhlavích a zápatích?**  
A: Rozhodně. Přistupte k požadovanému záhlaví nebo zápatí pomocí `HeaderFooterCollection` a použijte metodu `replace` s vhodnými možnostmi.

**Q: Co dělá volba `UseLegacyOrder`?**  
A: `UseLegacyOrder` nutí vyhledávací/nahrazovací engine procházet uzly v původním pořadí používaném staršími verzemi Aspose.Words, což může být užitečné pro kompatibilitu se staršími dokumenty.

---

**Poslední aktualizace:** 2026-01-03  
**Testováno s:** Aspose.Words pro Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}