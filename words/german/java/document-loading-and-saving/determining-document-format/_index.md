---
date: 2026-02-22
description: Erfahren Sie, wie Sie das Dokumentformat in Java mit Aspose.Words erkennen
  und Dateien automatisch nach Format verschieben. Identifizieren Sie DOC, DOCX und
  weitere.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Dokumentformat in Java mit Aspose.Words für Java erkennen
url: /de/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentformat in Java mit Aspose.Words für Java erkennen

Wenn Sie **detect document format java** in einem Stapel von Dateien benötigen, kann die Möglichkeit, sie automatisch in die richtigen Ordner zu sortieren, Stunden manueller Arbeit sparen. In diesem Tutorial zeigen wir, wie Aspose.Words für Java das Erkennen von Word, RTF, HTML, ODT und vielen anderen Formaten erleichtert und dann **Dateien nach Format verschieben** in organisierte Verzeichnisse.

## Schnelle Antworten
- **Was bedeutet “detect document format java”?** Es ist der Prozess, programmgesteuert das Word‑Verarbeitungsformat (DOC, DOCX, RTF usw.) einer Datei mithilfe von Java‑Code zu identifizieren.  
- **Welche Bibliothek bietet diese Fähigkeit?** Aspose.Words für Java bietet die `FileFormatUtil.detectFileFormat` API.  
- **Kann das Dienstprogramm auch verschlüsselte Dateien verarbeiten?** Ja – das Flag `FileFormatInfo.isEncrypted()` gibt an, ob ein Dokument passwortgeschützt ist.  
- **Benötige ich eine Lizenz für den Produktionseinsatz?** Für den Einsatz außerhalb der Evaluierung ist eine kommerzielle Aspose.Words‑Lizenz erforderlich.  
- **Ist es möglich, Dateien nach der Erkennung automatisch zu verschieben?** Absolut – kombinieren Sie das Erkennungsergebnis mit `FileUtils.copyFile`, um Dateien in benutzerdefinierte Ordner zu sortieren.

## Was ist detect document format java?
`detect document format java` bezieht sich darauf, Java‑Code zu verwenden, um den Binär‑Header einer Datei zu prüfen und zu bestimmen, zu welchem Word‑Verarbeitungsformat sie gehört (z. B. DOC, DOCX, ODT). Aspose.Words liest die Datei, ohne das gesamte Dokument zu laden, wodurch die Operation schnell und speichereffizient ist.

## Warum Dateien nach Format verschieben?
Die Organisation von Dokumenten nach ihrem nativen Format vereinfacht nachgelagerte Prozesse:

- **Batch‑Konvertierungen** werden unkompliziert, wenn alle DOCX‑Dateien in einem Ordner liegen.  
- **Legacy‑Unterstützung**: Sie können vor‑97‑Word‑Dateien für eine spezielle Behandlung isolieren.  
- **Sicherheit**: Verschlüsselte Dokumente können automatisch in Quarantäne verschoben werden.  

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- [Aspose.Words für Java](https://releases.aspose.com/words/java/) (die neueste Version herunterladen)  
- Java Development Kit (JDK) 8 oder höher installiert  
- Grundlegende Kenntnisse in Java I/O und Streams  

## Schritt 1: Verzeichnisse für jedes Format einrichten

Wir erstellen zunächst eine saubere Ordnerstruktur, in die die erkannten Dateien verschoben werden. Das hält den Workflow übersichtlich und erleichtert das Hinzufügen neuer Formatkategorien später.

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

> **Pro Tipp:** Verwenden Sie absolute Pfade oder konfigurieren Sie das Basis‑Verzeichnis über eine Property‑Datei, um das Hard‑Coden von Pfaden im Produktionscode zu vermeiden.

## Schritt 2: Dokumentformat erkennen und Dateien verschieben

Der Kern von **detect document format java** befindet sich in der nachfolgenden Schleife. Sie scannt jede Datei, bestimmt ihren Typ und kopiert sie in den passenden Ordner.

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

Der `switch`‑Block kann erweitert werden, um jedes gewünschte Format abzudecken. Jeder Fall gibt eine freundliche Meldung aus und verschiebt die Datei anschließend in den entsprechenden Ordner.

## Vollständiger Quellcode zum Erkennen des Dokumentformats in Java

Unten finden Sie das vollständige, sofort ausführbare Beispiel, das die Verzeichniserstellung und die Erkennungslogik kombiniert. Kopieren Sie es in eine Java‑Klasse, passen Sie den Basis‑Pfad an und führen Sie es gegen einen Ordner mit gemischten Dokumenten aus.

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

## Häufige Probleme und Fehlerbehebung

| Problem | Warum es passiert | Wie zu beheben |
|---------|-------------------|----------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Die Datei ist beschädigt oder verwendet ein Nicht‑Word‑Format. | Überprüfen Sie die Dateierweiterung oder fügen Sie eine Rückfall‑Logik hinzu, um sie in den *Unknown*‑Ordner zu verschieben (wie im Beispiel bereits enthalten). |
| **Encrypted files throw an exception** | Die API versucht, den Inhalt zu lesen, bevor die Verschlüsselung geprüft wird. | Rufen Sie stets `info.isEncrypted()` auf, bevor Sie andere Operationen am Dokument ausführen. |
| **Directory creation fails on Linux** | Unzureichende Berechtigungen oder fehlender übergeordneter Ordner. | Stellen Sie sicher, dass der Java‑Prozess Schreibrechte hat und dass der Basis‑Pfad existiert. |

## Häufig gestellte Fragen

**Q: Wie installiere ich Aspose.Words für Java?**  
A: Sie können Aspose.Words für Java von [hier](https://releases.aspose.com/words/java/) herunterladen und den dort bereitgestellten Installationsanweisungen folgen.

**Q: Welche Dokumentformate werden für die Erkennung unterstützt?**  
A: Aspose.Words kann DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML und ältere vor‑97‑Formate sowie weitere Formate erkennen.

**Q: Kann dieser Code passwortgeschützte Dokumente verarbeiten?**  
A: Ja. Das Flag `FileFormatInfo.isEncrypted()` identifiziert verschlüsselte Dateien, sodass Sie sie in einen sicheren Ordner verschieben können, ohne sie zu öffnen.

**Q: Gibt es Auswirkungen auf die Leistung beim Scannen großer Ordner?**  
A: Die Erkennung liest nur den Dateikopf, sodass selbst Tausende von Dateien schnell verarbeitet werden. Für sehr große Stapel sollten Sie parallele Streams in Betracht ziehen.

**Q: Wie kann ich das Skript erweitern, um nicht unterstützte Formate zu konvertieren?**  
A: Nach der Erkennung können Sie `Document.save` mit dem gewünschten Ausgabeformat für jeden unterstützten Quelltyp aufrufen.

## Fazit

Durch die Verwendung von **detect document format java** mit Aspose.Words erhalten Sie eine zuverlässige Methode, Word‑bezogene Dateien automatisch zu sortieren, zu quarantänisieren oder zu konvertieren. Der Beispielcode zeigt, wie Sie eine saubere Ordnerhierarchie erstellen, das Format jeder Datei identifizieren und sie entsprechend verschieben – wodurch Sie Zeit sparen und manuelle Fehler reduzieren.

---

**Zuletzt aktualisiert:** 2026-02-22  
**Getestet mit:** Aspose.Words für Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}