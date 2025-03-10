---
title: Determinazione del formato del documento in Aspose.Words per Java
linktitle: Determinazione del formato del documento
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come rilevare i formati di documento in Java con Aspose.Words. Identifica DOC, DOCX e altro. Organizza i file in modo efficiente.
weight: 25
url: /it/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Determinazione del formato del documento in Aspose.Words per Java


## Introduzione alla determinazione del formato del documento in Aspose.Words per Java

Quando si lavora con l'elaborazione di documenti in Java, è fondamentale determinare il formato dei file con cui si ha a che fare. Aspose.Words per Java fornisce potenti funzionalità per identificare i formati dei documenti e vi guideremo attraverso il processo.

## Prerequisiti

Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:

- [Aspose.Words per Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) installato sul tuo sistema
- Conoscenza di base della programmazione Java

## Passaggio 1: impostazione della directory

Per prima cosa, dobbiamo impostare le directory necessarie per organizzare i nostri file in modo efficace. Creeremo directory per diversi tipi di documenti.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Creare le directory se non esistono già.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Abbiamo creato directory per i tipi di documenti supportati, sconosciuti, crittografati e precedenti al 97.

## Fase 2: Rilevamento del formato del documento

Ora, rileviamo il formato dei documenti nelle nostre directory. Per farlo, useremo Aspose.Words per Java.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Visualizza il tipo di documento
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Aggiungere casi per altri formati di documenti, se necessario
    }

    // Gestire documenti crittografati
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Gestire altri tipi di documenti
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

In questo frammento di codice, esaminiamo i file, ne rileviamo i formati e li organizziamo nelle rispettive directory.

## Codice sorgente completo per determinare il formato del documento in Aspose.Words per Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Creare le directory se non esistono già.
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
            // Visualizza il tipo di documento
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

## Conclusione

Determinare i formati dei documenti in Aspose.Words per Java è essenziale per un'elaborazione efficiente dei documenti. Con i passaggi descritti in questa guida, puoi identificare i tipi di documenti e gestirli di conseguenza nelle tue applicazioni Java.

## Domande frequenti

### Come faccio a installare Aspose.Words per Java?

 Puoi scaricare Aspose.Words per Java da[Qui](https://releases.aspose.com/words/java/) seguire le istruzioni di installazione fornite.

### Quali sono i formati di documento supportati?

Aspose.Words for Java supporta vari formati di documento, tra cui DOC, DOCX, RTF, HTML e altri. Puoi fare riferimento alla documentazione per un elenco completo.

### Come posso rilevare documenti crittografati utilizzando Aspose.Words per Java?

 Puoi usare il`FileFormatUtil.detectFileFormat()` metodo per rilevare documenti crittografati, come illustrato in questa guida.

### Ci sono delle limitazioni quando si lavora con formati di documenti più vecchi?

I formati di documento più vecchi, come MS Word 6 o Word 95, potrebbero avere limitazioni in termini di funzionalità e compatibilità con le applicazioni moderne. Considerare l'aggiornamento o la conversione di questi documenti quando necessario.

### Posso automatizzare il rilevamento del formato dei documenti nella mia applicazione Java?

Sì, puoi automatizzare il rilevamento del formato del documento integrando il codice fornito nella tua applicazione Java. Ciò ti consente di elaborare i documenti in base ai formati rilevati.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
