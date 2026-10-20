---
date: 2025-12-27
description: Naučte se, jak nastavit směr, načíst txt soubory, odstranit mezery a
  převést txt na docx pomocí Aspose.Words pro Javu.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Jak nastavit směr a načíst textové soubory pomocí Aspose.Words pro Java
url: /cs/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit směr a načíst textové soubory pomocí Aspose.Words pro Java

## Úvod do načítání textových souborů pomocí Aspose.Words pro Java

V tomto průvodci se dozvíte **jak nastavit směr** při načítání prostých textových dokumentů a uvidíte praktické způsoby, jak **načíst txt**, **odstranit mezery** a **převést txt na docx** pomocí Aspose.Words pro Java. Ať už vytváříte službu pro konverzi dokumentů nebo potřebujete jemnou kontrolu nad detekcí seznamů, tento tutoriál vás provede každým krokem s jasnými vysvětleními a připraveným kódem.

## Rychlé odpovědi
- **Jak nastavit směr textu pro načtený TXT soubor?** Použijte `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` nebo specifikujte `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Dokáže Aspose.Words detekovat číslované seznamy v prostém textu?** Ano – povolte `DetectNumberingWithWhitespaces` v `TxtLoadOptions`.
- **Jak mohu odstranit úvodní a koncové mezery?** Nastavte `TxtLeadingSpacesOptions.TRIM` a `TxtTrailingSpacesOptions.TRIM`.
- **Je možné převést TXT soubor na DOCX jedním řádkem?** Načtěte TXT pomocí `TxtLoadOptions` a zavolejte `Document.save("output.docx")`.
- **Jaká verze Javy je vyžadována?** Java 8+ je dostačující pro Aspose.Words 24.x.

## Co znamená „jak nastavit směr“ v Aspose.Words?

Když textový soubor obsahuje skripty zprava doleva (např. hebrejštinu nebo arabštinu), knihovna musí znát pořadí čtení. Výčtový typ `DocumentDirection` vám umožňuje **nastavit směr** ručně nebo nechat Aspose, aby jej automaticky detekovalo, což zajišťuje správné rozložení a bidi formátování.

## Proč použít Aspose.Words pro načítání TXT souborů?

- **Přesná detekce seznamů** – zpracovává číslované, odrážkové a seznamy oddělené mezerami.
- **Jemná manipulace s mezerami** – ořízne nebo zachová úvodní/koncové mezery.
- **Automatická detekce směru textu** – ideální pro vícejazyčné dokumenty.
- **Jednokroková konverze** – načtěte `.txt` a uložte jako `.docx`, `.pdf` nebo jakýkoli podporovaný formát.

## Požadavky
- Java 8 nebo novější.
- Knihovna Aspose.Words pro Java (přidejte Maven/Gradle závislost nebo JAR do svého projektu).
- Základní znalost Java I/O streamů.

## Průvodce krok za krokem

### Krok 1: Detekce seznamů (jak načíst txt)

Pro načtení textového dokumentu a automatickou detekci seznamů vytvořte instanci `TxtLoadOptions` a povolte detekci seznamů. Níže uvedený kód ukazuje několik stylů seznamů a povoluje číslování s ohledem na mezery.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Tip:** Pokud potřebujete jen základní detekci seznamů, můžete vynechat možnost whitespace – Aspose i tak rozpozná standardní vzory `1.` a `1)`.

### Krok 2: Nastavení možností mezer (jak oříznout mezery)

Úvodní a koncové mezery často způsobují problémy s formátováním. Použijte `TxtLeadingSpacesOptions` a `TxtTrailingSpacesOptions` k řízení tohoto chování.

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

> **Proč je to důležité:** Ořezání mezer zabraňuje nechtěnému odsazení ve výsledném DOCX, což dělá dokument čistým bez ručního post‑zpracování.

### Krok 3: Řízení směru textu (jak nastavit směr)

Pro jazyky zprava doleva nastavte směr dokumentu před načtením. Níže uvedený příklad načte hebrejský textový soubor a vypíše bidi příznak pro potvrzení směru.

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

> **Častý úskalí:** Zapomenutí nastavit `DocumentDirection` může vést k rozbitému arabskému/hebrejskému textu, kde se znaky zobrazují ve špatném pořadí.

### Kompletní zdrojový kód pro načítání textových souborů pomocí Aspose.Words pro Java

Níže je kompletní, připravený ke spuštění zdroj, který kombinuje detekci seznamů, manipulaci s mezerami a řízení směru. Můžete jej zkopírovat do jedné třídy a spustit tři testovací metody samostatně.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Časté problémy a řešení

| Problém | Příčina | Řešení |
|---------|---------|--------|
| Seznamy nebyly detekovány | `DetectNumberingWithWhitespaces` ponechán `false` pro seznamy oddělené mezerami | Povolte `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Extra odsazení po načtení | Úvodní mezery byly zachovány | Nastavte `TxtLeadingSpacesOptions.TRIM` |
| Hebrejský text se zobrazuje obráceně | Směr dokumentu nebyl nastaven nebo byl nastaven na `LEFT_TO_RIGHT` | Použijte `DocumentDirection.AUTO` nebo `RIGHT_TO_LEFT` |
| Výstupní DOCX je prázdný | Vstupní stream nebyl resetován před druhým načtením | Znovu vytvořte `ByteArrayInputStream` pro každé volání načtení |

