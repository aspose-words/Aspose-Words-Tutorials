---
date: 2025-12-20
description: Tanulja meg, hogyan szervezheti a fájlokat típus szerint, és hogyan ismerheti
  fel a dokumentumformátumokat Java-ban az Aspose.Words segítségével. Támogatja a
  DOC, DOCX, RTF és további formátumokat.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Fájlok rendezése típus szerint az Aspose.Words for Java használatával
url: /hu/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fájlok típus szerinti rendezése az Aspose.Words for Java segítségével

Amikor egy Java‑alkalmazásban **fájlok típus szerinti rendezésére** van szükség, az első lépés a dokumentumok formátumának megbízható meghatározása. Az Aspose.Words for Java ezt egyszerűvé teszi, lehetővé téve a DOC, DOCX, RTF, HTML, ODT és számos más formátum – még a titkosított vagy ismeretlen fájlok – felismerését. Ebben az útmutatóban bemutatjuk, hogyan állítsunk be mappákat, hogyan detektáljuk a fájlformátumokat, és hogyan rendezhetjük automatikusan a fájlokat.

## Gyors válaszok
- **Mit jelent a “fájlok típus szerinti rendezése”?** Azt, hogy a dokumentumokat automatikusan a felismert formátumuk (pl. DOCX, PDF, RTF) alapján mappákba helyezzük.  
- **Melyik könyvtár segít a fájlformátum felismerésében Java‑ban?** Az Aspose.Words for Java biztosítja a `FileFormatUtil.detectFileFormat()` metódust.  
- **Az API képes ismeretlen fájltípusok azonosítására?** Igen – nem támogatott vagy felismerhetetlen fájlok esetén `LoadFormat.UNKNOWN` értéket ad vissza.  
- **Támogatott a titkosított dokumentumok felismerése?** Teljes mértékben; a `FileFormatInfo.isEncrypted()` jelző megmutatja, ha a fájl jelszóval védett.  
- **Szükség van licencre a termelésben való használathoz?** Igen, kereskedelmi környezetben érvényes Aspose.Words licenc szükséges.

## Bevezetés: Fájlok típus szerinti rendezése az Aspose.Words for Java segítségével

Java‑ban a dokumentumfeldolgozás során elengedhetetlen a fájlok formátumának meghatározása. Az Aspose.Words for Java erőteljes funkciókat kínál a **fájlformátum detektálásához Java‑ban**, és végigvezetjük a hatékony fájlrendezés folyamatán.

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg róla, hogy a következő előfeltételek teljesülnek:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) telepítve van a rendszerén
- Alapvető Java programozási ismeretek

## 1. lépés: Könyvtárak létrehozása

Először is létre kell hoznunk a szükséges könyvtárakat a fájlok hatékony rendezéséhez. Külön mappákat hozunk létre a különböző dokumentumtípusok számára.

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

Létrehoztuk a támogatott, ismeretlen, titkosított és pre‑97 dokumentumtípusok számára a megfelelő könyvtárakat.

## 2. lépés: Dokumentumformátum detektálása

Most detektáljuk a könyvtárainkban lévő dokumentumok formátumát. Ehhez az Aspose.Words for Java‑t használjuk.

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

Ebben a kódrészletben végigiterálunk a fájlokon, **fájlformátumot detektálunk Java‑ban**, és a megfelelő mappákba helyezzük őket.

## Teljes forráskód a dokumentumformátum meghatározásához az Aspose.Words for Java‑ban

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

## Hogyan detektáljuk a fájlformátumot Java‑ban

A `FileFormatUtil.detectFileFormat()` metódus a fájlfejlécet vizsgálja, és egy `FileFormatInfo` objektumot ad vissza. Ez az objektum tartalmazza a **load format** értékét, azt, hogy a fájl titkosított‑e, valamint egyéb hasznos metaadatokat. Ezen információk felhasználásával programozottan **azonosíthatunk ismeretlen fájltípusokat**, és eldönthetjük, hogyan dolgozzuk fel őket.

## Ismeretlen fájltípusok azonosítása

Ha az API `LoadFormat.UNKNOWN` értéket ad vissza, a fájl vagy sérült, vagy olyan formátumú, amelyet az Aspose.Words nem támogat. A példakódban ezeket a fájlokat az **Ismeretlen** mappába helyezzük, hogy később áttekinthetőek legyenek.

## Gyakori problémák és megoldások

| Probléma | Ok | Megoldás |
|----------|----|----------|
| A fájlok mindig a *Támogatott* mappába kerülnek | A `FileFormatUtil` nem tudta beolvasni a fejlécet (pl. a fájl üres) | Győződjön meg arról, hogy a helyes fájlútvonalat adja meg, és a fájl nem 0‑bájtos. |
| Titkosított fájlok kivételt dobnak | Titkosítás kezelése nélkül próbálja meg olvasni | Használja az `info.isEncrypted()` ellenőrzést a további feldolgozás előtt, ahogy a kódban is látható. |
| Pre‑97 Word dokumentumok nem kerülnek felismerésre | Régi formátumokhoz szükséges a `DOC_PRE_WORD_60` eset | Tartsa meg a `case LoadFormat.DOC_PRE_WORD_60` blokkot, hogy a *Pre97* mappába irányítsa őket. |

## Gyakran feltett kérdések

### Hogyan telepíthetem az Aspose.Words for Java‑t?

Az Aspose.Words for Java‑t letöltheti [innen](https://releases.aspose.com/words/java/), és kövesse a mellékelt telepítési útmutatót.

### Mely dokumentumformátumok támogatottak?

Az Aspose.Words for Java számos formátumot támogat, többek között DOC, DOCX, RTF, HTML, ODT és még sok mást. A teljes listáért tekintse meg a hivatalos dokumentációt.

### Hogyan detektálhatom a titkosított dokumentumokat az Aspose.Words for Java‑val?

Használja a `FileFormatUtil.detectFileFormat()` metódust; a visszaadott `FileFormatInfo.isEncrypted()` jelző jelzi a titkosítást, ahogyan ebben az útmutatóban is bemutatjuk.

### Vannak korlátozások a régi dokumentumformátumokkal kapcsolatban?

Az olyan régi formátumok, mint a MS Word 6 vagy Word 95, hiányozhatnak a modern funkciókból, és kompatibilitási problémákat okozhatnak. Amennyiben lehetséges, konvertálja őket újabb formátumokra.

### Automatizálhatom a dokumentumformátum detektálását a Java‑alkalmazásomban?

Igen, a megadott kód beilleszthető az alkalmazás feldolgozási csővezetékébe. Ez lehetővé teszi az automatikus rendezést és a formátumok alapján történő kezelését.

---

**Utolsó frissítés:** 2025-12-20  
**Tesztelt verzió:** Aspose.Words for Java 24.12 (legújabb)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}