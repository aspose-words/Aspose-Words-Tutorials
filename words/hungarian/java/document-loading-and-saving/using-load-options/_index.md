---
title: Betöltési opciók használata az Aspose.Words for Java programban
linktitle: Betöltési beállítások használata
second_title: Aspose.Words Java Document Processing API
description: Betöltési opciók elsajátítása az Aspose.Words for Java programban. Testreszabhatja a dokumentumbetöltést, kezelheti a titkosítást, átalakíthatja az alakzatokat, beállíthatja a Word-verziókat és sok mást a hatékony Java-dokumentumfeldolgozás érdekében.
weight: 11
url: /hu/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betöltési opciók használata az Aspose.Words for Java programban


## Bevezetés az Aspose.Words for Java betöltési beállításainak használatába

Ebben az oktatóanyagban megvizsgáljuk, hogyan dolgozhatunk az Aspose.Words for Java betöltési beállításaival. A Betöltési beállítások lehetővé teszik a dokumentumok betöltésének és feldolgozásának testreszabását. Különféle forgatókönyvekkel foglalkozunk, beleértve a piszkos mezők frissítését, a titkosított dokumentumok betöltését, az alakzatok Office Math formátumba konvertálását, az MS Word verzió beállítását, az ideiglenes mappa megadását, a figyelmeztetések kezelését és a metafájlok PNG formátumba konvertálását. Lépésről lépésre merüljünk bele.

## Frissítse a Dirty Fields-t

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Ez a kódrészlet bemutatja, hogyan kell frissíteni a szennyezett mezőket a dokumentumban. A`setUpdateDirtyFields(true)` módszerrel biztosítják, hogy a szennyezett mezők frissítésre kerüljenek a dokumentum betöltése során.

## Töltsön be titkosított dokumentumot

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Itt egy jelszóval titkosított dokumentumot töltünk be. A`LoadOptions` A konstruktor elfogadja a dokumentum jelszavát, és a dokumentum mentésekor új jelszót is megadhat`OdtSaveOptions`.

## Alakzat konvertálása Office Math-re

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Ez a kód bemutatja, hogyan lehet alakzatokat Office Math objektummá konvertálni a dokumentumbetöltés során. A`setConvertShapeToOfficeMath(true)`módszer lehetővé teszi ezt az átalakítást.

## Állítsa be az MS Word verziót

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Megadhatja az MS Word verzióját a dokumentum betöltéséhez. Ebben a példában a verziót a Microsoft Word 2010-re állítottuk be`setMswVersion`.

## Ideiglenes mappa használata

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Az ideiglenes mappa beállításával`setTempFolder`, szabályozhatja, hogy a dokumentumfeldolgozás során hol tárolják az ideiglenes fájlokat.

## Figyelmeztetés visszahívás

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Kezelje a figyelmeztetéseket, amint azok a dokumentum betöltése közben jelentkeznek.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Ez a kód bemutatja, hogyan állíthat be egy figyelmeztető visszahívást a figyelmeztetések kezelésére a dokumentum betöltése közben. Testreszabhatja az alkalmazás viselkedését figyelmeztetések esetén.

## Konvertálja a metafájlokat PNG-re

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 A metafájlok (pl. WMF) PNG-képekké konvertálásához a dokumentum betöltése során használhatja a`setConvertMetafilesToPng(true)` módszer.

## Teljes forráskód az Aspose.Words for Java betöltési opcióinak használatához

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
	// Hozzon létre egy új LoadOptions objektumot, amely alapértelmezés szerint betölti a dokumentumokat az MS Word 2019 specifikációi szerint
	// és módosítsa a betöltési verziót Microsoft Word 2010-re.
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
		//Kinyomtatja a figyelmeztetéseket és azok részleteit, amint azok a dokumentum betöltése során felmerülnek.
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

## Következtetés

Ebben az oktatóanyagban az Aspose.Words for Java betöltési beállításaival való munka különféle szempontjaiba ástunk bele. A Betöltési beállítások kulcsfontosságú szerepet játszanak a dokumentumok betöltésének és feldolgozásának testreszabásában, lehetővé téve, hogy a dokumentumfeldolgozást az Ön egyedi igényeihez igazítsa. Foglaljuk össze az útmutatóban tárgyalt legfontosabb pontokat:

## GYIK

### Hogyan kezelhetem a figyelmeztetéseket a dokumentum betöltése közben?

 Figyelmeztető visszahívást állíthat be az alábbi módon`warningCallback()` fenti módszerrel. Testreszabhatja a`DocumentLoadingWarningCallback` osztályt, hogy az alkalmazás követelményei szerint kezelje a figyelmeztetéseket.

### Átalakíthatom az alakzatokat Office Math objektumokká a dokumentum betöltésekor?

 Igen, az alakzatokat Office Math objektumokká konvertálhatja a használatával`loadOptions.setConvertShapeToOfficeMath(true)`.

### Hogyan adhatom meg az MS Word verzióját a dokumentum betöltéséhez?

 Használat`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` az MS Word verziójának megadásához a dokumentum betöltéséhez.

###  Mi a célja a`setTempFolder` method in Load Options?

 A`setTempFolder`metódus lehetővé teszi annak a mappának a megadását, ahol a dokumentumfeldolgozás során ideiglenes fájlokat tárolnak.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
