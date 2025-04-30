---
"description": "Zvládnutí možností načítání v Aspose.Words pro Javu. Přizpůsobení načítání dokumentů, zpracování šifrování, převod tvarů, nastavení verzí Wordu a další pro efektivní zpracování dokumentů v Javě."
"linktitle": "Použití možností načítání"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Použití možností načítání v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použití možností načítání v Aspose.Words pro Javu


## Úvod do práce s možnostmi načítání v Aspose.Words pro Javu

V tomto tutoriálu se podíváme na práci s možnostmi načítání v Aspose.Words pro Javu. Možnosti načítání vám umožňují přizpůsobit způsob načítání a zpracování dokumentů. Probereme různé scénáře, včetně aktualizace neplatných polí, načítání šifrovaných dokumentů, převodu tvarů do formátu Office Math, nastavení verze MS Word, určení dočasné složky, zpracování varování a převodu metasouborů do formátu PNG. Pojďme se do toho ponořit krok za krokem.

## Aktualizace nečistých polí

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Tento úryvek kódu ukazuje, jak aktualizovat neplatná pole v dokumentu. `setUpdateDirtyFields(true)` Metoda se používá k zajištění aktualizace nečistých polí během načítání dokumentu.

## Načíst šifrovaný dokument

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Zde načteme zašifrovaný dokument pomocí hesla. `LoadOptions` konstruktor přijímá heslo dokumentu a při ukládání dokumentu můžete také zadat nové heslo pomocí `OdtSaveOptions`.

## Převod tvaru do matematických formátů Office

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Tento kód ukazuje, jak převést tvary na objekty Office Math během načítání dokumentu. `setConvertShapeToOfficeMath(true)` metoda umožňuje tuto konverzi.

## Nastavení verze MS Wordu

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

Pro načítání dokumentů můžete zadat verzi MS Word. V tomto příkladu jsme nastavili verzi na Microsoft Word 2010 pomocí `setMswVersion`.

## Použít dočasnou složku

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Nastavením dočasné složky pomocí `setTempFolder`, můžete ovládat, kam se během zpracování dokumentů ukládají dočasné soubory.

## Zpětné volání varování

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Zpracovávejte varování, jakmile se objeví během načítání dokumentu.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Tento kód ukazuje, jak nastavit zpětné volání varování pro zpracování varování během načítání dokumentu. Chování aplikace můžete přizpůsobit, když dojde k varování.

## Převod metasouborů do PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

Pro převod metasouborů (např. WMF) na obrázky PNG během načítání dokumentu můžete použít `setConvertMetafilesToPng(true)` metoda.

## Kompletní zdrojový kód pro práci s možnostmi načítání v Aspose.Words pro Javu

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Vytvořte nový objekt LoadOptions, který bude standardně načítat dokumenty dle specifikace MS Word 2019.
	// a změňte načítací verzi na Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Vytiskne varování a jejich podrobnosti, jakmile se objeví během načítání dokumentu.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Závěr

V tomto tutoriálu jsme se ponořili do různých aspektů práce s možnostmi načítání v Aspose.Words pro Javu. Možnosti načítání hrají klíčovou roli při přizpůsobení způsobu načítání a zpracování dokumentů, což vám umožňuje přizpůsobit zpracování dokumentů vašim specifickým potřebám. Shrňme si klíčové body, které tento průvodce zahrnuje:

## Často kladené otázky

### Jak mohu řešit varování během načítání dokumentu?

Zpětné volání varování můžete nastavit, jak je znázorněno na `warningCallback()` výše uvedenou metodu. Přizpůsobte `DocumentLoadingWarningCallback` třída pro zpracování varování podle požadavků vaší aplikace.

### Mohu při načítání dokumentu převést tvary na objekty Office Math?

Ano, tvary můžete převést na objekty Office Math pomocí `loadOptions.setConvertShapeToOfficeMath(true)`.

### Jak určím verzi MS Wordu pro načítání dokumentů?

Použití `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` pro určení verze MS Word pro načítání dokumentů.

### Jaký je účel `setTempFolder` metoda v Možnostech načtení?

Ten/Ta/To `setTempFolder` Metoda umožňuje zadat složku, kam se ukládají dočasné soubory během zpracování dokumentu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}