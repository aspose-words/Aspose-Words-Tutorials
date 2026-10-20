---
date: 2026-02-22
description: Naučte se, jak v Javě detekovat formát dokumentu pomocí Aspose.Words
  a automaticky přesouvat soubory podle formátu. Identifikujte DOC, DOCX a další.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Detekce formátu dokumentu v Javě pomocí Aspose.Words for Java
url: /cs/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detekce formátu dokumentu java pomocí Aspose.Words pro Java

Když potřebujete **detect document format java** v dávce souborů, schopnost je automaticky roztřídit do správných složek může ušetřit hodiny ruční práce. V tomto tutoriálu vám ukážeme, jak Aspose.Words pro Java usnadňuje identifikaci formátů Word, RTF, HTML, ODT a mnoha dalších, a následně **move files by format** do uspořádaných adresářů.

## Rychlé odpovědi
- **Co znamená “detect document format java”?** Je to proces programového identifikování formátu souboru pro zpracování textu (DOC, DOCX, RTF atd.) pomocí Java kódu.  
- **Která knihovna tuto funkci poskytuje?** Aspose.Words pro Java nabízí API `FileFormatUtil.detectFileFormat`.  
- **Umí nástroj také pracovat s šifrovanými soubory?** Ano – příznak `FileFormatInfo.isEncrypted()` vám řekne, zda je dokument chráněn heslem.  
- **Potřebuji licenci pro produkční použití?** Pro ne‑evaluační nasazení je vyžadována komerční licence Aspose.Words.  
- **Je možné po detekci soubory automaticky přesunout?** Rozhodně – kombinujte výsledek detekce s `FileUtils.copyFile` pro řazení souborů do vlastních složek.

## Co je detect document format java?
`detect document format java` označuje použití Java kódu k prozkoumání binárního hlavičkového souboru a určení, do jakého formátu zpracování textu patří (např. DOC, DOCX, ODT). Aspose.Words čte soubor bez úplného načtení dokumentu, což činí operaci rychlou a paměťově úspornou.

## Proč přesouvat soubory podle formátu?
Organizace dokumentů podle jejich nativního formátu zjednodušuje následné zpracování:

- **Hromadné konverze** jsou jednoduché, když jsou všechny soubory DOCX v jedné složce.  
- **Podpora starších verzí**: můžete izolovat soubory Word před rokem 97 pro speciální zpracování.  
- **Bezpečnost**: šifrované dokumenty mohou být automaticky karanténovány.

## Požadavky

Before we begin, make sure you have:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (stáhněte nejnovější verzi)  
- Java Development Kit (JDK) 8 nebo vyšší nainstalovaný  
- Základní znalost Java I/O a streamů  

## Krok 1: Nastavte adresáře pro každý formát

Nejprve vytvoříme čistou strukturu složek, kam budou detekované soubory přesunuty. To udržuje pracovní postup přehledný a usnadňuje pozdější přidání nových kategorií formátů.

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

> **Tip:** Používejte absolutní cesty nebo nakonfigurujte základní adresář pomocí souboru properties, abyste se vyhnuli pevně zakódovaným cestám v produkčním kódu.

## Krok 2: Detekujte formát dokumentu a přesouvejte soubory

Jádro **detect document format java** se nachází v níže uvedeném cyklu. Prochází každý soubor, určuje jeho typ a kopíruje jej do příslušné složky.

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

`switch` blok lze rozšířit tak, aby pokrýval všechny formáty, které vás zajímají. Každý případ vypíše přátelskou zprávu a poté přesune soubor do odpovídající složky.

## Kompletní zdrojový kód pro detekci formátu dokumentu java

Níže je kompletní, připravený příklad, který kombinuje nastavení adresářů a logiku detekce. Zkopírujte jej do Java třídy, upravte základní cestu a spusťte jej proti složce smíšených dokumentů.

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

## Časté problémy a řešení

| Problém | Proč k tomu dochází | Jak opravit |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Soubor je poškozený nebo používá formát, který není Word. | Ověřte příponu souboru nebo přidejte záložní řešení, které jej přesune do složky *Unknown* (již ve vzorku). |
| **Encrypted files throw an exception** | API se snaží načíst obsah před kontrolou šifrování. | Vždy zavolejte `info.isEncrypted()` před jakoukoli jinou operací s dokumentem. |
| **Directory creation fails on Linux** | Nedostatečná oprávnění nebo chybějící nadřazená složka. | Zajistěte, aby Java proces měl právo zápisu a aby základní cesta existovala. |

## Často kladené otázky

**Q: Jak nainstaluji Aspose.Words pro Java?**  
A: Aspose.Words pro Java můžete stáhnout [zde](https://releases.aspose.com/words/java/) a postupovat podle poskytnutých instalačních instrukcí.

**Q: Jaké formáty dokumentů jsou podporovány pro detekci?**  
A: Aspose.Words dokáže detekovat DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML a starší formáty před rokem 97, mezi jinými.

**Q: Dokáže tento kód pracovat s dokumenty chráněnými heslem?**  
A: Ano. Příznak `FileFormatInfo.isEncrypted()` identifikuje šifrované soubory, což vám umožní je přesunout do zabezpečené složky, aniž byste je otevírali.

**Q: Má skenování velkých složek dopad na výkon?**  
A: Detekce čte pouze hlavičku souboru, takže i tisíce souborů jsou zpracovány rychle. Pro velmi velké dávky zvažte paralelní streamy.

**Q: Jak mohu rozšířit skript pro konverzi nepodporovaných formátů?**  
A: Po detekci můžete zavolat `Document.save` s požadovaným výstupním formátem pro jakýkoli podporovaný zdrojový typ.

## Závěr

Používáním **detect document format java** s Aspose.Words získáte spolehlivý způsob, jak automaticky řadit, karanténovat nebo konvertovat soubory související s Wordem. Ukázkový kód demonstruje, jak vytvořit čistou hierarchii složek, identifikovat formát každého souboru a přesunout jej podle toho – ušetří vám čas a sníží manuální chyby.

---

**Poslední aktualizace:** 2026-02-22  
**Testováno s:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}