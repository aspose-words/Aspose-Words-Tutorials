---
title: Hledání a nahrazování textu v Aspose.Words pro Javu
linktitle: Hledání a nahrazování textu
second_title: Aspose.Words Java Document Processing API
description: Naučte se najít a nahradit text v dokumentech aplikace Word pomocí Aspose.Words for Java. Podrobný průvodce s příklady kódu. Vylepšete své dovednosti manipulace s dokumenty Java.
weight: 15
url: /cs/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hledání a nahrazování textu v Aspose.Words pro Javu


## Úvod do hledání a nahrazování textu v Aspose.Words pro Javu

Aspose.Words for Java je výkonné Java API, které vám umožňuje pracovat s dokumenty Wordu programově. Jedním z běžných úkolů při práci s dokumenty aplikace Word je hledání a nahrazování textu. Ať už potřebujete aktualizovat zástupné symboly v šablonách nebo provádět složitější textové manipulace, Aspose.Words pro Java vám může pomoci dosáhnout vašich cílů efektivně.

## Předpoklady

Než se ponoříme do podrobností o hledání a nahrazování textu, ujistěte se, že máte splněny následující předpoklady:

- Vývojové prostředí Java
- Aspose.Words pro knihovnu Java
- Ukázkový dokument aplikace Word pro práci

 Knihovnu Aspose.Words for Java si můžete stáhnout z[zde](https://releases.aspose.com/words/java/).

## Vyhledání a nahrazení jednoduchého textu

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Najít a nahradit text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Uložte upravený dokument
doc.save("modified-document.docx");
```

 V tomto příkladu načteme dokument aplikace Word, vytvoříme a`DocumentBuilder` a použijte`replace` metoda k nalezení a nahrazení "starého textu" za "nový-text" v dokumentu.

## Použití regulárních výrazů

Regulární výrazy poskytují výkonné možnosti porovnávání vzorů pro vyhledávání a nahrazování textu. Aspose.Words for Java podporuje regulární výrazy pro pokročilejší operace hledání a nahrazování.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Používejte regulární výrazy pro hledání a nahrazování textu
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Uložte upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme vzor regulárního výrazu k vyhledání a nahrazení textu v dokumentu.

## Ignorování textu uvnitř polí

Aspose.Words můžete nakonfigurovat tak, aby při provádění operací hledání a nahrazování ignoroval text uvnitř polí.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte IgnoreFields na hodnotu true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Při nahrazování textu použijte možnosti
doc.getRange().replace("text-to-replace", "new-text", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To je užitečné, když chcete vyloučit text uvnitř polí, jako jsou slučovací pole, z nahrazení.

## Ignorování textu uvnitř Odstranit revize

Aspose.Words můžete nakonfigurovat tak, aby ignoroval text uvnitř odstraněných revizí během operací hledání a nahrazení.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte IgnoreDeleted na true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Při nahrazování textu použijte možnosti
doc.getRange().replace("text-to-replace", "new-text", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To vám umožní vyloučit nahrazení textu, který byl označen ke smazání ve sledovaných změnách.

## Ignorování textu uvnitř revizí vložení

Aspose.Words můžete nakonfigurovat tak, aby ignoroval text uvnitř revizí vkládání během operací hledání a nahrazování.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte IgnoreInserted na hodnotu true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Při nahrazování textu použijte možnosti
doc.getRange().replace("text-to-replace", "new-text", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To vám umožní vyloučit nahrazení textu, který byl označen jako vložený do sledovaných změn.

## Nahrazení textu HTML

K nahrazení textu obsahem HTML můžete použít Aspose.Words for Java.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions s vlastním nahrazením zpětného volání
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Při nahrazování textu použijte možnosti
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

 V tomto příkladu používáme vlastní`ReplaceWithHtmlEvaluator` k nahrazení textu obsahem HTML.

## Nahrazení textu v záhlaví a zápatí

Můžete najít a nahradit text v záhlaví a zápatí dokumentu aplikace Word.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Získejte sbírku záhlaví a zápatí
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Vyberte typ záhlaví nebo zápatí, ve kterém chcete nahradit text (např. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Vytvořte instanci FindReplaceOptions a použijte ji na rozsah zápatí
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To umožňuje provádět nahrazování textu konkrétně v záhlaví a zápatí.

## Zobrazení změn pro objednávky záhlaví a zápatí

Pomocí Aspose.Words můžete zobrazit změny v pořadí záhlaví a zápatí v dokumentu.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Získejte první sekci
Section firstPageSection = doc.getFirstSection();

//Vytvořte instanci FindReplaceOptions a použijte ji na rozsah dokumentu
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Nahraďte text, který ovlivňuje pořadí záhlaví a zápatí
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To vám umožní vizualizovat změny související s pořadím záhlaví a zápatí v dokumentu.

## Nahrazení textu poli

Text můžete nahradit poli pomocí Aspose.Words for Java.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte vlastní zpětné volání nahrazující pole
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Při nahrazování textu použijte možnosti
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

 V tomto příkladu nahradíme text poli a určíme typ pole (např.`FieldType.FIELD_MERGE_FIELD`).

## Nahrazení hodnotitelem

K dynamickému určení náhradního textu můžete použít vlastní vyhodnocovací nástroj.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte vlastní nahrazující zpětné volání
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Při nahrazování textu použijte možnosti
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme vlastní hodnotitel (`MyReplaceEvaluator`) k nahrazení textu.

## Nahrazení za Regex

Aspose.Words for Java umožňuje nahradit text pomocí regulárních výrazů.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Používejte regulární výrazy pro hledání a nahrazování textu
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Uložte upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme vzor regulárního výrazu k vyhledání a nahrazení textu v dokumentu.

## Rozpoznávání a substituce v rámci náhradních vzorů

Pomocí Aspose.Words for Java můžete rozpoznat a provést substituce v rámci nahrazovacích vzorů.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions s UseSubstitutions nastavenou na hodnotu true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Při nahrazování textu vzorem použijte volby
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To vám umožňuje provádět substituce v rámci vzorů náhrad za pokročilejší náhrady.

## Nahrazení řetězcem

Pomocí Aspose.Words for Java můžete nahradit text jednoduchým řetězcem.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Nahraďte text řetězcem
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Uložte upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu nahradíme „text-k-replace“ v dokumentu „new-string“.

## Použití Legacy Order

Při provádění operací hledání a nahrazování můžete použít starší pořadí.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte UseLegacyOrder na hodnotu true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Při nahrazování textu použijte možnosti
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To vám umožňuje používat starší pořadí pro operace hledání a nahrazení.

## Nahrazení textu v tabulce

Můžete najít a nahradit text v tabulkách v dokumentu aplikace Word.

```java
// Vložte dokument
Document doc = new Document("your-document.docx");

// Získejte konkrétní tabulku (např. první tabulku)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// nahrazení textu v tabulce použijte FindReplaceOptions
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Uložte upravený dokument
doc.save("modified-document.docx");
```

To vám umožňuje provádět nahrazování textu konkrétně v tabulkách.

## Závěr

Aspose.Words for Java poskytuje komplexní možnosti pro vyhledávání a nahrazování textu v dokumentech aplikace Word. Ať už potřebujete provádět jednoduché nahrazování textu nebo pokročilejší operace pomocí regulárních výrazů, manipulací s poli nebo vlastních hodnotitelů, Aspose.Words pro Java vás pokryje. Nezapomeňte prozkoumat rozsáhlou dokumentaci a příklady poskytnuté společností Aspose, abyste mohli využít plný potenciál této výkonné knihovny Java.

## FAQ

### Jak si stáhnu Aspose.Words for Java?

 Aspose.Words for Java si můžete stáhnout z webové stránky na adrese[tento odkaz](https://releases.aspose.com/words/java/).

### Mohu k nahrazení textu použít regulární výrazy?

Ano, v Aspose.Words for Java můžete použít regulární výrazy pro nahrazení textu. To vám umožní provádět pokročilejší a flexibilnější operace hledání a nahrazování.

### Jak mohu při výměně ignorovat text uvnitř polí?

Chcete-li ignorovat text uvnitř polí během nahrazování, můžete nastavit`IgnoreFields` vlastnictvím`FindReplaceOptions` na`true`. To zajistí, že text v polích, jako jsou slučovací pole, bude vyloučen z nahrazování.

### Mohu nahradit text uvnitř záhlaví a zápatí?

 Ano, text v záhlaví a zápatí dokumentu Word můžete nahradit. Jednoduše otevřete příslušné záhlaví nebo zápatí a použijte`replace` metodou s požadovaným`FindReplaceOptions`.

### K čemu slouží možnost UseLegacyOrder?

 The`UseLegacyOrder` možnost v`FindReplaceOptions` umožňuje použít starší pořadí při provádění operací hledání a nahrazování. To může být užitečné v určitých scénářích, kde je požadováno chování starší objednávky.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
