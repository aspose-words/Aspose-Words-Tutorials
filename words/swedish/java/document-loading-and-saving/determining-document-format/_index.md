---
title: Bestämma dokumentformat i Aspose.Words för Java
linktitle: Bestämma dokumentformat
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du upptäcker dokumentformat i Java med Aspose.Words. Identifiera DOC, DOCX och mer. Organisera filer effektivt.
weight: 25
url: /sv/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bestämma dokumentformat i Aspose.Words för Java


## Introduktion till bestämning av dokumentformat i Aspose.Words för Java

När du arbetar med dokumentbehandling i Java är det avgörande att bestämma formatet på filerna du har att göra med. Aspose.Words för Java tillhandahåller kraftfulla funktioner för att identifiera dokumentformat, och vi guidar dig genom processen.

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar:

- [Aspose.Words för Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) installerat på ditt system
- Grundläggande kunskaper i Java-programmering

## Steg 1: Kataloginställning

Först måste vi skapa de nödvändiga katalogerna för att organisera våra filer effektivt. Vi skapar kataloger för olika dokumenttyper.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Skapa katalogerna om de inte redan finns.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Vi har skapat kataloger för stödda, okända, krypterade och före 97 dokumenttyper.

## Steg 2: Identifiera dokumentformat

Låt oss nu upptäcka formatet på dokumenten i våra kataloger. Vi kommer att använda Aspose.Words för Java för att uppnå detta.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Visa dokumenttypen
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Lägg till ärenden för andra dokumentformat efter behov
    }

    // Hantera krypterade dokument
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Hantera andra dokumenttyper
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

I det här kodavsnittet itererar vi igenom filerna, upptäcker deras format och organiserar dem i respektive katalog.

## Komplett källkod för att bestämma dokumentformat i Aspose.Words för Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Skapa katalogerna om de inte redan finns.
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
            // Visa dokumenttypen
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

## Slutsats

Att bestämma dokumentformat i Aspose.Words för Java är avgörande för effektiv dokumentbehandling. Med stegen som beskrivs i den här guiden kan du identifiera dokumenttyper och hantera dem därefter i dina Java-applikationer.

## FAQ's

### Hur installerar jag Aspose.Words för Java?

 Du kan ladda ner Aspose.Words för Java från[här](https://releases.aspose.com/words/java/)och följ installationsanvisningarna.

### Vilka är de dokumentformat som stöds?

Aspose.Words för Java stöder olika dokumentformat, inklusive DOC, DOCX, RTF, HTML och mer. Du kan hänvisa till dokumentationen för en fullständig lista.

### Hur kan jag upptäcka krypterade dokument med Aspose.Words för Java?

 Du kan använda`FileFormatUtil.detectFileFormat()` metod för att upptäcka krypterade dokument, som visas i den här guiden.

### Finns det några begränsningar när man arbetar med äldre dokumentformat?

Äldre dokumentformat, som MS Word 6 eller Word 95, kan ha begränsningar när det gäller funktioner och kompatibilitet med moderna applikationer. Överväg att uppgradera eller konvertera dessa dokument vid behov.

### Kan jag automatisera identifiering av dokumentformat i min Java-applikation?

Ja, du kan automatisera identifiering av dokumentformat genom att integrera den medföljande koden i din Java-applikation. Detta gör att du kan bearbeta dokument baserat på deras upptäckta format.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
