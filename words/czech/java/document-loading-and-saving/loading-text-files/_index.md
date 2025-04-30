---
"description": "Odemkněte sílu Aspose.Words pro Javu. Naučte se načítat textové dokumenty, spravovat seznamy, ovládat mezery a ovládat směr textu."
"linktitle": "Načítání textových souborů pomocí"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Načítání textových souborů pomocí Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Načítání textových souborů pomocí Aspose.Words pro Javu


## Úvod do načítání textových souborů pomocí Aspose.Words pro Javu

V této příručce se podíváme na to, jak načítat textové soubory pomocí Aspose.Words pro Javu a jak s nimi manipulovat jako s dokumenty Wordu. Probereme různé aspekty, jako je detekce seznamů, práce s mezerami a ovládání směru textu.

## Krok 1: Detekce seznamů

Chcete-li načíst textový dokument a detekovat seznamy, postupujte takto:

```java
// Vytvořte dokument v prostém textu ve formě řetězce s částmi, které lze interpretovat jako seznamy.
// Po načtení budou Aspose.Words vždy detekovány první tři seznamy,
// a po načtení pro ně budou vytvořeny objekty List.
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
// bude detekován jako seznam pouze tehdy, pokud je proměnná „DetectNumberingWithWhitespaces“ v objektu LoadOptions nastavena na hodnotu true,
// aby se zabránilo chybné detekci odstavců začínajících čísly jako seznamů.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Načtěte dokument s použitím parametru LoadOptions a ověřte výsledek.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Tento kód ukazuje, jak načíst textový dokument s různými formáty seznamů a jak je použít `DetectNumberingWithWhitespaces` možnost správné detekce seznamů.

## Krok 2: Možnosti zpracování prostorů

Pro ovládání počátečních a koncových mezer při načítání textového dokumentu můžete použít následující kód:

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

V tomto příkladu načteme textový dokument a ořízneme úvodní a koncové mezery pomocí `TxtLeadingSpacesOptions.TRIM` a `TxtTrailingSpacesOptions.TRIM`.

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

Tento kód nastaví směr dokumentu na automatickou detekci (`DocumentDirection.AUTO`) a načte textový dokument s hebrejským textem. Směr dokumentu můžete podle potřeby upravit.

## Kompletní zdrojový kód pro načítání textových souborů pomocí Aspose.Words pro Javu

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Vytvořte dokument v prostém textu ve formě řetězce s částmi, které lze interpretovat jako seznamy.
	// Po načtení budou Aspose.Words vždy detekovány první tři seznamy,
	// a po načtení pro ně budou vytvořeny objekty List.
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
	// bude detekován jako seznam pouze tehdy, pokud je proměnná „DetectNumberingWithWhitespaces“ v objektu LoadOptions nastavena na hodnotu true,
	// aby se zabránilo chybné detekci odstavců začínajících čísly jako seznamů.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Načtěte dokument s použitím parametru LoadOptions a ověřte výsledek.
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

V této příručce jsme prozkoumali, jak načítat textové soubory pomocí Aspose.Words pro Javu, detekovat seznamy, zpracovávat mezery a ovládat směr textu. Tyto techniky vám umožňují efektivně manipulovat s textovými dokumenty ve vašich Java aplikacích.

## Často kladené otázky

### Co je Aspose.Words pro Javu?

Aspose.Words pro Javu je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům programově vytvářet, manipulovat a převádět dokumenty Wordu v aplikacích Java. Nabízí širokou škálu funkcí pro práci s textem, tabulkami, obrázky a dalšími prvky dokumentů.

### Jak mohu začít s Aspose.Words pro Javu?

Chcete-li začít s Aspose.Words pro Javu, postupujte takto:
1. Stáhněte a nainstalujte knihovnu Aspose.Words pro Javu.
2. Viz dokumentace na adrese [Referenční příručka k Aspose.Words pro Java API](https://reference.aspose.com/words/java/) pro podrobné informace a příklady.
3. Prozkoumejte ukázkový kód a tutoriály a naučte se, jak knihovnu efektivně používat.

### Jak načtu textový dokument pomocí Aspose.Words pro Javu?

Chcete-li načíst textový dokument pomocí Aspose.Words pro Javu, můžete použít `TxtLoadOptions` třída a `Document` třída. Ujistěte se, že jste podle potřeby zadali vhodné možnosti pro zpracování mezer a směru textu. Podrobný příklad naleznete v podrobném návodu v tomto článku.

### Mohu převést načtený textový dokument do jiných formátů?

Ano, Aspose.Words pro Javu umožňuje převést načtený textový dokument do různých formátů, včetně DOCX, PDF a dalších. Můžete použít `Document` třída pro provádění konverzí. Konkrétní příklady konverzí naleznete v dokumentaci.

### Jak mám zpracovat mezery v načtených textových dokumentech?

Způsob zpracování úvodních a koncových mezer v načtených textových dokumentech můžete ovládat pomocí `TxtLoadOptions`Možnosti jako `TxtLeadingSpacesOptions` a `TxtTrailingSpacesOptions` umožňují ořezávat nebo zachovat mezery podle potřeby. Příklad naleznete v části „Možnosti zpracování mezer“ v této příručce.

### Jaký je význam směru textu v Aspose.Words pro Javu?

Směr textu je nezbytný pro dokumenty obsahující smíšené písma nebo jazyky, jako je hebrejština nebo arabština. Aspose.Words pro Javu nabízí možnosti pro určení směru textu, což zajišťuje správné vykreslování a formátování textu v těchto jazycích. Sekce „Ovládání směru textu“ v této příručce ukazuje, jak směr textu nastavit.

### Kde najdu další zdroje a podporu pro Aspose.Words pro Javu?

Další zdroje, dokumentaci a podporu naleznete na [Dokumentace k Aspose.Words pro Javu](https://reference.aspose.com/words/java/)Můžete se také zapojit do komunitních fór Aspose.Words nebo kontaktovat podporu Aspose s žádostí o pomoc s konkrétními problémy nebo dotazy.

### Je Aspose.Words pro Javu vhodný pro komerční projekty?

Ano, Aspose.Words pro Javu je vhodný pro osobní i komerční projekty. Nabízí možnosti licencování pro různé scénáře použití. Nezapomeňte si prostudovat licenční podmínky a ceny na webových stránkách Aspose a vybrat si vhodnou licenci pro váš projekt.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}