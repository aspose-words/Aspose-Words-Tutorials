---
title: Dokumentumok mentése Markdown néven az Aspose.Words for Java programban
linktitle: Dokumentumok mentése Markdown néven
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan konvertálhat Word dokumentumokat Markdown formátumba az Aspose.Words for Java segítségével. Ez a lépésenkénti útmutató a táblázat igazítását, a képkezelést és egyebeket ismerteti.
weight: 18
url: /hu/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése Markdown néven az Aspose.Words for Java programban


## Bevezetés a dokumentumok jelölésként történő mentésébe az Aspose.Words for Java programban

Ebben a lépésenkénti útmutatóban bemutatjuk, hogyan lehet dokumentumokat Markdown néven menteni az Aspose.Words for Java használatával. A Markdown egy könnyű jelölőnyelv, amelyet általában szöveges dokumentumok formázására használnak. Az Aspose.Words for Java segítségével egyszerűen konvertálhatja Word-dokumentumait Markdown formátumba. Kitérünk a Markdown fájlok mentésének különböző szempontjaira, beleértve a táblázattartalom igazítását és a képek kezelését.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

- Java Development Kit (JDK) telepítve a rendszerére.
-  Aspose.Words for Java könyvtár. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

## 1. lépés: Word-dokumentum létrehozása

Kezdjük egy Word dokumentum létrehozásával, amelyet később Markdown formátumba konvertálunk. Ezt a dokumentumot igényei szerint testreszabhatja.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy táblázatot két cellával
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Mentse el a dokumentumot Markdown néven
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 Ebben a példában egy egyszerű táblázatot hozunk létre két cellával, és beállítjuk a bekezdések igazítását ezeken a cellákon belül. Ezután a dokumentumot Markdown néven mentjük a`MarkdownSaveOptions`.

## 2. lépés: A táblázattartalom igazításának testreszabása

Az Aspose.Words for Java lehetővé teszi a táblázattartalom igazításának testreszabását Markdownként történő mentéskor. A táblázat tartalmát igazíthatja balra, jobbra, középre, vagy hagyhatja, hogy a táblázat minden oszlopának első bekezdése alapján automatikusan meghatározza.

A táblázattartalom igazításának testreszabása a következőképpen történik:

```java
// Állítsa a táblázat tartalmának igazítását balra
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Állítsa a táblázat tartalmának igazítását jobbra
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Állítsa a táblázat tartalmának igazítását középre
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Állítsa a táblázattartalom igazítását automatikusra (az első bekezdés határozza meg)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Azáltal, hogy megváltoztatja a`TableContentAlignment` tulajdonsággal szabályozhatja, hogy a táblákon belüli tartalom hogyan igazodjon a Markdown-ba való konvertáláskor.

## 3. lépés: Képek kezelése

 Ha képeket szeretne felvenni a Markdown dokumentumba, meg kell adnia a mappát, ahol a képek találhatók. Az Aspose.Words for Java lehetővé teszi a képek mappájának beállítását a`MarkdownSaveOptions`.

A következőképpen állíthatja be a képek mappát, és mentheti el a dokumentumot képekkel:

```java
// Töltsön be képeket tartalmazó dokumentumot
Document doc = new Document("document_with_images.docx");

// Állítsa be a képek mappa elérési útját
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Mentse el a dokumentumot képekkel
doc.save("document_with_images.md", saveOptions);
```

 Ügyeljen arra, hogy cserélje ki`"document_with_images.docx"` a képeket tartalmazó Word-dokumentum elérési útjával és`"images_folder/"` a mappa tényleges elérési útjával, ahol a képeket tárolják.

## Teljes forráskód dokumentumok mentéséhez Markdown-ként az Aspose.Words for Java-ban

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
	// A táblázaton belüli összes bekezdést igazítandóvá teszi.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Az igazítás ebben az esetben a megfelelő táblázatoszlop első bekezdéséből történik.
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

Ebben az útmutatóban megvizsgáltuk, hogyan lehet dokumentumokat Markdown néven menteni az Aspose.Words for Java használatával. Kitértünk egy Word-dokumentum létrehozására, a táblázattartalom-igazítás testreszabására és a képek Markdown-fájlokban való kezelésére. Mostantól hatékonyan konvertálhatja Word-dokumentumait Markdown formátumba, így alkalmassá téve azokat a különböző közzétételi platformokra és dokumentációs igényekre.

## GYIK

### Hogyan telepíthetem az Aspose.Words for Java programot?

 Az Aspose.Words for Java úgy telepíthető, hogy a könyvtárat belefoglalja a Java projektbe. A könyvtárat innen töltheti le[itt](https://releases.aspose.com/words/java/) és kövesse a dokumentációban található telepítési utasításokat.

### Konvertálhatok összetett Word-dokumentumokat táblázatokkal és képekkel Markdown-ba?

Igen, az Aspose.Words for Java támogatja a táblázatokat, képeket és különféle formázási elemeket tartalmazó összetett Word-dokumentumok Markdown-ba való konvertálását. Testreszabhatja a Markdown kimenetet a dokumentum összetettségének megfelelően.

### Hogyan kezelhetem a Markdown fájlokban lévő képeket?

 Ha képeket szeretne felvenni a Markdown-fájlokba, állítsa be a képek mappa elérési útját a segítségével`setImagesFolder`módszer be`MarkdownSaveOptions`. Győződjön meg arról, hogy a képfájlok a megadott mappában vannak tárolva, és az Aspose.Words for Java ennek megfelelően kezeli a képhivatkozásokat.

### Elérhető az Aspose.Words for Java próbaverziója?

Igen, beszerezheti az Aspose.Words for Java próbaverzióját az Aspose webhelyéről. A próbaverzió lehetővé teszi a könyvtár képességeinek felmérését a licenc megvásárlása előtt.

### Hol találok további példákat és dokumentációt?

 További példákért, dokumentációért és részletes információkért az Aspose.Words for Java-ról látogassa meg a[dokumentáció](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
