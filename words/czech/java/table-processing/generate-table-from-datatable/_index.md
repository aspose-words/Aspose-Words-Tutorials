---
title: Generovat tabulku z Datatable
linktitle: Generovat tabulku z Datatable
second_title: Aspose.Words Java Document Processing API
description: Naučte se generovat tabulku z DataTable pomocí Aspose.Words for Java. Vytvářejte profesionální dokumenty Word s formátovanými tabulkami bez námahy.
weight: 11
url: /cs/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generovat tabulku z Datatable

## Zavedení

Vytváření tabulek dynamicky z datových zdrojů je běžným úkolem mnoha aplikací. Ať už generujete sestavy, faktury nebo souhrny dat, možnost programově naplnit tabulku daty vám může ušetřit spoustu času a úsilí. V tomto tutoriálu prozkoumáme, jak vygenerovat tabulku z DataTable pomocí Aspose.Words for Java. Rozdělíme proces do zvládnutelných kroků, abychom zajistili, že budete jasně rozumět každé části.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:

1.  Java Development Kit (JDK): Ujistěte se, že máte na svém počítači nainstalovaný JDK. Můžete si jej stáhnout z[Web společnosti Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Aspose.Words for Java: Budete potřebovat knihovnu Aspose.Words. Nejnovější verzi si můžete stáhnout z[Stránka vydání Aspose](https://releases.aspose.com/words/java/).

3. IDE: Integrované vývojové prostředí (IDE) jako IntelliJ IDEA nebo Eclipse usnadní kódování.

4. Základní znalost Javy: Znalost konceptů programování v Javě vám pomůže lépe porozumět úryvkům kódu.

5. Ukázková data: V tomto tutoriálu použijeme soubor XML s názvem „Seznam lidí.xml“ k simulaci zdroje dat. Tento soubor můžete vytvořit s ukázkovými daty pro testování.

## Krok 1: Vytvořte nový dokument

Nejprve musíme vytvořit nový dokument, kde bude naše tabulka umístěna. Toto je plátno pro naši práci.

```java
Document doc = new Document();
```

 Zde vytvoříme nový`Document` objekt. To bude sloužit jako náš pracovní dokument, kde budeme sestavovat naši tabulku.

## Krok 2: Inicializujte DocumentBuilder

 Dále použijeme`DocumentBuilder` třídy, což nám umožňuje snáze manipulovat s dokumentem.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

 The`DocumentBuilder` objekt poskytuje metody pro vkládání tabulek, textu a dalších prvků do dokumentu.

## Krok 3: Nastavte orientaci stránky

Protože očekáváme, že naše tabulka bude široká, nastavíme orientaci stránky na šířku.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Tento krok je zásadní, protože zajišťuje, že se náš stůl hezky vejde na stránku, aniž by byl oříznut.

## Krok 4: Načtení dat z XML

 Nyní musíme načíst naše data ze souboru XML do souboru a`DataTable`. Odtud pocházejí naše data.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

 Zde si přečteme soubor XML a načteme první tabulku z datové sady. Tento`DataTable` bude obsahovat data, která chceme zobrazit v našem dokumentu.

## Krok 5: Importujte tabulku z DataTable

Nyní přichází ta vzrušující část: import našich dat do dokumentu jako tabulky.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

 Metodu nazýváme`importTableFromDataTable` , kolem`DocumentBuilder` , naše`DataTable`a boolean označující, zda se mají zahrnout záhlaví sloupců.

## Krok 6: Upravte styl tabulky

Jakmile máme náš stůl, můžeme použít nějaký styl, aby vypadal dobře.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Tento kód aplikuje na tabulku předdefinovaný styl, čímž zvyšuje její vizuální přitažlivost a čitelnost.

## Krok 7: Odstraňte nežádoucí buňky

Pokud máte nějaké sloupce, které nechcete zobrazit, například sloupec obrázků, můžete je snadno odstranit.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Tento krok zajistí, že naše tabulka zobrazí pouze relevantní informace.

## Krok 8: Uložte dokument

Nakonec náš dokument s vygenerovanou tabulkou uložíme.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Tento řádek uloží dokument do určeného adresáře, což vám umožní zkontrolovat výsledky.

## Metoda importTableFromDataTable

 Pojďme se blíže podívat na`importTableFromDataTable` metoda. Tato metoda je zodpovědná za vytvoření struktury tabulky a její naplnění daty.

### Krok 1: Spusťte tabulku

Nejprve musíme v dokumentu spustit novou tabulku.

```java
Table table = builder.startTable();
```

Tím se inicializuje nová tabulka v našem dokumentu.

### Krok 2: Přidejte záhlaví sloupců

 Pokud chceme zahrnout záhlaví sloupců, zaškrtneme`importColumnHeadings` vlajka.

```java
if (importColumnHeadings) {
    // Uložte původní formátování
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Nastavte formátování nadpisu
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Vložte názvy sloupců
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Obnovte původní formátování
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

 Tento blok kódu formátuje řádek záhlaví a vkládá názvy sloupců z`DataTable`.

### Krok 3: Naplňte tabulku daty

 Nyní projdeme každou řadou`DataTable` pro vložení dat do tabulky.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

této části zpracováváme různé typy dat, přiměřeně formátujeme data a vkládáme jiná data jako text.

### Krok 4: Ukončete tabulku

Po vložení všech dat nakonec tabulku dokončíme.

```java
builder.endTable();
```

 Tento řádek označuje konec naší tabulky a umožňuje`DocumentBuilder` abychom věděli, že jsme s touto částí skončili.

## Závěr

A tady to máte! Úspěšně jste se naučili, jak generovat tabulku z DataTable pomocí Aspose.Words for Java. Pomocí těchto kroků můžete snadno vytvářet dynamické tabulky ve svých dokumentech na základě různých zdrojů dat. Ať už generujete sestavy nebo faktury, tato metoda zefektivní váš pracovní postup a zlepší váš proces vytváření dokumentů.

## FAQ

### Co je Aspose.Words for Java?
Aspose.Words for Java je výkonná knihovna pro vytváření, manipulaci a převod dokumentů aplikace Word programově.

### Mohu používat Aspose.Words zdarma?
 Ano, Aspose nabízí bezplatnou zkušební verzi. Můžete si jej stáhnout z[zde](https://releases.aspose.com/).

### Jak upravím styl tabulek v Aspose.Words?
Styly můžete aplikovat pomocí předdefinovaných identifikátorů stylů a voleb poskytovaných knihovnou.

### Jaké typy dat mohu vkládat do tabulek?
Můžete vložit různé typy dat, včetně textu, čísel a dat, které lze odpovídajícím způsobem naformátovat.

### Kde mohu získat podporu pro Aspose.Words?
 Podporu a dotazy můžete najít na[Aspose fórum](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
