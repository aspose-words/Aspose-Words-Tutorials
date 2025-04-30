---
"description": "Scopri come rilevare i formati di file dei documenti utilizzando Aspose.Words per .NET con questa guida completa e dettagliata."
"linktitle": "Rileva il formato del file del documento"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Rileva il formato del file del documento"
"url": "/it/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rileva il formato del file del documento

## Introduzione

Nel mondo digitale odierno, gestire in modo efficiente i diversi formati di documento è fondamentale. Che si tratti di Word, PDF, HTML o altri formati, essere in grado di rilevare ed elaborare correttamente questi file può far risparmiare molto tempo e fatica. In questo tutorial, esploreremo come rilevare i formati di file di documento utilizzando Aspose.Words per .NET. Questa guida ti illustrerà tutto ciò che devi sapere, dai prerequisiti a una guida dettagliata passo passo.

## Prerequisiti

Prima di immergerci nel codice, assicuriamoci di avere tutto il necessario:

- Aspose.Words per .NET: puoi scaricarlo da [Qui](https://releases.aspose.com/words/net/)Assicurati di avere una licenza valida. In caso contrario, puoi ottenerne una [licenza temporanea](https://purchase.aspose.com/temporary-license/).
- Visual Studio: qualsiasi versione recente funzionerà correttamente.
- .NET Framework: assicurati di aver installato la versione corretta.

## Importa spazi dei nomi

Per iniziare, dovrai importare gli spazi dei nomi necessari nel tuo progetto:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Per semplificare la comprensione, scomponiamo l'esempio in più passaggi.

## Passaggio 1: impostare le directory

Per prima cosa dobbiamo impostare le directory in cui i file verranno ordinati in base al loro formato.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Creare le directory se non esistono già.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Passaggio 2: ottenere l'elenco dei file

Successivamente, otterremo un elenco dei file dalla directory, escludendo i documenti danneggiati.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Passaggio 3: Rileva i formati dei file

Ora, esaminiamo ogni file e ne rileviamo il formato utilizzando Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Visualizza il tipo di documento
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Conclusione

Rilevare i formati dei file di documento utilizzando Aspose.Words per .NET è un processo semplice. Impostando le directory, ottenendo l'elenco dei file e utilizzando Aspose.Words per rilevare i formati, è possibile organizzare e gestire i documenti in modo efficiente. Questo approccio non solo fa risparmiare tempo, ma garantisce anche la corretta gestione di diversi formati di documento.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per lavorare con i documenti Word a livello di programmazione. Consente agli sviluppatori di creare, modificare e convertire documenti in vari formati.

### Aspose.Words può rilevare documenti crittografati?
Sì, Aspose.Words è in grado di rilevare se un documento è crittografato e di gestirlo di conseguenza.

### Quali formati può rilevare Aspose.Words?
Aspose.Words è in grado di rilevare un'ampia gamma di formati, tra cui DOC, DOCX, RTF, HTML, MHTML, ODT e molti altri.

### Come posso ottenere una licenza temporanea per Aspose.Words?
Puoi ottenere una licenza temporanea dal [Acquisto Aspose](https://purchase.aspose.com/temporary-license/) pagina.

### Dove posso trovare la documentazione per Aspose.Words?
La documentazione per Aspose.Words può essere trovata [Qui](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}