---
title: Inserisci oggetto Ole in Word con pacchetto Ole
linktitle: Inserisci oggetto Ole in Word con pacchetto Ole
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come inserire oggetti OLE nei documenti Word usando Aspose.Words per .NET. Segui la nostra guida dettagliata passo dopo passo per incorporare i file senza problemi.
weight: 10
url: /it/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci oggetto Ole in Word con pacchetto Ole

## Introduzione

Se hai mai voluto incorporare un file in un documento Word, sei nel posto giusto. Che si tratti di un file ZIP, un foglio Excel o qualsiasi altro tipo di file, incorporarlo direttamente nel tuo documento Word può essere incredibilmente utile. Immagina di avere uno scomparto segreto nel tuo documento in cui puoi nascondere ogni sorta di tesoro. E oggi, ti spiegheremo come farlo usando Aspose.Words per .NET. Pronti a diventare un mago di Word? Immergiamoci!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. Aspose.Words per .NET: se non lo hai ancora fatto, scaricalo da[Qui](https://releases.aspose.com/words/net/).
2. Un ambiente di sviluppo: Visual Studio o qualsiasi altro ambiente di sviluppo .NET.
3. Nozioni di base di C#: non è necessario essere esperti, ma conoscere C# può essere utile.
4. Directory dei documenti: una cartella in cui è possibile archiviare e recuperare documenti.

## Importazione degli spazi dei nomi

Prima di tutto, mettiamo in ordine i nostri namespace. Devi includere i seguenti namespace nel tuo progetto:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Proviamo a suddividerlo in piccoli passaggi, così sarà più facile seguirlo.

## Passaggio 1: imposta il tuo documento

Immagina di essere un artista con una tela bianca. Per prima cosa, abbiamo bisogno della nostra tela bianca, che è il nostro documento Word. Ecco come impostarla:

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Questo codice inizializza un nuovo documento Word e imposta un DocumentBuilder, che utilizzeremo per inserire contenuti nel nostro documento.

## Passaggio 2: leggi il tuo vecchio oggetto

Ora leggiamo il file che vuoi incorporare. Immagina di raccogliere il tesoro che vuoi nascondere nel tuo scomparto segreto:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Questa riga legge tutti i byte dal file ZIP e li memorizza in un array di byte.

## Passaggio 3: Inserisci l'oggetto Ole

Ora arriva la parte magica. Incorporeremo il file nel nostro documento Word:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Qui, creiamo un flusso di memoria dall'array di byte e utilizziamo il`InsertOleObject` per incorporarlo nel documento. Impostiamo anche il nome del file e il nome visualizzato per l'oggetto incorporato.

## Passaggio 4: salva il documento

Infine, salviamo il nostro capolavoro:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

In questo modo il documento con il file incorporato viene salvato nella directory specificata.

## Conclusione

Ed ecco fatto! Hai incorporato con successo un oggetto OLE in un documento Word usando Aspose.Words per .NET. È come aggiungere una gemma nascosta all'interno del tuo documento che può essere svelata in qualsiasi momento. Questa tecnica può essere incredibilmente utile per una varietà di applicazioni, dalla documentazione tecnica ai report dinamici. 

## Domande frequenti

### Posso incorporare altri tipi di file utilizzando questo metodo?
Sì, puoi incorporare vari tipi di file, come fogli Excel, PDF e immagini.

### Ho bisogno di una licenza per Aspose.Words?
 Sì, hai bisogno di una licenza valida. Puoi ottenere una[licenza temporanea](https://purchase.aspose.com/temporary-license/) per la valutazione.

### Come posso personalizzare il nome visualizzato dell'oggetto OLE?
 Puoi impostare il`DisplayName` proprietà del`OlePackage` per personalizzarlo.

### Aspose.Words è compatibile con .NET Core?
Sì, Aspose.Words supporta sia .NET Framework che .NET Core.

### Posso modificare l'oggetto OLE incorporato nel documento Word?
No, non puoi modificare l'oggetto OLE direttamente in Word. Devi aprirlo nella sua applicazione nativa.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