## Často kladené otázky

### Otázka: Co je Aspose.Words pro Java?

O: Aspose.Words pro Java je výkonná knihovna pro zpracování dokumentů, která vývojářům umožňuje programově vytvářet, manipulovat a převádět Word dokumenty v Java aplikacích. Podporuje širokou škálu funkcí, od jednoduchého načítání textu po složité formátování a konverzi.

### Otázka: Jak mohu začít s Aspose.Words pro Java?

O: 1. Stáhněte a nainstalujte knihovnu Aspose.Words pro Java. 2. Odkazujte se na dokumentaci na [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) pro podrobné informace a příklady. 3. Prozkoumejte ukázkový kód a tutoriály, abyste se naučili knihovnu efektivně používat.

### Otázka: Jak načíst textový dokument pomocí Aspose.Words pro Java?

O: Použijte třídu `TxtLoadOptions` spolu s konstruktorem `Document`. Specifikujte možnosti jako detekci seznamů, manipulaci s mezerami nebo směr textu, jak je ukázáno v výše uvedených krocích.

### Otázka: Mohu načtený textový dokument převést do jiných formátů?

O: Ano. Po načtení TXT souboru do objektu `Document` zavolejte `doc.save("output.pdf")`, `doc.save("output.docx")` nebo jakýkoli jiný podporovaný formát.

### Otázka: Jak zacházet s mezerami v načtených textových dokumentech?

O: Řiďte úvodní a koncové mezery pomocí `TxtLeadingSpacesOptions` a `TxtTrailingSpacesOptions`. Nastavte je na `TRIM` pro odstranění nechtěných mezer, nebo na `PRESERVE`, pokud potřebujete zachovat původní odsazení.

### Otázka: Jaký je význam směru textu v Aspose.Words pro Java?

O: Směr textu zajišťuje správné vykreslení skriptů zprava doleva (hebrejština, arabština atd.). Nastavením `DocumentDirection` garantujete, že bidi text bude v výsledném dokumentu zobrazen správně.

### Otázka: Kde najdu další zdroje a podporu pro Aspose.Words pro Java?

O: Navštivte [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) pro API reference, ukázky kódu a podrobné návody. Můžete se také připojit k fórům komunity Aspose nebo kontaktovat podporu Aspose pro konkrétní otázky.

### Otázka: Je Aspose.Words pro Java vhodný pro komerční projekty?

O: Ano. Nabízí licenční možnosti jak pro osobní, tak komerční použití. Prohlédněte si licenční podmínky na webu Aspose a vyberte vhodný plán pro váš projekt.

## Závěr

Nyní máte kompletní sadu nástrojů pro **načtení txt souborů**, **detekci seznamů**, **odstranění mezer** a **nastavení směru** při převodu prostého textu na bohaté Word dokumenty pomocí Aspose.Words pro Java. Použijte tyto vzory k automatizaci pracovních postupů s dokumenty, zlepšení vícejazyčné podpory a zajištění čistého, profesionálního výstupu pokaždé.

---

**Poslední aktualizace:** 2025-12-27  
**Testováno s:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}