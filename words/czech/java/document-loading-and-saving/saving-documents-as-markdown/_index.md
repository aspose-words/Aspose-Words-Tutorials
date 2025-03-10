---
title: Ukládání dokumentů jako Markdown v Aspose.Words pro Java
linktitle: Ukládání dokumentů jako Markdown
second_title: Aspose.Words Java Document Processing API
description: Naučte se převádět dokumenty aplikace Word do formátu Markdown pomocí Aspose.Words for Java. Tento podrobný průvodce popisuje zarovnání stolu, manipulaci s obrázky a další.
weight: 18
url: /cs/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů jako Markdown v Aspose.Words pro Java


## Úvod do ukládání dokumentů jako Markdown v Aspose.Words for Java

V tomto podrobném průvodci si ukážeme, jak ukládat dokumenty jako Markdown pomocí Aspose.Words for Java. Markdown je lehký značkovací jazyk, který se běžně používá pro formátování textových dokumentů. S Aspose.Words for Java můžete snadno převést své dokumenty Word do formátu Markdown. Probereme různé aspekty ukládání souborů Markdown, včetně zarovnání obsahu tabulky a manipulace s obrázky.

## Předpoklady

Než začnete, ujistěte se, že máte následující předpoklady:

- Java Development Kit (JDK) nainstalovaný ve vašem systému.
-  Aspose.Words pro knihovnu Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

## Krok 1: Vytvoření dokumentu aplikace Word

Začněme vytvořením dokumentu Word, který později převedeme do formátu Markdown. Tento dokument si můžete upravit podle svých požadavků.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte tabulku se dvěma buňkami
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Uložte dokument jako Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 V tomto příkladu vytvoříme jednoduchou tabulku se dvěma buňkami a nastavíme zarovnání odstavců uvnitř těchto buněk. Poté dokument uložíme jako Markdown pomocí`MarkdownSaveOptions`.

## Krok 2: Přizpůsobte zarovnání obsahu tabulky

Aspose.Words for Java umožňuje přizpůsobit zarovnání obsahu tabulky při ukládání jako Markdown. Obsah tabulky můžete zarovnat doleva, doprava, na střed nebo jej nechat být určen automaticky na základě prvního odstavce v každém sloupci tabulky.

Zde je návod, jak přizpůsobit zarovnání obsahu tabulky:

```java
// Nastavte zarovnání obsahu tabulky doleva
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Nastavte zarovnání obsahu tabulky doprava
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Nastavte zarovnání obsahu tabulky na střed
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Nastavit zarovnání obsahu tabulky na automatické (určeno podle prvního odstavce)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Změnou`TableContentAlignment` můžete ovládat, jak je obsah uvnitř tabulek zarovnán při převodu na Markdown.

## Krok 3: Manipulace s obrázky

 Chcete-li do dokumentu Markdown zahrnout obrázky, musíte určit složku, kde jsou obrázky umístěny. Aspose.Words for Java umožňuje nastavit složku obrázků v`MarkdownSaveOptions`.

Zde je návod, jak nastavit složku obrázků a uložit dokument s obrázky:

```java
// Vložte dokument obsahující obrázky
Document doc = new Document("document_with_images.docx");

// Nastavte cestu ke složce obrázků
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Uložte dokument s obrázky
doc.save("document_with_images.md", saveOptions);
```

 Nezapomeňte vyměnit`"document_with_images.docx"` s cestou k vašemu dokumentu Word obsahujícímu obrázky a`"images_folder/"` se skutečnou cestou ke složce, kde jsou uloženy vaše obrázky.

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
	// Umožňuje zarovnat všechny odstavce uvnitř tabulky.
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

této příručce jsme prozkoumali, jak ukládat dokumenty jako Markdown pomocí Aspose.Words for Java. Zabývali jsme se vytvořením dokumentu aplikace Word, přizpůsobením zarovnání obsahu tabulky a manipulací s obrázky v souborech Markdown. Nyní můžete efektivně převádět své dokumenty Word do formátu Markdown, takže jsou vhodné pro různé platformy pro publikování a potřeby dokumentace.

## FAQ

### Jak nainstaluji Aspose.Words for Java?

 Aspose.Words for Java lze nainstalovat zahrnutím knihovny do vašeho projektu Java. Knihovnu si můžete stáhnout z[zde](https://releases.aspose.com/words/java/) a postupujte podle pokynů k instalaci uvedených v dokumentaci.

### Mohu převést složité dokumenty Wordu s tabulkami a obrázky do Markdown?

Ano, Aspose.Words for Java podporuje převod složitých dokumentů Wordu s tabulkami, obrázky a různými prvky formátování do Markdown. Výstup Markdown můžete přizpůsobit podle složitosti dokumentu.

### Jak mohu zacházet s obrázky v souborech Markdown?

 Chcete-li zahrnout obrázky do souborů Markdown, nastavte cestu ke složce obrázků pomocí`setImagesFolder`metoda v`MarkdownSaveOptions`. Ujistěte se, že soubory obrázků jsou uloženy v určené složce, a Aspose.Words for Java podle toho zpracuje odkazy na obrázky.

### Je k dispozici zkušební verze Aspose.Words for Java?

Ano, zkušební verzi Aspose.Words for Java můžete získat z webu Aspose. Zkušební verze umožňuje vyhodnotit možnosti knihovny před zakoupením licence.

### Kde najdu další příklady a dokumentaci?

 Další příklady, dokumentaci a podrobné informace o Aspose.Words for Java naleznete na[dokumentace](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
