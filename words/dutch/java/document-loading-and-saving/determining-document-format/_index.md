---
date: 2025-12-20
description: Leer hoe je bestanden op type kunt organiseren en documentformaten kunt
  detecteren in Java met Aspose.Words. Ondersteunt DOC, DOCX, RTF en meer.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Bestanden organiseren op type met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bestanden organiseren op type met Aspose.Words voor Java

Wanneer je **bestanden op type** moet organiseren in een Java‑applicatie, is de eerste stap om betrouwbaar het formaat van elk document te bepalen. Aspose.Words voor Java maakt dit eenvoudig, waardoor je DOC, DOCX, RTF, HTML, ODT en vele andere formaten kunt detecteren – zelfs versleutelde of onbekende bestanden. In deze gids lopen we door het instellen van mappen, het detecteren van bestandsformaten en het automatisch sorteren van je bestanden.

## Snelle antwoorden
- **Wat betekent “bestanden organiseren op type”?** Het betekent dat documenten automatisch worden verplaatst naar mappen op basis van hun gedetecteerde formaat (bijv. DOCX, PDF, RTF).  
- **Welke bibliotheek helpt bij het detecteren van bestandsformaat in Java?** Aspose.Words voor Java biedt `FileFormatUtil.detectFileFormat()`.  
- **Kan de API onbekende bestandstypen identificeren?** Ja – het retourneert `LoadFormat.UNKNOWN` voor niet‑ondersteunde of niet‑herkenbare bestanden.  
- **Wordt detectie van versleutelde documenten ondersteund?** Absoluut; de `FileFormatInfo.isEncrypted()`‑vlag geeft aan of een bestand met een wachtwoord is beveiligd.  
- **Heb ik een licentie nodig voor productiegebruik?** Een geldige Aspose.Words‑licentie is vereist voor commerciële implementaties.

## Introductie: Bestanden organiseren op type met Aspose.Words voor Java

Wanneer je werkt met documentverwerking in Java, is het cruciaal om het formaat van de bestanden die je verwerkt te bepalen. Aspose.Words voor Java biedt krachtige functies voor **detect file format java**, en we lopen je door het proces van het efficiënt organiseren van je bestanden.

## Vereisten

Voordat we beginnen, zorg dat je de volgende vereisten hebt:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) geïnstalleerd op je systeem
- Basiskennis van Java-programmeren

## Stap 1: Mapstructuur instellen

Eerst moeten we de benodigde mappen opzetten om onze bestanden effectief te organiseren. We zullen mappen maken voor verschillende documenttypen.

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

We hebben mappen gemaakt voor ondersteunde, onbekende, versleutelde en pre‑97 documenttypen.

## Stap 2: Documentformaat detecteren

Laten we nu het formaat van de documenten in onze mappen detecteren. We gebruiken Aspose.Words voor Java om dit te bereiken.

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

In dit fragment itereren we door de bestanden, **detect file format java**, en organiseren ze in de juiste mappen.

## Complete broncode voor het bepalen van documentformaat in Aspose.Words voor Java

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

## Hoe bestandsformaat detecteren in Java

De `FileFormatUtil.detectFileFormat()`‑methode inspecteert de bestandsheader en retourneert een `FileFormatInfo`‑object. Dit object geeft je het **load format**, of het bestand versleuteld is, en andere nuttige metadata. Met deze informatie kun je programmatisch **identify unknown file types** identificeren en bepalen hoe elk bestand te verwerken.

## Onbekende bestandstypen identificeren

Wanneer de API `LoadFormat.UNKNOWN` retourneert, is het bestand ofwel beschadigd of gebruikt een formaat dat Aspose.Words niet ondersteunt. In onze voorbeeldcode verplaatsen we die bestanden naar de **Unknown**‑map zodat je ze later kunt bekijken.

## Veelvoorkomende problemen en oplossingen

| Issue | Reason | Fix |
|-------|--------|-----|
| Bestanden worden altijd geplaatst in de *Supported* map | `FileFormatUtil` kon de header niet lezen (bijv. bestand is leeg) | Zorg ervoor dat je het juiste bestandspad doorgeeft en dat het bestand niet nul‑bytes is. |
| Versleutelde bestanden veroorzaken een uitzondering | Poging te lezen zonder versleuteling af te handelen | Gebruik `info.isEncrypted()` controle vóór verdere verwerking, zoals in de code getoond. |
| Pre‑97 Word‑documenten niet gedetecteerd | Oudere formaten hebben de `DOC_PRE_WORD_60`‑case nodig | Behoud de `case LoadFormat.DOC_PRE_WORD_60`‑blok om ze naar de *Pre97* map te leiden. |

## Veelgestelde vragen

### Hoe installeer ik Aspose.Words voor Java?

Je kunt Aspose.Words voor Java downloaden van [hier](https://releases.aspose.com/words/java/) en de meegeleverde installatie‑instructies volgen.

### Wat zijn de ondersteunde documentformaten?

Aspose.Words voor Java ondersteunt verschillende documentformaten, waaronder DOC, DOCX, RTF, HTML, ODT en meer. Raadpleeg de officiële documentatie voor een volledige lijst.

### Hoe kan ik versleutelde documenten detecteren met Aspose.Words voor Java?

Gebruik de `FileFormatUtil.detectFileFormat()`‑methode; de geretourneerde `FileFormatInfo.isEncrypted()`‑vlag geeft versleuteling aan, zoals in deze gids gedemonstreerd.

### Zijn er beperkingen bij het werken met oudere documentformaten?

Oudere formaten zoals MS Word 6 of Word 95 kunnen moderne functies missen en kunnen compatibiliteitsproblemen hebben. Overweeg ze waar mogelijk naar nieuwere formaten te converteren.

### Kan ik documentformaatdetectie automatiseren in mijn Java‑applicatie?

Ja, integreer de meegeleverde code in de verwerkings‑pipeline van je applicatie. Dit maakt automatische sortering en verwerking mogelijk op basis van gedetecteerde formaten.

---

**Laatst bijgewerkt:** 2025-12-20  
**Getest met:** Aspose.Words for Java 24.12 (latest)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}