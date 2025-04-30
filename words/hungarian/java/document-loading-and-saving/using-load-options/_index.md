---
"description": "Aspose.Words betöltési beállításainak elsajátítása Java-hoz. Dokumentumbetöltés testreszabása, titkosítás kezelése, alakzatok konvertálása, Word-verziók beállítása és sok más a hatékony Java-dokumentumfeldolgozáshoz."
"linktitle": "Betöltési beállítások használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Betöltési opciók használata az Aspose.Words Java-ban"
"url": "/hu/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betöltési opciók használata az Aspose.Words Java-ban


## Bevezetés a betöltési opciók használatába az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan használhatók a Betöltési beállítások az Aspose.Words for Java programban. A Betöltési beállítások lehetővé teszik a dokumentumok betöltésének és feldolgozásának testreszabását. Különböző forgatókönyveket fogunk áttekinteni, beleértve a piszkos mezők frissítését, a titkosított dokumentumok betöltését, az alakzatok Office Math formátumba konvertálását, az MS Word verziójának beállítását, egy ideiglenes mappa megadását, a figyelmeztetések kezelését és a metafájlok PNG formátumba konvertálását. Nézzük meg lépésről lépésre.

## Piszkos mezők frissítése

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Ez a kódrészlet bemutatja, hogyan frissíthetők a „piszkos mezők” egy dokumentumban. `setUpdateDirtyFields(true)` A metódus biztosítja, hogy a piszkos mezők frissüljenek a dokumentum betöltése során.

## Titkosított dokumentum betöltése

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Itt egy jelszóval titkosított dokumentumot töltünk be. `LoadOptions` A konstruktor elfogadja a dokumentum jelszavát, és a dokumentum mentésekor új jelszót is megadhat a használatával. `OdtSaveOptions`.

## Alakzat konvertálása Office Math formátumba

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Ez a kód bemutatja, hogyan lehet alakzatokat Office Math objektumokká konvertálni a dokumentum betöltése során. `setConvertShapeToOfficeMath(true)` metódus teszi lehetővé ezt az átalakítást.

## MS Word verzió beállítása

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

Megadhatja az MS Word verzióját a dokumentum betöltéséhez. Ebben a példában a verziót Microsoft Word 2010-re állítottuk be a következő használatával: `setMswVersion`.

## Ideiglenes mappa használata

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Az ideiglenes mappa beállításával a következő használatával: `setTempFolder`, szabályozhatja, hogy a dokumentumfeldolgozás során hol tárolódnak az ideiglenes fájlok.

## Figyelmeztetés visszahívása

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // A dokumentum betöltése során felmerülő figyelmeztetéseket azonnal kezelni kell.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Ez a kód bemutatja, hogyan állíthat be egy figyelmeztető visszahívást a dokumentum betöltése közbeni figyelmeztetések kezelésére. Testreszabhatja az alkalmazás viselkedését figyelmeztetések esetén.

## Metafájlok konvertálása PNG-vé

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

A metafájlok (pl. WMF) PNG képekké konvertálásához a dokumentum betöltése során használhatja a `setConvertMetafilesToPng(true)` módszer.

## Teljes forráskód a betöltési opciók használatához az Aspose.Words Java-ban

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
	// Hozz létre egy új LoadOptions objektumot, amely alapértelmezés szerint az MS Word 2019 specifikációjának megfelelően tölti be a dokumentumokat.
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
		// Kinyomtatja a figyelmeztetéseket és azok részleteit, amint azok a dokumentum betöltése során felmerülnek.
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

Ebben az oktatóanyagban az Aspose.Words for Java programban a betöltési beállításokkal való munka különböző aspektusait vizsgáltuk. A betöltési beállítások kulcsszerepet játszanak a dokumentumok betöltésének és feldolgozásának testreszabásában, lehetővé téve a dokumentumfeldolgozás testreszabását az Ön igényeihez. Foglaljuk össze az útmutatóban tárgyalt főbb pontokat:

## GYIK

### Hogyan kezelhetem a figyelmeztetéseket a dokumentum betöltése során?

Beállíthat egy figyelmeztető visszahívást, ahogy az a képen látható. `warningCallback()` a fenti módszerrel. Szabja testre a `DocumentLoadingWarningCallback` osztály a figyelmeztetések kezelésére az alkalmazás követelményeinek megfelelően.

### Konvertálhatok alakzatokat Office Math objektumokká egy dokumentum betöltésekor?

Igen, az alakzatokat Office Math objektumokká alakíthatja a következővel: `loadOptions.setConvertShapeToOfficeMath(true)`.

### Hogyan adhatom meg az MS Word verzióját a dokumentum betöltéséhez?

Használat `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` a dokumentum betöltéséhez használt MS Word verzió megadásához.

### Mi a célja a `setTempFolder` metódus a Betöltési beállításokban?

A `setTempFolder` A metódus lehetővé teszi annak a mappának a megadását, ahol az ideiglenes fájlok tárolódnak a dokumentumfeldolgozás során.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}