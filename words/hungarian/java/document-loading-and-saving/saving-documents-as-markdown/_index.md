---
"description": "Tanuld meg, hogyan konvertálhatsz Word dokumentumokat Markdown formátumba az Aspose.Words for Java segítségével. Ez a lépésről lépésre szóló útmutató a táblázatok igazítását, a képkezelést és egyebeket ismerteti."
"linktitle": "Dokumentumok mentése Markdown formátumban"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok mentése Markdown formátumban az Aspose.Words for Java programban"
"url": "/hu/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése Markdown formátumban az Aspose.Words for Java programban


## Bevezetés a dokumentumok Markdown formátumban történő mentéséhez az Aspose.Words for Java programban

Ebben a lépésről lépésre bemutatjuk, hogyan menthet dokumentumokat Markdown formátumban az Aspose.Words for Java segítségével. A Markdown egy könnyűsúlyú jelölőnyelv, amelyet általában szöveges dokumentumok formázására használnak. Az Aspose.Words for Java segítségével könnyedén konvertálhatja Word-dokumentumait Markdown formátumba. Áttekintjük a Markdown-fájlok mentésének különböző aspektusait, beleértve a táblázatok tartalmának igazítását és a képek kezelését.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- Java fejlesztőkészlet (JDK) telepítve van a rendszerére.
- Aspose.Words Java könyvtárhoz. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).

## 1. lépés: Word-dokumentum létrehozása

Kezdjük egy Word-dokumentum létrehozásával, amelyet később Markdown formátumba konvertálunk. Ezt a dokumentumot az igényeid szerint testreszabhatod.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Két cellás táblázat beszúrása
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Dokumentum mentése Markdown néven
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Ebben a példában létrehozunk egy egyszerű táblázatot két cellával, és beállítjuk a cellákon belüli bekezdések igazítását. Ezután Markdown néven mentjük a dokumentumot a következő használatával: `MarkdownSaveOptions`.

## 2. lépés: A táblázat tartalmának igazításának testreszabása

Az Aspose.Words for Java lehetővé teszi a táblázat tartalmának igazításának testreszabását Markdown formátumban történő mentéskor. A táblázat tartalmát balra, jobbra, középre igazíthatja, vagy hagyhatja, hogy a program automatikusan határozza meg az egyes táblázatoszlopok első bekezdése alapján.

A táblázat tartalmának igazítását a következőképpen szabhatja testre:

```java
// Táblázat tartalmának balra igazítása
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Táblázat tartalmának jobbra igazítása
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Táblázat tartalmának középre igazítása
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// A táblázat tartalmának igazítását állítsa automatikusra (az első bekezdés alapján)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

A megváltoztatásával `TableContentAlignment` tulajdonsággal szabályozhatja, hogy a táblázatokban lévő tartalom hogyan legyen igazítva a Markdown formátumba konvertáláskor.

## 3. lépés: Képek kezelése

Képek Markdown-dokumentumba való felvételéhez meg kell adnia azt a mappát, ahol a képek találhatók. Az Aspose.Words for Java lehetővé teszi a képek mappa beállítását a `MarkdownSaveOptions`.

Így állíthatja be a képek mappáját és mentheti el a dokumentumot képekkel:

```java
// Töltsön be egy képet tartalmazó dokumentumot
Document doc = new Document("document_with_images.docx");

// Állítsa be a képek mappa elérési útját
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Dokumentum mentése képekkel
doc.save("document_with_images.md", saveOptions);
```

Mindenképpen cserélje ki `"document_with_images.docx"` a képeket és a Word-dokumentumod elérési útjával `"images_folder/"` a képek tárolására szolgáló mappa tényleges elérési útjával.

## Teljes forráskód dokumentumok Markdown formátumban történő mentéséhez Aspose.Words for Java-ban

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
	// A táblázaton belüli összes bekezdést igazítja.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Az igazítás ebben az esetben a megfelelő táblázatoszlop első bekezdésétől lesz elvégezve.
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

## Következtetés

Ebben az útmutatóban azt vizsgáltuk meg, hogyan menthetünk dokumentumokat Markdown formátumban az Aspose.Words for Java segítségével. Áttekintettük a Word-dokumentumok létrehozását, a táblázatok tartalmának igazítását és a képek kezelését a Markdown-fájlokban. Mostantól hatékonyan konvertálhatja Word-dokumentumait Markdown-formátumba, így azok különböző közzétételi platformokhoz és dokumentációs igényekhez igazíthatók.

## GYIK

### Hogyan telepíthetem az Aspose.Words-öt Java-hoz?

Az Aspose.Words for Java telepíthető a könyvtár Java projektbe való beillesztésével. A könyvtárat innen töltheti le: [itt](https://releases.aspose.com/words/java/) és kövesse a dokumentációban található telepítési utasításokat.

### Átalakíthatok összetett, táblázatokat és képeket tartalmazó Word-dokumentumokat Markdown formátumba?

Igen, az Aspose.Words for Java támogatja az összetett, táblázatokat, képeket és különféle formázási elemeket tartalmazó Word-dokumentumok Markdown formátumba konvertálását. A Markdown kimenetet a dokumentum összetettségének megfelelően testreszabhatja.

### Hogyan kezelhetem a képeket a Markdown fájlokban?

Képek Markdown-fájlokba való felvételéhez állítsa be a képek mappa elérési útját a `setImagesFolder` módszer `MarkdownSaveOptions`Győződjön meg róla, hogy a képfájlok a megadott mappában vannak tárolva, és az Aspose.Words for Java ennek megfelelően fogja kezelni a képhivatkozásokat.

### Van elérhető próbaverzió az Aspose.Words-nek Java-hoz?

Igen, letöltheti az Aspose.Words for Java próbaverzióját az Aspose weboldaláról. A próbaverzió lehetővé teszi a könyvtár képességeinek kiértékelését a licenc megvásárlása előtt.

### Hol találok további példákat és dokumentációt?

További példákért, dokumentációért és az Aspose.Words for Java részletes információiért kérjük, látogassa meg a következőt: [dokumentáció](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}