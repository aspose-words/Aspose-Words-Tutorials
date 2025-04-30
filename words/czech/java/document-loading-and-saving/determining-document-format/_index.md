---
"description": "Naučte se, jak detekovat formáty dokumentů v Javě pomocí Aspose.Words. Identifikujte DOC, DOCX a další. Efektivně organizujte soubory."
"linktitle": "Určení formátu dokumentu"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Určení formátu dokumentu v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/determining-document-format/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Určení formátu dokumentu v Aspose.Words pro Javu


## Úvod do určování formátu dokumentu v Aspose.Words pro Javu

Při práci se zpracováním dokumentů v Javě je zásadní určit formát souborů, se kterými pracujete. Aspose.Words pro Javu poskytuje výkonné funkce pro identifikaci formátů dokumentů a my vás tímto procesem provedeme.

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:

- [Aspose.Words pro Javu](https://releases.aspose.com/words/java/)
- Sada pro vývoj Java (JDK) nainstalovaná ve vašem systému
- Základní znalost programování v Javě

## Krok 1: Nastavení adresáře

Nejprve musíme nastavit potřebné adresáře pro efektivní uspořádání našich souborů. Vytvoříme adresáře pro různé typy dokumentů.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Vytvořte adresáře, pokud ještě neexistují.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Vytvořili jsme adresáře pro podporované, neznámé, šifrované a starší typy dokumentů než 97.

## Krok 2: Detekce formátu dokumentu

Nyní se podíváme na formát dokumentů v našich adresářích. K tomu použijeme Aspose.Words pro Javu.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Zobrazit typ dokumentu
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // V případě potřeby přidejte případy pro další formáty dokumentů
    }

    // Zpracování šifrovaných dokumentů
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Zpracování dalších typů dokumentů
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

V tomto úryvku kódu iterujeme soubory, detekujeme jejich formáty a uspořádáme je do příslušných adresářů.

## Kompletní zdrojový kód pro určení formátu dokumentu v Aspose.Words pro Javu

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Vytvořte adresáře, pokud ještě neexistují.
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
            // Zobrazit typ dokumentu
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

## Závěr

Určení formátů dokumentů v Aspose.Words pro Javu je nezbytné pro efektivní zpracování dokumentů. Pomocí kroků popsaných v této příručce můžete identifikovat typy dokumentů a odpovídajícím způsobem s nimi pracovat ve svých aplikacích Java.

## Často kladené otázky

### Jak nainstaluji Aspose.Words pro Javu?

Aspose.Words pro Javu si můžete stáhnout z [zde](https://releases.aspose.com/words/java/) a postupujte podle přiložených pokynů k instalaci.

### Jaké jsou podporované formáty dokumentů?

Aspose.Words pro Javu podporuje různé formáty dokumentů, včetně DOC, DOCX, RTF, HTML a dalších. Úplný seznam naleznete v dokumentaci.

### Jak mohu detekovat šifrované dokumenty pomocí Aspose.Words pro Javu?

Můžete použít `FileFormatUtil.detectFileFormat()` metoda pro detekci šifrovaných dokumentů, jak je ukázáno v této příručce.

### Existují nějaká omezení při práci se staršími formáty dokumentů?

Starší formáty dokumentů, jako například MS Word 6 nebo Word 95, mohou mít omezení, pokud jde o funkce a kompatibilitu s moderními aplikacemi. V případě potřeby zvažte upgrade nebo konverzi těchto dokumentů.

### Mohu automatizovat detekci formátu dokumentu v mé aplikaci Java?

Ano, detekci formátu dokumentů můžete automatizovat integrací poskytnutého kódu do vaší aplikace Java. To vám umožní zpracovávat dokumenty na základě jejich detekovaných formátů.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}