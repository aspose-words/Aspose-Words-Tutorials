---
"description": "Naučte se, jak pomocí Aspose.Words pro Javu najít a nahradit text v dokumentech Word. Podrobný návod s příklady kódu. Zlepšete si dovednosti v manipulaci s dokumenty v Javě."
"linktitle": "Hledání a nahrazování textu"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Hledání a nahrazování textu v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/finding-and-replacing-text/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hledání a nahrazování textu v Aspose.Words pro Javu


## Úvod do vyhledávání a nahrazování textu v Aspose.Words pro Javu

Aspose.Words pro Javu je výkonné Java API, které umožňuje programově pracovat s dokumenty Wordu. Jedním z běžných úkolů při práci s dokumenty Wordu je hledání a nahrazování textu. Ať už potřebujete aktualizovat zástupné symboly v šablonách nebo provádět složitější manipulace s textem, Aspose.Words pro Javu vám může pomoci efektivně dosáhnout vašich cílů.

## Předpoklady

Než se ponoříme do detailů hledání a nahrazování textu, ujistěte se, že máte splněny následující předpoklady:

- Vývojové prostředí v Javě
- Aspose.Words pro knihovnu Java
- Ukázkový dokument Wordu pro práci

Knihovnu Aspose.Words pro Javu si můžete stáhnout z [zde](https://releases.aspose.com/words/java/).

## Hledání a nahrazování jednoduchého textu

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte nástroj pro tvorbu dokumentů
DocumentBuilder builder = new DocumentBuilder(doc);

// Najít a nahradit text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Uložit upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu načteme dokument aplikace Word, vytvoříme `DocumentBuilder`a použijte `replace` metoda pro nalezení a nahrazení „old-text“ textem „new-text“ v dokumentu.

## Používání regulárních výrazů

Regulární výrazy poskytují výkonné funkce pro porovnávání vzorů pro vyhledávání a nahrazování textu. Aspose.Words pro Javu podporuje regulární výrazy pro pokročilejší operace hledání a nahrazování.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte nástroj pro tvorbu dokumentů
DocumentBuilder builder = new DocumentBuilder(doc);

// Použití regulárních výrazů pro vyhledávání a nahrazování textu
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Uložit upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme regulární výraz k nalezení a nahrazení textu v dokumentu.

## Ignorování textu uvnitř polí

Aspose.Words můžete nakonfigurovat tak, aby při provádění operací hledání a nahrazování ignoroval text uvnitř polí.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte IgnoreFields na hodnotu true.
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Použití možností při nahrazování textu
doc.getRange().replace("text-to-replace", "new-text", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To je užitečné, pokud chcete vyloučit text uvnitř polí, jako jsou slučovací pole, z nahrazování.

## Ignorování textu uvnitř mazání revizí

Aspose.Words můžete nakonfigurovat tak, aby během operací hledání a nahrazování ignoroval text uvnitř revizí odstraněných položek.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte IgnoreDeleted na hodnotu true.
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Použití možností při nahrazování textu
doc.getRange().replace("text-to-replace", "new-text", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To umožňuje vyloučit text, který byl ve sledovaných změnách označen k odstranění, z nahrazování.

## Ignorování textu uvnitř vložených revizí

Aspose.Words můžete nakonfigurovat tak, aby během operací hledání a nahrazování ignoroval text uvnitř vložených revizí.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte IgnoreInserted na hodnotu true.
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Použití možností při nahrazování textu
doc.getRange().replace("text-to-replace", "new-text", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To umožňuje vyloučit text, který byl ve sledovaných změnách označen jako vložený, z nahrazování.

## Nahrazení textu HTML kódem

K nahrazení textu obsahem HTML můžete použít Aspose.Words pro Javu.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvoření instance FindReplaceOptions s vlastním zpětným voláním nahrazující funkce
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Použití možností při nahrazování textu
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme vlastní `ReplaceWithHtmlEvaluator` nahradit text HTML obsahem.

## Nahrazení textu v záhlaví a zápatí

Text v záhlaví a zápatí dokumentu Word můžete vyhledat a nahradit.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Získejte kolekci záhlaví a zápatí
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Vyberte typ záhlaví nebo zápatí, ve kterém chcete nahradit text (např. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Vytvořte instanci FindReplaceOptions a použijte ji na rozsah zápatí.
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To umožňuje provádět nahrazování textu konkrétně v záhlavích a zápatích.

## Zobrazení změn v pořadí záhlaví a zápatí

Pomocí Aspose.Words můžete zobrazit změny v pořadí záhlaví a zápatí v dokumentu.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Získejte první část
Section firstPageSection = doc.getFirstSection();

// Vytvořte instanci FindReplaceOptions a aplikujte ji na rozsah dokumentu.
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Nahradit text, který ovlivňuje pořadí záhlaví a zápatí
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To vám umožní vizualizovat změny související s pořadím záhlaví a zápatí v dokumentu.

## Nahrazení textu poli

Text můžete nahradit poli pomocí Aspose.Words pro Javu.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte vlastní zpětné volání pro nahrazující pole.
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Použití možností při nahrazování textu
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu nahradíme text poli a určíme typ pole (např. `FieldType.FIELD_MERGE_FIELD`).

## Nahrazení hodnotitelem

K dynamickému určení nahrazujícího textu můžete použít vlastní vyhodnocovač.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte vlastní zpětné volání nahrazující funkce.
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Použití možností při nahrazování textu
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme vlastní vyhodnocovač (`MyReplaceEvaluator`) pro nahrazení textu.

## Nahrazení regulárním výrazem

Aspose.Words pro Javu umožňuje nahrazovat text pomocí regulárních výrazů.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Použití regulárních výrazů pro vyhledávání a nahrazování textu
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Uložit upravený dokument
doc.save("modified-document.docx");
```

V tomto příkladu používáme regulární výraz k nalezení a nahrazení textu v dokumentu.

## Rozpoznávání a substituce v rámci substitučních vzorů

Pomocí Aspose.Words pro Javu můžete rozpoznat a provést substituce v rámci náhradních vzorů.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions s UseSubstitutions nastavenou na hodnotu true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Použití možností při nahrazování textu vzorem
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To vám umožňuje provádět substituce v rámci náhradních vzorů pro pokročilejší nahrazení.

## Nahrazení řetězcem

Text můžete nahradit jednoduchým řetězcem pomocí Aspose.Words pro Javu.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Nahradit text řetězcem
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Uložit upravený dokument
doc.save("modified-document.docx");
```

tomto příkladu nahradíme v dokumentu řetězec „text-k-nahrazení“ řetězcem „nový-řetězec“.

## Používání starší objednávky

Při provádění operací hledání a nahrazování můžete použít starší pořadí.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Vytvořte instanci FindReplaceOptions a nastavte UseLegacyOrder na hodnotu true.
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Použití možností při nahrazování textu
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To umožňuje použít starší pořadí pro operace hledání a nahrazování.

## Nahrazení textu v tabulce

V tabulkách v dokumentu Word můžete najít a nahradit text.

```java
// Načíst dokument
Document doc = new Document("your-document.docx");

// Získání konkrétní tabulky (např. první tabulky)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Použití funkce FindReplaceOptions pro nahrazení textu v tabulce
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Uložit upravený dokument
doc.save("modified-document.docx");
```

To umožňuje provádět nahrazování textu specificky v tabulkách.

## Závěr

Aspose.Words pro Javu nabízí komplexní funkce pro vyhledávání a nahrazování textu v dokumentech Wordu. Ať už potřebujete provádět jednoduché nahrazování textu nebo pokročilejší operace pomocí regulárních výrazů, manipulace s poli nebo vlastních vyhodnocovačů, Aspose.Words pro Javu vám pomůže. Nezapomeňte si prohlédnout rozsáhlou dokumentaci a příklady, které Aspose poskytuje, abyste mohli plně využít potenciál této výkonné knihovny Java.

## Často kladené otázky

### Jak si stáhnu Aspose.Words pro Javu?

Aspose.Words pro Javu si můžete stáhnout z webových stránek na adrese [tento odkaz](https://releases.aspose.com/words/java/).

### Mohu použít regulární výrazy pro nahrazení textu?

Ano, v Aspose.Words pro Javu můžete použít regulární výrazy pro nahrazování textu. To vám umožní provádět pokročilejší a flexibilnější operace hledání a nahrazování.

### Jak mohu ignorovat text uvnitř polí během nahrazování?

Chcete-li během nahrazování ignorovat text uvnitř polí, můžete nastavit `IgnoreFields` majetek `FindReplaceOptions` na `true`Tím je zajištěno, že text v polích, jako jsou slučovací pole, bude z nahrazení vyloučen.

### Mohu nahradit text uvnitř záhlaví a zápatí?

Ano, text v záhlaví a zápatí dokumentu Word můžete nahradit. Stačí přejít na příslušné záhlaví nebo zápatí a použít `replace` metoda s požadovaným `FindReplaceOptions`.

### K čemu slouží možnost UseLegacyOrder?

Ten/Ta/To `UseLegacyOrder` možnost v `FindReplaceOptions` umožňuje použít starší pořadí při provádění operací hledání a nahrazování. To může být užitečné v určitých scénářích, kde je požadováno chování staršího pořadí.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}