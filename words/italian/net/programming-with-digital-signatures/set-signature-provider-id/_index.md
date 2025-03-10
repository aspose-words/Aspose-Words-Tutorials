---
title: Imposta l'ID del fornitore della firma nel documento Word
linktitle: Imposta l'ID del fornitore della firma nel documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Imposta in modo sicuro un ID fornitore di firma nei documenti Word usando Aspose.Words per .NET. Segui la nostra guida dettagliata di 2000 parole per firmare digitalmente i tuoi documenti.
weight: 10
url: /it/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta l'ID del fornitore della firma nel documento Word

## Introduzione

Ciao! Quindi, hai questo fantastico documento Word che necessita di una firma digitale, giusto? Ma non una firma qualsiasi: devi impostare uno specifico ID del fornitore di firme. Che tu stia gestendo documenti legali, contratti o qualsiasi altra documentazione, aggiungere una firma digitale sicura è fondamentale. In questo tutorial, ti guiderò attraverso l'intero processo di impostazione di un ID del fornitore di firme in un documento Word utilizzando Aspose.Words per .NET. Pronti? Cominciamo!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. Aspose.Words per la libreria .NET: se non lo hai già fatto,[scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: Visual Studio o qualsiasi IDE compatibile con C#.
3. Documento Word: un documento con una riga per la firma (`Signature line.docx`).
4.  Certificato digitale: A`.pfx` file del certificato (ad esempio,`morzal.pfx`).
5. Conoscenza di base di C#: solo le basi, non preoccuparti, siamo qui per aiutarti!

Ora passiamo all'azione!

## Importazione degli spazi dei nomi

Prima di tutto, assicurati di includere i namespace necessari nel tuo progetto. Questo è essenziale per accedere alla libreria Aspose.Words e alle classi correlate.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

Bene, scomponiamolo in passaggi semplici e digeribili.

## Passaggio 1: carica il documento Word

Il primo passo è caricare il documento Word che contiene la riga della firma. Questo documento verrà modificato per includere la firma digitale con l'ID del fornitore di firma specificato.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 Qui specifichiamo la directory in cui si trova il tuo documento. Sostituisci`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo del tuo documento.

## Passaggio 2: accedi alla riga della firma

Successivamente, dobbiamo accedere alla riga della firma all'interno del documento. La riga della firma è incorporata come oggetto forma nel documento Word.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 Questa riga di codice ottiene la prima forma nel corpo della prima sezione del documento e la converte in una`SignatureLine` oggetto.

## Passaggio 3: Imposta le opzioni di firma

Ora creiamo le opzioni di firma, che includono l'ID del fornitore e l'ID della riga di firma dalla riga di firma a cui si è avuto accesso.

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

Queste opzioni verranno utilizzate durante la firma del documento per garantire che sia impostato il corretto ID del fornitore della firma.

## Passaggio 4: caricare il certificato

 Per firmare il documento digitalmente, hai bisogno di un certificato. Ecco come caricare il tuo`.pfx` file:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Sostituire`"aw"` con la password per il file del certificato, se presente.

## Fase 5: Firmare il documento

 Infine, è il momento di firmare il documento utilizzando il`DigitalSignatureUtil.Sign` metodo.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 Questo firma il tuo documento e lo salva come un nuovo file,`Digitally signed.docx`.

## Conclusione

Ed ecco fatto! Hai impostato con successo un ID fornitore di firma in un documento Word utilizzando Aspose.Words per .NET. Questo processo non solo protegge i tuoi documenti, ma assicura anche che siano conformi agli standard di firma digitale. Ora, vai avanti e provalo con i tuoi documenti. Hai domande? Dai un'occhiata alle FAQ qui sotto o vai su[Forum di supporto Aspose](https://forum.aspose.com/c/words/8).

## Domande frequenti

### Che cos'è un Signature Provider ID?

Un Signature Provider ID identifica in modo univoco il fornitore della firma digitale, garantendone autenticità e sicurezza.

### Posso usare qualsiasi file .pfx per la firma?

Sì, purché sia un certificato digitale valido. Assicurati di avere la password corretta se è protetto.

### Come posso ottenere un file .pfx?

È possibile ottenere un file .pfx da un'autorità di certificazione (CA) o generarne uno utilizzando strumenti come OpenSSL.

### Posso firmare più documenti contemporaneamente?

Sì, è possibile scorrere più documenti e applicare a ciascuno di essi lo stesso processo di firma.

### Cosa succede se nel mio documento non è presente una riga per la firma?

Per prima cosa, dovrai inserire una riga di firma. Aspose.Words fornisce metodi per aggiungere righe di firma a livello di programmazione.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
