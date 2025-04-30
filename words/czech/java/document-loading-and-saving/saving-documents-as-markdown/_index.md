---
"description": "Naučte se, jak převést dokumenty Wordu do formátu Markdown pomocí Aspose.Words pro Javu. Tato podrobná příručka zahrnuje zarovnání tabulek, práci s obrázky a další."
"linktitle": "Ukládání dokumentů ve formátu Markdown"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Ukládání dokumentů jako Markdown v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů jako Markdown v Aspose.Words pro Javu


## Úvod do ukládání dokumentů ve formátu Markdown v Aspose.Words pro Javu

tomto podrobném návodu si ukážeme, jak ukládat dokumenty ve formátu Markdown pomocí Aspose.Words pro Javu. Markdown je odlehčený značkovací jazyk, který se běžně používá pro formátování textových dokumentů. S Aspose.Words pro Javu můžete snadno převést dokumenty Wordu do formátu Markdown. Probereme různé aspekty ukládání souborů Markdown, včetně zarovnání obsahu tabulek a práce s obrázky.

## Předpoklady

Než začnete, ujistěte se, že máte následující předpoklady:

- Na vašem systému nainstalovaná sada pro vývoj Java (JDK).
- Knihovna Aspose.Words pro Javu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

## Krok 1: Vytvoření dokumentu Word

Začněme vytvořením dokumentu Word, který později převedeme do formátu Markdown. Tento dokument si můžete přizpůsobit podle svých požadavků.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložení tabulky se dvěma buňkami
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Uložit dokument jako Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

tomto příkladu vytvoříme jednoduchou tabulku se dvěma buňkami a nastavíme zarovnání odstavců v rámci těchto buněk. Poté dokument uložíme jako Markdown pomocí příkazu `MarkdownSaveOptions`.

## Krok 2: Úprava zarovnání obsahu tabulky

Aspose.Words pro Javu umožňuje přizpůsobit zarovnání obsahu tabulky při ukládání ve formátu Markdown. Obsah tabulky můžete zarovnat vlevo, vpravo, na střed nebo jej nechat určit automaticky na základě prvního odstavce v každém sloupci tabulky.

Zde je návod, jak přizpůsobit zarovnání obsahu tabulky:

```java
// Nastavit zarovnání obsahu tabulky doleva
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Nastavit zarovnání obsahu tabulky doprava
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Nastavení zarovnání obsahu tabulky na střed
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Nastavte zarovnání obsahu tabulky na automatické (určené prvním odstavcem)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Změnou `TableContentAlignment` vlastnost , můžete ovládat, jak se obsah uvnitř tabulek zarovná při převodu do Markdownu.

## Krok 3: Zpracování obrázků

Chcete-li do dokumentu Markdownu zahrnout obrázky, musíte zadat složku, ve které se obrázky nacházejí. Aspose.Words pro Javu umožňuje nastavit složku s obrázky v `MarkdownSaveOptions`.

Zde je návod, jak nastavit složku s obrázky a uložit dokument s obrázky:

```java
// Načíst dokument obsahující obrázky
Document doc = new Document("document_with_images.docx");

// Nastavte cestu ke složce obrázků
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Uložte dokument s obrázky
doc.save("document_with_images.md", saveOptions);
```

Nezapomeňte vyměnit `"document_with_images.docx"` s cestou k dokumentu Wordu obsahujícímu obrázky a `"images_folder/"` se skutečnou cestou ke složce, kde jsou uloženy vaše obrázky.

## Kompletní zdrojový kód pro ukládání dokumentů jako Markdown v Aspose.Words pro Javu

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
	// Zarovná všechny odstavce uvnitř tabulky.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Zarovnání v tomto případě bude převzato z prvního odstavce v odpovídajícím sloupci tabulky.
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

## Závěr

této příručce jsme prozkoumali, jak ukládat dokumenty ve formátu Markdown pomocí Aspose.Words pro Javu. Probrali jsme vytvoření dokumentu Word, úpravu zarovnání obsahu tabulek a práci s obrázky v souborech Markdown. Nyní můžete efektivně převádět dokumenty Word do formátu Markdown, což je činí vhodnými pro různé publikační platformy a potřeby dokumentace.

## Často kladené otázky

### Jak nainstaluji Aspose.Words pro Javu?

Aspose.Words pro Javu lze nainstalovat zahrnutím knihovny do vašeho projektu Java. Knihovnu si můžete stáhnout z [zde](https://releases.aspose.com/words/java/) a postupujte podle pokynů k instalaci uvedených v dokumentaci.

### Mohu převést složité dokumenty Wordu s tabulkami a obrázky do formátu Markdown?

Ano, Aspose.Words pro Javu podporuje převod složitých dokumentů Word s tabulkami, obrázky a různými formátovacími prvky do formátu Markdown. Výstup v Markdownu si můžete přizpůsobit složitosti vašeho dokumentu.

### Jak mohu pracovat s obrázky v souborech Markdown?

Chcete-li do souborů Markdown zahrnout obrázky, nastavte cestu ke složce obrázků pomocí `setImagesFolder` metoda v `MarkdownSaveOptions`Ujistěte se, že obrazové soubory jsou uloženy v zadané složce a Aspose.Words pro Javu bude s odkazy na obrázky nakládat odpovídajícím způsobem.

### Je k dispozici zkušební verze Aspose.Words pro Javu?

Ano, zkušební verzi Aspose.Words pro Javu si můžete stáhnout z webových stránek Aspose. Zkušební verze vám umožňuje otestovat možnosti knihovny před zakoupením licence.

### Kde najdu další příklady a dokumentaci?

Další příklady, dokumentaci a podrobné informace o Aspose.Words pro Javu naleznete na [dokumentace](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}