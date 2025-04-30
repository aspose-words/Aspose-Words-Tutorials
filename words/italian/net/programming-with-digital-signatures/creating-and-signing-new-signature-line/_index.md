---
"description": "Scopri come creare e firmare digitalmente una riga di firma in un documento Word utilizzando Aspose.Words per .NET con questo tutorial passo passo. Perfetto per l'automazione dei documenti."
"linktitle": "Creazione e firma di una nuova riga di firma"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Creazione e firma di una nuova riga di firma"
"url": "/it/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Creazione e firma di una nuova riga di firma

## Introduzione

Ciao! Hai un documento Word e devi aggiungere una riga per la firma e poi firmarlo digitalmente. Sembra complicato? Assolutamente no! Grazie ad Aspose.Words per .NET, puoi farlo senza problemi con poche righe di codice. In questo tutorial, ti guideremo attraverso l'intero processo, dalla configurazione dell'ambiente al salvataggio del documento con una nuova firma. Pronto? Iniziamo!

## Prerequisiti

Prima di passare al codice, assicuriamoci di avere tutto il necessario:
1. Aspose.Words per .NET - Puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. Un ambiente di sviluppo .NET: Visual Studio è altamente consigliato.
3. Un documento da firmare: crea un semplice documento Word o usane uno esistente.
4. Un file di certificato: necessario per le firme digitali. È possibile utilizzare un `.pfx` file.
5. Immagini per la riga della firma: facoltativamente, un file immagine per la firma.

## Importa spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari. Questo passaggio è fondamentale perché configura l'ambiente per l'utilizzo delle funzionalità di Aspose.Words.

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

Ora creiamo un nuovo documento Word usando Aspose.Words. Questo sarà il nostro canvas su cui aggiungeremo la riga della firma.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 3: inserimento della riga della firma

È qui che avviene la magia. Inseriamo una riga per la firma nel nostro documento utilizzando `DocumentBuilder` classe.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Passaggio 4: salvataggio del documento con la riga della firma

Una volta posizionata la riga per la firma, dobbiamo salvare il documento. Questo è un passaggio intermedio prima di procedere alla firma.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Passaggio 5: impostazione delle opzioni di firma

Ora impostiamo le opzioni per la firma del documento. Questo include la specifica dell'ID della riga della firma e dell'immagine da utilizzare.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Fase 6: Caricamento del certificato

Le firme digitali richiedono un certificato. Qui carichiamo il file del certificato che verrà utilizzato per firmare il documento.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Fase 7: Firma del documento

Questo è il passaggio finale. Utilizziamo il `DigitalSignatureUtil` classe per firmare il documento. Il documento firmato viene salvato con un nuovo nome.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusione

Ed ecco fatto! Con questi passaggi, hai creato con successo un nuovo documento Word, aggiunto una riga per la firma e firmato digitalmente utilizzando Aspose.Words per .NET. È uno strumento potente che semplifica l'automazione dei documenti. Che si tratti di contratti, accordi o documenti formali, questo metodo garantisce che siano firmati e autenticati in modo sicuro.

## Domande frequenti

### Posso utilizzare altri formati immagine per la riga della firma?
Sì, puoi usare vari formati immagine come PNG, JPG, BMP, ecc.

### È necessario utilizzare un `.pfx` presentare domanda per il certificato?
Sì, un `.pfx` file è un formato comune per l'archiviazione di informazioni crittografiche, tra cui certificati e chiavi private.

### Posso aggiungere più righe di firma in un singolo documento?
Assolutamente! Puoi inserire più righe di firma ripetendo il passaggio per ogni firma.

### Cosa succede se non ho un certificato digitale?
Dovrai ottenere un certificato digitale da un'autorità di certificazione attendibile o generarne uno utilizzando strumenti come OpenSSL.

### Come posso verificare la firma digitale nel documento?
È possibile aprire il documento firmato in Word e andare ai dettagli della firma per verificarne l'autenticità e l'integrità.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}