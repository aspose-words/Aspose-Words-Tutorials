---
title: Creazione e firma di una nuova riga di firma
linktitle: Creazione e firma di una nuova riga di firma
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come creare e firmare digitalmente una riga di firma in un documento Word usando Aspose.Words per .NET con questo tutorial passo dopo passo. Perfetto per l'automazione dei documenti.
weight: 10
url: /it/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creazione e firma di una nuova riga di firma

## Introduzione

Ciao! Quindi, hai un documento Word e devi aggiungere una riga di firma e poi firmarlo digitalmente. Sembra complicato? Niente affatto! Grazie ad Aspose.Words per .NET, puoi ottenere questo risultato senza problemi con solo poche righe di codice. In questo tutorial, ti guideremo attraverso l'intero processo, dalla configurazione del tuo ambiente al salvataggio del tuo documento con una nuova firma brillante. Pronti? Tuffiamoci!

## Prerequisiti

Prima di passare al codice, assicuriamoci di avere tutto ciò di cui hai bisogno:
1.  Aspose.Words per .NET - Puoi[scaricalo qui](https://releases.aspose.com/words/net/).
2. Un ambiente di sviluppo .NET: Visual Studio è altamente consigliato.
3. Un documento da firmare: crea un semplice documento Word o utilizzane uno esistente.
4.  Un file di certificato: è necessario per le firme digitali. Puoi usare un`.pfx` file.
5. Immagini per la riga della firma: facoltativamente, un file immagine per la firma.

## Importazione degli spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari. Questo passaggio è cruciale in quanto imposta l'ambiente per l'utilizzo delle funzionalità di Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Passaggio 1: impostazione della directory dei documenti

Ogni progetto ha bisogno di un buon inizio. Impostiamo il percorso per la directory dei tuoi documenti. È qui che i tuoi documenti verranno salvati e recuperati.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: creazione di un nuovo documento

Ora, creiamo un nuovo documento Word usando Aspose.Words. Questa sarà la nostra tela dove aggiungeremo la riga della firma.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Fase 3: Inserimento della riga della firma

 Qui è dove avviene la magia. Inseriamo una riga di firma nel nostro documento utilizzando`DocumentBuilder` classe.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Fase 4: Salvataggio del documento con la riga della firma

Una volta che la riga della firma è a posto, dobbiamo salvare il documento. Questo è un passaggio intermedio prima di procedere alla firma.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Passaggio 5: Impostazione delle opzioni di firma

Ora, impostiamo le opzioni per la firma del documento. Ciò include la specifica dell'ID della riga della firma e dell'immagine da utilizzare.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Fase 6: Caricamento del certificato

Le firme digitali richiedono un certificato. Qui, carichiamo il file del certificato che verrà utilizzato per firmare il documento.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Fase 7: Firma del documento

 Questo è il passaggio finale. Utilizziamo il`DigitalSignatureUtil`classe per firmare il documento. Il documento firmato viene salvato con un nuovo nome.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusione

Ed ecco fatto! Con questi passaggi, hai creato con successo un nuovo documento Word, aggiunto una riga di firma e firmato digitalmente usando Aspose.Words per .NET. È uno strumento potente che rende l'automazione dei documenti un gioco da ragazzi. Che tu abbia a che fare con contratti, accordi o documenti formali, questo metodo garantisce che siano firmati e autenticati in modo sicuro.

## Domande frequenti

### Posso utilizzare altri formati di immagine per la riga della firma?
Sì, puoi utilizzare vari formati di immagine come PNG, JPG, BMP, ecc.

###  È necessario utilizzare un`.pfx` file for the certificate?
 Sì, un`.pfx` file è un formato comune per l'archiviazione di informazioni crittografiche, tra cui certificati e chiavi private.

### Posso aggiungere più righe di firma in un singolo documento?
Assolutamente! Puoi inserire più righe di firma ripetendo il passaggio di inserimento per ogni firma.

### Cosa succede se non ho un certificato digitale?
Dovrai ottenere un certificato digitale da un'autorità di certificazione attendibile o generarne uno utilizzando strumenti come OpenSSL.

### Come posso verificare la firma digitale nel documento?
È possibile aprire il documento firmato in Word e andare ai dettagli della firma per verificarne l'autenticità e l'integrità.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
