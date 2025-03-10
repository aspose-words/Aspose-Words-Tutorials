---
title: Dokumentumformátum meghatározása az Aspose.Words for Java programban
linktitle: dokumentum formátumának meghatározása
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan észlelheti a dokumentumformátumokat Java nyelven az Aspose.Words segítségével. A DOC, DOCX és egyebek azonosítása. A fájlok hatékony rendszerezése.
weight: 25
url: /hu/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumformátum meghatározása az Aspose.Words for Java programban


## Bevezetés az Aspose.Words for Java dokumentumformátumának meghatározásába

Amikor Java-ban dolgozunk dokumentumfeldolgozással, nagyon fontos meghatározni a kezelt fájlok formátumát. Az Aspose.Words for Java hatékony szolgáltatásokat nyújt a dokumentumformátumok azonosításához, mi pedig végigvezetjük a folyamaton.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) telepítve a rendszerére
- Java programozási alapismeretek

## 1. lépés: Címtárbeállítás

Először is be kell állítanunk a szükséges könyvtárakat a fájlok hatékony rendszerezéséhez. A különböző dokumentumtípusokhoz könyvtárakat hozunk létre.

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

támogatott, ismeretlen, titkosított és 97 előtti dokumentumtípusokhoz könyvtárakat hoztunk létre.

## 2. lépés: Dokumentumformátum észlelése

Most pedig határozzuk meg a könyvtárainkban lévő dokumentumok formátumát. Ennek eléréséhez az Aspose.Words for Java-t használjuk.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Jelenítse meg a dokumentum típusát
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Szükség esetén adjon hozzá eseteket más dokumentumformátumokhoz
    }

    // Titkosított dokumentumok kezelése
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Más típusú dokumentumok kezelése
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

Ebben a kódrészletben végigfutjuk a fájlokat, észleljük formátumukat, és a megfelelő könyvtárakba rendezzük őket.

## Teljes forráskód az Aspose.Words for Java dokumentumformátumának meghatározásához

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
            // Jelenítse meg a dokumentum típusát
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

A dokumentumformátumok meghatározása az Aspose.Words for Java programban elengedhetetlen a hatékony dokumentumfeldolgozáshoz. Az ebben az útmutatóban ismertetett lépésekkel azonosíthatja a dokumentumtípusokat, és megfelelően kezelheti őket Java-alkalmazásaiban.

## GYIK

### Hogyan telepíthetem az Aspose.Words for Java programot?

 Letöltheti az Aspose.Words for Java programot a[itt](https://releases.aspose.com/words/java/)és kövesse a mellékelt telepítési utasításokat.

### Melyek a támogatott dokumentumformátumok?

Az Aspose.Words for Java különféle dokumentumformátumokat támogat, beleértve a DOC, DOCX, RTF, HTML és egyebeket. A teljes listát a dokumentációban találja.

### Hogyan észlelhetem a titkosított dokumentumokat az Aspose.Words for Java használatával?

 Használhatja a`FileFormatUtil.detectFileFormat()` módszert a titkosított dokumentumok észlelésére, amint azt ebben az útmutatóban bemutatjuk.

### Vannak-e korlátozások a régebbi dokumentumformátumokkal való munka során?

A régebbi dokumentumformátumoknak, például az MS Word 6-nak vagy a Word 95-nek korlátai lehetnek a funkciók és a modern alkalmazásokkal való kompatibilitás tekintetében. Szükség esetén fontolja meg ezeknek a dokumentumoknak a frissítését vagy átalakítását.

### Automatizálhatom a dokumentumformátum észlelését a Java alkalmazásban?

Igen, automatizálhatja a dokumentumformátum észlelését, ha integrálja a mellékelt kódot a Java-alkalmazásba. Ez lehetővé teszi a dokumentumok feldolgozását az észlelt formátumok alapján.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
