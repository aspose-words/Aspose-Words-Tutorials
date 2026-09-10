---
date: 2025-12-20
description: Naučte se, jak organizovat soubory podle typu a detekovat formáty dokumentů
  v Javě s Aspose.Words. Podporuje DOC, DOCX, RTF a další.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organizujte soubory podle typu pomocí Aspose.Words pro Javu
url: /cs/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organizujte soubory podle typu pomocí Aspose.Words pro Java

Když potřebujete **organizovat soubory podle typu** v Java aplikaci, prvním krokem je spolehlivě určit formát každého dokumentu. Aspose.Words pro Java to usnadňuje a umožňuje detekovat formáty DOC, DOCX, RTF, HTML, ODT a mnoho dalších – dokonce i šifrované nebo neznámé soubory. V tomto průvodci vás provedeme nastavením složek, detekcí formátů souborů a automatickým řazením vašich souborů.

## Rychlé odpovědi
- **Co znamená „organizovat soubory podle typu“?** Znamená to automatické přesouvání dokumentů do složek na základě jejich detekovaného formátu (např. DOCX, PDF, RTF).  
- **Která knihovna pomáhá detekovat formát souboru v Javě?** Aspose.Words pro Java poskytuje `FileFormatUtil.detectFileFormat()`.  
- **Umí API identifikovat neznámé typy souborů?** Ano – vrací `LoadFormat.UNKNOWN` pro nepodporované nebo nerozpoznatelné soubory.  
- **Je podpora detekce šifrovaných dokumentů?** Ano; příznak `FileFormatInfo.isEncrypted()` vám řekne, zda je soubor chráněn heslem.  
- **Potřebuji licenci pro produkční použití?** Pro komerční nasazení je vyžadována platná licence Aspose.Words.

## Úvod: Organizujte soubory podle typu s Aspose.Words pro Java

Při práci se zpracováním dokumentů v Javě je klíčové určit formát souborů, se kterými pracujete. Aspose.Words pro Java poskytuje výkonné funkce pro **detect file format java**, a my vás provedeme procesem efektivního organizování vašich souborů.

## Požadavky

Před zahájením se ujistěte, že máte následující:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) nainstalovaný ve vašem systému
- Základní znalost programování v Javě

## Krok 1: Nastavení adresářů

Nejprve musíme nastavit potřebné adresáře pro efektivní organizaci našich souborů. Vytvoříme adresáře pro různé typy dokumentů.

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

Vytvořili jsme adresáře pro podporované, neznámé, šifrované a pre‑97 typy dokumentů.

## Krok 2: Detekce formátu dokumentu

Nyní detekujme formát dokumentů v našich adresářích. K tomu použijeme Aspose.Words pro Java.

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

V tomto úryvku procházíme soubory, **detect file format java**, a organizujeme je do příslušných složek.

## Kompletní zdrojový kód pro určení formátu dokumentu v Aspose.Words pro Java

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

## Jak detekovat formát souboru v Javě

Metoda `FileFormatUtil.detectFileFormat()` prozkoumá hlavičku souboru a vrátí objekt `FileFormatInfo`. Tento objekt vám sdělí **load format**, zda je soubor šifrovaný, a další užitečná metadata. Pomocí těchto informací můžete programově **identify unknown file types** a rozhodnout, jak s každým souborem zacházet.

## Identifikace neznámých typů souborů

Když API vrátí `LoadFormat.UNKNOWN`, soubor je buď poškozený, nebo používá formát, který Aspose.Words nepodporuje. V našem ukázkovém kódu přesuneme tyto soubory do složky **Unknown**, abyste je mohli později zkontrolovat.

## Časté problémy a řešení

| Problém | Důvod | Řešení |
|-------|--------|-----|
| Soubory jsou vždy umístěny ve složce *Supported* | `FileFormatUtil` nemohl přečíst hlavičku (např. soubor je prázdný) | Ujistěte se, že předáváte správnou cestu k souboru a že soubor není nulové velikosti. |
| Šifrované soubory vyvolají výjimku | Pokus o čtení bez ošetření šifrování | Použijte kontrolu `info.isEncrypted()` před dalším zpracováním, jak je ukázáno v kódu. |
| Pre‑97 Word dokumenty nejsou detekovány | Starší formáty vyžadují případ `DOC_PRE_WORD_60` | Nechte blok `case LoadFormat.DOC_PRE_WORD_60`, aby je směroval do složky *Pre97*. |

## Často kladené otázky

### Jak nainstaluji Aspose.Words pro Java?

Aspose.Words pro Java si můžete stáhnout z [zde](https://releases.aspose.com/words/java/) a postupovat podle poskytnutých instalačních instrukcí.

### Jaké dokumentové formáty jsou podporovány?

Aspose.Words pro Java podporuje různé dokumentové formáty, včetně DOC, DOCX, RTF, HTML, ODT a dalších. Kompletní seznam najdete v oficiální dokumentaci.

### Jak mohu detekovat šifrované dokumenty pomocí Aspose.Words pro Java?

Použijte metodu `FileFormatUtil.detectFileFormat()`; vrácený příznak `FileFormatInfo.isEncrypted()` indikuje šifrování, jak je ukázáno v tomto průvodci.

### Existují nějaká omezení při práci se staršími formáty dokumentů?

Starší formáty jako MS Word 6 nebo Word 95 mohou postrádat moderní funkce a mohou mít problémy s kompatibilitou. Zvažte jejich konverzi na novější formáty, pokud je to možné.

### Můžu automatizovat detekci formátu dokumentu v mé Java aplikaci?

Ano, vložte poskytnutý kód do zpracovatelského potrubí vaší aplikace. To umožní automatické řazení a zpracování na základě detekovaných formátů.

---

**Poslední aktualizace:** 2025-12-20  
**Testováno s:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}