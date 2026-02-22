---
date: 2026-02-22
description: Lär dig hur du upptäcker dokumentformat i Java med Aspose.Words och automatiskt
  flyttar filer efter format. Identifiera DOC, DOCX och mer.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Detektera dokumentformat i Java med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/determining-document-format/
weight: 25
---

}} etc.

Also keep markdown tables.

Translate bullet points, sentences.

Let's produce final Swedish version.

Be careful with "detect document format java" phrase: maybe keep as is? The phrase is technical term; we can keep as is but maybe translate surrounding text. Keep the phrase as is because it's a term. But can also keep lower-case. We'll keep as is.

Also "Aspose.Words for Java" stays.

Let's translate.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detect document format java using Aspose.Words for Java

När du behöver **detect document format java** i en mängd filer, kan förmågan att automatiskt sortera dem i rätt mappar spara timmar av manuellt arbete. I den här handledningen visar vi hur Aspose.Words for Java gör det enkelt att identifiera Word, RTF, HTML, ODT och många andra format, och sedan **move files by format** till organiserade kataloger.

## Quick Answers
- **What does “detect document format java” mean?** Det är processen att programmässigt identifiera ett dokuments Word‑behandlingsformat (DOC, DOCX, RTF osv.) med Java‑kod.  
- **Which library provides this capability?** Aspose.Words for Java erbjuder API‑metoden `FileFormatUtil.detectFileFormat`.  
- **Can the utility also handle encrypted files?** Ja – flaggan `FileFormatInfo.isEncrypted()` talar om för dig om ett dokument är lösenordsskyddat.  
- **Do I need a license for production use?** En kommersiell Aspose.Words‑licens krävs för icke‑utvärderingsdistributioner.  
- **Is it possible to move files automatically after detection?** Absolut – kombinera detekteringsresultatet med `FileUtils.copyFile` för att sortera filer till egna mappar.

## What is detect document format java?
`detect document format java` avser att använda Java‑kod för att undersöka ett fils binära header och avgöra vilket Word‑behandlingsformat det tillhör (t.ex. DOC, DOCX, ODT). Aspose.Words läser filen utan att helt ladda dokumentet, vilket gör operationen snabb och minnes‑effektiv.

## Why move files by format?
Att organisera dokument efter deras ursprungsformat förenklar efterföljande bearbetning:

- **Batch conversions** blir enkla när alla DOCX‑filer ligger i en och samma mapp.  
- **Legacy support**: du kan isolera pre‑97 Word‑filer för särskild hantering.  
- **Security**: krypterade dokument kan automatiskt karantänas.  

## Prerequisites

Innan vi börjar, se till att du har:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (ladda ner den senaste versionen)  
- Java Development Kit (JDK) 8 eller högre installerat  
- Grundläggande kunskap om Java I/O och streams  

## Step 1: Set up directories for each format

Vi skapar först en ren mappstruktur där de detekterade filerna kommer att flyttas. Detta håller arbetsflödet prydligt och gör det enkelt att lägga till nya formatkategorier senare.

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

> **Pro tip:** Använd absoluta sökvägar eller konfigurera baskatalogen via en properties‑fil för att undvika hårdkodade sökvägar i produktionskod.

## Step 2: Detect the document format and move files

Kärnan i **detect document format java** finns i loopen nedan. Den skannar varje fil, bestämmer dess typ och kopierar den till rätt mapp.

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

`switch`‑blocket kan utökas för att täcka alla format du är intresserad av. Varje case skriver ut ett vänligt meddelande och flyttar sedan filen till den matchande mappen.

## Complete source code for detecting document format java

Nedan är det fullständiga, körklara exemplet som kombinerar kataloginställning och detekteringslogik. Kopiera det till en Java‑klass, justera bas‑sökvägen och kör det mot en mapp med blandade dokument.

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

## Common issues and troubleshooting

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Filen är korrupt eller använder ett icke‑Word‑format. | Verifiera filändelsen, eller lägg till en fallback för att flytta den till *Unknown*-mappen (redan i exemplet). |
| **Encrypted files throw an exception** | API:t försöker läsa innehållet innan kryptering kontrolleras. | Anropa alltid `info.isEncrypted()` innan någon annan operation på dokumentet. |
| **Directory creation fails on Linux** | Otillräckliga rättigheter eller saknad föräldramapp. | Säkerställ att Java‑processen har skrivrättigheter och att bas‑sökvägen finns. |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: Du kan ladda ner Aspose.Words for Java från [here](https://releases.aspose.com/words/java/) och följa installationsinstruktionerna som medföljer.

**Q: What document formats are supported for detection?**  
A: Aspose.Words kan detektera DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML samt äldre pre‑97‑format, bland andra.

**Q: Can this code handle password‑protected documents?**  
A: Ja. Flaggan `FileFormatInfo.isEncrypted()` identifierar krypterade filer, så att du kan flytta dem till en säker mapp utan att öppna dem.

**Q: Is there a performance impact when scanning large folders?**  
A: Detektering läser bara filens header, så även tusentals filer behandlas snabbt. För mycket stora batcher kan du överväga parallella streams.

**Q: How can I extend the script to convert unsupported formats?**  
A: Efter detektering kan du anropa `Document.save` med önskat utdataformat för vilken som helst av de stödjade källtyperna.

## Conclusion

Genom att använda **detect document format java** med Aspose.Words får du ett pålitligt sätt att automatiskt sortera, karantänsätta eller konvertera Word‑relaterade filer. Exempelkoden visar hur du skapar en ren mapphierarki, identifierar varje fils format och flyttar den därefter – vilket sparar tid och minskar manuella fel.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}