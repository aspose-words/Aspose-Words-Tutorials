---
"description": "Tanuld meg, hogyan ismerd fel a dokumentumformátumokat Java-ban az Aspose.Words segítségével. Azonosítsd a DOC, DOCX és egyebeket. Rendszerezd hatékonyan a fájlokat."
"linktitle": "Dokumentumformátum meghatározása"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumformátum meghatározása az Aspose.Words programban Java-ban"
"url": "/hu/java/document-loading-and-saving/determining-document-format/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumformátum meghatározása az Aspose.Words programban Java-ban


## Bevezetés a dokumentumformátum meghatározásába az Aspose.Words Java-ban

Amikor Java nyelven dolgozunk dokumentumfeldolgozással, kulcsfontosságú meghatározni a kezelt fájlok formátumát. Az Aspose.Words for Java hatékony funkciókat kínál a dokumentumformátumok azonosításához, és mi végigvezetjük Önt a folyamaton.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételekkel rendelkezünk:

- [Aspose.Words Java-hoz](https://releases.aspose.com/words/java/)
- Java fejlesztőkészlet (JDK) telepítve a rendszerére
- Alapvető Java programozási ismeretek

## 1. lépés: Címtár beállítása

Először is létre kell hoznunk a szükséges könyvtárakat a fájljaink hatékony rendszerezéséhez. Létrehozunk könyvtárakat a különböző dokumentumtípusokhoz.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Hozza létre a könyvtárakat, ha még nem léteznek.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Létrehoztunk könyvtárakat a támogatott, ismeretlen, titkosított és a 97 előtti dokumentumtípusokhoz.

## 2. lépés: Dokumentumformátum észlelése

Most pedig vizsgáljuk meg a könyvtárainkban található dokumentumok formátumát. Ehhez az Aspose.Words for Java programot fogjuk használni.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // A dokumentum típusának megjelenítése
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Szükség szerint adjon hozzá eseteket más dokumentumformátumokhoz
    }

    // Titkosított dokumentumok kezelése
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Más dokumentumtípusok kezelése
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

Ebben a kódrészletben végigmegyünk a fájlokon, megállapítjuk a formátumukat, és a megfelelő könyvtárakba rendezzük őket.

## Teljes forráskód a dokumentumformátum meghatározásához az Aspose.Words programban Java-hoz

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Hozza létre a könyvtárakat, ha még nem léteznek.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // A dokumentum típusának megjelenítése
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Következtetés

dokumentumformátumok meghatározása az Aspose.Words for Java programban elengedhetetlen a hatékony dokumentumfeldolgozáshoz. Az útmutatóban ismertetett lépésekkel azonosíthatja a dokumentumtípusokat, és ennek megfelelően kezelheti azokat a Java-alkalmazásaiban.

## GYIK

### Hogyan telepíthetem az Aspose.Words-öt Java-hoz?

Az Aspose.Words Java-hoz készült verzióját letöltheted innen: [itt](https://releases.aspose.com/words/java/) és kövesse a mellékelt telepítési utasításokat.

### Milyen dokumentumformátumok támogatottak?

Az Aspose.Words for Java számos dokumentumformátumot támogat, beleértve a DOC, DOCX, RTF, HTML és egyebeket. A teljes listát a dokumentációban találja.

### Hogyan tudom felismerni a titkosított dokumentumokat az Aspose.Words for Java használatával?

Használhatod a `FileFormatUtil.detectFileFormat()` módszer a titkosított dokumentumok észlelésére, ahogy az ebben az útmutatóban is látható.

### Vannak-e korlátozások a régebbi dokumentumformátumokkal való munka során?

régebbi dokumentumformátumok, mint például az MS Word 6 vagy a Word 95, korlátozottak lehetnek a funkciók és a modern alkalmazásokkal való kompatibilitás tekintetében. Érdemes lehet frissíteni vagy konvertálni ezeket a dokumentumokat, ha szükséges.

### Automatizálhatom a dokumentumformátum-észlelést a Java alkalmazásomban?

Igen, automatizálhatja a dokumentumformátum-észlelést a megadott kód Java-alkalmazásába való integrálásával. Ez lehetővé teszi a dokumentumok feldolgozását az észlelt formátumok alapján.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}