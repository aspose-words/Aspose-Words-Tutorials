---
"description": "Tanuld meg, hogyan menthetsz dokumentumokat szövegfájlként az Aspose.Words for Java programban. Kövesd lépésről lépésre bemutatott útmutatónkat Java kódpéldákkal."
"linktitle": "Dokumentumok mentése szövegfájlként"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok mentése szövegfájlként az Aspose.Words for Java programban"
"url": "/hu/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése szövegfájlként az Aspose.Words for Java programban


## Bevezetés a dokumentumok szövegfájlként történő mentéséhez az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan menthetünk dokumentumokat szövegfájlként az Aspose.Words for Java könyvtár segítségével. Az Aspose.Words egy hatékony Java API a Word dokumentumokkal való munkához, és számos lehetőséget kínál a dokumentumok különböző formátumokban, beleértve az egyszerű szöveget is, történő mentésére. Bemutatjuk a lépések elvégzését, és közben minta Java kódot is mutatunk.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

- Java fejlesztőkészlet (JDK) telepítve van a rendszerére.
- Az Aspose.Words Java könyvtár integrálva van a projektedbe. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).
- Java programozási alapismeretek.

## 1. lépés: Dokumentum létrehozása

Egy dokumentum szövegfájlként való mentéséhez először létre kell hoznunk egy dokumentumot az Aspose.Words használatával. Íme egy egyszerű Java kódrészlet egy tartalommal rendelkező dokumentum létrehozásához:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Ebben a kódban létrehozunk egy új dokumentumot, és hozzáadunk néhány szöveget, beleértve a különböző nyelveken írt szövegeket is.

## 2. lépés: Szövegmentési beállítások megadása

Ezután meg kell adnunk a szövegmentési beállításokat, amelyek meghatározzák, hogyan kell a dokumentumot szövegfájlként menteni. Különböző beállításokat konfigurálhatunk, például kétirányú jelek hozzáadását, lista behúzását és egyebeket. Nézzünk két példát:

### 1. példa: Kétirányú jelek hozzáadása

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Ebben a példában létrehozunk egy `TxtSaveOptions` objektumot, és állítsa be a `AddBidiMarks` ingatlan `true` kétirányú jeleket tartalmazzon a szövegkimenetben.

### 2. példa: Tabulátor karakter használata lista behúzásához

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Itt úgy konfiguráljuk a mentési beállításokat, hogy tabulátor karaktert használjanak a lista behúzásához, 1-es számmal.

## 3. lépés: Mentse el a dokumentumot szövegként

Most, hogy meghatároztuk a szövegmentési beállításokat, menthetjük a dokumentumot szövegfájlként. A következő kód bemutatja, hogyan kell ezt megtenni:

```java
doc.save("output.txt", saveOptions);
```

Csere `"output.txt"` a kívánt fájlelérési úttal, ahová a szövegfájlt menteni szeretné.

## Teljes forráskód dokumentumok szövegfájlként történő mentéséhez az Aspose.Words for Java programban

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Hozz létre egy listát három behúzási szinttel.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Hozz létre egy listát három behúzási szinttel.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Következtetés

Ebben az oktatóanyagban megtanultuk, hogyan menthetünk dokumentumokat szövegfájlként az Aspose.Words for Java programban. Áttekintettük a dokumentumok létrehozásának, a szövegmentési beállítások megadásának és a dokumentum szöveges formátumban történő mentésének lépéseit. Az Aspose.Words nagyfokú rugalmasságot biztosít a dokumentumok mentése terén, lehetővé téve a kimenet testreszabását az adott igényekhez.

## GYIK

### Hogyan adhatok hozzá kétirányú jeleket a szövegkimenethez?

Kétirányú jelek hozzáadásához a szövegkimenethez, állítsa be a `AddBidiMarks` tulajdona `TxtSaveOptions` hogy `true`Például:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Testreszabhatom a lista behúzás karakterét?

Igen, testreszabhatja a lista behúzásának karakterét a konfigurálásával. `ListIndentation` tulajdona `TxtSaveOptions`Például a lista behúzásához tabulátor karaktert használhat, és a következőképpen teheti:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Alkalmas az Aspose.Words for Java többnyelvű szövegek kezelésére?

Igen, az Aspose.Words for Java alkalmas többnyelvű szövegek kezelésére. Különböző nyelveket és karakterkódolásokat támogat, így sokoldalú választás a különböző nyelveken írt dokumentumokkal való munkához.

### Hogyan férhetek hozzá további dokumentációhoz és forrásokhoz az Aspose.Words for Java-hoz?

Az Aspose.Words for Java átfogó dokumentációját és forrásait az Aspose dokumentációs weboldalán találja: [Aspose.Words Java dokumentációhoz](https://reference.aspose.com/words/java/).

### Hol tudom letölteni az Aspose.Words programot Java-hoz?

Az Aspose.Words for Java könyvtárat letöltheted az Aspose weboldaláról: [Aspose.Words letöltése Java-hoz](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}