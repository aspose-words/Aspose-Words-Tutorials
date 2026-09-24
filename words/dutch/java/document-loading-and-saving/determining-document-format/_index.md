---
date: 2026-02-22
description: Leer hoe u documentformaten in Java kunt detecteren met Aspose.Words
  en bestanden automatisch op formaat kunt verplaatsen. Identificeer DOC, DOCX en
  meer.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Documentformaat detecteren in Java met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detect document format java met Aspose.Words voor Java

Wanneer u **detect document format java** moet uitvoeren in een batch bestanden, kan de mogelijkheid om ze automatisch in de juiste mappen te sorteren uren handmatig werk besparen. In deze tutorial laten we zien hoe Aspose.Words voor Java het eenvoudig maakt om Word, RTF, HTML, ODT en vele andere formaten te identificeren, en vervolgens **bestanden per formaat** te verplaatsen naar georganiseerde directories.

## Quick Answers
- **Wat betekent “detect document format java”?** Het is het proces waarbij programmatic matig het bestandsformaat van een tekstverwerkingsdocument (DOC, DOCX, RTF, enz.) wordt geïdentificeerd met Java‑code.  
- **Welke bibliotheek biedt deze functionaliteit?** Aspose.Words voor Java biedt de `FileFormatUtil.detectFileFormat`‑API.  
- **Kan het hulpprogramma ook versleutelde bestanden verwerken?** Ja – de `FileFormatInfo.isEncrypted()`‑vlag geeft aan of een document met een wachtwoord is beveiligd.  
- **Heb ik een licentie nodig voor productiegebruik?** Een commerciële Aspose.Words‑licentie is vereist voor niet‑evaluatie‑implementaties.  
- **Is het mogelijk om bestanden automatisch te verplaatsen na detectie?** Absoluut – combineer het detectieresultaat met `FileUtils.copyFile` om bestanden in aangepaste mappen te sorteren.

## What is detect document format java?
`detect document format java` verwijst naar het gebruik van Java‑code om de binaire header van een bestand te inspecteren en te bepalen tot welk tekstverwerkingsformaat het behoort (bijv. DOC, DOCX, ODT). Aspose.Words leest het bestand zonder het volledige document te laden, waardoor de bewerking snel en geheugen‑efficiënt is.

## Why move files by format?
Documenten organiseren op hun oorspronkelijke formaat vereenvoudigt verdere verwerking:

- **Batchconversies** worden eenvoudig wanneer alle DOCX‑bestanden zich in één map bevinden.  
- **Legacy‑ondersteuning**: u kunt pre‑97 Word‑bestanden isoleren voor speciale behandeling.  
- **Beveiliging**: versleutelde documenten kunnen automatisch in quarantaine worden geplaatst.  

## Prerequisites

Voordat we beginnen, zorg dat u het volgende heeft:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (download de nieuwste versie)  
- Java Development Kit (JDK) 8 of hoger geïnstalleerd  
- Basiskennis van Java I/O en streams  

## Step 1: Set up directories for each format

We maken eerst een nette mapstructuur waarin de gedetecteerde bestanden worden verplaatst. Dit houdt de workflow overzichtelijk en maakt het later eenvoudig om nieuwe formaat‑categorieën toe te voegen.

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

> **Pro tip:** Gebruik absolute paden of configureer de basismap via een properties‑bestand om hard‑coded paden in productcode te vermijden.

## Step 2: Detect the document format and move files

De kern van **detect document format java** bevindt zich in de onderstaande lus. Hij scant elk bestand, bepaalt het type en kopieert het naar de juiste map.

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

Het `switch`‑blok kan worden uitgebreid om elk formaat dat u nodig heeft te ondersteunen. Elke case geeft een vriendelijke melding weer en verplaatst vervolgens het bestand naar de bijbehorende map.

## Complete source code for detecting document format java

Hieronder vindt u het volledige, kant‑klaar voorbeeld dat de map‑opzet en detectielogica combineert. Kopieer het naar een Java‑klasse, pas het basispad aan en voer het uit op een map met gemengde documenten.

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
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Het bestand is corrupt of gebruikt een niet‑Word‑formaat. | Controleer de bestandsextensie, of voeg een fallback toe om het naar de *Unknown*‑map te verplaatsen (reeds in het voorbeeld). |
| **Encrypted files throw an exception** | De API probeert de inhoud te lezen voordat de versleuteling wordt gecontroleerd. | Roep altijd `info.isEncrypted()` aan vóór enige andere bewerking op het document. |
| **Directory creation fails on Linux** | Onvoldoende rechten of ontbrekende bovenliggende map. | Zorg dat het Java‑proces schrijfrechten heeft en dat het basispad bestaat. |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: U kunt Aspose.Words for Java downloaden van [hier](https://releases.aspose.com/words/java/) en de installatie‑instructies volgen.

**Q: What document formats are supported for detection?**  
A: Aspose.Words kan DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML en oudere pre‑97 formaten detecteren, onder andere.

**Q: Can this code handle password‑protected documents?**  
A: Ja. De `FileFormatInfo.isEncrypted()`‑vlag identificeert versleutelde bestanden, zodat u ze naar een beveiligde map kunt verplaatsen zonder ze te openen.

**Q: Is there a performance impact when scanning large folders?**  
A: Detectie leest alleen de bestandsheader, dus zelfs duizenden bestanden worden snel verwerkt. Voor zeer grote batches kunt u overwegen parallelle streams te gebruiken.

**Q: How can I extend the script to convert unsupported formats?**  
A: Na detectie kunt u `Document.save` aanroepen met het gewenste uitvoerformaat voor elk ondersteund bron‑type.

## Conclusion

Door **detect document format java** te gebruiken met Aspose.Words, krijgt u een betrouwbare manier om Word‑gerelateerde bestanden automatisch te sorteren, in quarantaine te plaatsen of te converteren. De voorbeeldcode laat zien hoe u een nette maphiërarchie maakt, elk bestand’s formaat identificeert en het vervolgens verplaatst – waardoor u tijd bespaart en handmatige fouten vermindert.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}