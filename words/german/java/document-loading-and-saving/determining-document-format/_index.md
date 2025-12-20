---
date: 2025-12-20
description: Erfahren Sie, wie Sie Dateien nach Typ organisieren und Dokumentformate
  in Java mit Aspose.Words erkennen. Unterstützt DOC, DOCX, RTF und mehr.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Dateien nach Typ organisieren mit Aspose.Words für Java
url: /de/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dateien nach Typ organisieren mit Aspose.Words für Java

Wenn Sie in einer Java‑Anwendung **Dateien nach Typ organisieren** müssen, ist der erste Schritt, das Format jedes Dokuments zuverlässig zu bestimmen. Aspose.Words für Java macht das einfach und ermöglicht das Erkennen von DOC, DOCX, RTF, HTML, ODT und vielen anderen Formaten – sogar verschlüsselte oder unbekannte Dateien. In diesem Leitfaden zeigen wir, wie Sie Ordner einrichten, Dateiformate erkennen und Ihre Dateien automatisch sortieren.

## Quick Answers
- **Was bedeutet „Dateien nach Typ organisieren“?** Es bedeutet, Dokumente automatisch in Ordner zu verschieben, basierend auf ihrem erkannten Format (z. B. DOCX, PDF, RTF).  
- **Welche Bibliothek hilft beim Erkennen des Dateiformats in Java?** Aspose.Words für Java stellt `FileFormatUtil.detectFileFormat()` bereit.  
- **Kann die API unbekannte Dateitypen identifizieren?** Ja – sie gibt `LoadFormat.UNKNOWN` zurück für nicht unterstützte oder nicht erkennbare Dateien.  
- **Wird die Erkennung verschlüsselter Dokumente unterstützt?** Absolut; das Flag `FileFormatInfo.isEncrypted()` zeigt an, ob eine Datei passwortgeschützt ist.  
- **Benötige ich eine Lizenz für den Produktionseinsatz?** Für kommerzielle Bereitstellungen ist eine gültige Aspose.Words‑Lizenz erforderlich.

## Introduction: Organize Files by Type with Aspose.Words for Java

Beim Arbeiten mit der Dokumentenverarbeitung in Java ist es entscheidend, das Format der zu verarbeitenden Dateien zu bestimmen. Aspose.Words für Java bietet leistungsstarke Funktionen für **detect file format java**, und wir führen Sie durch den Prozess, Ihre Dateien effizient zu organisieren.

## Prerequisites

Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) auf Ihrem System installiert
- Grundkenntnisse in der Java‑Programmierung

## Step 1: Directory Setup

Zuerst müssen wir die notwendigen Verzeichnisse einrichten, um unsere Dateien effektiv zu organisieren. Wir erstellen Ordner für verschiedene Dokumenttypen.

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

Wir haben Verzeichnisse für unterstützte, unbekannte, verschlüsselte und Pre‑97‑Dokumenttypen erstellt.

## Step 2: Detecting Document Format

Jetzt erkennen wir das Format der Dokumente in unseren Verzeichnissen. Wir verwenden Aspose.Words für Java, um dies zu erreichen.

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

In diesem Snippet iterieren wir über die Dateien, **detect file format java**, und ordnen sie den entsprechenden Ordnern zu.

## Complete Source Code For Determining Document Format in Aspose.Words for Java

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

## How to Detect File Format Java

Die Methode `FileFormatUtil.detectFileFormat()` untersucht den Dateikopf und gibt ein `FileFormatInfo`‑Objekt zurück. Dieses Objekt teilt Ihnen das **load format**, ob die Datei verschlüsselt ist und weitere nützliche Metadaten mit. Mit diesen Informationen können Sie programmgesteuert **identify unknown file types** und entscheiden, wie jede Datei verarbeitet werden soll.

## Identify Unknown File Types

Wenn die API `LoadFormat.UNKNOWN` zurückgibt, ist die Datei entweder beschädigt oder verwendet ein Format, das Aspose.Words nicht unterstützt. In unserem Beispielcode verschieben wir diese Dateien in den **Unknown**‑Ordner, damit Sie sie später prüfen können.

## Common Issues and Solutions

| Issue | Reason | Fix |
|-------|--------|-----|
| Dateien werden immer im *Supported*‑Ordner abgelegt | `FileFormatUtil` konnte den Header nicht lesen (z. B. Datei ist leer) | Stellen Sie sicher, dass Sie den korrekten Dateipfad übergeben und die Datei nicht null‑Byte groß ist. |
| Verschlüsselte Dateien werfen eine Ausnahme | Versuch, ohne Behandlung der Verschlüsselung zu lesen | Verwenden Sie die Prüfung `info.isEncrypted()` bevor Sie weitere Verarbeitung durchführen, wie im Code gezeigt. |
| Pre‑97‑Word‑Dokumente werden nicht erkannt | Ältere Formate benötigen den Fall `DOC_PRE_WORD_60` | Belassen Sie den Block `case LoadFormat.DOC_PRE_WORD_60`, um sie in den *Pre97*‑Ordner zu leiten. |

## Frequently Asked Questions

### How do I install Aspose.Words for Java?

Sie können Aspose.Words für Java von [hier](https://releases.aspose.com/words/java/) herunterladen und den bereitgestellten Installationsanweisungen folgen.

### What are the supported document formats?

Aspose.Words für Java unterstützt verschiedene Dokumentformate, darunter DOC, DOCX, RTF, HTML, ODT und mehr. Eine vollständige Liste finden Sie in der offiziellen Dokumentation.

### How can I detect encrypted documents using Aspose.Words for Java?

Verwenden Sie die Methode `FileFormatUtil.detectFileFormat()`; das zurückgegebene Flag `FileFormatInfo.isEncrypted()` weist auf eine Verschlüsselung hin, wie in diesem Leitfaden demonstriert.

### Are there any limitations when working with older document formats?

Ältere Formate wie MS Word 6 oder Word 95 können moderne Funktionen vermissen und Kompatibilitätsprobleme aufweisen. Es wird empfohlen, sie nach Möglichkeit in neuere Formate zu konvertieren.

### Can I automate document format detection in my Java application?

Ja, binden Sie den bereitgestellten Code in die Verarbeitungspipeline Ihrer Anwendung ein. Dadurch wird eine automatische Sortierung und Handhabung basierend auf den erkannten Formaten ermöglicht.

---

**Last Updated:** 2025-12-20  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}