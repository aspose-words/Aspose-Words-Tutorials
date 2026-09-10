---
date: 2025-12-24
description: Tanulja meg, hogyan hozhat létre egyszerű szövegfájlt Word dokumentumokból
  az Aspose.Words for Java használatával. Ez az útmutató bemutatja, hogyan konvertálja
  a Word-et txt formátumba, hogyan használjon tabulátor behúzást, és hogyan mentse
  a Word-et txt‑ként.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Hogyan hozzunk létre egyszerű szövegfájlt az Aspose.Words for Java-val
url: /hu/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre egyszerű szövegfájlt az Aspose.Words for Java segítségével

## Bevezetés a dokumentumok szövegfájlokként való mentésébe az Aspose.Words for Java-ban

Ebben az útmutatóban megtanulja, hogyan **hozzon létre egyszerű szövegfájlt** egy Word dokumentumból az Aspose.Words for Java könyvtár segítségével. Akár **word to txt konvertálásra**, jelentésgenerálás automatizálására, vagy egyszerűen csak nyers szöveg kinyerésére van szüksége további feldolgozáshoz, ez az útmutató végigvezeti Önt a teljes munkafolyamaton – a dokumentum létrehozásától a mentési beállítások finomhangolásáig, mint például **tabulátor behúzás használata** vagy bidi jelek hozzáadása. Kezdjünk is!

## Gyors válaszok
- **Mi a fő osztály egy dokumentum létrehozásához?** `Document` from Aspose.Words.
- **Melyik opció ad hozzá bidi jeleket a jobbról balra író nyelvekhez?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Hogyan lehet a listaelemeket tabulátorokkal behúzni?** Set `ListIndentation.Character` to `'\t'`.
- **Szükségem van licencre a fejlesztéshez?** A free trial works for testing; a license is required for production.
- **Menthetem a fájlt egy egyedi névvel és útvonallal?** Yes—pass the full path to `doc.save()`.

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg róla, hogy a következő előfeltételek rendelkezésre állnak:

- Java Development Kit (JDK) telepítve van a rendszerén.  
- Aspose.Words for Java könyvtár integrálva van a projektjébe. Letöltheti [innen](https://releases.aspose.com/words/java/).  
- Alapvető Java programozási ismeretek.

## 1. lépés: Dokumentum létrehozása

A **word txt‑ként való mentéséhez** először egy `Document` példányra van szükség. Az alábbi egyszerű Java kódrészlet létrehoz egy dokumentumot, és néhány sor többnyelvű szöveget ír bele:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Ebben a kódban új dokumentumot hozunk létre, angol, héber és arab szöveget adunk hozzá, és engedélyezzük a jobbról balra formázást a héber bekezdéshez.

## 2. lépés: Szöveg mentési beállítások meghatározása

Ezután beállítjuk, hogyan lesz a dokumentum egyszerű szövegfájlként mentve. Az Aspose.Words a `TxtSaveOptions` osztályt biztosítja, amely lehetővé teszi a bidi jelektől a lista behúzásáig minden vezérlését.

### Példa 1: Bidi jelek hozzáadása (hogyan mentse a txt‑t megfelelő RTL támogatással)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Az `AddBidiMarks` `true`-ra állítása biztosítja, hogy a jobbról balra író karakterek helyesen jelenjenek meg a keletkezett **egyszerű szövegfájlban**.

### Példa 2: Tabulátor karakter használata a lista behúzásához (tabulátor behúzás használata)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Itt azt mondjuk az Aspose.Words-nak, hogy minden lista szint előtt egy tabulátor karaktert (`'\t'`) helyezzen el, így a szövegkimenet könnyebben olvasható lesz.

## 3. lépés: Dokumentum mentése szövegként

Most, hogy a mentési beállítások készen állnak, a dokumentumot **egyszerű szövegfájlként** menthetjük:

```java
doc.save("output.txt", saveOptions);
```

Cserélje le az `"output.txt"`-t a teljes útvonalra, ahová a fájlt menteni szeretné.

## Teljes forráskód a dokumentumok szövegfájlokként való mentéséhez az Aspose.Words for Java-ban

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## Gyakori problémák és megoldások

| Probléma | Megoldás |
|----------|----------|
| **A bidi karakterek összekevert szövegként jelennek meg** | Győződjön meg róla, hogy a `setAddBidiMarks(true)` engedélyezve van, és a kimeneti fájlt UTF‑8 kódolással nyitja meg. |
| **A lista behúzása hibásnak tűnik** | Ellenőrizze, hogy a `ListIndentation.Count` és a `Character` a kívánt értékekre van beállítva (tabulátor `'\t'` vagy szóköz `' '` ). |
| **A fájl nem jött létre** | Ellenőrizze, hogy a könyvtár útvonala létezik, és az alkalmazásnak írási jogosultsága van. |

## Gyakran feltett kérdések

### Hogyan adhatok hozzá bidi jeleket a szövegkimenethez?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Testreszabhatom a lista behúzási karaktert?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Alkalmas-e az Aspose.Words for Java a többnyelvű szöveg kezelésére?

Igen, az Aspose.Words for Java széles körű nyelveket és karakterkódolásokat támogat, így ideális a többnyelvű tartalom kinyerésére és egyszerű szövegként való mentésére.

### Hol találok további dokumentációt és forrásokat az Aspose.Words for Java-hoz?

Átfogó dokumentációt és forrásokat a Aspose.Words for Java Dokumentációs oldalon talál: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Hol tölthetem le az Aspose.Words for Java-t?

A könyvtárat a hivatalos oldalról töltheti le: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Mi van, ha **word to txt** konvertálásra van szükség kötegelt folyamatban?

Tegye a fenti kódot egy ciklusba, amely betölti az egyes `.docx` fájlokat, alkalmazza ugyanazt a `TxtSaveOptions`-t, és minden fájlt `.txt`‑ként ment. Győződjön meg róla, hogy az erőforrásokat a `Document` objektumok minden iteráció után felszabadítja.

### Támogatja-e az API a közvetlen mentést stream‑be a fájl helyett?

Igen, átadhat egy `OutputStream`‑et a `doc.save(outputStream, saveOptions)` metódusnak memória‑beli feldolgozáshoz vagy webszolgáltatások integrálásakor.

---

**Utoljára frissítve:** 2025-12-24  
**Tesztelve ezzel:** Aspose.Words for Java 24.12 (latest)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}