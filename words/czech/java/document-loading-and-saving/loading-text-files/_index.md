---
title: Načítání textových souborů pomocí Aspose.Words pro Java
linktitle: Načítání textových souborů pomocí
second_title: Aspose.Words Java Document Processing API
description: Odemkněte sílu Aspose.Words pro Java. Naučte se načítat textové dokumenty, spravovat seznamy, manipulovat s mezerami a ovládat směr textu.
weight: 13
url: /cs/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Načítání textových souborů pomocí Aspose.Words pro Java


## Úvod do načítání textových souborů pomocí Aspose.Words pro Javu

V této příručce prozkoumáme, jak načíst textové soubory pomocí Aspose.Words for Java a jak s nimi pracovat jako s dokumenty aplikace Word. Pokryjeme různé aspekty, jako je zjišťování seznamů, manipulace s mezerami a ovládání směru textu.

## Krok 1: Detekce seznamů

Chcete-li načíst textový dokument a zjistit seznamy, postupujte takto:

```java
// Vytvořte dokument ve formátu prostého textu ve formě řetězce s částmi, které lze interpretovat jako seznamy.
// Při načítání budou Aspose.Words vždy detekovány první tři seznamy,
// Po načtení se pro ně vytvoří objekty seznamu.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//Čtvrtý seznam s mezerami mezi číslem seznamu a obsahem položky seznamu,
// bude detekováno jako seznam pouze v případě, že je "DetectNumberingWithWhitespaces" v objektu LoadOptions nastaveno na hodnotu true,
// abyste předešli tomu, že odstavce začínající čísly nebudou mylně rozpoznány jako seznamy.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Načtěte dokument při použití LoadOptions jako parametru a ověřte výsledek.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Tento kód ukazuje, jak načíst textový dokument s různými formáty seznamů a použít`DetectNumberingWithWhitespaces` možnost správně detekovat seznamy.

## Krok 2: Práce s možnostmi Spaces

Chcete-li ovládat úvodní a koncové mezery při načítání textového dokumentu, můžete použít následující kód:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

 V tomto příkladu načteme textový dokument a ořízneme úvodní a koncové mezery pomocí`TxtLeadingSpacesOptions.TRIM` a`TxtTrailingSpacesOptions.TRIM`.

## Krok 3: Ovládání směru textu

Chcete-li určit směr textu při načítání textového dokumentu, můžete použít následující kód:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Tento kód nastavuje směr dokumentu na automatickou detekci (`DocumentDirection.AUTO`a načte textový dokument s hebrejským textem. Směr dokumentu můžete upravit podle potřeby.

## Kompletní zdrojový kód pro načítání textových souborů pomocí Aspose.Words pro Javu

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Vytvořte dokument ve formátu prostého textu ve formě řetězce s částmi, které lze interpretovat jako seznamy.
	// Při načítání budou Aspose.Words vždy detekovány první tři seznamy,
	// Po načtení se pro ně vytvoří objekty seznamu.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Čtvrtý seznam s mezerami mezi číslem seznamu a obsahem položky seznamu,
	// bude detekováno jako seznam pouze v případě, že je "DetectNumberingWithWhitespaces" v objektu LoadOptions nastaveno na hodnotu true,
	// abyste předešli tomu, že odstavce začínající čísly nebudou mylně rozpoznány jako seznamy.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Načtěte dokument při použití LoadOptions jako parametru a ověřte výsledek.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Závěr

V této příručce jsme prozkoumali, jak načíst textové soubory pomocí Aspose.Words pro Java, zjistit seznamy, zacházet s mezerami a ovládat směr textu. Tyto techniky vám umožňují efektivně manipulovat s textovými dokumenty ve vašich aplikacích Java.

## FAQ

### Co je Aspose.Words for Java?

Aspose.Words for Java je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty Word programově v aplikacích Java. Poskytuje širokou škálu funkcí pro práci s textem, tabulkami, obrázky a dalšími prvky dokumentu.

### Jak mohu začít s Aspose.Words pro Java?

Chcete-li začít s Aspose.Words pro Java, postupujte takto:
1. Stáhněte a nainstalujte knihovnu Aspose.Words for Java.
2.  Podívejte se na dokumentaci na[Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) pro podrobné informace a příklady.
3. Prozkoumejte ukázkový kód a výukové programy, abyste se naučili, jak knihovnu efektivně používat.

### Jak načtu textový dokument pomocí Aspose.Words for Java?

 Chcete-li načíst textový dokument pomocí Aspose.Words for Java, můžete použít`TxtLoadOptions` třída a`Document` třída. Ujistěte se, že jste podle potřeby zadali vhodné volby pro manipulaci s mezerami a směr textu. Podrobný příklad naleznete v podrobném průvodci v tomto článku.

### Mohu převést načtený textový dokument do jiných formátů?

 Ano, Aspose.Words for Java umožňuje převést načtený textový dokument do různých formátů, včetně DOCX, PDF a dalších. Můžete použít`Document` třídy provádět konverze. Konkrétní příklady převodu naleznete v dokumentaci.

### Jak zacházím s mezerami v načtených textových dokumentech?

 Pomocí můžete ovládat, jak se zachází s úvodními a koncovými mezerami v načtených textových dokumentech`TxtLoadOptions` . Možnosti jako`TxtLeadingSpacesOptions` a`TxtTrailingSpacesOptions`umožňují oříznout nebo zachovat místa podle potřeby. Příklad naleznete v části „Možnosti manipulace s prostory“ v této příručce.

### Jaký je význam směrování textu v Aspose.Words pro Javu?

Směr textu je nezbytný pro dokumenty obsahující smíšená písma nebo jazyky, jako je hebrejština nebo arabština. Aspose.Words for Java poskytuje možnosti pro určení směru textu a zajišťuje správné vykreslování a formátování textu v těchto jazycích. Část "Ovládání směru textu" v této příručce ukazuje, jak nastavit směr textu.

### Kde najdu další zdroje a podporu pro Aspose.Words for Java?

 Další zdroje, dokumentaci a podporu naleznete na adrese[Aspose.Words pro dokumentaci Java](https://reference.aspose.com/words/java/). Můžete se také zúčastnit komunitních fór Aspose.Words nebo kontaktovat podporu Aspose pro pomoc s konkrétními problémy nebo dotazy.

### Je Aspose.Words for Java vhodný pro komerční projekty?

Ano, Aspose.Words for Java je vhodný pro osobní i komerční projekty. Nabízí možnosti licencování pro různé scénáře použití. Nezapomeňte si přečíst licenční podmínky a ceny na webu Aspose, abyste vybrali vhodnou licenci pro svůj projekt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
