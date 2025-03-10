---
title: Použití možností načtení v Aspose.Words pro Java
linktitle: Pomocí možností načíst
second_title: Aspose.Words Java Document Processing API
description: Zvládnutí možností zatížení v Aspose.Words pro Java. Přizpůsobte si načítání dokumentů, zpracujte šifrování, převádějte tvary, nastavte verze aplikace Word a další pro efektivní zpracování dokumentů Java.
weight: 11
url: /cs/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití možností načtení v Aspose.Words pro Java


## Úvod do práce s možnostmi načtení v Aspose.Words pro Javu

tomto tutoriálu prozkoumáme, jak pracovat s možnostmi načtení v Aspose.Words pro Java. Možnosti načtení umožňují upravit způsob načítání a zpracování dokumentů. Pokryjeme různé scénáře, včetně aktualizace špinavých polí, načítání šifrovaných dokumentů, převod tvarů do Office Math, nastavení verze MS Word, určení dočasné složky, zpracování varování a převod metasouborů do PNG. Pojďme se ponořit krok za krokem.

## Aktualizujte špinavá pole

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Tento fragment kódu ukazuje, jak aktualizovat špinavá pole v dokumentu. The`setUpdateDirtyFields(true)` Tato metoda se používá k zajištění aktualizace nečistých polí během načítání dokumentu.

## Načíst šifrovaný dokument

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Zde načteme zašifrovaný dokument pomocí hesla. The`LoadOptions` konstruktor přijímá heslo dokumentu a můžete také zadat nové heslo při ukládání dokumentu pomocí`OdtSaveOptions`.

## Převést tvar na Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Tento kód ukazuje, jak převést obrazce na objekty Office Math během načítání dokumentu. The`setConvertShapeToOfficeMath(true)`metoda tuto konverzi umožňuje.

## Nastavte verzi MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Můžete určit verzi MS Word pro načítání dokumentu. V tomto příkladu jsme nastavili verzi na Microsoft Word 2010 pomocí`setMswVersion`.

## Použijte dočasnou složku

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Nastavením dočasné složky pomocí`setTempFolder`, můžete řídit, kam se ukládají dočasné soubory během zpracování dokumentu.

## Varování zpětné volání

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // S varováními zacházejte tak, jak se objeví během zavádění dokumentu.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Tento kód ukazuje, jak nastavit zpětné volání upozornění pro zpracování upozornění během načítání dokumentu. Můžete přizpůsobit chování vaší aplikace, když se objeví varování.

## Převést metasoubory do PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Chcete-li během načítání dokumentu převést metasoubory (např. WMF) na obrázky PNG, můžete použít`setConvertMetafilesToPng(true)` metoda.

## Kompletní zdrojový kód pro práci s možnostmi načtení v Aspose.Words pro Javu

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
	// Vytvořte nový objekt LoadOptions, který bude standardně načítat dokumenty podle specifikace MS Word 2019
	// a změňte verzi načítání na Microsoft Word 2010.
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
		//Vytiskne varování a jejich podrobnosti tak, jak se objeví během zavádění dokumentu.
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

V tomto tutoriálu jsme se ponořili do různých aspektů práce s možnostmi načtení v Aspose.Words pro Java. Možnosti načítání hrají klíčovou roli při přizpůsobení způsobu načítání a zpracování dokumentů, což vám umožňuje přizpůsobit zpracování dokumentů vašim konkrétním potřebám. Shrňme si klíčové body obsažené v této příručce:

## FAQ

### Jak mohu zvládnout varování během načítání dokumentu?

 Můžete nastavit varovné zpětné volání, jak je znázorněno na`warningCallback()` metoda výše. Přizpůsobte si`DocumentLoadingWarningCallback` třídy pro zpracování varování podle požadavků vaší aplikace.

### Mohu při načítání dokumentu převést tvary na objekty Office Math?

 Ano, tvary můžete převést na objekty Office Math pomocí`loadOptions.setConvertShapeToOfficeMath(true)`.

### Jak určím verzi MS Word pro načítání dokumentů?

 Použití`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` specifikovat verzi MS Word pro načítání dokumentu.

###  Jaký je účel`setTempFolder` method in Load Options?

 The`setTempFolder`umožňuje určit složku, do které se ukládají dočasné soubory během zpracování dokumentu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
