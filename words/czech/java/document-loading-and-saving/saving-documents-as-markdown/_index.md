---
date: 2025-12-22
description: Naučte se exportovat markdown převodem dokumentů Word do Markdown pomocí
  Aspose.Words pro Java. Tento podrobný průvodce zahrnuje zarovnání tabulek, práci
  s obrázky a další.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Jak exportovat Markdown pomocí Aspose.Words pro Java
url: /cs/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak exportovat Markdown pomocí Aspose.Words pro Java

## Úvod do exportu Markdown v Aspose.Words pro Java

V tomto krok‑za‑krokem tutoriálu **se naučíte, jak exportovat markdown** z dokumentů Word pomocí Aspose.Words pro Java. Markdown je lehký značkovací jazyk, který je ideální pro dokumentaci, generátory statických stránek a mnoho publikačních platforem. Na konci tohoto průvodce budete schopni **převést Word do markdown**, přizpůsobit zarovnání tabulek a **pracovat s obrázky v markdown** bez námahy.

## Rychlé odpovědi
- **Jaká je hlavní třída pro ukládání jako Markdown?** `MarkdownSaveOptions`
- **Mohou být obrázky vloženy automaticky?** Ano – nastavte složku pro obrázky pomocí `setImagesFolder`.
- **Jak mohu řídit zarovnání tabulky?** Použijte `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Jaké jsou minimální požadavky?** JDK 8+ a knihovna Aspose.Words pro Java.
- **Je k dispozici zkušební verze?** Ano, stáhněte si ji z webu Aspose.

## Co znamená „jak exportovat markdown“?
Exportování markdownu znamená převést bohatý textový dokument Word (`.docx`) na prostý textový soubor `.md`, který zachovává nadpisy, tabulky a obrázky v syntaxi Markdown.

## Proč použít Aspose.Words pro Java k převodu docx s obrázky?
Aspose.Words zvládá složité rozvržení, vložené obrázky a struktury tabulek bez ztráty věrnosti. Navíc poskytuje jemno‑granulární kontrolu nad výstupem Markdown, jako je zarovnání tabulek a správa složky s obrázky.

## Předpoklady

- Java Development Kit (JDK) nainstalovaný ve vašem systému.
- Knihovna Aspose.Words pro Java. Můžete si ji stáhnout [zde](https://releases.aspose.com/words/java/).

## Krok 1: Vytvořte jednoduchý Word dokument

Nejprve vytvoříme malý dokument, který obsahuje tabulku. To nám umožní později ukázat **přizpůsobení zarovnání tabulky**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

V tomto úryvku:

1. Vytvořte nový `Document`.
2. Použijte `DocumentBuilder` k vložení dvoubuňkové tabulky.
3. Použijte **right** a **center** zarovnání odstavců uvnitř každé buňky.
4. Uložte soubor jako Markdown pomocí `MarkdownSaveOptions`.

## Krok 2: Přizpůsobte zarovnání obsahu tabulky

Aspose.Words vám umožňuje určit, jak budou buňky tabulky vykresleny ve finálním Markdownu. Můžete vynutit zarovnání vlevo, vpravo, na střed nebo nechat knihovnu rozhodnout automaticky na základě prvního odstavce v každém sloupci.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Přepnutím vlastnosti `TableContentAlignment` řídíte **přizpůsobení zarovnání tabulky** pro výstupní Markdown.

## Krok 3: Práce s obrázky při exportu do markdown

Když dokument obsahuje obrázky, budete chtít, aby se tyto obrázky správně zobrazily v generovaném souboru `.md`. Nastavte složku, kam má Aspose.Words uložit extrahované obrázky.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Nahraďte `"document_with_images.docx"` cestou k vašemu zdrojovému souboru a `"images_folder/"` umístěním, kde chcete obrázky uložit. Výsledný Markdown bude obsahovat odkazy na obrázky, které ukazují na tuto složku, což vám umožní **pracovat s obrázky v markdown** bez problémů.

## Kompletní zdrojový kód pro ukládání dokumentů jako Markdown v Aspose.Words pro Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Časté problémy a řešení

| Problém | Řešení |
|---------|--------|
| Obrázky se nezobrazují v souboru `.md` | Ověřte, že `setImagesFolder` ukazuje na zapisovatelný adresář a že složka je správně odkazována v generovaném Markdownu. |
| Zarovnání tabulky vypadá špatně | Použijte `TableContentAlignment.AUTO`, aby Aspose.Words určil nejlepší zarovnání na základě prvního odstavce v každém sloupci. |
| Výstupní soubor je prázdný | Ujistěte se, že objekt `Document` skutečně obsahuje obsah před voláním `save`. |

## Často kladené otázky

**Q: Jak nainstaluji Aspose.Words pro Java?**  
A: Aspose.Words pro Java lze nainstalovat zahrnutím knihovny do vašeho Java projektu. Knihovnu můžete stáhnout [zde](https://releases.aspose.com/words/java/) a postupovat podle instalačních pokynů uvedených v dokumentaci.

**Q: Mohu převést složité Word dokumenty s tabulkami a obrázky do Markdown?**  
A: Ano, Aspose.Words pro Java podporuje převod složitých Word dokumentů s tabulkami, obrázky a různými formátovacími prvky do Markdownu. Výstupní Markdown můžete přizpůsobit podle složitosti vašeho dokumentu.

**Q: Jak mohu pracovat s obrázky v Markdown souborech?**  
A: Nastavte cestu ke složce pro obrázky pomocí metody `setImagesFolder` v `MarkdownSaveOptions`. Ujistěte se, že soubory obrázků jsou uloženy ve specifikované složce; Aspose.Words vygeneruje odpovídající odkazy na obrázky v Markdownu.

**Q: Je k dispozici zkušební verze Aspose.Words pro Java?**  
A: Ano, zkušební verzi Aspose.Words pro Java můžete získat na webu Aspose. Zkušební verze vám umožní vyzkoušet funkce knihovny před zakoupením licence.

**Q: Kde najdu více příkladů a dokumentaci?**  
A: Pro více příkladů, dokumentaci a podrobné informace o Aspose.Words pro Java navštivte [dokumentaci](https://reference.aspose.com/words/java/).

---

**Poslední aktualizace:** 2025-12-22  
**Testováno s:** Aspose.Words pro Java 24.12 (nejnovější v době psaní)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}