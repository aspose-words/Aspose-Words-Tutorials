---
date: 2025-12-20
description: Scopri come organizzare i file per tipo e rilevare i formati dei documenti
  in Java con Aspose.Words. Supporta DOC, DOCX, RTF e altri.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organizza i file per tipo usando Aspose.Words per Java
url: /it/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organizza i file per tipo usando Aspose.Words per Java

Quando è necessario **organizzare i file per tipo** in un'applicazione Java, il primo passo è determinare in modo affidabile il formato di ciascun documento. Aspose.Words per Java rende questo processo semplice, consentendo di rilevare DOC, DOCX, RTF, HTML, ODT e molti altri formati – anche file crittografati o sconosciuti. In questa guida vedremo come impostare le cartelle, rilevare i formati dei file e ordinare automaticamente i tuoi file.

## Risposte rapide
- **Cosa significa “organizzare i file per tipo”?** Significa spostare automaticamente i documenti in cartelle in base al loro formato rilevato (ad es., DOCX, PDF, RTF).  
- **Quale libreria aiuta a rilevare il formato del file in Java?** Aspose.Words per Java fornisce `FileFormatUtil.detectFileFormat()`.  
- **L'API può identificare tipi di file sconosciuti?** Sì – restituisce `LoadFormat.UNKNOWN` per file non supportati o non riconoscibili.  
- **È supportata la rilevazione di documenti crittografati?** Assolutamente; il flag `FileFormatInfo.isEncrypted()` indica se un file è protetto da password.  
- **È necessaria una licenza per l'uso in produzione?** È richiesta una licenza valida di Aspose.Words per le distribuzioni commerciali.

## Introduzione: Organizza i file per tipo con Aspose.Words per Java

Quando si lavora con l'elaborazione di documenti in Java, è fondamentale determinare il formato dei file che si gestiscono. Aspose.Words per Java offre funzionalità potenti per **detect file format java**, e ti guideremo attraverso il processo di organizzazione efficiente dei tuoi file.

## Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

- [Aspose.Words per Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) installato sul tuo sistema
- Conoscenze di base della programmazione Java

## Passo 1: Configurazione delle directory

Per prima cosa, dobbiamo creare le directory necessarie per organizzare i file in modo efficace. Creeremo cartelle per i diversi tipi di documento.

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

Abbiamo creato directory per i tipi supportati, sconosciuti, crittografati e pre‑97.

## Passo 2: Rilevamento del formato del documento

Ora, rileviamo il formato dei documenti nelle nostre directory. Useremo Aspose.Words per Java per ottenere questo risultato.

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

In questo snippet iteriamo sui file, **detect file format java**, e li organizziamo nelle cartelle appropriate.

## Codice sorgente completo per determinare il formato del documento in Aspose.Words per Java

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

## Come rilevare il formato del file in Java

Il metodo `FileFormatUtil.detectFileFormat()` analizza l'intestazione del file e restituisce un oggetto `FileFormatInfo`. Questo oggetto indica il **load format**, se il file è crittografato e altre informazioni utili. Utilizzando queste informazioni è possibile **identify unknown file types** in modo programmatico e decidere come processare ciascuno di essi.

## Identifica i tipi di file sconosciuti

Quando l'API restituisce `LoadFormat.UNKNOWN`, il file è corrotto o utilizza un formato non supportato da Aspose.Words. Nel nostro esempio di codice spostiamo questi file nella cartella **Unknown** così da poterli esaminare in seguito.

## Problemi comuni e soluzioni

| Problema | Motivo | Soluzione |
|----------|--------|-----------|
| I file vengono sempre collocati nella cartella *Supported* | `FileFormatUtil` non riesce a leggere l'intestazione (ad es., file vuoto) | Assicurati di passare il percorso corretto del file e che il file non sia di dimensione zero. |
| I file crittografati generano un'eccezione | Tentativo di lettura senza gestire la crittografia | Usa il controllo `info.isEncrypted()` prima di ulteriori elaborazioni, come mostrato nel codice. |
| I documenti Word pre‑97 non vengono rilevati | I formati più vecchi richiedono il caso `DOC_PRE_WORD_60` | Mantieni il blocco `case LoadFormat.DOC_PRE_WORD_60` per instradarli nella cartella *Pre97*. |

## Domande frequenti

### Come installo Aspose.Words per Java?

Puoi scaricare Aspose.Words per Java dal [qui](https://releases.aspose.com/words/java/) e seguire le istruzioni di installazione fornite.

### Quali sono i formati di documento supportati?

Aspose.Words per Java supporta vari formati di documento, tra cui DOC, DOCX, RTF, HTML, ODT e molti altri. Consulta la documentazione ufficiale per l'elenco completo.

### Come posso rilevare i documenti crittografati usando Aspose.Words per Java?

Utilizza il metodo `FileFormatUtil.detectFileFormat()`; il flag `FileFormatInfo.isEncrypted()` restituito indica la crittografia, come dimostrato in questa guida.

### Ci sono limitazioni quando si lavora con formati di documento più vecchi?

I formati più vecchi, come MS Word 6 o Word 95, potrebbero non includere funzionalità moderne e presentare problemi di compatibilità. Considera la conversione in formati più recenti quando possibile.

### Posso automatizzare il rilevamento del formato del documento nella mia applicazione Java?

Sì, inserisci il codice fornito nel flusso di elaborazione della tua applicazione. Questo abilita l'ordinamento e la gestione automatici in base ai formati rilevati.

---

**Ultimo aggiornamento:** 2025-12-20  
**Testato con:** Aspose.Words per Java 24.12 (latest)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}