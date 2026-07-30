---
date: 2025-12-27
description: Tudja meg, hogyan állíthatja be a LoadOptions-t az Aspose.Words for Java-ban,
  beleértve a temp mappa megadását, a Word verzió beállítását, a metafájlok PNG-re
  konvertálását és a forma matematikává alakítását a rugalmas dokumentumfeldolgozáshoz.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Hogyan állítsuk be a LoadOptions-t az Aspose.Words for Java-ban
url: /hu/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állítsuk be a LoadOptions-t az Aspose.Words for Java-ban

Ebben az útmutatóban végigvezetjük, **hogyan állítsuk be a LoadOptions-t** különféle valós életbeli helyzetekben az Aspose.Words for Java használata során. A LoadOptions finomhangolt vezérlést biztosít a dokumentum megnyitásának módja felett – akár frissíteni kell a piszkos mezőket, titkosított fájlokkal dolgozni, alakzatokat Office Math-ra konvertálni, vagy megadni a könyvtárnak, hogy hol tárolja az ideiglenes adatokat. A végére képes lesz testre szabni a betöltési viselkedést, hogy pontosan megfeleljen az alkalmazás követelményeinek.

## Gyors válaszok
- **Mi az a LoadOptions?** Egy konfigurációs objektum, amely befolyásolja, hogyan tölti be az Aspose.Words a dokumentumot.  
- **Frissíthetek mezőket betöltés közben?** Igen – állítsa be a `setUpdateDirtyFields(true)`-t.  
- **Hogyan nyithatok meg jelszóval védett fájlt?** Adja át a jelszót a `LoadOptions` konstruktorának.  
- **Lehet-e megváltoztatni az ideiglenes mappát?** Használja a `setTempFolder("path")`-t.  
- **Melyik metódus konvertálja az alakzatokat Office Math-ra?** `setConvertShapeToOfficeMath(true)`.

## Miért használjuk a LoadOptions-t?
A LoadOptions lehetővé teszi, hogy elkerülje a betöltés utáni feldolgozási lépéseket, csökkentse a memóriahasználatot, és biztosítsa, hogy a dokumentum pontosan úgy legyen értelmezve, ahogy szükséges. Például a metafájlok PNG-re konvertálása betöltés közben megakadályozza a későbbi raszterizálási problémákat, és az MS Word verzió megadása segít megőrizni a megjelenés pontosságát régi fájlok esetén.

## Előkövetelmények
- Java 17 vagy újabb  
- Aspose.Words for Java (legújabb verzió)  
- Érvényes Aspose licenc a termeléshez  

## Lépésről‑lépésre útmutató

### Piszkos mezők frissítése

Ha egy dokumentum olyan mezőket tartalmaz, amelyeket szerkesztettek, de nem frissítettek, megmondhatja az Aspose.Words-nak, hogy automatikusan frissítse őket betöltés közben.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*A `setUpdateDirtyFields(true)` hívás biztosítja, hogy minden piszkos mező újraszámításra kerüljön, amint a dokumentum megnyílik.*

### Titkosított dokumentum betöltése

Ha a forrásfájl jelszóval védett, adja meg a jelszót a `LoadOptions` példány létrehozásakor. Új jelszót is beállíthat, amikor más formátumba ment.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Alakzat konvertálása Office Math-ra

Néhány régi dokumentum egyenleteket rajz alakzatokként tárol. Ennek az opciónak az engedélyezése az alakzatokat natív Office Math objektumokká konvertálja, amelyek később könnyebben szerkeszthetők.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS Word verzió beállítása

A cél Word verzió megadása segíti a könyvtárat a megfelelő megjelenítési szabályok kiválasztásában, különösen régi fájlformátumok esetén.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Ideiglenes mappa használata

Nagy dokumentumok ideiglenes fájlokat generálhatnak (pl. képek kicsomagolásakor). Ezeket a fájlokat egy általad választott mappába irányíthatod, ami hasznos elszigetelt környezetekben.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Figyelmeztető visszahívás

Betöltés közben az Aspose.Words figyelmeztetéseket generálhat (pl. nem támogatott funkciók). Egy visszahívás megvalósítása lehetővé teszi, hogy naplózd vagy reagálj ezekre az eseményekre.

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

### Metafájlok konvertálása PNG-re

A WMF-hez hasonló metafájlok betöltés közben PNG-re raszterizálhatók, biztosítva a konzisztens megjelenítést a különböző platformokon.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Teljes forráskód a Load Options használatához az Aspose.Words for Java-ban

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

## Gyakori felhasználási esetek és tippek

- **Kötegelt konverziós csővezetékek** – Kombináld a `setTempFolder`-t egy ütemezett feladattal, hogy több száz fájlt dolgozz fel anélkül, hogy megtöltenéd a rendszer ideiglenes könyvtárát.  
- **Régi dokumentumok migrációja** – Használd a `setMswVersion`-t a `setConvertShapeToOfficeMath`-val együtt, hogy a régi mérnöki dokumentumokat modern formátumba hozd, miközben megőrzöd az egyenleteket.  
- **Biztonságos dokumentumkezelés** – Párosítsd a `loadEncryptedDocument`-et az `OdtSaveOptions`-szal, hogy új jelszóval újra titkosítsd a fájlokat más formátumban.  

## Gyakran ismételt kérdések

**K: Hogyan kezelhetem a figyelmeztetéseket a dokumentum betöltése közben?**  
V: Implementálj egy egyedi `IWarningCallback`-et (ahogy a *Figyelmeztető visszahívás* példában látható) és regisztráld a `loadOptions.setWarningCallback(...)`-val. Ez lehetővé teszi, hogy a figyelmeztetés súlyossága alapján naplózd, figyelmen kívül hagyd vagy megszakítsd a folyamatot.

**K: Konvertálhatok alakzatokat Office Math objektumokká a dokumentum betöltésekor?**  
V: Igen – hívd meg a `loadOptions.setConvertShapeToOfficeMath(true)`-t a `Document` létrehozása előtt. A könyvtár automatikusan helyettesíti a kompatibilis alakzatokat natív Office Math objektumokkal.

**K: Hogyan adhatom meg az MS Word verziót a dokumentum betöltéséhez?**  
V: Használd a `loadOptions.setMswVersion(MsWordVersion.WORD_2010)`-t (vagy bármely más enum értéket), hogy megmond a Aspose.Words-nak, melyik Word verzió megjelenítési szabályait alkalmazza.

**K: Mi a `setTempFolder` metódus célja a LoadOptions-ban?**  
V: Ez irányítja a betöltés során keletkező összes ideiglenes fájlt (például kicsomagolt képeket) egy általad ellenőrzött mappába, ami elengedhetetlen a korlátozott rendszer‑temp könyvtárakkal rendelkező környezetekben.

**K: Lehetséges a metafájlok, például a WMF PNG-re konvertálása betöltés közben?**  
V: Teljesen – engedélyezd a `loadOptions.setConvertMetafilesToPng(true)`-val. Ez biztosítja, hogy a raszter képek PNG-ként legyenek tárolva, javítva a kompatibilitást a modern megjelenítőkkel.

## Következtetés

Áttekintettük a **LoadOptions beállításának** alapvető technikáit az Aspose.Words for Java-ban, a piszkos mezők frissítésétől a titkosított fájlok kezelésén, az alakzatok konvertálásán, a Word verzió megadásán, az ideiglenes tárolás irányításán és még sok máson át. Ezeknek az opcióknak a kihasználásával robusztus, nagy teljesítményű dokumentumfeldolgozó csővezetékeket építhetsz, amelyek alkalmazkodnak a különféle bemeneti helyzetekhez.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}