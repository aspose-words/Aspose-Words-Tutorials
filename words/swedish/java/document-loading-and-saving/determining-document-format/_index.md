---
date: 2025-12-20
description: Lär dig hur du organiserar filer efter typ och upptäcker dokumentformat
  i Java med Aspose.Words. Stöder DOC, DOCX, RTF och mer.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organisera filer efter typ med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organisera filer efter typ med Aspose.Words för Java

När du behöver **organisera filer efter typ** i en Java‑applikation är första steget att på ett pålitligt sätt bestämma varje dokuments format. Aspose.Words för Java gör detta enkelt och låter dig upptäcka DOC, DOCX, RTF, HTML, ODT och många andra format – även krypterade eller okända filer. I den här guiden går vi igenom hur du skapar mappar, upptäcker filformat och automatiskt sorterar dina filer.

## Snabba svar
- **Vad betyder “organisera filer efter typ”?** Det betyder att automatiskt flytta dokument till mappar baserat på deras upptäckta format (t.ex. DOCX, PDF, RTF).  
- **Vilket bibliotek hjälper till att upptäcka filformat i Java?** Aspose.Words för Java tillhandahåller `FileFormatUtil.detectFileFormat()`.  
- **Kan API:et identifiera okända filtyper?** Ja – det returnerar `LoadFormat.UNKNOWN` för format som inte stöds eller som inte kan kännas igen.  
- **Stöds upptäckt av krypterade dokument?** Absolut; flaggan `FileFormatInfo.isEncrypted()` visar om en fil är lösenordsskyddad.  
- **Behöver jag en licens för produktionsanvändning?** En giltig Aspose.Words‑licens krävs för kommersiella implementationer.

## Introduktion: Organisera filer efter typ med Aspose.Words för Java

När du arbetar med dokumentbehandling i Java är det avgörande att fastställa formatet på de filer du hanterar. Aspose.Words för Java erbjuder kraftfulla funktioner för **detect file format java**, och vi guidar dig genom processen att organisera dina filer på ett effektivt sätt.

## Förutsättningar

Innan vi börjar, se till att du har följande:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) installerat på ditt system
- Grundläggande kunskaper i Java‑programmering

## Steg 1: Mappstruktur

Först måste vi skapa de nödvändiga mapparna för att organisera våra filer på ett effektivt sätt. Vi kommer att skapa mappar för olika dokumenttyper.

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

Vi har skapat mappar för stödda, okända, krypterade och pre‑97‑dokumenttyper.

## Steg 2: Upptäcka dokumentformat

Nu ska vi upptäcka formatet på dokumenten i våra mappar. Vi använder Aspose.Words för Java för att uppnå detta.

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

I detta kodexempel itererar vi genom filerna, **detect file format java**, och organiserar dem i lämpliga mappar.

## Komplett källkod för att bestämma dokumentformat i Aspose.Words för Java

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

## Hur man upptäcker filformat i Java

Metoden `FileFormatUtil.detectFileFormat()` undersöker filens huvud och returnerar ett `FileFormatInfo`‑objekt. Detta objekt berättar för dig **load format**, om filen är krypterad och annan användbar metadata. Med denna information kan du programatiskt **identify unknown file types** och besluta hur varje fil ska behandlas.

## Identifiera okända filtyper

När API:et returnerar `LoadFormat.UNKNOWN` är filen antingen korrupt eller använder ett format som Aspose.Words inte stödjer. I vårt exempel flyttar vi dessa filer till **Unknown**‑mappen så att du kan granska dem senare.

## Vanliga problem och lösningar

| Problem | Orsak | Lösning |
|---------|-------|---------|
| Filer placeras alltid i *Supported*-mappen | `FileFormatUtil` kunde inte läsa huvudet (t.ex. filen är tom) | Säkerställ att du anger rätt filsökväg och att filen inte är tom (0 byte). |
| Krypterade filer kastar ett undantag | Försök att läsa utan att hantera kryptering | Använd `info.isEncrypted()`‑kontrollen innan vidare behandling, som visas i koden. |
| Pre‑97 Word‑dokument upptäcks inte | Äldre format kräver `DOC_PRE_WORD_60`‑fallet | Behåll `case LoadFormat.DOC_PRE_WORD_60`‑blocket för att dirigera dem till *Pre97*-mappen. |

## Vanliga frågor

### Hur installerar jag Aspose.Words för Java?

Du kan ladda ner Aspose.Words för Java från [här](https://releases.aspose.com/words/java/) och följa installationsinstruktionerna som medföljer.

### Vilka dokumentformat stöds?

Aspose.Words för Java stödjer olika dokumentformat, inklusive DOC, DOCX, RTF, HTML, ODT och fler. Se den officiella dokumentationen för en komplett lista.

### Hur kan jag upptäcka krypterade dokument med Aspose.Words för Java?

Använd metoden `FileFormatUtil.detectFileFormat()`; den returnerade flaggan `FileFormatInfo.isEncrypted()` indikerar kryptering, som demonstrerat i den här guiden.

### Finns det begränsningar när man arbetar med äldre dokumentformat?

Äldre format som MS Word 6 eller Word 95 kan sakna moderna funktioner och kan ha kompatibilitetsproblem. Överväg att konvertera dem till nyare format när det är möjligt.

### Kan jag automatisera dokumentformatdetektering i min Java‑applikation?

Ja, integrera den medföljande koden i din applikations bearbetningspipeline. Detta möjliggör automatisk sortering och hantering baserat på upptäckta format.

---

**Senast uppdaterad:** 2025-12-20  
**Testad med:** Aspose.Words för Java 24.12 (senaste)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}