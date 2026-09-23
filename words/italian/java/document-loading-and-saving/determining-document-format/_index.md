---
date: 2026-02-22
description: Scopri come rilevare il formato dei documenti Java con Aspose.Words e
  spostare automaticamente i file in base al formato. Identifica DOC, DOCX e molto
  altro.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Rileva il formato del documento Java usando Aspose.Words per Java
url: /it/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# rilevare il formato del documento java usando Aspose.Words per Java

Quando hai bisogno di **detect document format java** in un batch di file, la possibilità di ordinarli automaticamente nelle cartelle corrette può far risparmiare ore di lavoro manuale. In questo tutorial ti mostreremo come Aspose.Words per Java renda semplice identificare Word, RTF, HTML, ODT e molti altri formati, e poi **move files by format** in directory organizzate.

## Risposte rapide
- **Cosa significa “detect document format java”?** È il processo di identificare programmaticamente il formato di elaborazione testi di un file (DOC, DOCX, RTF, ecc.) usando codice Java.  
- **Quale libreria fornisce questa funzionalità?** Aspose.Words per Java offre l'API `FileFormatUtil.detectFileFormat`.  
- **La utility può gestire anche file crittografati?** Sì – il flag `FileFormatInfo.isEncrypted()` indica se un documento è protetto da password.  
- **È necessaria una licenza per l'uso in produzione?** È richiesta una licenza commerciale di Aspose.Words per le distribuzioni non‑valutazione.  
- **È possibile spostare i file automaticamente dopo la rilevazione?** Assolutamente – combina il risultato della rilevazione con `FileUtils.copyFile` per ordinare i file in cartelle personalizzate.

## Cos'è detect document format java?
`detect document format java` si riferisce all'uso di codice Java per ispezionare l'intestazione binaria di un file e determinare a quale formato di elaborazione testi appartiene (ad es., DOC, DOCX, ODT). Aspose.Words legge il file senza caricare completamente il documento, rendendo l'operazione veloce ed efficiente in termini di memoria.

## Perché spostare i file per formato?
Organizzare i documenti per il loro formato nativo semplifica l'elaborazione a valle:

- **Conversioni batch** diventano semplici quando tutti i file DOCX si trovano in una cartella.  
- **Supporto legacy**: puoi isolare i file Word pre‑97 per una gestione speciale.  
- **Sicurezza**: i documenti crittografati possono essere messi in quarantena automaticamente.  

## Prerequisiti

Prima di iniziare, assicurati di avere:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (scarica l'ultima versione)  
- Java Development Kit (JDK) 8 o superiore installato  
- Familiarità di base con Java I/O e stream  

## Passo 1: Configura le directory per ogni formato

Creiamo innanzitutto una struttura di cartelle pulita dove i file rilevati saranno spostati. Questo mantiene il flusso di lavoro ordinato e rende più semplice aggiungere nuove categorie di formato in seguito.

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

> **Consiglio professionale:** Usa percorsi assoluti o configura la directory base tramite un file di proprietà per evitare di codificare percorsi in modo rigido nel codice di produzione.

## Passo 2: Rileva il formato del documento e sposta i file

Il cuore di **detect document format java** si trova nel ciclo qui sotto. Scansiona ogni file, ne determina il tipo e lo copia nella cartella appropriata.

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

Il blocco `switch` può essere ampliato per coprire tutti i formati di tuo interesse. Ogni caso stampa un messaggio informativo e poi sposta il file nella cartella corrispondente.

## Codice sorgente completo per rilevare il formato del documento java

Di seguito trovi l'esempio completo, pronto per l'esecuzione, che combina la configurazione delle directory e la logica di rilevazione. Copialo in una classe Java, regola il percorso base e eseguilo su una cartella di documenti misti.

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

## Problemi comuni e risoluzione

| Problema | Perché accade | Come risolvere |
|----------|----------------|----------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Il file è corrotto o utilizza un formato non‑Word. | Verifica l'estensione del file, oppure aggiungi un fallback per spostarlo nella cartella *Unknown* (già presente nel campione). |
| **Encrypted files throw an exception** | L'API tenta di leggere il contenuto prima di verificare la crittografia. | Chiama sempre `info.isEncrypted()` prima di qualsiasi altra operazione sul documento. |
| **Directory creation fails on Linux** | Permessi insufficienti o cartella genitore mancante. | Assicurati che il processo Java abbia i permessi di scrittura e che il percorso base esista. |

## Domande frequenti

**Q: Come installo Aspose.Words per Java?**  
**A:** Puoi scaricare Aspose.Words per Java da [qui](https://releases.aspose.com/words/java/) e seguire le istruzioni di installazione fornite.

**Q: Quali formati di documento sono supportati per la rilevazione?**  
**A:** Aspose.Words può rilevare DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML e formati più vecchi pre‑97, tra gli altri.

**Q: Questo codice può gestire documenti protetti da password?**  
**A:** Sì. Il flag `FileFormatInfo.isEncrypted()` identifica i file crittografati, consentendoti di spostarli in una cartella sicura senza aprirli.

**Q: C'è un impatto sulle prestazioni durante la scansione di cartelle grandi?**  
**A:** La rilevazione legge solo l'intestazione del file, quindi anche migliaia di file vengono processati rapidamente. Per batch molto grandi, considera l'uso di stream paralleli.

**Q: Come posso estendere lo script per convertire formati non supportati?**  
**A:** Dopo la rilevazione, puoi chiamare `Document.save` con il formato di output desiderato per qualsiasi tipo di sorgente supportato.

## Conclusione

Utilizzando **detect document format java** con Aspose.Words, ottieni un metodo affidabile per ordinare automaticamente, mettere in quarantena o convertire file correlati a Word. Il codice di esempio dimostra come creare una gerarchia di cartelle pulita, identificare il formato di ciascun file e spostarlo di conseguenza—facendoti risparmiare tempo e riducendo gli errori manuali.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}