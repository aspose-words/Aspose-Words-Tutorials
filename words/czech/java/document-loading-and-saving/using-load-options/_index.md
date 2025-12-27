---
date: 2025-12-27
description: Naučte se, jak nastavit LoadOptions v Aspose.Words pro Javu, včetně toho,
  jak zadat dočasnou složku, nastavit verzi Wordu, převést metafily na PNG a převést
  tvar na matematiku pro flexibilní zpracování dokumentů.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Jak nastavit LoadOptions v Aspose.Words pro Java
url: /cs/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit LoadOptions v Aspose.Words pro Java

V tomto tutoriálu projdeme **jak nastavit LoadOptions** pro různé reálné scénáře při práci s Aspose.Words pro Java. LoadOptions vám poskytují jemnou kontrolu nad tím, jak je dokument otevřen – ať už potřebujete aktualizovat špinavá pole, pracovat s šifrovanými soubory, převádět tvary na Office Math, nebo říct knihovně, kde má ukládat dočasná data. Na konci budete schopni přizpůsobit chování načítání tak, aby přesně vyhovovalo požadavkům vaší aplikace.

## Rychlé odpovědi
- **Co je LoadOptions?** Konfigurační objekt, který ovlivňuje, jak Aspose.Words načítá dokument.  
- **Mohu aktualizovat pole při načítání?** Ano—nastavte `setUpdateDirtyFields(true)`.  
- **Jak otevřu soubor chráněný heslem?** Předáte heslo konstruktoru `LoadOptions`.  
- **Je možné změnit dočasnou složku?** Použijte `setTempFolder("path")`.  
- **Která metoda převádí tvary na Office Math?** `setConvertShapeToOfficeMath(true)`.

## Proč používat LoadOptions?
LoadOptions vám umožňují vyhnout se krokům zpracování po načtení, snížit spotřebu paměti a zajistit, aby byl dokument interpretován přesně podle vašich potřeb. Například převod metafilek na PNG během načítání zabraňuje pozdějším problémům s rasterizací a určení verze MS Word pomáhá udržet věrnost rozvržení při práci se staršími soubory.

## Předpoklady
- Java 17 nebo novější
- Aspose.Words pro Java (nejnovější verze)
- Platná licence Aspose pro produkční použití

## Průvodce krok za krokem

### Aktualizace špinavých polí

Když dokument obsahuje pole, která byla upravena, ale neaktualizována, můžete Aspose.Words říci, aby je během načítání automaticky aktualizovalo.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Volání `setUpdateDirtyFields(true)` zajistí, že všechna špinavá pole budou přepočítána hned po otevření dokumentu.*

### Načtení šifrovaného dokumentu

Pokud je váš zdrojový soubor chráněn heslem, poskytněte heslo při vytváření instance `LoadOptions`. Můžete také nastavit nové heslo při ukládání do jiného formátu.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Převod tvaru na Office Math

Některé starší dokumenty ukládají rovnice jako kreslené tvary. Povolení této možnosti převádí tyto tvary na nativní objekty Office Math, které je později snadnější upravovat.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Nastavení verze MS Word

Určení cílové verze Word pomáhá knihovně vybrat správná pravidla vykreslování, zejména při práci se staršími formáty souborů.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Použití dočasné složky

Velké dokumenty mohou generovat dočasné soubory (např. při extrahování obrázků). Můžete tyto soubory nasměrovat do vámi zvolené složky, což je užitečné v sandboxovaných prostředích.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback pro varování

Během načítání může Aspose.Words vyvolat varování (např. nepodporované funkce). Implementace callbacku vám umožní tato varování zaznamenat nebo na ně reagovat.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Převod metafilek na PNG

Metafily jako WMF lze během načítání rasterizovat do PNG, což zajišťuje konzistentní vykreslování napříč platformami.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Kompletní zdrojový kód pro práci s Load Options v Aspose.Words pro Java

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## Běžné případy použití a tipy
- **Dávkové konverzní pipeline** – Kombinujte `setTempFolder` s naplánovanou úlohou pro zpracování stovek souborů, aniž byste zaplnili systémový dočasný adresář.  
- **Migrace starých dokumentů** – Použijte `setMswVersion` spolu s `setConvertShapeToOfficeMath`, abyste staré technické dokumenty převedli do moderního formátu při zachování rovnic.  
- **Bezpečná manipulace s dokumenty** – Spojte `loadEncryptedDocument` s `OdtSaveOptions` pro opětovné šifrování souborů novým heslem v jiném formátu.  

## Často kladené otázky

**Q: Jak mohu během načítání dokumentu zpracovávat varování?**  
A: Implementujte vlastní `IWarningCallback` (jak je ukázáno v příkladu *Callback pro varování*) a zaregistrujte jej pomocí `loadOptions.setWarningCallback(...)`. To vám umožní zaznamenávat, ignorovat nebo přerušit na základě závažnosti varování.

**Q: Mohu při načítání dokumentu převádět tvary na objekty Office Math?**  
A: Ano—před vytvořením `Document` zavolejte `loadOptions.setConvertShapeToOfficeMath(true)`. Knihovna automaticky nahradí kompatibilní tvary nativními objekty Office Math.

**Q: Jak specifikuji verzi MS Word pro načítání dokumentu?**  
A: Použijte `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (nebo jinou hodnotu výčtu), aby Aspose.Words vědělo, jaká pravidla vykreslování konkrétní verze Wordu má použít.

**Q: Jaký je účel metody `setTempFolder` v LoadOptions?**  
A: Směřuje všechny dočasné soubory generované během načítání (např. extrahované obrázky) do složky, kterou ovládáte, což je nezbytné v prostředích s omezenými systémovými dočasnými adresáři.

**Q: Je možné během načítání převést metafily jako WMF na PNG?**  
A: Rozhodně—povolte to pomocí `loadOptions.setConvertMetafilesToPng(true)`. Tím zajistíte, že rastrové obrázky budou uloženy jako PNG, což zlepšuje kompatibilitu s moderními prohlížeči.

## Závěr

Probrali jsme základní techniky **jak nastavit LoadOptions** v Aspose.Words pro Java, od aktualizace špinavých polí po práci s šifrovanými soubory, převod tvarů, určení verze Wordu, směrování dočasného úložiště a další. Využitím těchto možností můžete vytvořit robustní, výkonné pipeline pro zpracování dokumentů, které se přizpůsobí široké škále vstupních scénářů.

---

**Poslední aktualizace:** 2025-12-27  
**Testováno s:** Aspose.Words for Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}