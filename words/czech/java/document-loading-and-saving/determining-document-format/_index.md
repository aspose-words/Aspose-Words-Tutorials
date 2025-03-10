---
title: Určení formátu dokumentu v Aspose.Words pro Java
linktitle: Určení formátu dokumentu
second_title: Aspose.Words Java Document Processing API
description: Naučte se detekovat formáty dokumentů v Javě pomocí Aspose.Words. Identifikujte DOC, DOCX a další. Efektivně organizujte soubory.
weight: 25
url: /cs/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Určení formátu dokumentu v Aspose.Words pro Java


## Úvod do určování formátu dokumentu v Aspose.Words pro Javu

Při práci se zpracováním dokumentů v Javě je zásadní určit formát souborů, se kterými pracujete. Aspose.Words for Java poskytuje výkonné funkce pro identifikaci formátů dokumentů a my vás celým procesem provedeme.

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) nainstalovaný ve vašem systému
- Základní znalost programování v Javě

## Krok 1: Nastavení adresáře

Nejprve musíme nastavit potřebné adresáře, abychom mohli efektivně organizovat naše soubory. Vytvoříme adresáře pro různé typy dokumentů.

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

Vytvořili jsme adresáře pro podporované, neznámé, šifrované dokumenty a dokumenty starší než 97.

## Krok 2: Zjištění formátu dokumentu

Nyní zjistíme formát dokumentů v našich adresářích. K dosažení tohoto cíle použijeme Aspose.Words for Java.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Zobrazte typ dokumentu
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Podle potřeby přidejte pouzdra pro jiné formáty dokumentů
    }

    // Zpracovávat šifrované dokumenty
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Zvládněte jiné typy dokumentů
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

V tomto úryvku kódu procházíme soubory, zjišťujeme jejich formáty a organizujeme je do příslušných adresářů.

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
            // Zobrazte typ dokumentu
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

Určení formátů dokumentů v Aspose.Words pro Java je nezbytné pro efektivní zpracování dokumentů. Pomocí kroků uvedených v této příručce můžete identifikovat typy dokumentů a podle toho s nimi zacházet ve svých aplikacích Java.

## FAQ

### Jak nainstaluji Aspose.Words for Java?

 Aspose.Words for Java si můžete stáhnout z[zde](https://releases.aspose.com/words/java/) postupujte podle dodaných pokynů k instalaci.

### Jaké jsou podporované formáty dokumentů?

Aspose.Words for Java podporuje různé formáty dokumentů, včetně DOC, DOCX, RTF, HTML a dalších. Úplný seznam naleznete v dokumentaci.

### Jak zjistím šifrované dokumenty pomocí Aspose.Words for Java?

 Můžete použít`FileFormatUtil.detectFileFormat()` způsob detekce zašifrovaných dokumentů, jak je ukázáno v této příručce.

### Existují nějaká omezení při práci se staršími formáty dokumentů?

Starší formáty dokumentů, jako je MS Word 6 nebo Word 95, mohou mít omezení z hlediska funkcí a kompatibility s moderními aplikacemi. V případě potřeby zvažte upgrade nebo konverzi těchto dokumentů.

### Mohu automatizovat zjišťování formátu dokumentu v mé aplikaci Java?

Ano, můžete automatizovat detekci formátu dokumentu integrací poskytnutého kódu do vaší Java aplikace. To vám umožní zpracovávat dokumenty na základě jejich zjištěných formátů.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
