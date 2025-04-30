---
"description": "Naučte se, jak generovat tabulku z DataTable pomocí Aspose.Words pro Javu. Vytvářejte profesionální dokumenty Word s formátovanými tabulkami bez námahy."
"linktitle": "Generovat tabulku z datové tabulky"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Generovat tabulku z datové tabulky"
"url": "/cs/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generovat tabulku z datové tabulky

## Zavedení

Dynamické vytváření tabulek z datových zdrojů je běžným úkolem v mnoha aplikacích. Ať už generujete reporty, faktury nebo souhrny dat, možnost programově naplnit tabulku daty vám může ušetřit spoustu času a úsilí. V tomto tutoriálu se podíváme na to, jak vygenerovat tabulku z DataTable pomocí Aspose.Words pro Javu. Rozdělíme proces do zvládnutelných kroků, abyste měli jasnou představu o každé části.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete k zahájení:

1. Vývojářská sada Java (JDK): Ujistěte se, že máte na svém počítači nainstalovanou JDK. Můžete si ji stáhnout z [Webové stránky společnosti Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Aspose.Words pro Javu: Budete potřebovat knihovnu Aspose.Words. Nejnovější verzi si můžete stáhnout z [Stránka s vydáními Aspose](https://releases.aspose.com/words/java/).

3. IDE: Integrované vývojové prostředí (IDE) jako IntelliJ IDEA nebo Eclipse usnadní kódování.

4. Základní znalost Javy: Znalost programovacích konceptů v Javě vám pomůže lépe porozumět úryvkům kódu.

5. Ukázková data: V tomto tutoriálu použijeme soubor XML s názvem „Seznam lidí.xml“ k simulaci zdroje dat. Tento soubor můžete vytvořit s ukázkovými daty pro testování.

## Krok 1: Vytvořte nový dokument

Nejprve musíme vytvořit nový dokument, kde bude umístěna naše tabulka. Toto je plátno pro naši práci.

```java
Document doc = new Document();
```

Zde vytvoříme novou instanci `Document` objekt. Toto bude sloužit jako náš pracovní dokument, ve kterém budeme vytvářet naši tabulku.

## Krok 2: Inicializace nástroje DocumentBuilder

Dále použijeme `DocumentBuilder` třída, která nám umožňuje snadnější manipulaci s dokumentem.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten/Ta/To `DocumentBuilder` Objekt poskytuje metody pro vkládání tabulek, textu a dalších prvků do dokumentu.

## Krok 3: Nastavení orientace stránky

Protože očekáváme, že naše tabulka bude široká, nastavíme orientaci stránky na šířku.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Tento krok je klíčový, protože zajišťuje, že se naše tabulka pěkně vejde na stránku, aniž by byla oříznutá.

## Krok 4: Načtení dat z XML

Nyní musíme načíst data ze souboru XML do `DataTable`Odtud pocházejí naše data.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

Zde načteme soubor XML a načteme první tabulku z datové sady. Toto `DataTable` bude obsahovat data, která chceme v dokumentu zobrazit.

## Krok 5: Import tabulky z DataTable

A teď přichází ta vzrušující část: import našich dat do dokumentu jako tabulky.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

Metodu nazýváme `importTableFromDataTable`, procházející kolem `DocumentBuilder`, naše `DataTable`a booleovskou hodnotu, která označuje, zda se mají zahrnout záhlaví sloupců.

## Krok 6: Stylizace tabulky

Jakmile máme stůl hotový, můžeme ho trochu upravit, aby vypadal dobře.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Tento kód aplikuje na tabulku předdefinovaný styl, čímž vylepšuje její vizuální atraktivitu a čitelnost.

## Krok 7: Odstranění nežádoucích buněk

Pokud máte sloupce, které nechcete zobrazovat, například sloupec s obrázky, můžete ho snadno odebrat.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Tento krok zajišťuje, že naše tabulka zobrazuje pouze relevantní informace.

## Krok 8: Uložte dokument

Nakonec uložíme náš dokument s vygenerovanou tabulkou.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Tento řádek uloží dokument do zadaného adresáře, což vám umožní prohlédnout si výsledky.

## Metoda importTableFromDataTable

Pojďme se blíže podívat na `importTableFromDataTable` metoda. Tato metoda je zodpovědná za vytvoření struktury tabulky a její naplnění daty.

### Krok 1: Spuštění tabulky

Nejprve musíme v dokumentu vytvořit novou tabulku.

```java
Table table = builder.startTable();
```

Tím se v našem dokumentu inicializuje nová tabulka.

### Krok 2: Přidání záhlaví sloupců

Pokud chceme zahrnout záhlaví sloupců, zaškrtneme `importColumnHeadings` vlajka.

```java
if (importColumnHeadings) {
    // Uložit původní formátování
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Nastavení formátování nadpisů
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Vložit názvy sloupců
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Obnovit původní formátování
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

Tento blok kódu formátuje řádek záhlaví a vkládá názvy sloupců z `DataTable`.

### Krok 3: Naplnění tabulky daty

Nyní procházíme každý řádek `DataTable` vložit data do tabulky.

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

V této části se budeme zabývat různými datovými typy, vhodným formátováním dat a vkládáním dalších dat jako textu.

### Krok 4: Ukončení tabulky

Nakonec tabulku dokončíme, jakmile jsou vložena všechna data.

```java
builder.endTable();
```

Tato čára označuje konec naší tabulky a umožňuje `DocumentBuilder` abychom věděli, že jsme s touto částí hotovi.

## Závěr

A tady to máte! Úspěšně jste se naučili, jak generovat tabulku z DataTable pomocí Aspose.Words pro Javu. Dodržováním těchto kroků můžete snadno vytvářet dynamické tabulky ve svých dokumentech na základě různých zdrojů dat. Ať už generujete reporty nebo faktury, tato metoda zefektivní váš pracovní postup a vylepší proces vytváření dokumentů.

## Často kladené otázky

### Co je Aspose.Words pro Javu?
Aspose.Words pro Javu je výkonná knihovna pro programovou tvorbu, manipulaci a konverzi dokumentů Wordu.

### Mohu používat Aspose.Words zdarma?
Ano, Aspose nabízí bezplatnou zkušební verzi. Můžete si ji stáhnout z [zde](https://releases.aspose.com/).

### Jak upravím styl tabulek v Aspose.Words?
Styly můžete aplikovat pomocí předdefinovaných identifikátorů stylů a možností poskytovaných knihovnou.

### Jaké typy dat mohu vkládat do tabulek?
Můžete vkládat různé datové typy, včetně textu, čísel a dat, které lze odpovídajícím způsobem formátovat.

### Kde mohu získat podporu pro Aspose.Words?
Podporu a dotazy můžete najít na [Fórum Aspose](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}