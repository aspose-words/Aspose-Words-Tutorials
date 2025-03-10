---
title: Dokumentumok mentése szöveges fájlként az Aspose.Words for Java programban
linktitle: Dokumentumok mentése szöveges fájlként
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan menthet el dokumentumokat szöveges fájlként az Aspose.Words for Java programban. Kövesse lépésenkénti útmutatónkat Java kódpéldákkal.
weight: 24
url: /hu/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése szöveges fájlként az Aspose.Words for Java programban


## Bevezetés a dokumentumok szöveges fájlként történő mentésébe az Aspose.Words for Java programban

Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet dokumentumokat szövegfájlként menteni az Aspose.Words for Java könyvtár használatával. Az Aspose.Words egy hatékony Java API a Word-dokumentumokkal való munkavégzéshez, és különféle lehetőségeket kínál a dokumentumok különböző formátumokban történő mentésére, beleértve az egyszerű szöveget is. Leírjuk az ennek eléréséhez szükséges lépéseket, és minta Java kódot biztosítunk az út során.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- Java Development Kit (JDK) telepítve a rendszerére.
-  Aspose.Words for Java könyvtár integrálva a projektbe. Letöltheti innen[itt](https://releases.aspose.com/words/java/).
- Java programozási alapismeretek.

## 1. lépés: Hozzon létre egy dokumentumot

Egy dokumentum szöveges fájlként való mentéséhez először létre kell hoznunk egy dokumentumot az Aspose.Words használatával. Íme egy egyszerű Java kódrészlet bizonyos tartalmú dokumentum létrehozásához:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Ebben a kódban új dokumentumot hozunk létre, és szöveget adunk hozzá, beleértve a különböző nyelvű szövegeket.

## 2. lépés: Adja meg a szöveges mentési beállításokat

Ezután meg kell határoznunk a szöveges mentési beállításokat, amelyek meghatározzák, hogyan kell a dokumentumot szövegfájlként menteni. Különféle beállításokat konfigurálhatunk, például kétirányú jelölések hozzáadását, a lista behúzását stb. Nézzünk két példát:

### 1. példa: Kétirányú jelölések hozzáadása

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 Ebben a példában létrehozunk egy`TxtSaveOptions` objektumot és állítsa be a`AddBidiMarks`tulajdonát`true` hogy a szövegkimenetben kétirányú jelek szerepeljenek.

### 2. példa: Tabulátor használata a lista behúzásához

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Itt úgy állítjuk be a mentési beállításokat, hogy egy tabulátor karaktert használjunk a lista behúzásához 1-es számmal.

## 3. lépés: Mentse el a dokumentumot szövegként

Most, hogy meghatároztuk a szöveges mentési beállításokat, elmenthetjük a dokumentumot szöveges fájlként. A következő kód bemutatja, hogyan kell ezt megtenni:

```java
doc.save("output.txt", saveOptions);
```

 Cserélje ki`"output.txt"` a kívánt fájl elérési úttal, ahová a szövegfájlt menteni szeretné.

## Teljes forráskód a dokumentumok szöveges fájlként történő mentéséhez az Aspose.Words for Java programban

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
        // Hozzon létre egy listát három behúzási szinttel.
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
        // Hozzon létre egy listát három behúzási szinttel.
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

Ebben az oktatóanyagban megtanultuk, hogyan lehet dokumentumokat szövegfájlként menteni az Aspose.Words for Java programban. Áttekintettük a dokumentum létrehozásának, a szöveges mentési beállítások meghatározásának és a dokumentum szöveges formátumban történő mentésének lépéseit. Az Aspose.Words széles körű rugalmasságot biztosít a dokumentumok mentésekor, lehetővé téve, hogy a kimenetet az Ön egyedi igényeihez igazítsa.

## GYIK

### Hogyan adhatok kétirányú jeleket a szövegkimenethez?

 Ha kétirányú jeleket szeretne hozzáadni a szövegkimenethez, állítsa be a`AddBidiMarks` tulajdona`TxtSaveOptions` hogy`true`. Például:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Testreszabhatom a lista behúzás karakterét?

 Igen, testreszabhatja a lista behúzás karakterét a`ListIndentation` tulajdona`TxtSaveOptions`. Ha például egy tabulátor karaktert szeretne használni a lista behúzásához, tegye a következőket:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Az Aspose.Words for Java alkalmas többnyelvű szöveg kezelésére?

Igen, az Aspose.Words for Java alkalmas többnyelvű szövegek kezelésére. Különféle nyelveket és karakterkódolásokat támogat, így sokoldalú választás a különböző nyelvű dokumentumokkal való munkavégzéshez.

### Hogyan férhetek hozzá az Aspose.Words for Java további dokumentációjához és erőforrásaihoz?

 Az Aspose.Words for Java-hoz átfogó dokumentációt és forrásokat találhat az Aspose dokumentációs webhelyén:[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Honnan tölthetem le az Aspose.Words for Java programot?

 Az Aspose.Words for Java könyvtárat letöltheti az Aspose webhelyéről:[Töltse le az Aspose.Words for Java programot](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
