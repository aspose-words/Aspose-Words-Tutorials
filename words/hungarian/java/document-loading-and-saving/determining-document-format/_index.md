---
date: 2026-02-22
description: Ismerje meg, hogyan lehet Java-ban az Aspose.Words segítségével felismerni
  a dokumentum formátumát, és automatikusan áthelyezni a fájlokat formátum szerint.
  Azonosítsa a DOC, DOCX és egyéb formátumokat.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Dokumentumformátum felismerése Java-ban az Aspose.Words for Java használatával
url: /hu/java/document-loading-and-saving/determining-document-format/
weight: 25
---

 can keep as is. The phrase appears many times; maybe keep as is. But translation of surrounding text.

Let's produce.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java dokumentumformátum felismerése az Aspose.Words for Java segítségével

Amikor **detect document format java**-ra van szükség egy fájlkészletben, a fájlok automatikus rendezése a megfelelő mappákba órákat takaríthat meg a kézi munka terén. Ebben a bemutatóban megmutatjuk, hogyan teszi egyszerűvé az Aspose.Words for Java a Word, RTF, HTML, ODT és számos más formátum azonosítását, majd **move files by format** segítségével rendezett könyvtárakba helyezi őket.

## Gyors válaszok
- **Mit jelent a “detect document format java”?** Ez a folyamat azt jelenti, hogy Java kóddal programozottan azonosítjuk egy fájl Word‑feldolgozó formátumát (DOC, DOCX, RTF stb.).  
- **Melyik könyvtár biztosítja ezt a lehetőséget?** Az Aspose.Words for Java a `FileFormatUtil.detectFileFormat` API‑t kínálja.  
- **Kezelni tudja a titkosított fájlokat is?** Igen – a `FileFormatInfo.isEncrypted()` jelző megmondja, ha egy dokumentum jelszóval védett.  
- **Szükség van licencre a termelésben való használathoz?** Igen, egy kereskedelmi Aspose.Words licenc szükséges a nem‑értékelő telepítésekhez.  
- **Lehet automatikusan áthelyezni a fájlokat a felismerés után?** Természetesen – a felismerési eredményt kombinálhatjuk a `FileUtils.copyFile`‑lal, hogy a fájlokat egyedi mappákba rendezzük.

## Mi az a detect document format java?
A `detect document format java` arra utal, hogy Java kóddal megvizsgáljuk egy fájl bináris fejlécét, és meghatározzuk, melyik Word‑feldolgozó formátumhoz (pl. DOC, DOCX, ODT) tartozik. Az Aspose.Words a fájlt a teljes dokumentum betöltése nélkül olvassa, így a művelet gyors és memóriahatékony.

## Miért érdemes formátum szerint áthelyezni a fájlokat?
A dokumentumok natív formátumuk szerinti rendezése leegyszerűsíti a további feldolgozást:

- **Kötegelt konverziók** egyszerűen végrehajthatók, ha minden DOCX fájl egy mappában van.  
- **Örökölt támogatás**: elkülöníthetjük a pre‑97 Word fájlokat speciális kezeléshez.  
- **Biztonság**: a titkosított dokumentumok automatikusan karanténba helyezhetők.  

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg róla, hogy rendelkezik a következőkkel:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (töltse le a legújabb verziót)  
- Java Development Kit (JDK) 8 vagy újabb telepítve  
- Alapvető ismeretek a Java I/O‑ról és streamekről  

## 1. lépés: Könyvtárak létrehozása minden formátumhoz

Először egy tiszta mappastruktúrát hozunk létre, ahová a felismert fájlok kerülnek. Ez rendezi a munkafolyamatot, és könnyűvé teszi új formátumkategóriák hozzáadását később.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

> **Pro tipp:** Használjon abszolút útvonalakat, vagy állítsa be a báziskönyvtárat egy properties fájlban, hogy elkerülje a hard‑coded útvonalakat a termelési kódban.

## 2. lépés: Dokumentumformátum felismerése és fájlok áthelyezése

A **detect document format java** lényege az alábbi ciklusban található. Minden fájlt beolvas, meghatározza a típusát, és a megfelelő mappába másolja.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
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

A `switch` blokk bővíthető minden kívánt formátumra. Minden eset barátságos üzenetet ír ki, majd áthelyezi a fájlt a megfelelő mappába.

## Teljes forráskód a document format java felismeréséhez

Az alábbiakban a teljes, azonnal futtatható példát láthatja, amely egyesíti a könyvtárbeállítást és a felismerési logikát. Másolja be egy Java osztályba, állítsa be a bázisútvonalat, és futtassa egy vegyes dokumentumokat tartalmazó mappán.

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
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
            // Display the document type
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

## Gyakori problémák és hibaelhárítás

| Probléma | Miért fordul elő | Hogyan javítható |
|----------|------------------|-----------------|
| **`FileFormatUtil.detectFileFormat` **UNKNOWN** értéket ad** | A fájl sérült vagy nem‑Word formátumú. | Ellenőrizze a fájl kiterjesztését, vagy adjon hozzá egy tartalék áthelyezést a *Unknown* mappába (már a mintában szerepel). |
| **Titkosított fájlok kivételt dobnak** | Az API a titkosítás ellenőrzése előtt megpróbálja olvasni a tartalmat. | Mindig hívja meg az `info.isEncrypted()`‑t, mielőtt bármilyen más műveletet végezne a dokumentumon. |
| **Könyvtár létrehozása Linuxon sikertelen** | Nem elegendő jogosultság vagy hiányzó szülőkönyvtár. | Győződjön meg róla, hogy a Java folyamatnak írási joga van, és hogy a bázisútvonal létezik. |

## Gyakran ismételt kérdések

**Q: Hogyan telepíthetem az Aspose.Words for Java‑t?**  
A: Letöltheti az Aspose.Words for Java‑t a [here](https://releases.aspose.com/words/java/) címről, és kövesse a mellékelt telepítési útmutatót.

**Q: Milyen dokumentumformátumok támogatottak a felismeréshez?**  
A: Az Aspose.Words képes felismerni a DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML és a régebbi pre‑97 formátumokat, többek között.

**Q: Kezelni tudja a jelszóval védett dokumentumokat ez a kód?**  
A: Igen. A `FileFormatInfo.isEncrypted()` jelző azonosítja a titkosított fájlokat, így azok biztonságos mappába helyezhetők anélkül, hogy megnyitnánk őket.

**Q: Van teljesítménybeli hatása a nagy mappák beolvasásának?**  
A: A felismerés csak a fájl fejlécét olvassa, ezért akár több ezer fájl is gyorsan feldolgozható. Nagyon nagy kötegek esetén érdemes párhuzamos streameket használni.

**Q: Hogyan bővíthetem a szkriptet, hogy nem támogatott formátumokat konvertáljon?**  
A: A felismerés után meghívhatja a `Document.save`‑t a kívánt kimeneti formátummal bármely támogatott forrástípus esetén.

## Összegzés

Az **detect document format java** használatával az Aspose.Words segítségével megbízható módot kap a Word‑kapcsolódó fájlok automatikus rendezésére, karanténba helyezésére vagy konvertálására. A mintakód bemutatja, hogyan hozhat létre tiszta könyvtárhierarchiát, azonosíthatja minden fájl formátumát, és helyezheti át azt – időt takarít meg és csökkenti a kézi hibákat.

---

**Utoljára frissítve:** 2026-02-22  
**Tesztelve:** Aspose.Words for Java 24.12 (legújabb)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}