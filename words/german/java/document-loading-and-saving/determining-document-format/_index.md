---
title: Bestimmen des Dokumentformats in Aspose.Words für Java
linktitle: Festlegen des Dokumentformats
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words Dokumentformate in Java erkennen. Identifizieren Sie DOC, DOCX und mehr. Organisieren Sie Dateien effizient.
weight: 25
url: /de/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bestimmen des Dokumentformats in Aspose.Words für Java


## Einführung in die Bestimmung des Dokumentformats in Aspose.Words für Java

Bei der Dokumentverarbeitung in Java ist es wichtig, das Format der Dateien zu bestimmen, mit denen Sie arbeiten. Aspose.Words für Java bietet leistungsstarke Funktionen zum Identifizieren von Dokumentformaten und wir führen Sie durch den Prozess.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

- [Aspose.Words für Java](https://releases.aspose.com/words/java/)
- Auf Ihrem System ist Java Development Kit (JDK) installiert.
- Grundkenntnisse der Java-Programmierung

## Schritt 1: Verzeichnis einrichten

Zuerst müssen wir die notwendigen Verzeichnisse einrichten, um unsere Dateien effektiv zu organisieren. Wir erstellen Verzeichnisse für verschiedene Dokumenttypen.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Erstellen Sie die Verzeichnisse, falls sie noch nicht vorhanden sind.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Wir haben Verzeichnisse für unterstützte, unbekannte, verschlüsselte und vor 97 veröffentlichte Dokumenttypen erstellt.

## Schritt 2: Dokumentformat erkennen

Lassen Sie uns nun das Format der Dokumente in unseren Verzeichnissen ermitteln. Dazu verwenden wir Aspose.Words für Java.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Anzeige des Dokumenttyps
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Fügen Sie nach Bedarf Fälle für andere Dokumentformate hinzu
    }

    // Umgang mit verschlüsselten Dokumenten
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Umgang mit anderen Dokumenttypen
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

In diesem Codeausschnitt durchlaufen wir die Dateien, erkennen ihre Formate und organisieren sie in den entsprechenden Verzeichnissen.

## Vollständiger Quellcode zur Bestimmung des Dokumentformats in Aspose.Words für Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Erstellen Sie die Verzeichnisse, falls sie noch nicht vorhanden sind.
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
            // Anzeige des Dokumenttyps
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

## Abschluss

Das Bestimmen von Dokumentformaten in Aspose.Words für Java ist für eine effiziente Dokumentverarbeitung unerlässlich. Mit den in diesem Handbuch beschriebenen Schritten können Sie Dokumenttypen identifizieren und sie in Ihren Java-Anwendungen entsprechend verarbeiten.

## Häufig gestellte Fragen

### Wie installiere ich Aspose.Words für Java?

 Sie können Aspose.Words für Java herunterladen von der[Hier](https://releases.aspose.com/words/java/)und befolgen Sie die bereitgestellten Installationsanweisungen.

### Welche Dokumentformate werden unterstützt?

Aspose.Words für Java unterstützt verschiedene Dokumentformate, darunter DOC, DOCX, RTF, HTML und mehr. Eine vollständige Liste finden Sie in der Dokumentation.

### Wie kann ich mit Aspose.Words für Java verschlüsselte Dokumente erkennen?

 Sie können die`FileFormatUtil.detectFileFormat()` Methode zum Erkennen verschlüsselter Dokumente, wie in diesem Handbuch gezeigt.

### Gibt es Einschränkungen bei der Arbeit mit älteren Dokumentformaten?

Ältere Dokumentformate wie MS Word 6 oder Word 95 weisen möglicherweise Einschränkungen hinsichtlich der Funktionen und der Kompatibilität mit modernen Anwendungen auf. Erwägen Sie bei Bedarf ein Upgrade oder eine Konvertierung dieser Dokumente.

### Kann ich die Dokumentformaterkennung in meiner Java-Anwendung automatisieren?

Ja, Sie können die Dokumentformaterkennung automatisieren, indem Sie den bereitgestellten Code in Ihre Java-Anwendung integrieren. Auf diese Weise können Sie Dokumente basierend auf ihren erkannten Formaten verarbeiten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
